---
title: "Installing ubuntu into a _OLD_ computer"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by avatar3 on 2006-02-18
Hey, i was wondering could i install Ubuntu (Without X) to my old old computer and just run irssi on it ? I tried with the install CD but the crappy computer cant boot from CD-Drive and i cant get into BIOS. So is there a way install it via disket or something ? 

-Avatar3

---

### Post by Klaidas on 2006-02-18
When your computer boots, press delete or escape button, that should get you into BIOS :)

---

### Post by az on 2006-02-18
[QUOTE=avatar3]Hey, i was wondering could i install Ubuntu (Without X) to my old old computer and just run irssi on it ? I tried with the install CD but the crappy computer cant boot from CD-Drive and i cant get into BIOS. So is there a way install it via disket or something ? 

-Avatar3[/QUOTE]
You can find smart boot manager (SBM) on the install cd.  In the install directory.

Use rawrite in windows if you are not alreay using linux (use dd) to write the file to a floppy and then boot it.

It should find your cdrom and you can boot it.


How old is your computer?  What are the specs?

---

### Post by Ghetto_Smurf on 2006-02-18
how OLD is your computer? if THAT old i would recomend a server install (no X), and then, if you need X, download xfce or fluxbox

---

### Post by avatar3 on 2006-02-18
Klaidas: Ive tried it and all the F buttons

its really old..

Processor, no idea.. its some amd that hasent even got a fan..
RAM,   24mb
Hardrive, 2GB
CD-ROM, something crappy
and all other parts are the same class.. 


And its currently running NOTHING. it used to have a windows 95, but then my friend formated it.. and then he lost his nerves with it and gave it to me ^^

---

### Post by montablac on 2006-02-18
i used to have a computer like that

sept i had two HDDs

but any way

you wont be able to run 5.10,not enough ram

try 5.04

that worked for me,then when i went up to 128k ram i installed 5.10 with no problim

---

### Post by Ghetto_Smurf on 2006-02-18
i dont know about 5.04, but 5.10 needs at leats 64mb for a server install. perhaps 5.04 will be a better choice

---

### Post by Lord Illidan on 2006-02-18
Or forget Ubuntu and use Damn Small Linux.

---

### Post by Ghetto_Smurf on 2006-02-18
Lord Illidan, that depends on wether he want ubuntu or not. not impossible, but hard to get ubuntu on that pc

---

### Post by Lord Illidan on 2006-02-18
[quote=Ghetto_Smurf]Lord Illidan, that depends on wether he want ubuntu or not. not impossible, but hard to get ubuntu on that pc[/quote]

On 24 mb? No offence, but I'll believe it when I see it. Even if it works, it will be darn near unusable.

---

### Post by patrick295767 on 2006-02-18
[QUOTE=avatar3]Klaidas: Ive tried it and all the F buttons

its really old..

Processor, no idea.. its some amd that hasent even got a fan..
RAM,   24mb
Hardrive, 2GB
CD-ROM, something crappy
and all other parts are the same class.. 


