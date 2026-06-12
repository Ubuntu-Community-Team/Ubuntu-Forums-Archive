---
title: "Cannot run any distro anymore"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by celsofaf on 2007-06-06
Hello. I had the habit of keeping different linux distros at the same time (plus one Windows XP partition) until early this year. Now the problem is: I simply can't install anything. OK, let me explain. Or better: I don't know how to properly explain.

It started a few weeks ago. I installed the new Feisty Fawn and loved it, kept using it. Then suddenly the PC started freezing once in a while. Then, I had an unsuccesfull upgrade of packages: it sent me segmentation fault errors or something. And then it simply didn't want to complete the boot, with segmentation fault errors and saying that apt is not installed! Instead of looking for the source of the problem and asking for help here, I decided altogether to try the new Linux Mint 3.0 Cassandra and drop Feisty out. OK, wonderful. But a bit later it started to crash. Then I decided to search for something... I might then have had filesystem problems. Checked everything with fsck - it was FINE, to my surprise.

...so some hours ago I simply decided to eliminate all my linux partitions, then created a new partition because I need to run Linux. Thanks God my personal data is always save and backed up. I tried to install Mint... fail. Won't boot. Tried to install Feisty... fail. Won't boot (the progress bar doesn't move). I tried several times. Sometimes the installer would just quit without telling to reboot, sometimes it did tell to reboot.

I'm under Windows right now. I don't have a floppy drive, so I had to boot Windows manualy through the GRUB command line.

It's more than 3am here and I realy need to sleep something. Any clues? Or, perhaps... is my motherboard or harddrive dying? I tried installing on both harddrives also.

Thanks in advance!

---

### Post by jrusso2 on 2007-06-06
If you got a spare hard drive there I might try to see if you can install on a different hard drive maybe check the hard drive for errors.

Since it was working before and it seems to be freezing now it might be some hardware problem.

One way to check this is to take out all the extra cards out and just using the video card see if you can install.

---

### Post by celsofaf on 2007-06-06
> **jrusso2 said:**
> If you got a spare hard drive there I might try to see if you can install on a different hard drive maybe check the hard drive for errors.

Yes, I did it. I have two hard drives, tried instalying on both. :(

> **jrusso2 said:**
> Since it was working before and it seems to be freezing now it might be some hardware problem.

I hope not! I'll try again later today.

> **jrusso2 said:**
> One way to check this is to take out all the extra cards out and just using the video card see if you can install.

I already do it, as the only offboard card I have is the video one.

](*,)

---

### Post by ronb on 2007-06-06
Have you tried MEMTEST?

---

### Post by notquitemichael on 2007-06-06
have you tried droping the splash screen and running a loud (i.e. not quiet) boot as your options. ubuntu might just be sticking on something that you'll be able to sort.

---

### Post by celsofaf on 2007-06-06
> **ronb said:**
> Have you tried MEMTEST?

No. In fact, it was only after reading your message that I searched and understood what's memtest for. :) When  I get back home later, I'll do a memtest - and pray that my RAM is not damaged.

> **notquitemichael said:**
> have you tried droping the splash screen and running a loud (i.e. not quiet) boot as your options. ubuntu might just be sticking on something that you'll be able to sort.

How do I do it? ;) oops...

---

### Post by diatribe on 2007-06-06
edit your /boot/grub/menu.lst file, in your first kernel where you see quiet and splash, remove splash and quiet

---

### Post by celsofaf on 2007-06-06
OK. Ran memtest86+ for some minutes, just enough to see there are actualy problems with my RAM! :( :( But somehow I can boot and use Windows just fine... I'll see if tomorrow or later I take off one of my two RAM chips (I have two 512MB DDR chips) at a time to see if the problem lies in just one of them or - thanks God not! - in both.

:(

---

### Post by Hobo Joe on 2007-06-06
Hmmm, it seems really strange to me that you can boot into Windows even though memtest says that there are problems with the RAM. 
How much ram do you have? And how many separate sticks + individual sizes is it in?

---

### Post by celsofaf on 2007-06-07
> **Hobo Joe said:**
> Hmmm, it seems really strange to me that you can boot into Windows even though memtest says that there are problems with the RAM. 
How much ram do you have? And how many separate sticks + individual sizes is it in?

Yes, quite strange! But my RAM are two 512MB sticks. Let's see what happens tomorrow...

---

### Post by celsofaf on 2007-06-07
...and BINGO! Yes, the oldest of my two RAM sticks is the one causing problems. I took it off, ran memtest86+ and there is no problem with the other stick. Thanks God the problem is not with both! I can use my PC very well with "only" 512MB of RAM, so this is not realy an issue.

Now I'm happy: installed succesfully Ubuntu Feisty and Arch, and both are running smooth and well, as before.

Thank you all for your inputs. :)

---

