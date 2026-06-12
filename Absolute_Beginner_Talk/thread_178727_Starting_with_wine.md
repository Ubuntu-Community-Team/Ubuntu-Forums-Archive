---
title: "Starting with wine"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by darby74 on 2006-05-18
I have a dual boot Ubuntu/Windows system and have wine installed on Ubuntu.I have Quicken on Windows and would like to install it on Ubuntu using wine.

I`ve read most of the Help files but can`t get my head round how to get started, do I use the Quicken CD or what? A pointer in the right direction would be very much appreciated.

Thank you.

---

### Post by louis_nichols on 2006-05-18
Well, it's just like in windows: double click setup.exe ! :)

---

### Post by Nano Geek on 2006-05-18
If you haven't yet, try reading [this]("http://www.ubuntuforums.org/showthread.php?t=149585&highlight=HOWTO+wine") HOWTO.

---

### Post by louis_nichols on 2006-05-18
The howto is a nice idea, but a completely informed decision needs to take into account the fact that there are those among the wine developers who don't see winetools as a very good thing.

While it's undeniable, what it does does well, I suggest you read [this link]("http://www.winehq.org/?issue=304#WineTools%20&%20Wine") and [this link]("http://www.winehq.org/?issue=308#WineTools..%20part%20II").

I take no side in this matter. I just posted this because people should know.

---

### Post by darby74 on 2006-05-18
I will have to ask you gentlemen to be a little patient with me.

I type winecfg in a terminal and wine appears, where do I go from there?

I don`t want to install IE just Quicken.

Thank you.

---

### Post by Nano Geek on 2006-05-18
> I don`t want to install IE just Quicken.Then just pop in your Quicken cd, wait for it to open the file browser window, and click on setup.exe.

---

### Post by darby74 on 2006-05-18
OK. Wine is running after winecfg in terminal, I put the CD in and when install.exe appears in the file browser I click on it and get Couldn't display "/media/cdrom0/install.exe".

Thank you for your patience.

---

### Post by wpshooter on 2006-05-18
[QUOTE=darby74]I will have to ask you gentlemen to be a little patient with me.

I type winecfg in a terminal and wine appears, where do I go from there?

I don`t want to install IE just Quicken.

Thank you.[/QUOTE]

Please let us know if you figure out how to do this.

I tried to get Peachtree Accounting installed and running using this WINE program a while back and I could never get it to do anything.  I did ask for help on here and I read the instructions on setting up the WINE program, but they did not help me to get Peachtree running on Ubuntu.  

I just don't think it is possible to get programs like this to run on Ubuntu/linux.

Good luck.

---

### Post by Nano Geek on 2006-05-18
In a command line, try typing```
wine /media/cdrom0/install.exe
```Just make sure that the Quicken cd is in your main cd drive.

---

### Post by darby74 on 2006-05-18
Installed straight away.

Unfortunately when I click on the Quicken icon on the desktop the Quicken splash screen appears and locks up the desktop. I think perhaps I should have a look at Gnucash!!

Thanks anyway.

---

### Post by hentaidan on 2006-05-18
What version of Quicken are you using?

If you ever are having trouble with an application and Wine, or want to know if the program will work, check out the Application Database at wine: [http://appdb.winehq.org]("http://appdb.winehq.org")

---

