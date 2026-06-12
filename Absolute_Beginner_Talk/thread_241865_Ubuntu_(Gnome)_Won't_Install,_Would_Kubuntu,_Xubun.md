---
title: "Ubuntu (Gnome) Won't Install, Would Kubuntu, Xubuntu, or the Alternate Install?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Paul133 on 2006-08-22
Well, I've downloaded, verified, and burnt Ubuntu ISO files twice and it'll load into the Virtual CD, but it hangs when I double click Install.](*,)  Perhaps the alternate (text) install would work or maybe another graphics manager (such as Xfce or KDE). If not, I guess I'll try Mepis, but I really like the Ubuntu forums, support , and no enterprise edition (that's what I hate about Mepis, only slightly better than RedHat). Or I suppose I could try Debian. But so what do yuo think will work?:confused:

---

### Post by codejunkie on 2006-08-22
> **Paul133 said:**
> Well, I've downloaded, verified, and burnt Ubuntu ISO files twice and it'll load into the Virtual CD, but it hangs when I double click Install.](*,)  Perhaps the alternate (text) install would work or maybe another graphics manager (such as Xfce or KDE). If not, I guess I'll try Mepis, but I really like the Ubuntu forums, support , and no enterprise edition (that's what I hate about Mepis, only slightly better than RedHat). Or I suppose I could try Debian. But so what do yuo think will work?:confused:
what kind of computer or motherboard do you have? certian motherboards require different boot options to be entered before you can install, and some motherboards are just picky like mine it won't do a graphical install unless there is at least 512mb of ram installed, but it will work just five by doing the server install first and then using apt-get to install the desktop. so if you have a small amount of memory you might try doing a server install first and then complete the install by running ```
sudo apt-get install ubuntu-desktop
```when you get into the terminal.

---

### Post by aysiu on 2006-08-22
Try the Alternate CD. It's less buggy than the Desktop CD.

---

### Post by Paul133 on 2006-08-22
I've got a cheap Dell Inspiron 1200 which is 1.6 Ghz processor 256 MBH of RAM with integrated video (no video card) and a PCMCIA Dell wireless card (don't know the chipset). So should I try ```
 sudo apt-get install ubuntu-desktop 
``` and download and burn the server ISO instead of the desktop ISO since the server is smaller and faster? Will it be a graphical ot textual install?

---

### Post by Paul133 on 2006-08-22
Would it be better to install the alternate CD ISO or the server ISO and then ```
 apt-get install ubuntu-desktop 
```

---

### Post by codejunkie on 2006-08-22
> **Paul133 said:**
> Would it be better to install the alternate CD ISO or the server ISO and then ```
 apt-get install ubuntu-desktop 
```
i think you can perform the server install with either of those cd's and they are a text based installs.

---

### Post by Paul133 on 2006-08-22
Thanks. Do I need to burn it to a CD like the desktop CD?

---

### Post by bodhi.zazen on 2006-08-23
> **Paul133 said:**
> Well, I've downloaded, verified, and burnt Ubuntu ISO files twice and it'll load into the Virtual CD, but it hangs when I double click Install.](*,)  Perhaps the alternate (text) install would work or maybe another graphics manager (such as Xfce or KDE). If not, I guess I'll try Mepis, but I really like the Ubuntu forums, support , and no enterprise edition (that's what I hate about Mepis, only slightly better than RedHat). Or I suppose I could try Debian. But so what do yuo think will work?:confused:

Perhaps I'm missing something but to install Ubuntu you need to burn the iso to a CD, put the CD in the CDROM drive, and reboot the computer.

> *it'll load into the Virtual CD, but it hangs when I **double click Install**.*
sounds as if you are trying to install Ubuntu from a virtual CDROM in Windows. This is not how to install Ubuntu, any version.

---

### Post by jimmygoon on 2006-08-23
> **bodhi.zazen said:**
> Perhaps I'm missing something but to install Ubuntu you need to burn the iso to a CD, put the CD in the CDROM drive, and reboot the computer.


sounds as if you are trying to install Ubuntu from a virtual CDROM in Windows. This is not how to install Ubuntu, any version.

I know you're trying to help here bodhi, but to the original thread maker please ignore the above post... If you are booting off of the live cd and clicking INSTALL there then you are doing what you were supposed to.

As for your problem... I would recommend either the (alternate) text install or trying to install xubuntu for your lower system specs...

---

### Post by Skia_42 on 2006-08-23
Edit: Sorry, Jimmygoon is right. I, assumed you still needed to burn the disk.

[This]("https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-gettingstarted.html#id2524495") should help you in burning the iso. Specifically these instructions:
> 1.5. 	
How do I burn the ISO file to CD-R?
	
In Windows with Nero Burning ROM:


Download the ISO file to your hard drive. (See Where can I download Ubuntu? for download locations.) 

Insert a blank CD into your CD writer. 

Start Nero Burning ROM.

Follow the wizard and select Data CD. 

When the wizard finishes, click Burn Image on the File menu. 

In the Open dialog box, select the ISO file, and then click Open. 

In the wizard, click Burn to create the Ubuntu CD. 


In Ubuntu with Nautilus:


Download the ISO file to your hard drive. (See Where can I download Ubuntu? for download locations.) 

Insert a blank CD into your CD writer. 

In Nautilus, right click on the file you just downloaded, and choose Write to Disc. The Write to Disc dialog opens. 

In the dialog, choose your CD writer and speed, then click on Write. The Writing Files to Disc Progress dialog opens, and Nautilus starts writing the disk.

---

### Post by Paul133 on 2006-08-23
I suppose I wasn't clear. I mean that I burn the ISO file to a CD put it in the drive, reboot and quickly hit F12 then choose CD/DVD Drive to boot from and then Ubuntu loads and I get to Gnome and clikc Install, and the CD drive revs up then dies and nothing happens or a clank Install window comes up and nothing further loads. I was curious as to whether or not the server ISO is loaded fromm a disc b/c it doesn't function as a LiveCD (meant to say Live not virtual in my last post) just an installation. One final question before I install: I only have 1 HD and I need to keep Windows on it, how should I partition?

---

### Post by bodhi.zazen on 2006-08-23
If that is the case, why does he say:
> it'll load into the Virtual CD
that is the part that is throwing me.

---

### Post by Paul133 on 2006-08-23
I said "virtual CD" but I meant "LiveCD". Sorry.

---

### Post by bodhi.zazen on 2006-08-23
I see now.

I agree, try the alternate CD.

---

### Post by Paul133 on 2006-08-23
Alright. I'll try the alternate CD, not the server. I'll start that next tomorrow morning. As for now, I must log off and get some sleep. Thanks for all your help, this is why I want to stay with Ubuntu, the forums and community are great!!!

---

### Post by Paul133 on 2006-08-23
Right now, I think I'll try installing the alternate desktop Ubuntu and if that doesn't work, I'll install Xubuntu (regular, desktop). I'm also going to try a dual boot between (X)Ubuntu and XP. I'll keep you posted.

---

