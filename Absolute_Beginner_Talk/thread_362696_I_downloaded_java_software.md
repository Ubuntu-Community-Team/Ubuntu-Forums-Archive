---
title: "I downloaded java software"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by foxwiz on 2007-02-15
I just installed Ubuntu today and am having a little trouble.   I downloaded AVAST antivirus but it doesn't show up on the menu.  I downloaded it as a .deb file and I think it's installed but I'm not sure.  On the Applications menu, AVAST doesn't show up.

How can I tell if AVAST is installed and how can I get it on the menu?


Another question:  I wanted to play a wma song.  I was prompted to download java and I have a file on my desktop called jre-1_5_0_11-linus-i586-rpm.bin

How can I install this file?  What do I need to do?

Any help would be appreciated.   Please remember this is my first day with Linux and I need to be walked through, so the more verbose the answer, the better.

Thanks

Gary

---

### Post by dcstar on 2007-02-15
> **foxwiz said:**
> I just installed Ubuntu today and am having a little trouble.   I downloaded AVAST antivirus but it doesn't show up on the menu.  I downloaded it as a .deb file and I think it's installed but I'm not sure.  On the Applications menu, AVAST doesn't show up.

How can I tell if AVAST is installed and how can I get it on the menu?


Another question:  I wanted to play a wma song.  I was prompted to download java and I have a file on my desktop called jre-1_5_0_11-linus-i586-rpm.bin

How can I install this file?  What do I need to do?

Any help would be appreciated.   Please remember this is my first day with Linux and I need to be walked through, so the more verbose the answer, the better.

Thanks

Gary

If you want to see what files are installed with any package:

System-Administration-Synaptic, find the package and look in the Properties.

A package will only be in a menu when the package creator makes it thus.

For the JRE, use the package offered in the repositories, using external ones only causes problems.

As to the point of installing any AV package on Linux, there are numerous discussion threads on this and the majority consensus is "why bother".

To play WMA format files you may need non-standard multimedia packages, do a forum search on how to obtain these.

---

### Post by foxwiz on 2007-02-15
Thanks for the reply.  I found AVAST and it has a green box to the left of the entry.  How can I add it to the menu?  I don't see a way to do it.  Can you give me more instructions?  


For Java, you said 

For the JRE, use the package offered in the repositories, using external ones only causes problems.
  
Can you explain in greater detail?  I don't understand.

Sorry for being "brain dead" but I have never used Linux before.

Thank you

---

### Post by Maestro23 on 2007-02-15
> **foxwiz said:**
> I just installed Ubuntu today and am having a little trouble.   I downloaded AVAST antivirus but it doesn't show up on the menu.  I downloaded it as a .deb file and I think it's installed but I'm not sure.  On the Applications menu, AVAST doesn't show up.

How can I tell if AVAST is installed and how can I get it on the menu?


Another question:  I wanted to play a wma song.  I was prompted to download java and I have a file on my desktop called jre-1_5_0_11-linus-i586-rpm.bin

How can I install this file?  What do I need to do?

Any help would be appreciated.   Please remember this is my first day with Linux and I need to be walked through, so the more verbose the answer, the better.

Thanks

Gary

Welcome to the community.  Some links to read/bookmark:

Psychocats: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

How to install anything: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Restricted Formats(Mp3, AVI, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Linuxcommand.org(Terminal commands/Linux Filestructure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Since you are new, I would always try and get your programs from the Ubuntu repositories.  This can be done via Synaptic(GUI) or apt-get/aptitude(command line).  Described in one of the links above.  Installing from source(which is what you are trying to do, can be tricky).

The latest Java(Java6) is available in the repositories.  Start up Synaptic and do a search for Java 6 and you will see it and the other files that go with it.  Will be a whole lot easier on you.

As far as Antivirus software is concerned, you really don't need it in linux, unless you are sharing files with Windows on a Fat32 partition.  There is a great security link explaining why linux is so secure right now, but I can't think of it right now.

.deb packages are explained in the Install anything link above as well.

You can find out where a program is installed by going to a terminal and typing:

whereis <program name>

*Will tell you the path to the .bin file, which is what you need if you are going to create a Desktop launcher for a program, or add it to a menu.

I know that is a mouthful, but those links will really help you.

Good luck.

---

### Post by foxwiz on 2007-02-15
Thanks for the information.  I will start reading.  I got so frustrated with Windows Vista and Microsoft, I thought I would see what everyone was talking about with Linux.  A brave new world!

By the way, I like the way ubuntu desktop looks and I tried the Calc program and Word.  I was able to attach to my Windows printer on another box.  

Off to read now.

Thanks again,

Gary

---

### Post by mikewhatever on 2007-02-15
I remember using the link below for AVAST.
[http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html](http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html)
I'll have to warn you though, the interface is as ugly as hell.

You not need java to play wma, but definitely need the codecs, so check the link below:
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)

---

