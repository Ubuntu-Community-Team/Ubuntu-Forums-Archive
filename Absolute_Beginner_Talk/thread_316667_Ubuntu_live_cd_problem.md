---
title: "Ubuntu live cd problem"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-12-11
hi,

i was sucessfully able to install kubuntu and xubuntu from their live cds...
but when i come to ubuntu i am not able to install it from the live cd...
after the cd is inserted then after some time blank screen appears even the desktop doesnt appears...what should i do ?


my video hardware is nvidia geforce 2 
processor is amd athlon xp

---

### Post by renzokuken on 2006-12-11
have you checked that the CD was burned correctly, if kubuntu and xubuntu work then i dont see any reason why ubuntu shouldn't

try checking the CD

---

### Post by Dusty545 on 2006-12-11
I've got a feeling that there's an error with the disk you've been trying to boot from if, as you say, you were able to boot Kubuntu and Edubuntu.

Try running the disk on another computer and take a look at how that goes.

If you got the disk via download then run the md5.sum to make sure that all went well.  Also, check that you burned the ISO image correctly.

---

### Post by hyper_ch on 2006-12-11
if you have installed either system you can install the other desktops by simply issuing the commands below in the command line:

> 
sudo aptitude install ubuntu-desktop
or
sudo aptitude install kubuntu-destkop
or
sudo aptitude install xubuntu-desktop


---

### Post by renzokuken on 2006-12-11
have you checked that the CD was burned correctly, if kubuntu and xubuntu work then i dont see any reason why ubuntu shouldn't

try checking the CD

---

### Post by kurian on 2006-12-12
hi i have received almost 5 ubuntu cds from the shipit so idont see any reason for the cds to be wrongly written

and since xubuntu and kubuntu works fine i dont think there is any problem with my hardware...

is the ubuntu live cd different from other distros in any other way which causes this problem

---

### Post by Neostart on 2007-12-02
Hi all Ubuntu users.

After 4 or 5 hours time spending on figure out how to run Ubuntu I'm not sure it'll be ever possible.

I've done as follows:

1. Downloaded Ubuntu 7.10 desktop i386 edition for x86 architecture
2. Triple checked checksums for iso file
3. Burned with 3 separated freeware to DVD
4. Launched from CD with success

After that I saw graphical options like:

1. Launch Ubuntu
2. Launch or install
3. Install for manufacturers

and other fancy menu litings.

But Ubuntu doesn't start. I get sometimes acces to the command line prompt, but that's all.

I can't just install it unless I check the Live CD launch of Ubuntu.

I figured out also, that sumo command isn't available, and the Ubuntu site said to download 
freeware burner and click OK dialog message. Isn't that funny, that even with 2 checks, 5 burned discs and multiple options in this dialog, the system run fails?

I was curious first, now I'm a bit disappointed unsure if this version is stable or not.

My configuration is: Intel Celeron** 1,70Ghz** with **1,25 GB** memory and** 250GB** data storage.

Any possible explanations for this weird intallment behaviour?

---

### Post by jken146 on 2007-12-02
Neostart, have you tried the alternate installer CD?

---

### Post by Neostart on 2007-12-02
Could it be, that since my CPU is Intel/Celeron it needs amd64 installation?

I just guess ....

---

### Post by Neostart on 2007-12-02
I've tried 3three of them, separatedly download in diffrent zones, like Poland, USA, Australia.

---

### Post by jken146 on 2007-12-02
> Could it be, that since my CPU is Intel/Celeron it needs amd64 installation?
No, the 32 bit version will run on 64 bit systems.

> I've tried 3three of them, separatedly download in diffrent zones, like Poland, USA, Australia.
I didn't mean different mirrors.  I meant the text-based installer CD, known as the Alternate CD (You go to [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu), select your architecture and then tick the box at the bottom that says something like 'I need the alternate CD').  The alternate CD is useful if the live CD won't load.

---

### Post by Neostart on 2007-12-02
> **jken146 said:**
> Neostart, have you tried the alternate installer CD?

Yes, I've done it.

Now I'm waiting for amd64.iso ... if this fails ... i'll cry.

---

### Post by Neostart on 2007-12-02
> **jken146 said:**
> No, the 32 bit version will run on 64 bit systems.


I didn't mean different mirrors.  I meant the text-based installer CD, known as the Alternate CD (You go to [www.ubuntu.com/getubuntu](www.ubuntu.com/getubuntu), select your architecture and then tick the box at the bottom that says something like 'I need the alternate CD').  The alternate CD is useful if the live CD won't load.

