---
title: "help! links wanted"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by john131971 on 2005-12-04
First i'm exploring the world of linux and have ran into a couple of road blocks!

first question:

someone please explain the different version of iso in grub, the switch to k7 really speeds things up?

my system seems to stall on shut down but dom't see any error mess. only a blinking line?

i don't understand  how to install software from the desktop , you know the sh thingy. (from downloads in firefox)

Web links would be cool!   have ck'd the linux doc project and the only thing I  find is info regarding installing iso not software packages

thanks all!

---

### Post by aysiu on 2005-12-04
I don't even know if I understand what you're asking.

Do you just want links for generally better understanding Ubuntu/Linux? Do you want to know how to understanding Firefox?

If English is your native language, please try to type your questions as clearly as possible. If it's not, there are other Ubuntu forums for other languages.

---

### Post by john131971 on 2005-12-04
sorry if i wasn't very clear with my first post!

i have three different questions!

the main question is ...

how do i install software without using the  package manager,  a.k.a. from the command line with the source being in my firefox download folder.

II.

My system seems to freeze on shutdown.  how do i find or is their a shutdown log for the system;  which doesn't really matter at this point because if their is a problem the only thing i can do... is to  reformat and reinstall, which is starting to get old!

III.

Using the package manager i changed main kernel to k7 and now i have like four different boot options in grub.  Could some explain different files and versions available at start up!

I'm guessing on this one but i assume that at system boot up grub and I are selecting iso image to mount with file system being the same regardless of which image i load!   

thanks again

(edit typos>

---

### Post by aysiu on 2005-12-04
Much clearer. Thanks for retyping!

Unfortunately, I can answer only your first question:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

That's specifically for Firefox. Anything else, this may help:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by john131971 on 2005-12-04
thanks for the two links at the bottom of your messege!
i will spend weeks reading, oh my head is starting to hurt all ready!

thanks

---

### Post by kalos on 2005-12-04
Links huh?

Well there is [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) It should be helpful despite the fact that it is for Hoary (Ubuntu 5.04). (You probably want to read the "How to install/uninstall .deb files?" I think that is what you meant by your first question, but you might want to look at something like the [Commandline Howto](https://wiki.ubuntu.com/CommandlineHowto) first.)

There is the [UbuntuWiki]("https://wiki.ubuntu.com/") that aysiu linked to. There is a lot of ubuntu knowledge stored there.

There is the [Ubuntu Document Storage Facility](http://doc.gwos.org/index.php/Main_Page) that I think you were referring to.

Google is always your friend. You can also use [Linux Google](http://www.google.com/linux).

There was a post with lots of good links in it, but I can't seem to find it.


To specifically answer your questions:
**I.** Either use dpkg (for deb) or make (for tgz/tar.gz/etc), depending on what you're actually trying to do. Usually, where you downloaded the file from will give a hint as to what to do. If you have to use make, there is usually a README explaining what to do.

**II.** Your computer might not properly support advanced power management. (So Ubuntu shuts down, but it can't power off the PC.) How old is it? Do you get any output when you shut down?

**III.** Assuming you are running a k7 processor, using the k7 kernel will provide a performance boost. Explaining why is fairly technical, but I will try and keep it simple. If you want more detail, see [Wikipedia]("http://www.wikipedia.org") for [Computer architecture](http://en.wikipedia.org/wiki/Computer_architecture) or [Instruction (computer science)](http://en.wikipedia.org/wiki/Instruction (computer science)). Or check out a [university course](http://www.google.com/search?hl=en&q=site%3Aedu%20computer%20architecture&btnG=Google+Search) on it.
When you run a program, the computer performs small incremental tasks. These are instructions. The possible instructions for a computer are its instruction set. A program consists of many instructions.
As Intel has made newer chips, they have expanded the instruction set. Because of this, you can't run a program using a newer instruction set on an old processor.
The changes to the instruction set are often performance enhancements. The new processor can use new instructions to do things faster. Also, different instructions are faster on different processors (so one instruction is fast on old processor and slow on new, or vice versa).
To take this into account, you can get kernel updates (the iso you are talking about) that are optimized for your processor. They use instructions that are faster on your processor as much as possible.
And because these instructions execute faster, you will have a performance boost. HOWEVER, this boost may not be noticable or may only manifest in certain situations (if the improved instruction execution only applies to number-crunching, then you won't notice a difference when word processing).

Oh, and as far as getting answers on the forums, it is recommended that you make the subject as descriptive as possible. Try and describe what isn't working and how it's not working.

HTH
-kalos

---

### Post by john131971 on 2005-12-04
re: 2&3

hp a810n
754 newcastle 1800mhz 64 bit
512 ddr pc3200 (1.5vts.)
ati 9550 oc 256 (no 3d doesn't work) --xconfig stays 9600 pro--
250gb sata.

have the feeling that the kernel has detected battery backup as an power source and has screwed up power settings

standby and sleep work fine
but
power down seems to take forever 
long blinking line after system log run background info or command line countdown
hitting enter seems to speed things up 
reboots take forever almost as slow as windows

What do i know i'm just a noob asking questions!   I hope my questions aren't to dumb!

thanks once again and you have to start somewhere:KS

---

### Post by kalos on 2005-12-19
[QUOTE=john131971]
have the feeling that the kernel has detected battery backup as an power source and has screwed up power settings
[/QUOTE]

You might want to try adding a boot option that disables acpi see [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto)

-kalos

---

