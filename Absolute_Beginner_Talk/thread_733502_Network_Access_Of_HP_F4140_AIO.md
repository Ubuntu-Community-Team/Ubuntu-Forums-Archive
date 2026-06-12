---
title: "Network Access Of HP F4140 AIO"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by wpqc213 on 2008-03-23
I am attempting to use a networked printer here with my Ubuntu workstation. The printer is connected to a Windows XP Pro station via USB cable. I have set up the networking so as to be able to access files from the XP machine and vice versa but I cannot for the life of me get it to print.I have installed( or at least attempted to install) the files from HP that are actually on a Source Forge site.

I have selected the F4100 MFP driver file as that is as close as I can match for the printer I have. Any ideas anyone??  What have I missed or done wrong??
For the record my Linux machine can see the F4140 and says the share is accessible.

Thanks In Advance For Any Help!

Wayne

---

### Post by mikeyphi on 2008-03-24
Can you confirm that this site is where you got the driver?
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

---

### Post by wpqc213 on 2008-03-24
Yes, This is the location I was referred to from HP and the page I downloaded the installer from.

Thanks!

Wayne

---

### Post by mikeyphi on 2008-03-24
I suggest you try to install again.

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Use the HPLIP Installer - be sure to follow the site instructions exactly!! 

Remember that when you've moved the downloaded file to the required directory you will have to navigate to that directory in a terminal before using the "sh hplip-2.8.2.run" code. 
After that using the GUI should be OK to follow.

---

### Post by wpqc213 on 2008-03-24
I think that may be where the problems are starting. I remember getting several errors at one try. They were mainly saying there was no such file, no rule to install and so on.
I will give the install another shot tonight when I get home and report back. BTW when I download the files it is saved to desktop.

Thanks for the information and help!

Wayne

---

### Post by wpqc213 on 2008-03-25
Still having trouble getting the software to install. I get numerous errors most frequent is
that several dependencies are missing. When it attempts to force a build of those files it errors after a period saying there was no output within a specified period. Also one error  was wanting the repositories enabled. I followed that link and made the requested changes but it still does not complete the install.

I may be fighting a loosing battle with this but I will continue to try to beat it LOL!   From what I just read at the driver web site it looks as if network support is not possible with this printer on Ubuntu.From what it reads under the Direct Jet/Network tab the answer is NO.

Wayne

---

### Post by bbarrons on 2008-05-23
not sure if you got this to work or not but I have the same setup and have mine working. It wont do any scanner work thru the network but prints fine all day long. would you like the setup info to do it?
Bill B

---

### Post by wpqc213 on 2008-05-23
> **bbarrons said:**
> not sure if you got this to work or not but I have the same setup and have mine working. It wont do any scanner work thru the network but prints fine all day long. would you like the setup info to do it?
Bill B


Thanks Bill !
I would love to get the setup info from you on this!

Wayne Thomas

---

### Post by bbarrons on 2008-05-23
I have had this working since 6.06 I had to setup the windows xp box to share the printer and then got properties and turn off bidirectional support. you will find that on the ports tab right after sharing.
I then went to my linux box and opened up system settings and went to add printer. choose smb shared printer  click next . here is where I dont remeber if it was an anonymous login or guest, try either one.
then next, and I gave my xp box a static ip address because I didnt want to change this ea time it got a new address. I put in the static ip address of the xp box and the next line is what you named the printer in xp.
It will ask for a driver and I chose F4100 from the list.  finish and print a test page. if your printer reacts but still doesnt print then at least you are talking to it. That is how I found out that directional support had to be turned off. When it is off your printer wont tell your xp box when it is out of ink but I can deal with that.
I hope this makes sense I had to do most of this from memory but I have had 2 different linux boxes ( 1 ubuntu, 1 kubuntu) printing.
Dont waste your time trying to get the scanner to work.
 hope this helps.
Bill B

---

### Post by bbarrons on 2008-05-23
I have a server setup I was working on. I will go thru the ssetup I outlined and then post back to how it works.
 Bill

---

### Post by bbarrons on 2008-05-23
the ppd file you need is not in the current list. I was not able to get the printer to work until I downloaded the ppd file for a F4100
 here is the link   [http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-DeskJet_F4100&show=0](http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-DeskJet_F4100&show=0)
 when you setup the printer use guest as your account and when it asks for a driver go to other and select the location you saved the f4100 ppd file. works like a charm then.
 Bill

---

### Post by wpqc213 on 2008-05-23
Thanks so much!
I will get on this project tomorrow and get it up and running with the info you provided!

Wayne

---

### Post by bbarrons on 2008-06-18
Hi Wayne,
 were you ever able to get it to work?
 Bill

---

### Post by wpqc213 on 2008-06-18
> **bbarrons said:**
> Hi Wayne,
 were you ever able to get it to work?
 Bill


Yes I did!! Thanks for the help! Sorry I didn't get the reply back sooner!
I had everything running just fine but I had to
switch some equipment around for my PWS and had to off line that particular machine for a short time.

It does all I need it do do!
I only wish my weather software had Linux support!

Thanks,
Wayne

---