The problem is, I dont know which architecture to use, since amd64 is designed for Intel and x86 for Celeron, and my PC is a mix of them.

---

### Post by Joeb454 on 2007-12-02
amd64 is actually for 64 bit processors, like the Intel Core 2 Duo or Core Duo etc.

You do need the x86 version of the install as I'm guessing your cpu isn't 64 bit compatible

---

### Post by Dark_X on 2007-12-02
I had the same problem.  Start up the disk and at the boot menu hit F6 and type in vga=791 .  I hope this works for you, I have an ATI card.

---

### Post by Joeb454 on 2007-12-02
Dark_X just reminded me of something, I could never get the Live CD to boot on my desktop, so I gave up, then a few months after Fiesty (7.04) was released, I tried again, and got the same result, no boot...so I tried booting in "Safe Graphics Mode" and it worked...Ubuntu has lived on that desktop ever since

---

### Post by Neostart on 2007-12-02
> **Joeb454 said:**
> amd64 is actually for 64 bit processors, like the Intel Core 2 Duo or Core Duo etc.

You do need the x86 version of the install as I'm guessing your cpu isn't 64 bit compatible


Yes. my PC is Intel/Celeron 1.7Ghz x86 compatible. I added vga=791 after casper boot dialog and launched, but without success, the horizontal white blinking dos type cursor is still visible and nothing happens...

---

### Post by Joeb454 on 2007-12-02
Did you try booting in Safe Graphics Mode?

---

### Post by Neostart on 2007-12-02
> **Joeb454 said:**
> Did you try booting in Safe Graphics Mode?

Yes, twice.

I know, i did anything basic. Now I'm donloading alternate version. Maybe this help, but when I hear of text based install like those in the command prompt, I'm scared.

I was always using WXP. Don't know even the basic commands, not thinkin about installing something from the line to the line.


PS. In the Safe Mode I get into the command line prompt after the cute Ubuntu Splash screen.

---

### Post by Joeb454 on 2007-12-02
The alternate CD isn't too bad, it just doesn't load up the whole GUI that's all

---

### Post by Neostart on 2007-12-02
> **Joeb454 said:**
> The alternate CD isn't too bad, it just doesn't load up the whole GUI that's all

So the difference between graphic and text mode is just the design, not the launching properly.

Hmm...I'll  get hungry, since it's almost 2 am.

Do You think the problem lies in the** dvd burn** and the fact there is no such command like **SUDO**?

It's Infrared burned.

---

### Post by Joeb454 on 2007-12-02
How do you mean it's infrared burned?

If you are burning it from an existing Windows system try using imgburn (Google it, it'll be there somewhere near the top)

I use that and so far I've never had any issues with non working CD's

---

### Post by Neostart on 2007-12-02
> **Joeb454 said:**
> How do you mean it's infrared burned?

If you are burning it from an existing Windows system try using imgburn (Google it, it'll be there somewhere near the top)

I use that and so far I've never had any issues with non working CD's

First of, I dont use CD's cause it's historic tech, only DVD. Infrared is commonly burnout soft among Ubuntu dev's. I'll try, this w'll be my last 7th DVD. If nothin' happens, I will have to install Vista, cause the problem is, that Win users are more sophisticated in the area like those from Ubuntu and other semi branches.

Thx for tryin'.

---

### Post by colomob on 2007-12-02
do u have an HP by any chance?

---

### Post by Neostart on 2007-12-03
> **colomob said:**
> do u have an HP by any chance?

lol, no ....

---

### Post by JBAlaska on 2007-12-03
Try this, When you get to the main/install screen, type F6 and add this to the end of the boot string;
```
all_generic_ide
```

If that allows you to install ubuntu, you'll have to add "all_generic_ide" to the grub boot string permanently.

---

### Post by Neostart on 2007-12-03
> **JBAlaska said:**
> Try this, When you get to the main/install screen, type F6 and add this to the end of the boot string;
```
all_generic_ide
```

If that allows you to install ubuntu, you'll have to add "all_generic_ide" to the grub boot string permanently.

Ok. But this lets me install, and I'm afraid of losing 120GB data on my fat storage disc. So I've decided at the begining just to run Live CD, nothing more, unless it works fine for my PC, smoothier than Winnie.

---

### Post by Neostart on 2007-12-03
I added this command, and there was some change. Between menu and spash there was some linukz line, but then switched to command prompt unbeggingly ...:]

---

