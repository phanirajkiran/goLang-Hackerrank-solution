# goLang-Hackerrank-solution
goLang-Hackerrank-solution for String Operations Modify String. 1. "Trim starting and ending spaces" 2. "Remove digits from the string" 3. Reverse of a string

Quick Solution in golang

package main

import (
    "bufio"
    "fmt"
    "io"
    "strings"
    "regexp"
    "log"
)



/*
 * Complete the 'ModifyString' function below and add imports if needed.
 *
 * The function is expected to return a STRING.
 * The function accepts STRING str as parameter.
 */
func reverse(s string) string {
    rns := []rune(s) // convert to rune
    for i, j := 0, len(rns)-1; i < j; i, j = i+1, j-1 {
  
        // swap the letters of the string,
        // like first with last and so on.
        rns[i], rns[j] = rns[j], rns[i]
    }
  
    // return the reversed string.
    return string(rns)
}


func ModifyString(str string) string {

    res1:=strings.TrimSpace(str)
    reg, err := regexp.Compile("[^a-zA-Z]+")
    if err != nil {
        log.Fatal(err)
    }
    processedString := reg.ReplaceAllString(res1, "")
   
    strRev := reverse(processedString)
    
    return strRev
}



func main() {
    str:= "  098ol678l8675765e768H667  "
    result := ModifyString(str)

    fmt.Println(result)

   
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
