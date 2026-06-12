---
title: "(Complete beginner) Dual Boot: XP and Ubuntu"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by mountielad on 2007-02-26
[Apologies in advance for the lack of cyber lingo and what may seem like basic questions]

I've recently purchased a laptop (Dell Inspiron 1501: 512ram, XP Home Basic, 60gb, CD burner, WIFI). Having read a lot about large corporate vested interests with commercial applications I'm very keen to move to Ubuntu. Its philosophy, communality and non-commercialism is something badly needed.

I've been reading and asking around as much as possible about Ubuntu from Linux users. Unfortunately the information on the web can be daunting for someone starting out. I would like to keep the Windows XP programme (hence a dual boot). I use my laptop for Office applications, watching DVD's, playing and burning CD's, photo editing and the internet. I am not a gamer.

I have some questions which I would appreciate some level headed and clear feedback on.

[LIST]
[/LIST]Using a Dual Boot (LILO / GRUB) means that I select either XP or Ubuntu when I turn on my laptop or I can choose XP or Ubuntu for different applications depending on what I like?

[LIST]
[/LIST]Is there a _clear _step by step guide to setting up Dual Boot and how it actually works?

[LIST]
[/LIST]Will using Dual Boot with XP and Ubuntu reduce the efficiency or life or add stress to the hardware features of my laptop? 

[LIST]
[/LIST]Can I use all the normal programmes, anti-virus protection and features such as burning CD's, photo editing as XP on Ubuntu?

Once again apologies for what are probably very basic questions. Thank you.

---

### Post by undertakingyou on 2007-02-26
Welcome to ubuntu!!

Just a couple of notes.  If you have windows installed first, and then install ubuntu, Grub will set up dual boot automatically for you.  So that should be easy.

Next, linux/ubuntu has different but comperable programs for doing things like photo editing, anti-virus, CD burning, etc.  Everything is completely functional and quite easy to use.  Also, virus issues for a linux/ubuntu based machine are much smaller than for windows.  Linux/ubuntu has great stuff for watching DVD movies also.  Some things will need to be installed after you install ubuntu, but that isn't hard.

Hope this helps!!

---

### Post by mac.ryan on 2007-02-26
> **mountielad said:**
> 
[LIST]
[/LIST]Using a Dual Boot (LILO / GRUB) means that I select either XP or Ubuntu when I turn on my laptop or I can choose XP or Ubuntu for different applications depending on what I like?

Ubuntu will install grub automatically. When you turn on your machine you will have a list of installed operating systems (usually ubuntu + ubuntu recovery mode + ubuntu memtest + window$). You can highlight the one you want, press enter, and... voila`!

> 
[LIST]
[/LIST]Is there a _clear _step by step guide to setting up Dual Boot and how it actually works?


It is automatic. You only have to pay attention when you will have to partition (i.e. divide in different "sections") your HD. If you start from a fresh installation of both Windows and Ubuntu, this is easy. If you have already your HD full of progs, that might be a little bit more tricky, but not too difficult either. In this second case, there is plenty of info available online (basically you will have to defrag the HD to move all the Windows stuff at the beginning, and then "cut" the windows partition short, and use the freed space for Ubuntu.

> 
[LIST]
[/LIST]Will using Dual Boot with XP and Ubuntu reduce the efficiency or life or add stress to the hardware features of my laptop? 


At the contrary: the heads of the HD will move fairly less. The big advantage is however if you keep on separate partitions your windows, ubuntu and the data (in this way a problem on one partition won't compromise the functionality of the others. The above scheme of partitioning has the further advantage to make possible for you to access your files from both windows and linux, provided that you format the data partition in FAT32.

> 
[LIST]
[/LIST]Can I use all the normal programmes, anti-virus protection and features such as burning CD's, photo editing as XP on Ubuntu?


There is a programme called wine that allows that. I never used because:
[LIST=1]
[*] ubuntu comes fully packed with burning programmes, photo editing, office suites, etc, etc...
[*] ubuntu is immune to windows' viruses (there is however an antivirus that allows you to sanitise files in transit on your hardware, so that you don't spread possible infections.
[/LIST]

> Once again apologies for what are probably very basic questions. Thank you.

We are here to help! :)

---

### Post by tjtansey on 2007-02-26
The above post's give you the poop, the Live CD does most of the work for you.  As for photo editting and things of that nature, when you install Ubuntu, just make sure you mount the partition that XP is using.  The install wizard should walk you through it.  As long as that partition is FAT32 you will be able to read and write from both OS's.  As far as antivirus and things of that nature, they are available for Ubuntu in your program manager.

---

### Post by NewOldTimer on 2007-02-26
QUOTEmountielad;Is there a clear step by step guide to setting up Dual Boot and how it actually works?


see this...[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by mountielad on 2007-02-27
Many thanks folks.

I just find normal computer jargon daunting and with a new piece of technology I'm afriad it'll go gaga. But I've much greater confidence now.:)

---

### Post by tjtansey on 2007-02-27
Have no fear...it's why we're here):P

---

### Post by undertakingyou on 2007-02-27
> **tjtansey said:**
> The above post's give you the poop, the Live CD does most of the work for you.  As for photo editting and things of that nature, when you install Ubuntu, just make sure you mount the partition that XP is using.  The install wizard should walk you through it.  As long as that partition is FAT32 you will be able to read and write from both OS's.  As far as antivirus and things of that nature, they are available for Ubuntu in your program manager.

He's right.  But if your windows partition is NTFS you can mount it using ntfs-3g.  An open-source driver to enable read/write support to your windows drive.  You can find a how-to about it here: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

have a good day :KS

---

### Post by nick24 on 2007-02-27
> **NewOldTimer said:**
> QUOTEmountielad;Is there a clear step by step guide to setting up Dual Boot and how it actually works?


see this...[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I clicked on your link to a clear, and very easy, very detailed walkthrough how to install ubuntu, THANKYOU VERY MUCH. I have never seen a detailed walkthrough especially in a fourm.  I am pretty sure the thread beginner found it very helpfrul as well as many beginners including myself. Keep up the magnificent work. :KS

---

### Post by NewOldTimer on 2007-02-27
> **nick24 said:**
> I clicked on your link to a clear, and very easy, very detailed walkthrough how to install ubuntu, THANKYOU VERY MUCH. I have never seen a detailed walkthrough especially in a fourm.  I am pretty sure the thread beginner found it very helpfrul as well as many beginners including myself. Keep up the magnificent work. :KS

I'm glad you found the link useful, but the real thanks goes to the Author and those at "Psychocats.net". There is a lot of help at that site [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)  as well as a lot more here in the forum. Also for what it's worth try doing a search from right here on the forum pages, along with that, the great assistance from the community and google there shouldn't be anything you can't accomplish. Welcome aboard and pay it forward:)

---

