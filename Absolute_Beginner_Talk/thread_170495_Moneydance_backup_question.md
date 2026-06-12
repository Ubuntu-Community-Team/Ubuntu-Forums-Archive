---
title: "Moneydance backup question"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by phil66 on 2006-05-04
Running Moneydance 2006r4 on Ubuntu Breezy 5.10

App installed and now have backup file going to /home/ram7lc/downloads

File is named Moneydance.md-2006-05-03 in the download folder

Properties show the file type to be: md-2006-05-03 document

How do I open this file to be able to read the contents.

Tried opening by double clicking using terminal gedit nano file editor and even changing file name and file extension.

Nothing I have tried works

Would you please help

Ray

---

### Post by Sef on 2006-05-04
when the mouse is on the money dance back up, right click > properties > permissions.  What permissions are checked?

---

### Post by phil66 on 2006-05-04
Sef

Ower is ram7lc-Ray which is myself

group is same

Permissions is 644 
Owner read and write
group read
other read

Texr view  -rw-r--r--

Comparing downloads which is folder md-2006-05-03 is in the permissions for
downloads is 755 which includes execute

That permission is not in md-2006-05-03

Is this possibly my problem you are looking for

Ray

---

### Post by phil66 on 2006-05-05
Sure could use some help with this problem.

---

### Post by professor_chaos on 2006-05-05
[QUOTE=phil66]Running Moneydance 2006r4 on Ubuntu Breezy 5.10

App installed and now have backup file going to /home/ram7lc/downloads

File is named Moneydance.md-2006-05-03 in the download folder

Properties show the file type to be: md-2006-05-03 document

How do I open this file to be able to read the contents.

Tried opening by double clicking using terminal gedit nano file editor and even changing file name and file extension.

Nothing I have tried works

Would you please help

Ray[/QUOTE]


Can I ask you to do this from the terminal and tell us what happens...
```
more /home/ram7lc/downloads/Moneydance.md-2006-05-03
```
or
```
gedit /home/ram7lc/downloads/Moneydance.md-2006-05-03
```

---

### Post by phil66 on 2006-05-05
ram7lc@ubuntu:~$ more /home/ram7lc/downloads/Moneydance.md-2006-05-03
MoNeYdAnCe DaTaStReAm@USD    US Dollar?\uffff$2^LAZMKZ\u2592\u2514\u2409\u240b\u2592\u253c K\u252c\u2592\u240c\u2424\u2592@<ÍES·

Short example of file list continues and eventually list catagories and the same 0's and plus's I call it code but don't know

gedit with or without sudo says cannot open file

When I tried nano it had the same script as more but at the bottom it has a message convert to Mac

Thanks
Ray

---

### Post by professor_chaos on 2006-05-05
I sounds from your post (and I apologize for not having any experience with Moneydance) that this file is a binary file with some readable characters. Thats why gedit won't open the file. Perhaps moneydance has a reader that can read these files. 

from the commandline the command "file" followed by the filename will tell you what kind of file it thinks it is. For gedit to read the file, it should be text.

ex. 
```
file /home/ram7lc/downloads/Moneydance.md-2006-05-03
```

Also, the properties is just telling you what is after the final . in the filename. Ubuntu doesn't know what a md-2006-05-03 file is.

---

### Post by phil66 on 2006-05-06
ram7lc@ubuntu:~$ file /home/ram7lc/downloads/Moneydance.md-2006-05-03
/home/ram7lc/downloads/Moneydance.md-2006-05-03: data
ram7lc@ubuntu:~$ file /home/ram7lc/downloads/Moneydance.md-2006-05-03
/home/ram7lc/downloads/Moneydance.md-2006-05-03: data
ram7lc@ubuntu:~$

Is this saying it is a data file???

Thanks for the help
Ray

---

### Post by beameup on 2006-06-26
I know this is an old thread, but you just had to rename the backup file with a .md extension. Then you can open it with Moneydance. 
Also try the MoneyDance forum next time you have a specific MD question.

---

