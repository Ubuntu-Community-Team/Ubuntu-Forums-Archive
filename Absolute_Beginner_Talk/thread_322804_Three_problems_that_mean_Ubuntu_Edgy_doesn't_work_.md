---
title: "Three problems that mean Ubuntu Edgy doesn't work for me."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Philip_Crookes on 2006-12-21
I'm a willing user of Ubuntu Edgy, I'm keen to get Windows out of my life and my computers.

But there are three issues that demonstrate just how far Ubuntu, and maybe Linux,  has to go to be acceptable outside a community that's geekier than I am.

1. Printing and scanning.

1.1 I have a Brother HL1240 printer, and have installed the HL 1240 ppd file from the Brother website. The printer accepts the first job sent to it, but then locks up. I have to unplug it for ten seconds and plug it in again before it will accept another print job. I've searched for this problem without result, and asked about this in Linux discussion areas but nobody has replied. So a printer that worked perfectly in Windows XP doesn't work properly in Ubuntu Linux on this machine.

1.2 I researched good photo printers for Linux and chose the Epson R800. After a great deal of hassle, I've installed the printer under CUPS Foomatic. Except that although it shows up in the printer list, and claims it's printing, nothing actually prints. So a brand new printer, installed according to the rather badly written documentation I downloaded, doesn't work in Linux.

1.3 I have a Microtek 4000tf film scanner. It works well in Windows. It doesn't work at all in Ubuntu. I've asked without result about this in Usenet alt.os.linux.ubuntu, and searched far and wide in the Linux and Ubuntu forums and discussion groups, but apart from an archived newsgroup posting in French saying how well it works, I've found nothing. The writer of the French email is no longer available at that address to describe what he did to make it work so well.

2. Networking. I have a router that links our various computers together. One of those computers runs Windows XP, and houses the playout system for our small radio station. I would like to be able to use my main computer (this one, in the den, running Ubuntu) to listen to and edit sound files, and write them back to the Windows computer. While I can see the files on the Windows computer, and transfer them to and from the Unbuntu machine. I can't listen to them and can't edit them without transferring the file, working on it, saving it to the Ubuntu machine and then transferring it back to the Windows machine.

I have looked into the concept of mounting a Windows network folder, have religiously followed various sets of instructions that seem to be about doing more or less that, but none of it works. I have tried to add a line to /ect/fstab. I get error messages like 'smb connection failed', which is just one step better than CP/M's infamous BDOS ERR ON A.

What's more, I can't see my other Ubuntu machine on the network. So networking looks to be a lot easier in Windows than it is in Linux. I don't know enough to be able to know where to look to find whatever it is that I am missing.

I've asked about this in Usenet and in ubuntu forums, but nobody has replied.

3. Sound editing software. Like many people, I've been using Audacity for simple sound editing. But for some reason, the version of Audacity that can be installed in Ubuntu is much older than the one that can be installed in Windows. This may be the reason that there seems to be a conflict with the sound system that means if I want to load and edit a sound file, I have to go into System/Preferences/Sound and turn of 'enable software mixing", at which point other sound functions may stop working.

I read somewhere that if I download and compile the newer Audacity, this may not be a problem any more. I don't know how to compile a program, and nothing I that I know about and have here tells me. 

I've bought books on Ubuntu, but they tend to be about earlier versions, self-congratulatory and uninformative. I've written books on computer topics before, but I don't know enough to write my own book about this.

The Ubuntu Edgy Guide at [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) is no doubt a labor of much love, and contains interesting information on a number of things. But there is no topic search, and the paragraphs seem to be arranged by when they were written rather than what they are about, which makes it fairly unusable. And no, I don't know enough about it to fix it.

I agree that everything that is wrong is my fault, that I have made some mistake or misunderstood something or just not known something that is common knowledge among others. It's just not common knowledge among me.

I'm posting this is alt.os.linux.ubuntu, and in ubuntuforums.org in the hope of stirring up some answers that will actually solve these seemingly undocumented problems

Should I be moving to another Linux distro? Please don't waste time telling me to get a Mac or go back to Windows. I don't like Apple or its locked down proprietary DRM'ed products, and I don't want to go back to the offensive and expensive paranoia of Microsoft. 

Philip
.

---

### Post by deadgobby on 2006-12-21
Holy cow there. I would start off with Ubuntu wiki site
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
You can find most of the program in synaptic. You could try different linux O/S systems. Suse has great HW detection, but can be a little tricky to add on extra repositories. Once you know how it flows you'll love it too. The bad side of Suse is that you'll need to DL 5 ISO 's or 3 DVD. You can get Suse open for free. But, as with Ubie. You'll need to DL the codecs.
 
GObby

---

### Post by LookTJ on 2006-12-21
Try looking at [this](http://ubuntuguide.org) for your sound editing software installation.

---

### Post by kolinab on 2006-12-21
Philip,

Sorry you're having a tough time getting things going. I'm so new to this Ubuntu thing that I can't really give you any technical advice. Your post made me feel bad - you sound kind of down that Ubuntu's not working for you. No doubt this kind of thing can be REALLY frustrating, especially when all you want to do is be productive with the hardware you have painstakingly selected to do what you want it to do.

But I bet the reason these things aren't working for you ISN'T your fault. As far as I have learned so far, configuring hardware can sometimes be a challenge in Linux.

I'm learning more about where to get good information on configuring hardware. One resource I have found useful is looking on manufacturer's sites for drivers or even message boards where fellow linux users (or aspiring users) may be lurking or posting. Try lots of honest google searches (I'm not suggesting you haven't done all these things; you seem like a rather resourceful person) and search the heck out of these forums. Maybe you've done all that.

Hopefully you'll get the help you need - I'm sorry I'm not much help and that I'm really just blabbing. But keep your head up and if you have to move along to a distribution that works more easily with your hardware then I wish you luck there too.

Sorry I can't be of help but I felt like posting on the matter!

Regards,

K

---

### Post by Sef on 2006-12-21
Have you read [Linuxprinting]("http://linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1240") for setting up your Brother?

Have you read [Linuxprinting]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R800") for setting up your Epson?

Also check out [Turboprint]("http://www.irseesoft.de/linux/english.html")'s free drivers.

The Sane-Project says that your [scanner]("http://www.sane-project.org/cgi-bin/driver.pl?manu=microtek&model=4000tf&bus=any&v=&p=") is unsupported.

---

### Post by riven0 on 2006-12-21
Can't help you with all your problems, but check [here for your brother printer]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1240"). Seems like it works 'mostly'. Apparently you should try the "hl1250" driver. You should check synaptic first.

The epson r800 seems to work 'mostly' also. Again, [here is a page of info]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R800"). It may help getting it working. 

I don't know anything about the scanner, and I can't find relevant info at Google Linux.

Regarding file sharing with Windows, I'm assuming you have samba set up, but did you follow [this howto]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto")? 

And regarding Ubuntu books, try Ubuntu Hacks or Ubuntu Unleashed. I heard both of those were pretty good.

Welcome to Ubuntu :KS

EDIT: Looks like Sef got to it before me. :D

---

### Post by jvc26 on 2006-12-21
Your R300 should work with Ubuntu... mine works on Ubuntu edgy installed under CUPS - the way I installed has already been mentioned in a link ^^. Hope you get most of your problems resolved!
Il

---

