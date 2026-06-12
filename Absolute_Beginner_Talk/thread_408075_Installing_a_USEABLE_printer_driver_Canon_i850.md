---
title: "Installing a USEABLE printer driver Canon i850"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-04-12
Using Xubuntu, latest version just downloaded yesterday. There are drivers for a related printer, a BJC-6000, but not for the i850 USB printer. When set to the correct letter size, it will fill only about 1/3 of the page. This is not acceptable and I wonder if I'm better off going back to Windows for print jobs. I was hoping for a stable OS that would allow me to do at least most of my daily computer work, and everything looked good until I got to setting up a printer. 

Is it Linux, or is it Ubuntu, that's the culprit?

I'm sure there is a work-around, so I'm asking for help. I can't seem to overwrite write-protected files, so one attempt was aborted. I can log in as superuser in terminal, but not at the GUI login screen. 

There should be a package that can be downloaded and auto-installed as long as this printer family has been in the hands of the general public. Of course, I don't expect much help from Canon. 

f someone can help me, step-by-step, I would appreciate it. Please don't assume anything on my part. I am an experienced Windows user. I was able to figure out a long time ago how to get a video driver to work on a laptop by doing some tweaking of some files in an editor in a linux distro (Suse, I think, or maybe Caldera), back in 1999 or 2000. 

If the recommendation is to install Kubuntu or Ubuntu instead, I had issues with Ubuntu not booting, and Kubuntu gave me errors when I tried to add/remove programs, effectively locking me out of customizing my OS to suit my needs. I cna try again, but if there's a way to get Xubuntu to work, let's do it!

Thanks!!!

Donald

---

### Post by Malakia on 2007-04-12
Try this link to help you set up your printer. I use it to get my Canon Pixma IP1500 to work. 

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon")

---

### Post by t2000kw on 2007-04-12
> **Malakia said:**
> Try this link to help you set up your printer. I use it to get my Canon Pixma IP1500 to work. 

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon")

I got to the point where it says to run this command, I assume in terminal:

# apt-get install libcnbj-2.2 bjfilter-2.2 pstocanonbj

and I get nothing. No error, either.

---

### Post by ramjet_1953 on 2007-04-12
Have you done this?

[COLOR="Blue"]For Ubuntu Users

If you are an Ubuntu (Edgy Eft) user, use the following apt-line.[/COLOR] 

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

The above is entered by clicking [COLOR="Blue"]System>Administration>Software Sources[/COLOR]
A window should open. Click on the [COLOR="Blue"]Third Party[/COLOR] Tab
Click [COLOR="Blue"]Add[/COLOR]
Paste the above link into the box that opens.

In a terminal type:

[COLOR="Red"]sudo apt-get update[/COLOR]

Type this in a terminal:

[COLOR="Red"]sudo apt-get install libcnbj-2.2 bjfilter-2.2 pstocanonbj
[/COLOR]

Regards,
Roger 8-)

---

### Post by t2000kw on 2007-04-13
It worked. I was doing something wrong before. When I copied and pasted these lines, it worked. Prints the entire page now.

Thanks!!!

---

### Post by t2000kw on 2007-04-19
FYI--I deleted the Linux partitions and tried SUSE Linux. There seems to be no way to get a pritner river to work properly under SUSE. And the help forums are not helpful at all. Here I got a few people who cared and were very helpful--so thanks to all of you!!!

I installed Ubuntu Fiesty Fawn this time. Before I even tried to install a printer, I did the apt-get thing. I then instaleld the i850 printer driver. Withuot goig back and reinstalling Feisty Fawn, I wonder if this driver was listed originally without my adding it???

The reason I ask is that, if I remember correctly, when I picked the working driver after all of your help, it had "PIXUS" listed as part of the name of the printer driver. Anyway, it's working. Not nearly as fast as the Windows driver for this model, but I was seldom in the "need for speed" anyway. 

I originally gave up on Ubuntu and instead went for Xubuntu because I got an error about something Gnome couldn't detect that could affect things like sound drivers and the like. However, I was able to play an audio CD from my CDROM drive, so sound seemed to work just fine. We'll give it a spin for a while and see how much is can replace Windows.

I'll have ot learn some about WINE and see if I can run my email program Agent with it with no problems. 

I'll have other questions, no doubt, but you all helped me get an important part of my system working. Next will be using WINE, and another will be the scanner. I did get that correctly identified under SUSE, so it can be done, I think, in Ubuntu.

---

### Post by dpar on 2007-04-19
I've been trying to get my i560 to work for months.........that link did the trick!!!!! Thanks very much.

---

