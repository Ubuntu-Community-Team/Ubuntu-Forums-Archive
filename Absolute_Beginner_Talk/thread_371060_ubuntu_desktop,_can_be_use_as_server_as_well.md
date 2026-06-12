---
title: "ubuntu desktop, can be use as server as well?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by warriore on 2007-02-26
Hi, I'm tottally new tu linuc and ubuntu, and I am just about to install ubuntu server with LAMP on a dell laptop, and I was just wondering, if ubuntu desktop was also able to be setup partially as a server with LAMP , as I would really like to start using a linux desktop as well to see what its like, but need to run the LAMP server. please advice, thanks in advance.

Ty

---

### Post by bodhi.zazen on 2007-02-26
Yes. Install Ubuntu desktop and then set up APM (L=Linux=Ubuntu desktop :) )

---

### Post by netkid91 on 2007-02-26
Yes, Ubuntu Desktop can be a server too.  The only difference on the install CD's is the server come with the server packages on it, and lacks the UI.  To install all of the server stuff, open a command prompt and type:
sudo apt-get install ubuntu-server
And you'll be set.

---

### Post by houstonbofh on 2007-02-26
If you install a LAMP server from the server CDs, you just need to run;
```
sudo apt-get install ubuntu-desktop
```
You now have a full desktop.  Also, consider that the linux command line and config files are absolutely dependent on syntax.  Capitalization and even spaces count.  From the look of your first post, this might eventually be a problem for you if you don't watch for it.

---

### Post by warriore on 2007-02-26
ok, thanks guys...so just pop in the ubuntu server cd that I have already burned and after installing it go to a command prompt and type in the:

 sudo apt-get install ubuntu-desktop

? 

also will I be promted to repartision the harddrive, because I have windows on it now and would like to get rid of all the data that is on it, will there in an option to erase the old os withits data and allocate 100% of the space tu ubuntu? 

If you could provide me with a step by step for the first part to get the desktop installed I would appreacite it. 

thank you all very much for your help.

sincerely,

ty

---

### Post by bodhi.zazen on 2007-02-26
Start here :

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by stokedfish on 2007-02-26
Sure, it can be.

If it makes sense or not is another question tho...   ;)

---

### Post by warriore on 2007-02-26
I just inserted the cd with ubuntu 6.06.1 s and restarted the computer, nothing happened, the windows os loaded normally...what am I doing wrong? I followed all the instructions on how to download, verify and burn the ubuntu cd...please advise

thank you!

ty

---

### Post by netkid91 on 2007-02-26
It's not booting from the CD, check you BIOS and setup the CD drive as the first boot device.

---

### Post by warriore on 2007-02-26
do I need to press something on my keyboard to boot from the cd rom? I tried it 2 times now and windows is loading normaly without the ubundu install kicking in...please advise as to what I need to do to boot the computer from the cd rom and install ubuntu...thank you

---

### Post by bodhi.zazen on 2007-02-26
You need to set up your BOIS to boot to CD ....

As your system boot hit Esc and all the F keys (F1, F2, .....)

---

### Post by warriore on 2007-02-26
I can imagine that it pust be painful for experienced programmers to answer silly questions, but I asure you, it is very painfull for a beginner to get his arms around this stuff. If you guys could be patient and do not assume, I would really apreciate it, to be honest, I don't even know where to look up the BIOS or set the cd as the first device...please advise...thanks for your patience guys

ty

---

### Post by warriore on 2007-02-26
ok thanks a lot, I'll try that! ty

---

### Post by Motoxrdude on 2007-02-26
> **bodhi.zazen said:**
> You need to set up your BOIS to boot to CD ....

As your system boot hit Esc and all the F keys (F1, F2, .....)

Try booting and press Esc, if that doesn't work restart and try F1, restart F2, restart Print Screen, until one works. Then look around for something that says "Boot order" and make sure your cdrom drive is before your hard drive on the list.
;)

---

### Post by warriore on 2007-02-26
as I pressed the esc and the f keys nothing happens I only get a prompt from windows asking in what mode do I want to load windows in, that is it...I guess I need to do the BIOS thing, if you could tell me where to go I would preciate it..thanks!

