---
title: "How do I make wine programs default?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2007-03-25
How do I make a program installed trough wine the automatic pdf reader for ubuntu?

---

### Post by eljalill on 2007-03-25
You could write a shell script,and save it in /usr/bin
and then make that shell script the custom.
Like:
```
 #!/bin/sh
ROOT_DRIVE="Z:\\"
for arg
do
	wine "/home/usr/.wine/drive_c/Program Files/your program/your program.exe"  "${ROOT_DRIVE}$(echo "$arg" | sed 's/\//\\/g')"
done

```

That's how I do it, but if there's a better way, I am also curious to learn

---

### Post by machoo02 on 2007-03-25
Just curious as to why you want to use a Windows-based .pdf reader, when there are numerous ones (Evince, Xpdf, Kpdf, Gpdf, and Adobe Acrobat Reader) that work natively?

---

### Post by jcrnan on 2007-03-25
machoo02: Because I use to have tons of pdf's up at once and I have yet to find a native pdf reader that is as lightweight as Foxit Reader.

eljalill: I'll try that :)

---

### Post by david_kt on 2007-03-26
> **eljalill said:**
> You could write a shell script,and save it in /usr/bin
and then make that shell script the custom.

That's how I do it, but if there's a better way, I am also curious to learn

To "disturb" the file system I think is not a good way, unless you want to make the default program system wide. Otherwise, just make it on user home folder:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Creating file associations
If you want certain files to open in a windows application by clicking on them, the best way is to create a script. For example I want Adobe Flash project files (*.fla) to open in Adobe's Flash editor if I double click it. 

You can for example create a file gedit ~/.wine/Flash\ 8. Now paste the example script in it, save and close gedit. 

Example script: 

#!/bin/sh 

QUICKPARLOCATION="c:\\Program Files\\Macromedia\\Flash 8\\Flash.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0Make sure the file is executable chmod +x ~/.wine/Flash\ 8 

After you completed this go to an *.fla file right click it, properties, go to the “open with” pane, click add, paste '/home/<yourusername>/.wine/Flash 8' in the command line and select the radio bullet. Now if everything went ok, you can doubleclick the file and it will be openend in Flash 8. 

DK

---

