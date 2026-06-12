---
title: "how do i use wine"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Mostlyharmless42 on 2007-06-28
I installed wine through the add/remove program app.  It installed some new programs, but i don't understand how to use it.  I'd like to use it to install Photoshop Elements 5.  Can anyone explain to me how i would do that??

---

### Post by drosophyllum on 2007-06-28
Did you configure wine?
wine has to be configured before you can do anything. 

how good is your computer? I have an alternative i think youll like but it needs a speedy comp.

---

### Post by chandler on 2007-06-28
Not sure how to install something, but to run a program run this in a terminal ```
wine /folder/file.exe
```

that's usually all you need.  So browse the Adobe Elements CD and look for a setup.exe and follow the example...  (wine /media/cdrom/Setup.exe)

---

### Post by Mostlyharmless42 on 2007-06-28
athlon 3200+ 64bit 
Geforce 6800 graphics card
1.5 gig RAM

Is that enough???

---

### Post by dreadlord_chris on 2007-06-28
> **Mostlyharmless42 said:**
> I installed wine through the add/remove program app.  It installed some new programs, but i don't understand how to use it.  I'd like to use it to install Photoshop Elements 5.  Can anyone explain to me how i would do that??

Here's a good HowTo on using Wine:
[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

---

### Post by chandler on 2007-06-28
Crossover?

---

### Post by Mostlyharmless42 on 2007-06-28
> **chandler said:**
> Not sure how to install something, but to run a program run this in a terminal ```
wine /folder/file.exe
```

that's usually all you need.  So browse the Adobe Elements CD and look for a setup.exe and follow the example...  (wine /media/cdrom/Setup.exe)

When i did that i got the following error windows:

Main_File_Version
Product_Registry_Parent
Product_Registry_Key

---

### Post by Mostlyharmless42 on 2007-06-28
> **dreadlord_chris said:**
> Here's a good HowTo on using Wine:
[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

This how to gives directions for Dapper Drake, will it still work on Feisty??

---

### Post by Mostlyharmless42 on 2007-06-28
I can't seem to connect to the server that the How-To says to download winetools from.  Where else can i get it from??

---

### Post by speaker219 on 2007-06-28
> **Mostlyharmless42 said:**
> I can't seem to connect to the server that the How-To says to download winetools from.  Where else can i get it from??

[http://download.formationos.net/winetools/winetools-0.9.4.tar.gz](http://download.formationos.net/winetools/winetools-0.9.4.tar.gz)

---

### Post by Mostlyharmless42 on 2007-06-28
how do i install winetools from that *.tar.gz 

i tried to follow the directions in the how to, but i couldn't get the computer to install winetools.

---

### Post by drosophyllum on 2007-06-28
i suggest you use virtual box and make a virtual windows machine, it will run like a normal windows machine only a bit slower, its better than wine because apps run native.

---

### Post by Mostlyharmless42 on 2007-06-28
how do i set up virtual box???  Is it a dual boot???

---

### Post by Mostlyharmless42 on 2007-06-28
ok, i've installd virtualbox, but i'm having difficulties installing windows.  Do you have any tips???

---

### Post by steveneddy on 2007-07-05
You guys stop picking on this poor kid. He obviously doesn't know anything about Linux.

All anyone ever says here is

"Do this"

or

"No, better yet! do that instead"

No one answers his original question about how to install winetools.

---

### Post by ubergeeknz on 2007-07-06
> **Mostlyharmless42 said:**
> how do i install winetools from that *.tar.gz 

i tried to follow the directions in the how to, but i couldn't get the computer to install winetools.

Can you provide a link to the howto..
What happened when you tried to follow the directions? what output did you get?

I think that on Ubuntu all you need to do is install the wine package using the synaptic package manager, or from the command line:

sudo apt-get install wine

You may need to enable the universe or multiverse repositories (search for universe / multiverse repository)

Be aware, not all windows apps will run in wine so the suggestion to use a Virtual Machine may be a good one.

---

