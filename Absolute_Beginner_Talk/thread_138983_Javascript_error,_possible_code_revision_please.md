---
title: "Javascript error, possible code revision please?"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by imrumpf on 2006-03-02
I do online work on this one site, and they have an option to upload csv files to import into your contact database. Problem is, I do it in windows and everything works fine...in Ubuntu, error messages. i viewed source and here is what i found:
```
    function frmImport_onSubmit(frmImport) {
        /*--------------------------------------------------------------
         * Purpose:
         *     onsubmit handler for the form named frmImport.  
         *       Makes sure a file was selected and that the selected file 
         *     is of the property type.
         *--------------------------------------------------------------*/
        if (frmImport.ExportFile.value == '') {
            alert('A file was not selected');
            return false;
        }
            
        //get the file name and make sure it is valid: only hyphen character is allowed.
        var strFilePath = frmImport.ExportFile.value;
        var intLastInstance = strFilePath.lastIndexOf("\\")
        var strFileName = strFilePath.substring(intLastInstance + 1,strFilePath.length);        
            
        if (!isValidFileName(strFileName)){
            alert('Import Error: Invalid file name\n');
            return false;
        }
```
Could somebody explain why i get that import error message all the time? i think it's because of the way files are identified ( / instead of C:, stuff like that). Could anybody see the problem i may have, and if so what would need to be changed to fix the problem? thanks in advance if anybody can help me out!

---

### Post by Pragmatist on 2006-03-03
What program are you running that is giving the error?  How are you running it?
If this is a command-line tool, cut and paste what you type into the terminal and what output you get.

---

### Post by imrumpf on 2006-03-03
sorry i didnt explain myself properly there. There is a website where I do online marketing, and when i get a contact i need to enter their information into my contact database. When i do them one at a time, everything works fine. But I recently got sent a csv file and there is an option to upload csv files to the server. I use their online tool, which is no more than a browse button, next, and cancel. i browse to the file and hit next, and it keps giving me that error everytime! the message says "Import Error: Invalid file name". I tried different browsers (4 to be exact) and nothing worked. So i viewed source of the page and i saw a snippet of javascript and within it there was my error message! So i thought "okay, maybe that part is rejecting the filename for some odd reason". Problem is i don't understand javascript so I can find what would be causing this error. Every other site that has an upload tool works just fine, except this site. I was wondering if anybody could see a problem in that snippet, so i could suggest to the support staff what needs to be fixed (nobody there knows linux :()

Anyways help is always appreciated, thanks for looking it over.

---

### Post by Pragmatist on 2006-03-03
What happens if you make a copy of the .csv file and name the copy without the .csv extension?  Then try and upload this copy.

---

### Post by towsonu2003 on 2006-03-03
It says: get the file name and make sure it is valid: only hyphen character is allowed

Try changing the name to a very simple one (cvs.cvs maybe??)

[edit]I just noticed: why the hell did I look in that code? It's all greek to me... OMG I'm becoming an illiterate geek!

---

### Post by imrumpf on 2006-03-03
nothing works when renaming it. i named it 1.csv and no good :S works fine in windows though...maybe it has to do with somehting about the "\\" part??

---

### Post by Pragmatist on 2006-03-03
Must you use your web servers upload tool?  Can you upload using your own ftp client?  Check out: ```
man -k ftp
``` or ```
sudo synaptic
``` to find graphical ftp programs (do a search with keyword **ftp**)

Is this website your using private?  If not, include the URL and we can check it out; this might be simpler than explaining everything in detail.

---

### Post by Pragmatist on 2006-03-03
It occured to me that the website might not be that helpful since I assume you have an account with a password and are using the web-based upload utillity provided by your webserver.  In that case we can't duplicate that without an account.

Since the error message and your appreciation of the problem indicate a bad filename, you need to paste here **exactly** what you are typing in.  If you are browsing to select the file instead of typing it in, can you see the filename the utility is registering?  The reason I ask is because you said you thought the ** \\ ** might be a problem.  Where are you seeing that?  > :S works fine in windows though What is **:S**

We need to see what you see.

---

### Post by imrumpf on 2006-03-04
sorry.... :S is a common symbol for an unanimated :???: smiley.