And its currently running NOTHING. it used to have a windows 95, but then my friend formated it.. and then he lost his nerves with it and gave it to me ^^[/QUOTE]
  
  
With a 24mb of Ram, u can forget about Breezy [-(  And this for sure.
Or u can only use: XDMCP to connect of a faster PC
  
Breezy is made for PC with >=128MB and CPU >=~ 400-450Mhz
  
U can use this old PC as a Linux Server Installation (no X).
  
I would recommand you older version of Linux. 
If you'd like I can provide you the corel linux from 1999 about
with netscape. 
U can try to change and update things on it if you are rather good in Linux. 
(It's not easy).
  
Or other distro... Damn small Linux works pretty nice.
  
Also, Imagine that the guy who created the FVWM desktop long time ago, that was meant for pc with low ram 4 or 8MB, if I recall well.
  
Good Luck

Greetings,

Patrick
==========
(My Old PC; compaq presario 1685 64MB ram used with xdmcp on a server linux (everthg works with scripts) and this pc is running very fast (via xdmcp).

---

### Post by patrick295767 on 2006-02-18
[QUOTE=Ghetto_Smurf]Lord Illidan, that depends on wether he want ubuntu or not. not impossible, but hard to get ubuntu on that pc[/QUOTE]
  
It depends what he wanna do (if he can afford waiting waiting ... ): if it's dillo and twm desktop, that can maybe be overcome (with hoary)... 
...
Worth to try !
  
Let us know the resutls of ur installation.
  
Patrick

---

### Post by george_apan on 2006-02-18
I think that you could at least try ubuntu and see how it goes. I actually believe that it would work. irssi is only terminal based and you could try a server install and then install only that and maybe a couple of more terminal apps that you'll need. Of course forget anything about a gui but since you don't need one you should be OK.

About the booting issue, use a smart boot manager (SBM) floppy. I have the same problem on my laptop, I cannot boot from the internal cd-rom since I replaced it and SBM works perfect.

---

### Post by avatar3 on 2006-02-19
How to install that smartbooteditor? Didnt really get it inthe homepage..

And please if you can provide the old linux :)

---

### Post by george_apan on 2006-02-19
On a windows machine download the sbminst.exe from here:
[http://btmgr.webframe.org/3.6/sbminst.exe](http://btmgr.webframe.org/3.6/sbminst.exe)
and the support file from here:
[http://btmgr.webframe.org/cwsdpmi.exe](http://btmgr.webframe.org/cwsdpmi.exe)
and put them in the same directory
Then open a command prompt window and cd into that directory. You then type 
```
sbminst -d 0
```
in the command prompt while having a blank floppy disk in your floppy drive.
Reboot your computer, get into your bios settings and set it to boot from your floppy. That's it. SBM will load and you will have the option to boot from your CD.

---

### Post by avatar3 on 2006-02-20
george_apan: 

I am not really that good with computers.. And the computer is now running with nothing ("format C:") Isnt there anykind of step-by-step wizard available ? :-|

---

### Post by george_apan on 2006-02-20
What kind of computer are you on right now? Is it a windows machine? Or a linux one? Does it have a floppy? If it is a windows machine and it has a floppy drive download the two files that I linked above. Put them in C:\
Now open a command prompt window. I think you can find that under Start/Programs/Accessories/Command promt.
Now that you have a black command prompt window open put a blank floppy in the drive and type
```
cd \
sbminst -d 0

```
pressing enter after each line.
That's it. You should have created the floppy by now. I don't think I can make it easier.

If you get stuck somewhere post you problem here.

---

### Post by avatar3 on 2006-02-20
George: 

It is a windows machine, i did all you said. But when i get to the command prompt it doesnt work, it just gives somekind of "Not such command" or etc..

---

### Post by george_apan on 2006-02-22
OK, we'll have to see what you're doing wrong.

1. Where did you download the above files? Are they in C:\? That is, if you click on the "My computer" icon and then open your harddrive, do you see them in there, along with "Program Files" and "Windows"? Are they both there?
2. When you open the console what prompt do you get? You should be getting a ```
C:\>
```
prompt followed by a blinking cursor. If it is something like ```
C:\something\else
```
you should type ```
cd \
```
in order to go to C:\. OK?
3. Are you sure you're typing the command like this? ```
sbminst -d 0
```
Check for typos. If you're getting a "Bad command or file name" error here, either you're not typing everything right, or you do not have the files in C:\.

---

### Post by avatar3 on 2006-02-23
George, i have them in folder C:  And ive done all as you have said and i still get this : "sbminst wasnt regocnized as a internal or external command line", or something.. (my bad english :-k )

Any more ideas ? :cry:

---

### Post by T_Stormcrowe on 2006-02-23
I'm currently running Hoary on an old PII machine, I have 1.2 gig HD and 128meg RAM. I upgraded it to 128 from 64 meg due to machine freezing up from insufficient RAM. The only problems I'm currently having is it WILL NOT recognize or mount the fd. I finally got sick of it and just dropped in a USB and use either a jump drive or cd-RW. Then unit works fine in this config and I'm happy to get some use out of the ol' 'puter again! I think you are WAY short on RAM for Ubuntu, and can only offer the suggestion of DSL as mentioned above!

---

### Post by george_apan on 2006-02-23
[QUOTE=avatar3]George, i have them in folder C:  And ive done all as you have said and i still get this : "sbminst wasnt regocnized as a internal or external command line", or something.. (my bad english :-k )

Any more ideas ? :cry:[/QUOTE]
That shouldn't happen!:-? 
Try typing ```
C:\sbminst.exe -d 0
```
You actually type C:\ after the C:\> prompt. Do you get the same message?

---

### Post by avatar3 on 2006-02-23
Doing all you say, but still wont work. Gives the same error.. Is there any other way than this ?

---

### Post by george_apan on 2006-02-23
[QUOTE=avatar3]Doing all you say, but still wont work. Gives the same error.. Is there any other way than this ?[/QUOTE]
It should be working! Try launching the run window with Start/Run... and typing ```
c:\sbminst.exe -d 0
``` as before in the window. I don't get it at all.
Can you try downloading the files again? Maybe you had a corrupted download. And could you possibly try it on some other PC? Maybe you have a virus or something that gets in the way. Other than that, I can't think of anything else...:confused:

---

### Post by george_apan on 2006-02-23
And maybe you could try downloading the disk image (or copying from the ubuntu disk) and using rawwrite as in this HOWTO:
[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

---

### Post by Iowan on 2006-02-23
> And its currently running NOTHING. it used to have a windows 95, but then my friend formated it.. and then he lost his nerves with it and gave it to me ^^ > It is a windows machine,Maybe this is a silly question, but you DO mean actual Windows - not a DOS box?  Or does it even have DOS? Without that, there will be no Start/Run, no Program Files... etc.

---

### Post by avatar3 on 2006-02-25
Iowan, the computer that we are currently trying to install linux isnt running anything.. but the computer where i am now is a windows XP..

George_apan: i will try that. btw, thanks for the help this far :)

---

### Post by pytron on 2006-02-25
I think RAM is going to be your big issue.  I got Ubuntu 5.10 installed on a AMD K-6 (Pentium 2 equivalent) 400 MHz.  But it had 160MB of RAM (later upgraded to 384).  It took a long time (a few hours) to install.

---

### Post by avatar3 on 2006-02-26
George: i got the disket working now. But when i put it into the computer, it boots normally and then starts to read from the diskett and gives this.  "SBMK Bad!" And then nothing happens?  What could be the problem ? Should i try damn small linux ?

---

### Post by george_apan on 2006-02-26
At least we have something working! :) Now, I haven't seen this kind of error before but I found this with a bit of googling:
> We found a comment in a Web forum that SBM is finicky. The author, Jeffrey Cunningham, suggested that when you create the SBM floppy, you should immediately write-protect the disk. When SBM prompts you to "save changes," you should respond with 'n.' If you allow SBM to write to an unprotected floppy, the next time you boot you will get the "SBMK Bad!" error message.
Source: [http://www.networkworld.com/columnists/2005/022805gearhead.html](http://www.networkworld.com/columnists/2005/022805gearhead.html)

So you'll have to create the disk again as you did before and write-protect it at once, that is move that little plastic thing on the side until there is a hole. Does this work?

---

### Post by clarkth on 2006-02-26
[QUOTE=pytron]I think RAM is going to be your big issue.  I got Ubuntu 5.10 installed on a AMD K-6 (Pentium 2 equivalent) 400 MHz.  But it had 160MB of RAM (later upgraded to 384).  It took a long time (a few hours) to install.[/QUOTE]

This is my first post.  I just installed Ubuntu 5.10 onto an old PII 300 MHz computer with 256 MB of RAM and an 8 GB HD.  The install took a while, but no major problems and everything is working fine. :-D

---

### Post by HedgeHog74 on 2007-08-14
> **clarkth said:**
> This is my first post.  I just installed Ubuntu 5.10 onto an old PII 300 MHz computer with 256 MB of RAM and an 8 GB HD.  The install took a while, but no major problems and everything is working fine. :-D

Hope this works, as I am having the exact same error message booting from my sbm boot disc.  BRB, going to try this...

HH

My computer specs:

D-I-T Corporation
VIA Technologies, INC.
VT82C692BX
Award Modular BIOS V4.51PG (Firmware hasn't been upgraded- couldn't find any!)

Intel III 600Mhz (card mounted)
384 MB RAM (128MB x 3 slot banks)
3 hard drives (internal)- 13.5GB (from my old AMD K-6 3D machine, put on internal IDE ATAPI), 20GB, and 60GB drives (I'm going to use to 20 meg for Ubuntu...both are on IEEE SCSI Controller PCI card)
Creative SB Audiology 2 Value (24-bit) - PCI
NVIDIA GeForce4 MX 4000 (64MB) - PCI
Linksys LNE100TX(v5) - PCI - connected to router and then to cable modem.

Generic 110 - key keyboard
Pilot Mouse Optical (Kensington)
SyncMaster 191T

All drivers have been checked and updated from either a third party web site or from the manufacturers web site, so no drivers are out of date or in conflict (that I know of)

---

