---
title: "Ubuntu Login Loop"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by davulf on 2007-02-10
Hi there. I've just installed Ubuntu from a live CD on a separate partition on my laptop. After the initial restart (to remove CD) everything works fine. I download about 200mb of updates and install them. I am then prompted to restart my computer. This is where the problem begins.

Now in the boot menu I see Ubuntu 11, Ubuntu 11 (recovery), Ubuntu 10, Ubuntu 10 (recovery). Now, having formatted the partition prior to installing Ubuntu, and having only seen the one version there prior to the updates, I'm unsure as to what is different. So I decide to go with 11 (10 does the same thing, mind). I am prompted for my username and password. I enter these and the screen seems to load. I am then once again prompted for my username and password. This goes on indefinately. I have tried changing the session to all options, and nothing will work. 

I am slightly upset with this, as I would really like to get this running properly so that I may try out Beryl and 3d desktop with all the neat visuals. 

Any help would be appreciated. 

Thanks,
davulf

---

### Post by shareMenaPeace on 2007-02-10
When you at the login press ALT F2 to chnage to the console -  and ctrl-alt-F7  back, login and type 
```

df -h
```
Do you got free discspace?

---

### Post by tonyr1988 on 2007-02-10
The numbers are small, like 11 and 10, or were you just abbreviating?

The numbers are the *kernel* versions. When you updated, you probably downloaded a newer kernel (think of the kernel as the core operating system). But...it kept your old one, just in case something goes wrong.

Pick the biggest number (newest version) and go from there. You shouldn't have any problems. If everything goes alright, you can delete the extra entries from your

> /boot/grub/menu.lst

file. We can help you out with that if you need it (if you're unsure, ask for help...that's an important file :))

---

### Post by davulf on 2007-02-10
> **shareMenaPeace said:**
> When you at the login press ALT F2 to chnage to the console -  and ctrl-alt-F7  back, login and type 
```

df -h
```
Do you got free discspace?


Hey there. I gave that a shot. Alt + F2 doesn't do anything. I tried several times to no effect. The other key combination had no effect either.

Thank you both for your replies. I have to assume that if I start getting this to work that I will be posting here frequently :).

---

### Post by davulf on 2007-02-10
Wow. After some creativity I finally pulled up a console and typed the df -h. 

It would seem that the 2.3gb I allocated for Ubuntu is not enough. I figured it would take about the size of a dataCD (since that is what live uses) in order to run. 

Does anyone know how to make a partition bigger? I have an NTFS windows xp partition taking up about 72gb of space, and I could reduce that to make Ubuntu bigger.

Is that even possible?

Thanks,
davulf

---

### Post by tonyr1988 on 2007-02-10
Just boot up the LiveCD again and re-install it. You'll go through the partitioning again - just change the partitions to what you want. Make sure to leave room for your programs you want to install.

I'm using a little over 5GB now (with a decent amount of programs, including Beryl + a few games + some KDE apps), just to put it into perspective.

---

### Post by davulf on 2007-02-10
My drive is 80gb. Split currently as:

Ubuntu 2.3gb
Swap 256mb

Windows XP NTFS 73gb 

The space loss is just because the drives are never fully 80 or whatnot. So basically I have the 2.5gb that is not Windows NTFS. If I were to reinstall and partition, it would probably want me to format the Windows partition, which isn't going to happen. Is there no utility to use that I can break off a part of my windows partition and allocate that to Ubuntu? 

Thanks,
davulf

---

### Post by tonyr1988 on 2007-02-10
During the LiveCD install, it'll use GParted (the GNOME Partition Editor) to do the partition. You should be able to:

1) Delete the Ubuntu partition,
2) Resize down the WinXP partition, and
3) Make a new partition for Ubuntu.

If you didn't before, make sure you defrag your WinXP - sometimes resizing a fragmented NTFS can cause problems.

---

### Post by davulf on 2007-02-10
Thanks! 

I will give that a shot in the morning.

---

### Post by tonyr1988 on 2007-02-10
Hope it works for you. Make sure to defrag your WinXP partition and backup any important data. I have never had a problem with losing data, but you never know when something can go wrong.

---