i have included 2 pictures....one of it being tried in ubuntu, the other in windows. and here is the entire view source of that page's java....

```
    <SCRIPT LANGUAGE="JavaScript">
    <!--
    function btnCancel_onClick(){
        /*--------------------------------------------------------------
         * Purpose:
         *     event that fires when 'Cancel' button is clicked
         *--------------------------------------------------------------*/
        window.close();
    }

    function frmImport_onSubmit(frmImport) {
        /*--------------------------------------------------------------
         * Purpose:
         *     onsubmit handler for the form named frmImport.  
         *       Makes sure a file was selected and that the selected file 
         *     is of the property type.
         *--------------------------------------------------------------*/
        if (frmImport.ExportFile.value == '') {
            alert('A file was not selected');
            return false;
        }
            
        //get the file name and make sure it is valid: only hyphen character is allowed.
        var strFilePath = frmImport.ExportFile.value;
        var intLastInstance = strFilePath.lastIndexOf("\\")
        var strFileName = strFilePath.substring(intLastInstance + 1,strFilePath.length);        
            
        if (!isValidFileName(strFileName)){
            alert('Import Error: Invalid file name\n');
            return false;
        }
            
        return true;
    }
        
    function isValidFileName(strFileName) {
        /*--------------------------------------------------------------
         * Purpose:
         *     Returns true if the supplied file name is valid.
         *     allows spaces and hyphens in the file name.  File must 
         *     end with mdb, csv, or dbf extension.
         *--------------------------------------------------------------*/
        if (strFileName.search(/^[-\s\w]+(\.(mdb|csv|dbf))$/i) != -1) 
            return true;
        else
            return false;
    }
    
    function body_onLoad() {
        /*--------------------------------------------------------------
         * Purpose:
         *     OnLoad handler for the body element.  Produces a javascript
         *     alert if the QueryString contains "notables=true".
         *     This is the case when the user has select a file that does
         *     not contain any tables (e.g. empty .mdb file).
         *--------------------------------------------------------------*/
        
    }
    //-->
    </SCRIPT>
hope this helps even a bit...thanks a lot too!


``` [ATTACH]6682[/ATTACH][ATTACH]6683[/ATTACH]

---

### Post by dtfinch on 2006-03-04
--> strFilePath.lastIndexOf("\\")
"/" on everything but Windows.

EDIT: Sorry, didn't read above already mentioning "\\". Definitely the problem.

---

### Post by Pragmatist on 2006-03-04
Sorry, just noticed that someone else responded before I was finished answering.

You were right, > strFilePath.lastIndexOf("\\") means that it is taking the filename that follows the last backslash (The first of these backslashes means, "take this next backslash as a literal character"  As opposed to using the special meaning that javascript ascribes to the backslash character.)

In Windows, the backslash is used to delineate a filename path as in: C:\temp\1.csv

In Linux the forward slash is used to delineate a filename path as in:
/home/robert/1.csv

**Bottom line: This upload utility that is provided by your webserver only supports Windows filenames.**

---

### Post by imrumpf on 2006-03-04
so we know the \\ is the problem....now how would we fix that? could we maybe just leave it blank to look like ("")?

---

### Post by Pragmatist on 2006-03-04
Your not understanding.  The program takes a path like:
C:\directory1\directory2\directory3\filename
reads everything AFTER the last \  which in this case is the one right before filename.  So it ends up with filename.

Linux paths don't contain backslashes.  So the program never finds the last backslash because there aren't any backslashes at all.

Contact your web hosting company and ask them if they support non-windows filenames.

---

### Post by imrumpf on 2006-03-07
Awesome thanks for all the help! One more reason Ubuntu is the best Distro out there ;)  I'll e-mail the tech support and maybe they and I can work on a soultion so the system will real \ as well as /. Again thanks for all the help!

---

### Post by Pragmatist on 2006-03-07
If they are willing to make the change, probably all they would have to do is check if the first character is a letter or a foward slash.  Then they use a simple conditional:

If it is a letter (uppercase or lowercase) send to old code
if it is a forward slash send to new code.

The new code would be the same as the old except it would read to the last forward slash  strFilePath.lastIndexOf("\/") or if the forward slash has no special meaning in javascript then just  strFilePath.lastIndexOf("/")

---

