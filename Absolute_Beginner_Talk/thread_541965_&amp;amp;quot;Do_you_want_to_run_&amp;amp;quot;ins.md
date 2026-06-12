---
title: "&amp;amp;quot;Do you want to run &amp;amp;quot;insertfile.rtf&amp;amp;quot; or display its contents?&amp;amp;quot;"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
I have a similar question as this person does: [http://ubuntuforums.org/showthread.php?t=141881](http://ubuntuforums.org/showthread.php?t=141881) which was seemingly never answered.

Whenever I copy, say, an .rtf or .txt from Windows and left-click, it asks "Do you want to run "insertfile.rtf" or display its contents?" This seems odd, considering Windows does nothing like that when I run .rtfs created in Ubuntu.

This is annoying because I either have to open the program that I want to open it with and manually open the file from the program, or right-click and "open with". Either way, it's far more clicking than simply left-clicking. Why does Ubuntu do this, and how can I fix it?

---

### Post by geekphreak on 2007-09-03
Uncheck 'Allow executing file as program' from the Permissions tab of file's properties.

---

### Post by diatribe on 2007-09-03
many executable files are viewable in a text editor because it is simly code

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
> **geekphreak said:**
> Uncheck 'Allow executing file as program' from the Permissions tab of file's properties.

Unfortunately, I have to do that for every file from Windows, which defeats the purpose.

Does anyone know why Ubuntu does this?

---

### Post by schorsch on 2007-09-03
As diatribe mentioned: Shell scripts are set executable so that they can run. The file browser does not know if you klick on the file: "Hmm, does the user want to edit the file or does he want to run it?" So it is better to ask than to guess what the user wants to do. Compare it with windows: You have a *.reg file. Double click on it and the informations in it will be put in the registry without asking any further. Ups, I wanted to see the content of the *.reg file but now it is to late. I wish I had done a right klick on the file .....
And do not forget about security: You got an executable file from someone that includes something like "sudo dd if=/dev/zero of=/dev/hda" .... and just double click on it .... you won't be fast enough to stop before it messes up your boot record and partition table .. ;-)
IMHO it is just better to ask first if being unsure what to do.
But to solve your problem with large amounts of files: If there are only files in a directory  *DIR* that you do not want to run start a terminal session and type:
```
cd *DIR*; chmod a-x *
```
Thus all the files in *DIR* are not executable any longer and will be opened with the default application.

---

### Post by Paul133 on 2007-09-03
Put them in a directory and then run ```
sudo chmod -R  -x /the/directory/they/are/in
```

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
Thanks! Is there any way to do the equivalent of unchecking "run as executable" for all .rtf or .txt files that enter my system, or would that be a bad idea?

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-04
bump

---

