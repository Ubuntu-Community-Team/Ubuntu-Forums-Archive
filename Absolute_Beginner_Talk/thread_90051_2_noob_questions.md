---
title: "2 noob questions"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by thenoobest1 on 2005-11-14
ok, i know this is prolly gonna sound pretty stupid but keep in mind this is my first time ever even seeing linux, here goes... first off, i downloaded a program to play my xbox online since i cant afford xbox live. ([www.teamxlink.co.uk]("http://www.teamxlink.co.uk")) but i cant figure out how to install it.

and second, is there a "noob friendly" tutorial of installing wine?

---

### Post by throntax on 2005-11-14
I had a look at the Kaid software.. i think it runs in the background allowing 
you to connect to the internet with your xbox via your pc? does that sound right?

where you downloaded the file kaid-7.0.0.4-linux_x86.tar.bz2 type in a terminal 
(applications --> Accessories --> terminal)

bunzip2 kaid-7.0.0.4-linux_x86.tar.bz2

Which will make the file into kaid-7.0.0.4-linux_x86.tar ( it had been double compressed, so now you have to un-tar what's left.. type:

tar -xvf kaid-7.0.0.4-linux_x86.tar

which will make a directory called kaid.
change into that directory, and then become root and run the command kaid
(if you list it with details, 'ls -l' you'll notice the file 'kaid' has an 'x' in its permission section, which means it's executable ..) so type

sudo ./kaid

type in your password and it will say it's running! 
hope it does good things!
and i'm not sure about a newb step by step wine installation..
maybe try 
sudo apt-get install wine
?

---

### Post by ubuntu4everyone on 2005-11-14
wine is easy to install, just go on synaptic package manager search for wine click to install it. then go on to terminal and go in to the directory of the .exe app and type wine myapp.exe.



Hope this helps

---

### Post by throntax on 2005-11-14
:) oh yeah: replace kaid-7.0.0.4-linux_x86.tar with whatever version you downloaded, thats if the numbers are different..
the download page said that a Debian package will be available soon, (Debian packages work well with ubuntu ;) which will make it easier one day..

---

### Post by thenoobest1 on 2005-11-14
yea, thats exactly what that prog does... thanks for the fast response, im gonna give that a shot now

**edi**
this is the fastest forum ive ever been on lol... 2 posts while i was makin mine

---

### Post by throntax on 2005-11-14
cool . let everyone know how it goes..

---

### Post by ad noiseam on 2005-11-14
Installing programs on Ubuntu is totally different as on Windows. For most programs, you should go to "Add Applications" in the Gnome menu, and select what you want to install (you might want to click on "Advanced" and edit your repositories for more choice). The files will be downloaded and installed for you.

Some programs, however, are not in the repositories (understand: they have not been prepared for Ubuntu yet). Linux experts (which I am far from being) can then "compile" the programs from its source code in order to use it, but this is a difficult process.

However, there might be hope for you, judging from the page you linked. Ubuntu use the Debian system to install applications, and you might then be able to use the "debian package" mentionned on this site. However, the page with this ([http://www.xbox-linux.org/Xebian](http://www.xbox-linux.org/Xebian)) gives me a 404.

Good luck with Linux and Ubuntu. :)

---

### Post by thenoobest1 on 2005-11-14
i gave up on the kaid for now since there will be a release that will be easier to install later. but im still working on the wine. i tried browsing to the folder the exe was in and then going to the terminal and typing wine dreamweaver.exe and got "wine: cannot find 'dreamweaver.exe'" when i tried to load it. i took a screen shot too so you guys can see whats goin on. thanks again for all the help.

---

### Post by Gustav on 2005-11-14
You'll have to move to the directory where the *.exe file is. This is done with the 'cd' command:
```
cd  Dreamweaver\ 8
```
The '\' is there to tell that there is a space. You can use tab-completion to write directory or file-names, that is done by beginning to type the first letters and then press tab, this makes the terminal guess what you were about to type.

---

### Post by thenoobest1 on 2005-11-14
:???: thanks gustav, i was trying the cd command the DOS way with the / before that screen shot lol... i just realised what it looks like i was doin well, it launched dreamweaver... dreamweaver says i need to reinstall the program when it loads, the terminal says it failed to load vtable. 

basically what i did was make the program folder for dreamweaver shared on my windows pc and networked to my laptop runnin ubuntu to transfer the files over to a local folder. im guessing i should have tried to run the installer in linux to get file structure.

---

### Post by darrenrxm on 2005-11-14
Your not a noob just someone who needs help. Stop putting yourself down.

---

### Post by thenoobest1 on 2005-11-14
thanks for the encouragement... am i thinkin on the right track though as far as installin it from linux?

---

### Post by Kvark on 2005-11-14
Yeah, put in the Dreamweaver CD and try to run autorun.exe or setup.exe on the CD with Wine, it might work.

Another way that might work is to export the stuff about Dreamweaver from the Windows registry and import it to the Wine registry. To run Wine's reg editor you type regedit in a terminal just like you type regedit in a dos window to run Window's reg editor.

BTW. You can also run exe files with Wine by clicking on them but then you don't see the error messages in the terminal.

---

### Post by thenoobest1 on 2005-11-14
i got winrar to install using wine, havent had a chance to try macromedia suite yet... thats next. thanks for the help guys.

---

### Post by yimmmy on 2007-05-14
ok so what do i do to install this??
i have no clue

---

