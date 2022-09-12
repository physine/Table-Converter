# Table-Converter
This C# program converts tables between the following formats: md, json, html and csv


![cmd_hlep](https://user-images.githubusercontent.com/18222860/98047890-a2910100-1e24-11eb-9b01-2fff6006b21a.png)

/*

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

This program was developed and tested in VS Code (Version 1.50.1) on Windows 10 and works.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

This program is fully functional.
It converts any of the four formats (".html", ".json", ".csv", ".md") to any other format.

Though I tried compiling it via csc and got the following (just so your awair):

Program.cs(40,7): error CS0246: The type or namespace name 'HtmlAgilityPack' could not be found (are you missing a using directive or an assembly reference?)
Program.cs(41,19): error CS0234: The type or namespace name 'Json' does not exist in the namespace 'System.Text' (are you missing an assembly reference?)
Program.cs(43,7): error CS0246: The type or namespace name 'Newtonsoft' could not be found (are you missing a using directive or an assembly reference?) 
Program.cs(77,61): error CS0246: The type or namespace name 'JsonDocument' could not be found (are you missing a using directive or an assembly reference?) 
Program.cs(126,61): error CS0246: The type or namespace name 'HtmlDocument' could not be found (are you missing a using directive or an assembly reference?)

If run with dotnet run it will work just fine.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

To run the program enter:

    enter "dotnet run"

    from within the \tabconv folder

The output file will appear in the \tabconv folder.



How this program is designed

The input file format is convertect to as list of lists of type string.  This is known as the rawData.
This is to pervent having to convert from every file format to every other file format.

To convert to rawData with one the following methods:

        public static List<List<String>> getRawDataFromJson(JsonDocument doc)
        public static List<List<String>> getRawDataFromCsv(String fileContent)
        public static List<List<String>> getRawDataFromHtml(HtmlDocument doc)
        public static List<List<String>> getRawDataFromMd(String fileContent)

Then once rawData is set, one of the following metheds are use to format rawDate to the desired output format:

        public static String getJsonFromRawData(List<List<String>> rawData)
        public static String getCsvFromRawData(List<List<String>> rawData)
        public static String getHtmlFromRawData(List<List<String>> rawData)
        public static String getMdFromRawData(List<List<String>> rawData)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

Test input and output files:

In the \tabconv folder you may have noticed extra file, these files contain test data I used to make sure my code works as it should, feel free to use them as you wish :) though I can imagine you have your own.

Input test files:

table_test.html
table_test.csv
table_test.json
table_test.md

OutPut of the program being inputed with the above input files:

out.html
out.csv
out.json
out.md

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Some notes regarding output formatting:

- The output of json is prettified.
- I tried greatly to find a way to prettify the html output but could not find a way and I didn't have time to implament from scratch myself.  So the thml output is not pretty but it is correct.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Other:

    1) Some of the command line arguments have an uppercase copunterpart to avoid clashing the the same option under VS Code, these incluse:
        
        -v  -V  verbose
        -h  -H  help

    2) I often use int r and int c in nested for loops when converting formats.  The r represents table rows and c represents table columns within the rawData List<List<String>>.

    3) There are no known bugs within this program.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
