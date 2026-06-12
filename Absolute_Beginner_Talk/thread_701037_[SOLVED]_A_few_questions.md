---
title: "[SOLVED] A few questions"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by baudday on 2008-02-18
1.) I got a 64-bit Ubuntu 7.10 disc from the distribution center. So based on that, it should work. The problem is when I boot up and select the first option Start or install Ubuntu, it will just go to a blank screen and then the screen will act like there's no input and go into power save mode, while the keyboard's Num and Caps Lock lights flash. There is no way to get out of this other than to reset my pc. I have an AMD athlon 64-bit processor. Plenty of ram, 1 GB, and since disk space shouldn't matter I couldn't imagine that's the problem. I've searched around, and can't find any solutions to this problem, if anyone could help that would really be great, I'm pretty much sick of Windows.

2.) After I figure out 1, I plan on installing it. The problem is I'm away at college and don't have any of the discs for the drivers on me. If i want to do a clean install, no dual boot or partitioning, will the new installation wipe out all the drivers I have installed on there? I know a reformat will delete everything, but is there some way that I could just reinstall the operating system without erasing the drivers? I'm fine with losing the files, I don't have much on here. From what I know I would imagine not, but I don't know, maybe...

I appreciate any help.

---

### Post by emarkd on 2008-02-18
1.  Some video hardware doesn't work well with the live CD's.  Maybe download the Alternate CD and give that a shot.

2.  Drivers are OS-dependent, so you've got to have different drivers for Linux anyway.  There are tools that kinda "force" a Windows driver to work in Linux but they should probably be your last resort and only used if there are no native Linux options.

---

### Post by oedha on 2008-02-18
no 2. some of your hardware will run without "additional" driver......and none of us has driver cd :) just get in from the repo
next, if you still not sure........you can dual boot....with windows....

---

### Post by Hobo Joe on 2008-02-18
Download the [Alternate Install Disk.]("http://www.ubuntu.com/getubuntu/download") (Be sure to check the box)

With your video card, you won't be able to install via the LiveCD. What is your card model?

---

### Post by baudday on 2008-02-18
Since I ordered both, I tried the 32 bit version and that worked. Is that a problem? Running the 32 bit on a 64 bit processor? It works now, in fact I am writing this post with the live boot or whatever, it's working great.

Will I have the internet available like this after installation to download all the necessary graphics drivers and stuff?

Right now I'm noticing that the right portion of my screen is getting cut off, where do I change the resolution settings?

---

### Post by Hobo Joe on 2008-02-18
Yes, it works perfectly fine to install 32 bit on a 64 bit CPU.
And yes, you'll have internet access after the install, and you'll be able to set the graphics drivers properly as well.

Good luck!

---

### Post by baudday on 2008-02-18
thanks a lot for the help. Just wondering though, I know I can change the resolution, just wondering where exactly.

---

### Post by Hobo Joe on 2008-02-19
System > Preferences > Screen resolution.

You might not get perfect results with that on the LiveCD though.

---

### Post by northern lights on 2008-02-19
Should you still rather want to run x64, and the Live CD is indeed the core of the problem, u  can install Gutsy from the net:

From your Windows OS download "unetbootin-ubuntu710x64rev113.exe" from [sourceforge link]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411"). Execute, reboot, select Windows in grub - another menu should appear, select the ubuntu x64 installation.

Should your 32 bit system be completely configured and stable - let it go and ignore this idea...

---

### Post by baudday on 2008-02-19
Alright, well I just wanna thank everyone for the help. I was really nervous about doing this, and on edge the entire installation, but when it was over, everything worked perfectly, and it was 10x easier than Windows installation ever was. All the drivers were kept, and all I had to do was enable my graphics card driver. I am so glad I am finally on Ubuntu, after years of wondering...

---

### Post by oedha on 2008-02-19
no pain no gain :)

---

