---
title: "Canon Pixma ip1700 compatibility"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Samit on 2006-12-08
I have a Canon Pixma ip1700 printer. It came with my computer when I first got it a few months ago. I ran Windows xp until recently but wiped it off my hard drive (deliberately) and now strictly use Ubuntu.

 I tried to set up my printer from System> Administration > Printing but it doesn't seem to run at all. The printer is connected to my computer, an emachines T5048 with a usb cable. When I attempted to "add printer" it appeared to recognize it, but when I completed the steps and attempted to print an email sent to me by my sister nothing happened. Is this printer incompatible with linux? Or is there an alternative way to get it working?

If it is completely incompatible, can anyone recommend a good linux compatible replacement?

---

### Post by riven0 on 2006-12-08
Samit, I think you may be out of luck. Look [here]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700").

However, HP works great with Linux. I've got one and I don't have a problem.:)

---

### Post by Samit on 2006-12-08
*Sigh* Thanks rivenO. I see my printer is a "paperweight." I'll start saving for an HP.

---

### Post by dalert0140 on 2006-12-08
You might want to try having ubuntu automatically detecting it a few more times.It took about five attempts for my Canon S520 to be recognized by the system.

---

### Post by crispy_420 on 2006-12-08
If you want a replacement, what do you need? 

If a Canon i850 as my color printer and it works fine. But a rarely use it. My main printer is a small laser one, Samsung ML-2010. And it is perfect for black & white prints (not photo). As a bonus it advertises linux support.

---

