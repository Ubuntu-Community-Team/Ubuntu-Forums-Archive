---
title: "Ubuntu doesn't want me...."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by simpsonatwork on 2007-02-02
Two days ago i started installing Ubuntu (6.10) on my computer (Celeron 2.60, 1 Gb RAM, 256 Mb Nvidia 6600 GT, 80 Gb drive), so i thought as it is a Linux one (this is my first experience with it, but you know what people say when compare it with Win), all should be quick and simple. But it turned out that I was forced to reinstall it - by this moment - 5 times in 2 days.

I wanted to boot it along with Windows XP, so i installed XP on hard disk (first and only partition), made a backup of it, while it was fresh. Then i loaded Ubuntu live CD 6.10, downloaded from [www.ubuntu.com](www.ubuntu.com), went through the primary steps eg. name, log-in and so on, and partitioned it into 4 pieces:

 1) XP (NTFS), 2) partition prepared for Ubuntu (ext3, nearly 23 GB) , 3) linux swap 2GB partition and 4) a partition for docs (FAT32). And 

1. ran the installation for the first time. It hung on 27 percent, so i rebooted and

2. ran it for the second time. Entered all the same, installation has gone successfully! 

But then i've got that Ubuntu needs drivers for videocard, so i tried different methods, downloading drivers from [http://albertomilone.com](http://albertomilone.com), from nvidia site, from repository. None of them have worked, and without drivers (maybe, because i didn't see Ubuntu WITH drivers installed yet:( ) the system was running rather slowly, the standard of processor loading was near 30%. What is important, it was running much slower than Windows, so this was the point, and i decided to reinstall Ubuntu and try installing drivers from Alberto Milone guide ([http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)) on clean system again. 

3. So i just ran the live cd for the first time, and it hung again on 70%.

4. Then i reformatted the partitions for Ubuntu (the one which was expected to be the root and the other for swap), considering that some files from previous installation might have created the problem. Now it hang up on the last stage - on 94%, during the 'configuring boot loader' message. 

5. So this time i decided that Grub needs to be cleaned up (though, WTF?). So i ran Windows recovery console from its disc and ran 'fixmbr' command. Thus Grub records must have been deleted, and i checked it having successfully logined into XP. I reformatted linux-prepared partitions again and ran the Ubuntu installer. Now it hung on 95% (during the message about smth. 'loading linux floppy module'). 

Then, i've checked the disc (result - 0 errors in checksums found), checked my memory (also 0 errors), but my desire to reinstall again is a bit weak now........ 

So what i might have done wrong and what can i do now? Maybe it is not a stable trunk???

---

### Post by Tomosaur on 2007-02-02
6.10 is called 'Edgy Eft' - the name alone should have forewarned you :P It is not, nor has it ever been, advertised as a stable release. A lot of new tweaks and features were introduced, and although it runs perfectly well on my system, many people have also reported problems with it. You may wish to give up on 6.10 and install 6.06 (known as 'Dapper Drake'), which is very stable and comes with long term support. Alternatively, you could download the very latest release of Feisty, which, although it's still only alpha (as in, it's not officially 'released' yet) - some of the unstable areas of 6.10 may have been fixed.

I would reccommend you give Dapper a try though, since it's the latest stable version of Ubuntu. I can't see anything wrong with your hardware, so perhaps you just need to wait for the next stable release.

---

### Post by Eddie Wilson on 2007-02-02
Tomosaur is correct. I used 5.10 and then installed 6.06. Everything worked great. I tried to install 6.10 and had all kinds of problems. Dapper 6.06 is a very stable release. You shouldn't have any problems with it. I did install 6.10 on a small partition to play around with but 6.06 is my working os.
Good Luck,
Eddie

---

### Post by lamego on 2007-02-02
If the installer does not behave on a stable fashion you probably have an hw or driver related problem.

---

### Post by simpsonatwork on 2007-02-03
Thanks guys) i'll try dapper, it seems to be really reasonable not to hurry for the latest releases.

---

### Post by xpod on 2007-02-03
My original Dapper used to hang during install but just using "safe graphics mode" at boot up solved the problem.
Might try that first?

---

### Post by Shay Stephens on 2007-02-03
Something to consider also, hardware plays a big role in installation troubles.  The only computers I have had trouble personally with are the ones with flunky windows-only hardware.  Before blaming ubuntu for hating you, check your hardware to see if there is any known not to work in linux.

Once you have good hardware, installation is a snap.

---

