---
title: "How do I install hplip?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-03-28
I added a new printer which wasn't technically on the list of detected printers-HP Officejet Pro L7680 AIO. I tried printing with it, but the printing is overlapped, and black and white where it should be in color, but only in certain spots. I'm trying to install hplip. I have the option to do that when I add the printer, but when I click the install button, I'm prompted to open a file I cannot seem to open. So I went via synaptic package manager and installed it that way but now I get nothing, so I'm assuming something still has to be done from the command line.

What is the correct procedure? 

Thank you in advance.

---

### Post by dbbolton on 2007-03-28
i'm pretty sure it's just ```
sudo aptitude install hplip
```

---

### Post by john.nicholls on 2007-03-29
After hplip is installed, you access the toolbox by opening a terminal and typing
```
/usr/bin/hp-toolbox
```
or you can access different parts of the program individually. For example, to check ink levels, you enter
```
/usr/bin/hp-levels
```.
In Synaptic, look at the files installed to see which program options are available.

---

### Post by ramjet_1953 on 2007-03-29
If you want the very latest version, just go to the hplip website, download the install script for your version of ubuntu and follow the how-to on the sight.

It worked flawlessly for me and gave me the latest edition.

Regards,
Roger :cool:

---

### Post by 11hjpphty76lkjj on 2007-03-30
Just for future reference, the website is [http://hplip.sourceforge.net.]("http://hplip.sourceforge.net")

---

### Post by Aurora Borealis on 2007-04-01
Thank you all very much! If I may add an aside, now that I have this installed and the printing is coming out clear and in the right color, I'm noticing the print only appears on the left side of the page and stops in the middle. All the print is there; it's only on half the page, however. Is this a related problem, or is this something with the printer instead? (If it's the the printer, I'll open a new thread.)

---

### Post by ramjet_1953 on 2007-04-02
> **Aurora Borealis said:**
> Thank you all very much! If I may add an aside, now that I have this installed and the printing is coming out clear and in the right color, I'm noticing the print only appears on the left side of the page and stops in the middle. All the print is there; it's only on half the page, however. Is this a related problem, or is this something with the printer instead? (If it's the the printer, I'll open a new thread.)

Is this problem evident with all applications, or just with one?
Have you checked the formatting and scaling options? They may be set-up incorrectly.

Regards,
Roger 8)

---

### Post by 11hjpphty76lkjj on 2007-04-02
> **Aurora Borealis said:**
> Thank you all very much! If I may add an aside, now that I have this installed and the printing is coming out clear and in the right color, I'm noticing the print only appears on the left side of the page and stops in the middle. All the print is there; it's only on half the page, however. Is this a related problem, or is this something with the printer instead? (If it's the the printer, I'll open a new thread.)

 Be sure you have the correct paper size selected.  Sounds like thats the problem..  A

---

### Post by Aurora Borealis on 2007-04-04
Thank you both. I'll see what I can do.

---

### Post by Aurora Borealis on 2007-04-04
Ramjet, it's just when I print, at least that I can tell so far. I haven't used all the functions yet. I'll look into those configs and see where they're at.

---

### Post by Aurora Borealis on 2007-04-22
While we're at it, can someone tell me what this is (it seems to be standard with installation after installation):  cd to the download directory

How do I know what directory I'm in, and then how do I know the name of what I'm supposed to be going to? How do I know where downloads are, or anything else?

Thank you very much in advance for your help.

---

### Post by 11hjpphty76lkjj on 2007-04-23
This means go to the directory where you uncompressed hplip.

Ie,

~/Desktop/hplip-1.7.4

or

~/Downloads/hplip-1.7.4

but because it's a variable and one can download a file to any directory one can create it's hard to tell the user which directory to go to exactly.

~ = /home/<username>/

A

---

### Post by Aurora Borealis on 2007-04-25
Thank you for your reply. I guess it goes to desktop by default which I'm glad for, but I don't get this directory stuff. Right now I use self-extracting files. Is a directory created automatically when I download something?

---

### Post by 11hjpphty76lkjj on 2007-04-26
A directory isn't created when you download something. Although because there are so many different ways to download stuff there may be an application that creates a directory. So I can't say for sure.  Although when I download from firefox it just sticks it on my desktop.  But one can configure it so download in any directory of which you have access.

A

---

### Post by Aurora Borealis on 2007-05-02
Hm. Okay-how do I create a directory? I downloaded and then when I tried to cd to the directory, it said, No such file or directory.

The wierd thing is, it was my home file. So I don't know why I got the message.

---

### Post by 11hjpphty76lkjj on 2007-05-02
Have you looked at these directions perhaps?

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by Aurora Borealis on 2007-05-04
Thank you much!

---

### Post by Aurora Borealis on 2007-05-06
Hm. when I type in the command to run it, it doesn't work. This is supposed to create the directory. I thought I had it figured out why it wasn't working before, but maybe not because I'm still getting this:: 

Can't open hplip-1.7.4a.run

---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
   I used the code:sudo aptitude install hplip mentioned at the top of topic,and got a fully working Desk Jet F2100 AIO-though haven't checked the scanner function as of yet-after
unplugging,then replugging the USB cable into the computer to install the drivers properly!!

---

### Post by JT7 on 2008-02-19
Hi  - I have been trying to get some more life out an older Dell laptop.  I have been trying for hours to install hplip-2.8.2  Used the instructions from the hp site and I get all kinds ofe dependency errors,  I just tried the sudo apt as stated above and get 11 dependencies locked. It tries to go out and access or update - but times out.  Not sure what to do nex

---