### Post by Samit on 2006-12-10
I would definitely need a full color printer. Sometimes my sister attaches pictures of my niece (I'll have a nephew soon too!) so I would like a printer that could handle this.

---

### Post by TheIdeaMan on 2007-01-07
Samit,

Do you still have your Canon Pixma iP1700? If so, there's hope for printing to it under Linux.

There is a free (for personal use) program called [Turboprint]("http://turboprint.info/"). There's a .deb package you can download and double click to run with the GDebi GUI installer.

After it's installed, you should be able to go to "System | Administration | Printing" double click "New Printer", choose "Local Printer", check "Use a detected printer" (hopefully), then click "Forward." On the next screen change "Manufacturer" to "CANON TurboPrint" (third line on the right for me). Choose the "Canon_PIXMA_iP1700 TruboPrint" driver from the list and finish the Wizard like normal.

From then on, you should be able to print without problems and be able to manage several setting on the printer as well.

Hope that either resurrects the paperweight or saves you buying a new printer.

---

### Post by atlien on 2007-04-09
Thanks dude!  This Turboprint info needs to be a sticky.  That guy thought his printer was a paperweight with Ubuntu (as did I).  And others joined in to tell him it was.  

UNTRUE!

Turboprint is easy to install and JUST WORKS.  Please believe me.  I have no idea really, what I am doing with Ubuntu and I just followed the instructions of the above poster and was printing in 2-3 minutes.  

TurboPrint is free for personal use and it works.

Ubuntu 6.10 is what I am using.

---

### Post by majinebrain on 2007-04-16
I installed the TurboPrint debian package file from the website.  And my printer, Canon iP1700, prints.  Just one problem.  I get an annoying BANNER stuck randomly on the printed page.  Is this something just added in the newest version?

---

### Post by ramjet_1953 on 2007-04-17
I'm afraid that is what you get with the "free" version of TurboPrint.

You'll have to shell-out some cash to get rid of the banner.

Regards,
Roger :cool:

---

### Post by lemmy999 on 2007-04-17
Can i suggest you try the following thread. It worked for my IP1000 and may work for your 1700

[http://ubuntuforums.org/showthread.php?t=335655](http://ubuntuforums.org/showthread.php?t=335655)

---

### Post by sjh874 on 2007-06-21
I've recieved these instructions from Lobotomize.....
From the terminal:
Code:
$ sudo gedit /etc/apt/sources.list
---------
then at the end of the file I inserted:
Code:
# Canon print package
deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./
---------
next, from the terminal
Code:
# sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
---------
Make sure to run 
Code:
$ sudo apt-get update

only thing that goes wrong is that after I enter the Install line I get this....

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libcnbj-2.6

I mean from my standpoint (one who is merely beginning his journey into the realm of Linux) It appears that the file source dosn't exist anymore... Is that correct? is there any way to check?

If there are any better instructions to follw for making a Canon ip1700 work w/ Ubuntu please feel free to let me know.

Thanks for all the help!

---

### Post by Repent on 2007-06-21
Like others have suggested use turbo print, it's what I had to use to get my Canon printer up and running.
No matter how you look at it it's cheaper than buying a new printer and it flat out works.

---

### Post by Candace on 2007-06-30
Hi everyone,

I have tried the suggestions on this page to get my Canon ip1700 working with Ubuntu 7.04 and no luck. Does anyone else have a Canon working in Feisty Fawn? Perhaps something has been changed so these instructions no longer work...I downloaded the driver from Canon for the ip2200 and I CAN print from tomboy and text editor and from emails but NOT from pdf files or from openoffice.

I also tried downloading the .deb version of turboprint ([http://turboprint.info/](http://turboprint.info/)) and I get an error message to the effect that my architecture is i386 not AMD64. I don't think that is correct, at least in Windows (I am dual-booting) my architecture on my laptop came with amd64. Does anyone know how to get a Canon working with i386 architecture?

I need at least version 1.95-1 of turboprint because that is the one that supports my printer - Canon ip1700. I have tried both versions of the download from turboprint (for the powerPC and for the intel 64) and neither work for me. 

If anyone else has gone down this road - help would be appreciated.

---

### Post by Candace on 2007-06-30
Hi,

I finally got my canon pixma ip1700 working in ubuntu 7.04 with turboprint!!  (I used the driver here:  [http://turboprint.info/](http://turboprint.info/) and I downloaded the .tgz version of 1.95-2).

I am happy that it works, so I want to buy the licensed version, and (sorry I am a newb), can anyone tell me where to find the option to change from the free version to the registered version of turboprint, once I get the key?

Thank you.

---

### Post by t2000kw on 2007-07-28
This may be helpful for some of you. Not all of the printers being discussed are directly supported, but the driver for the i850 works OK, not full-featured like the WIndows driver, but it works at 600 x 600 dpi in color. 

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

---

### Post by dragonwings on 2007-07-29
[http://ubuntuforums.org/showthread.php?p=3007416#post3007416](http://ubuntuforums.org/showthread.php?p=3007416#post3007416)


Note not just for ip1000 read through theres a link for more drivers your printer is not listed just try differnt drivers till one works i suggest the ip4100 for a start.

---

### Post by Warren North on 2007-11-16
It is sad I get this far and I finally got Ubuntu to print and I get this banner and the only way is to pay for a filekey to get it removed. I can not believe with all the free stuff with linux. Then turbo print jumps in and offers a driver for $40 WTF???
I feel like I just entered the twlight zone. I almost thought I could leave microsoft stuff for good. But there is always a catch. There has got to be a free bee for the Printer Ip1700 Pixma, printer no banner, no pay, If I could get my Epson 2480 scanner and Ip1700 canon printer to work I would be free of the WIN OS. I should not have to pay for a small driver.
It is 2007 and we still have to go through this. If I pay I guess I pay. my point is so much can be charged then the advantages fade.
Still I am very impressed with Ubuntu. I know there is got to be a work around.
Thanks

---

### Post by t2000kw on 2007-11-16
If anything, blame the manufacturers, not Linux. Manufacturers have not looked forward to see that Linux is becoming more and more popular. Manufacturers provide drivers for the market they intend to reach, and some don't care about Linux--YET!!! This will change and as companies provide Linux drivers for their printers you will see the first one that does so become the king in the Linux community. It's just a matter of time as we find out that Microsoft has one after another vulnerability in their XP and Vista operating systems. One went on for a very long time before it got addressed. 

There are free drivers out there, you just have to do the research and find them. Canon Austrailia has some Linux drivers. It is listed as a "paperweight" but it also appears that the driver for the IP2200 will work with some changes to a file:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700)

If you plan ahead for your next printer, see which ones are supported in Linux, whether by manufacturer-provided drivers or open-source. Then buy one that is supported. 

My Canon i850 was detected and set up with the latest Ubuntu Gutsy--Feisty didn't see it and I had to do research and find a useful driver for it. That's taken care of for many printers with the Gutsy version, so if you're using an older version, consider upgrading. Back up your /home directory or partition (a /home partition is better) before you do, and if you've heavily customized your OS expect some bumps along the way. I had to wipe out everything and start over, then restore what I had in my /home partition.

---

### Post by Warren North on 2008-04-15
My ip1700 works now I got a cups driver using 2200 ver 2.60 recently downloaded.
Yes finally free printer, no banner bs. One step close to abondon windows forever.
I just need the epson scanner to work which it did once but that I address in another post.

---

### Post by Warren North on 2008-04-17
Finally I got a 2200 v2.6 driver form cups update. Now it works for free.
Whew one step closer.
All I need it to get my Epson 2480 scanner to work and that will be slammin.

---

### Post by hotpinkflamingo on 2008-04-18
Warren, where did you get the driver please?  I've tried everything in this thread, and the only thing that works is Turboprint and paying $40 for a driver is out of the question.

---

### Post by Erik765 on 2008-04-19
Ok, here's what I did to finally get it to work for FREE!
Download the turboprint evaluation[http://turboprint.info/]("http://turboprint.info/") 

Then follow these instructions (I had to install alien with synaptic first)

[https://answers.launchpad.net/ubuntu/+question/22555]("https://answers.launchpad.net/ubuntu/+question/22555")

Then go to CUPS at 127.0.0.1:631 and select 'manage printers', 'modify printer', 'continue', 'continue', then change the selection from 'CANON Turboprint' to 'canon' select 'continue' select 'Canon iP2200 Ver.2.60 (en), select 'modify printer'.

Voila.
You will now print (with no turboprint logo), well, atleast I did. As far as it not working in openoffice, not sure what to do here. I updated to 2.4 with no luck. I can print from pretty much any other program but those.

Good luck

---

### Post by hotpinkflamingo on 2008-04-19
Thanks a lot for your reply.  I did everything to the letter, and it didn't work for me sigh......

---

### Post by Erik765 on 2008-04-19
Have you tried restarting cups after you finished making the changes?

sudo /etc/init.d/cupsys restart

Give that a shot.

;)

I know this printer works with Linux, I had it working fine under Fedora 8.

---

### Post by hotpinkflamingo on 2008-04-20
Yes, I did restart cupsys.

---

### Post by Golem XIV on 2008-04-20
OpenSUSE has a package called *ddiwrapper*.  It uses Wine in order to run XP drivers for unsupported printers.  Apparently at the moment it only supports Canon drivers (including the iP1700).

You will probably have to download the source code and recompile it for Ubuntu.

---

### Post by rouge568 on 2008-04-23
Just found this out today - turboprint has no logo if printed at the lowest resolution possible. My iP1700 is now working!

---

### Post by sebovespa on 2008-06-24
but wy we need to purchse license?? how to print my note act:)

---

### Post by sebovespa on 2008-06-24
erik. i didnt found ip2200 on the list to modify.

---

### Post by sebovespa on 2008-06-24
tq rouge n both of u. it beutifuly no more logo by turning to 1-300dpi.
lala..la.la..

---

