---
title: "Wine &amp; Write It Now 3"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by PropheticWarrior on 2007-11-12
I'm a complete noob to linux but I so love the freedom and speed of the OS (I use Ubuntu) that I would love to completely abandon windows forever.  The problem is that I can't get my Write It Now 3 program to run in wine.  It installs fine and starts to run but displays a Java startup error, but the error message is blank.

What information do you need in order to help me.  I'm rusty at command line so if that is needed please be as specific as possible.

Thanks in advance.

---

### Post by por100pre1 on 2007-11-13
I've never tried that program, but I think it could require JRE for Windows. Check if installing [JRE]("http://www.java.com/en/download/manual.jsp") for Windows does the trick.

---

### Post by PropheticWarrior on 2007-11-20
Thanks! Your suggestion was dead on.  I contacted the developer and asked for help.  They informed me that the current version will run with either JRE 1.4 or 1.5.  So basically with JRE 1.4 installed for Windows and for Linux, I was able to get the program running.  I'll type that up and share with the community.  I just need to learn how to call a .jar file from a hidden folder so I can make a launcher for it.

---

### Post by por100pre1 on 2007-11-20
Check if this works:

```
java -jar */path/to/file.jar*
```

---

### Post by PropheticWarrior on 2007-12-02
Okay, here's how I got this program working in Ubuntu 7.10 using Wine 9.49.  Aspiring novelists enjoy...

Getting Write It Now 3 Working in Wine on Ubuntu

Before attempting this make sure that the Java Runtime Environment 1.4 is installed in both linux and wine (just to be safe).

1. Open the browse c:\drive in Wine
2. Move the install file for Write it Now 3 to that folder
3. Right Click and the select "open useing Windows Emulator"
4. When install is done copy the following files to your Home Folder

	- WinDemo.png
	- Splash.png
	- ideas310.txt
	- all Icon*.gif
        -all *.dict (canada, uk, us, & main)
If you don't do this then the program errors when it runs. Also without the icon files the program does not display the colored icons for the characters in your story. If you don't copy the .dict files (dictionary) then the spell check errors saying it can't find the dictionary files.

5. Run the program using the file: writeitnow.jar by right clicking and "open with Java 1.4". Trying to use the exe will trigger a blank java error.
6. You can either ignore error about the example file it can't find or you can copy example.wnw to the home folder as well.

You can make a launcher by right clicking on the file writeitnow3.jar.

1. left click on "Make Link"
2. drag to desktop or where ever you're going to put it.
3. Right click on the link and choose properties
4. Chose "Java 1.4" (Archive Manager is default) and then close.

When using the program it defaults to the home folder for all wnw files.  I just made a folder in my home folder specifically for write it now files.  You can't run the program by double-clicking the .wnw files like in Windows, but that's something I can live with.

---

