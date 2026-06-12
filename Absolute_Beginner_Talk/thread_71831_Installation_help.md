---
title: "Installation help"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by rzapeople on 2005-10-04
I have never used Linux before and I wanted to get started. So I got the uBuntu cd and wanted to install it on my notebook. I dont wanna delete/remove windows xp from it so I guess I'll have to install it (ubuntu) on a partition. Thats where I need experts to help me out becuase I tried and there were so many terms I came across upon my attempt at expert intallation that were all gobledeegook to me. So if any one can enlighten me on how i can go about doin this, please do. Step by step that is, and pretend you are telling this to some one who has no knowledge of how an OS works, but do not over state it... I feel left behind coz all I know is windows OS!!! :(

---

### Post by Mustard on 2005-10-04
Which particular terms are you unfamiliar with?

---

### Post by Strongbad on 2005-10-04
When you are partitioning your hard drive, you want to use a program that can handle linux partitions, like partition magic. First, you want to resize your ntfs (windows) partition so you have at least 10 gig for linux, then, create a small partition about the same size as your ram (400 mb or so), and format it as linux swap. Then take the remainder of your unalocated space, and create a reserfs (I think thats how you spell it...), ext2, or ext3 partition. I would recomend reserfs, but any of those three will work. After you have done all your partitioning, boot to your ubuntu disk, (you will need to set the first boot device to cdrom in your bios), and when you get to the pont where it asks you about partitioning, select manual partitioning, or something like that (it's been a little while since I installed it). Then, assign your reserfs, partition the mount point "/", and you may have to tell it which partition to use for swap, but i'm not sure. From there, it's pretty straight forward, the settup should detect your Windows, and put it in the boot loader.

good luck and have fun!:D

---

### Post by rzapeople on 2005-10-04
Do I create these partitions, the 400mb, reserfs in the 10gb partition that i just created? Sorry, still confused... I got the partitioning software already and created a 10gb partition, whats next from there???

---

### Post by matthewv on 2005-10-04
The 400 mb is a separate partition which is used as swap. You should have windows partition.. then your swap partition (usually bout 1.5x amount of physical RAM) then your main linux partition of about 10gig. During partitioning in the installer, instruct ubuntu to format the small partition (400mb or whatever) as swap, and the 10 gig as ext3 or reiserFS. From there the install should be straightforward.

---

### Post by John1744 on 2005-10-04
I'm doing the same thing as we speak, and this tutorial is a god send. 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by rzapeople on 2005-10-05
okay, I followed everything and the installation went on until the screen scrolls alot of lines and stuff. But when I try to start Ubuntu at the start up screen all I get is a test system with [ok] and a [fail] at 
*Synchronizing clock to ntp.ubuntulinux.org...
*ror: Temporary failure in name resolution...

and at the command line it asks for login: but quickly claims it cant find bios "Bios not found" and shuts down????

help....

I dont know if its worth it but at the beginning the installer complained about my system not having dhcp configured??

help....

---

### Post by rzapeople on 2005-10-05
seems like all I can access is the command line only and in recovery mode, I cant get the graphical user interface loaded....?

---

### Post by rzapeople on 2005-10-05
P.S. I am tryin to install version 5.04 "Hoary Hedgehog"....

---

### Post by rzapeople on 2005-10-06
Okay, I guess no one is willing to help me out. Well, I thought it could be something to with my video display. So I went to intel and downloaded the linux graphics driver. But how in the hell am I goin to install it. I mean I can access the recovery console but then the file is located in my windows partition and apart from that when it comes to Linux I'm more like the horses that tried to put humpty dumpty together after his untimely fall.... 
Like I said, I cant get the GUI to load. My screen doesnt show, instead it blanks out and does a little sound and looks as if its off. Then when I click the power button, the command line shows for a short while and then my computers switches itself off? See posting remarks in "GUI not loading"

Thank you

---

### Post by drgreborn on 2005-10-06
Ok when you reach the console line, login and type init 3 to go into GUI mode.  Or if that doesn't work type start X. Maybe you could tell us exactly all the steps you took to installing UBUNTU/KUBUNTU.

---

### Post by skoal on 2005-10-06
[QUOTE=rzapeople]I dont know if its worth it but at the beginning the installer complained about my system not having dhcp configured??[/QUOTE]
That would explain the "Synchronizing clock to ntp.ubuntulinux.org" bit.

How do you connect to the internet on your laptop? PCMCIA or an RJ jack? The latter is easier to get you up and running, then you can deal with the prior.

Wrap the following two _separate_ terminal commands output using vbulletin code formatting with the "#" button:

lspci

...and then...

ifconfig

In the meantime, you can try this [howto](http://www.ubuntuforums.org/showthread.php?t=27029).  Since you don't have internet access on that lappy just yet (I think), you can skip the "wget" part and download that package directly on a CD or floppy if possible.  Then "dpkg -i" it.  That howto could get you up and running video first.

\\//_

---

### Post by rzapeople on 2005-10-07
[QUOTE=drgreborn]Ok when you reach the console line, login and type init 3 to go into GUI mode.  Or if that doesn't work type start X. Maybe you could tell us exactly all the steps you took to installing UBUNTU/KUBUNTU.[/QUOTE]

I booted my laptop (Dell Inspiron 1200) from CD and created a 10gb partition on my hard drive(30GB) following the instructions outlined by one member ( [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) ). Then I went thru the installation process which seemed rather okay until where the GUI was supposed to load. Thats when I get the problem. The screen just goes blank. If i press the power button, I get the login prompt at the command line which is by the way, just frozen up. After a minute or less my computer just shuts down? The only thing I can do is log on to recovery mode and after that, I am lost. I wa thinking maybe its my screen resolution or something to do with a linux driver for my graphics card, Intel GMA 900. At intel.com they do have driver available for linux? But then again, how would I go about installing that, if thats what the solution is?
Thank you...

---

