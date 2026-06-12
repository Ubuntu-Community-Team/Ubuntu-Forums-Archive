---
title: "Boot error, unable to mount the partition"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by LivingPharaoh on 2007-02-06
I am not really sure what to write without completely embarrassing myself, but then again, it's only the internet so what the hey....

So I am not really a computer person at all. In fact, the only things I use my PC for are checking e-mail, gaming, instant messaging, and downloading and watching porn more or less. I am sure you are wondering why a person like myself even has a need for Ubuntu. :) But a friend referred me to Linux saying it is more secure and overall efficient than windows at pretty much everything, so I thought I would give it a try and see for myself.

I have the Ubuntu ship it CDs in the mail and they will get here in a few weeks ( I would burn my own but I am sure I would do it wrong and I don't have any blank disks lying around anyway, so meh).  But in the meantime, since I am a complete know nothing, I thought I would take the initiative and familiarize myself with the OS by downloading the this prototype from here. [COLOR="Red"]https://wiki.ubuntu.com/install.exe/Prototype[/COLOR] It is a version you can download and install through Windows.

So the process of downloading and installing was all pretty self explanatory, even for a simpleton like myself, but now when I boot up my system and select Ubuntu as the OS it gives me the message

"Error 19, unable to mount the partition

press any key to continue"

So my questions are as follows:

1. What is this partition in non 1337 speak?
2. What does the word "mount" mean in this context?
3. How does one go about mounting said partition?

Yes I know I am an idiot, so let's just get that out of the way right away. ;)

---

### Post by LivingPharaoh on 2007-02-06
Oh, and I did take the time to look through the "New to Ubuntu? Look here first!" stickies and searching the key words for helpful info but it was all over my head.

---

### Post by LivingPharaoh on 2007-02-07
well, thanks anyway I guess.

---

### Post by lagomorph on 2007-02-07
I looked up error 19 on the internet after seeing your post.  It says that you are loading initrd before loading the linux kernel.  I didn't do my installation using the prototype.  Instead I chose the live cd and installed from there - and it has worked many times.

Your hard disk is divided into what are called partitions.  Each operating system keeps its files on these partitions.  Windows and Linux use different types of file systems.   One part of the disk is called the Master boot record, it contains the boot loader which directs the computer to load up the opeating system.  During these directions, partitions are mounted in order to be accessible to the operating system.  Sometimes there are errors and error 19 is just one of many that can happen.

All this can be found on the net in much more accurate detail.  I think you may have to redo your installation.  I found that the live cd is the easiest way to go.  Be careful to back up all your data.  In my opinion, the best way to go is to use a spare hard disk for Linux initially - learn linux a bit and then use your full-of-valuable data disk.  Otherwise it has the potential to bite you and you may feel quite miserable if you have to resort to fixing your mbr and reformatting your drive.

Sorry I can't be of further help - it is not something I've come across in my installation of Ubuntu.

---

### Post by LivingPharaoh on 2007-02-08
Oh you have already been more help than you know! Thanks man.

---