ty

---

### Post by netkid91 on 2007-02-26
Delete is another common key try it.

---

### Post by warriore on 2007-02-26
the delete key did not work either, hmmm, where do I look up the bios order boot? thank you guys

I just installed irc and I'm in the #ubuntu chat room if any one can go there and chat from there, seems easier....

---

### Post by RbikeRider on 2007-02-26
You can manually boot from CD by pressing the corresponding F-key.  Example: Continue pressing F12 on Dell computers when computer restarts will bring up a boot option and you can select CD ROM.  You may need to google for the documentation for your model computer to find which key lets you manually select the boot device.  Also - Make sure the CD you are using was burned from the ISO as an ISO disk instead of just burning the ISO to the CD.  Good luck.

---

### Post by warriore on 2007-02-26
thanks, you the man! a proper answer! really apreciate it! thanks

ty

---

### Post by bodhi.zazen on 2007-02-26
LOL I am happy it is working

I would have thought that F12 was one of the keys I advised :

> As your system boot hit Esc and all the F keys (F1, F2, .....)

:lolflag:

---

### Post by warriore on 2007-02-26
F12 did the magic trip! thanks to all you guys

---

### Post by warriore on 2007-02-26
:) I gave up on F8 and wanted to through the computer out the window :) thanks for your help, my bad

---

### Post by warriore on 2007-02-26
hi stockedfish, can you ilaborate on your comment please? see, I just want to get the server side up and running and use it to dvelop my website, and just as I am know looking at the installed ubuntu server screen, that is waiting for proper server commands to do things, I get a headache just looking at it, so I was hoping that the desktop would provide me with the UI through which I can still control the server and do the things I need to do, internet connection, upload files, set upthe mail server, etc...with little bit more easy....now, it could be that I'm being totally delusional and such a nifty setup is just not realistic, being new to programming and unix etc. I'm fishing around for the best, easiest, setups I can get my hands on....so I would love to hear from you and your thoughts? thanks

ty

---

### Post by RbikeRider on 2007-02-26
Its been a while since I have used Webmin, but it worked great on Fedora.  There is a debian package available for download: [http://www.webmin.com/download.html](http://www.webmin.com/download.html).  Just to make sure I posted something correct, I quickly installed Webmin on my Ubuntu system, which seems to work fine.  Here are the steps you will need to get this working.

1. Download debian package from link above.
2. From your desktop double click the downloaded debian package to begin installation.
3. Once installation is complete, open browser and enter the following address [https://localhost:10000](https://localhost:10000)
4. Log in using "root" as user name and your root password for your system.

I just noticed the webmin interface has changed since I used it last, but I did find that you can make the interface look similar to the website's view.  Hope this helps.  (Once you get this installed, you can access webmin from another computer on your network by replacing "localhost" with your Ubuntu's IP address)

---

### Post by houstonbofh on 2007-02-27
Almost all of the server programs are done with config files.  However, being able to have a web browser open while you change them is nice. :)

---

### Post by warriore on 2007-02-27
before i got your post, i installed the ubuntu desktop after i installed the ubuntu lamp server...since I the desktop does it still make sense to use the webadmin or is there another tool on the desktop that will let me administer the server? thanks a lot 

could someone dirrect me to a solid resource for learning how to administer properly all aspects of a lamp server, getting the site up and running, cinfig the email server, etc....it seems to be hard to find a good source, or a one stop resource that expalins everything in steps and really guides you through things....if you know please let me know...thanks for all your help so far...by the way, i really like the ubuntu desktop, i hope i never have to go back to windows :)

---

### Post by bodhi.zazen on 2007-02-27
> **warriore said:**
> could someone dirrect me to a solid resource for learning how to administer properly all aspects of a lamp server, getting the site up and running, cinfig the email server, etc....it seems to be hard to find a good source, or a one stop resource that expalins everything in steps and really guides you through things....if you know please let me know...thanks for all your help so far...by the way, i really like the ubuntu desktop, i hope i never have to go back to windows :)

Start here, there are several references ...

[http://www.ubuntuforums.org/showthread.php?t=371653](http://www.ubuntuforums.org/showthread.php?t=371653)

---

