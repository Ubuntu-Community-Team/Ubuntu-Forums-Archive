---
title: "path-to-directory"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by roboading on 2007-03-20
Posting this i kinda feel like an idiot but anyway installed ubuntu last night(talk about insane install and boot up compared to windows). I was trying to install wow so im checking the guide provided in the documentation and the problem i have is i dont know how ubuntus path directories work i know how they work on window and mac(c:\programs\xxx\xxxx) here is what i have to type into terminal:

 cd /<path-to-directory>/
 wine Installer.exe

i tried some of the following but nothing seemed to work:

/computer/system file/home/<username>/world of warcraft/
/system file/home/<username>/world of warcraft/
/home/<username>/world of warcraft/

anyone see what im doing wrong?

thanks

---

### Post by taurus on 2007-03-20
Try something like

```
cd ~/"World of Warcraft"
wine Installer.exe
```

Linux/Unix is a case sensitive so "world of warcraft" is not the same as "World of Warcraft" and if there is a space between the name, you need to use the quotes or \.

---

### Post by eljalill on 2007-03-20
Leave out the "/" in the beginning...
Furthermore your lowest directory is / .
Then comes usr, etc, home and all the others. Depending on the program, there are installed somewhere in these. 
You files are in /home/username. But when you open a terminal, you are already in your home folder. Everyprogram (almost) puts a configuration file here. these are called .worldofwarcraft for example.

Also you can find programs and directories and files through
locate filename 
in the terminal. The output is the full path of that file.

---

### Post by M$LOL on 2007-03-20
You are looking for

/home/<username>/.wine/dosdevices/c:/'Program Files'/'world of warcraft'/

cd to them one at a time so as not to make a mistake with a huge line of code.

---

### Post by KenSentMe on 2007-03-20
Maybe it's a good idea to read this page on the Ubuntu wiki. It has all information on basic commands you can use in terminal.

The most important command in your case i think would be ls. This is similar like the dir command in Windows/Dos (dir also works on Ubuntu though, but ls is more commonly used). It lists all the files in the current folder.

The folder which has your personal files is called the home folder and you can find it at: /home/<username>. The files on your desktop are at /home/<username>/Desktop. 

For a more graphical view of your filesystem you could use nautilus (go to Locations on your top menu and choose personal) or use the search function in the same menu. (i hope i get the names right, i don't use english as my main language).

Hope this helps you navigation through the system.

---

### Post by Efwis on 2007-03-20
oops

---

### Post by roboading on 2007-03-20
i see... thanks for the help and ill be reading the wiki stuff

---

