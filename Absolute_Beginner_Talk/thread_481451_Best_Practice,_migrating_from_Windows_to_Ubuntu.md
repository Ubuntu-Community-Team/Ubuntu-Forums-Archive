---
title: "Best Practice, migrating from Windows to Ubuntu?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Robin.Muilwijk on 2007-06-22
Hi all,

This is my first post, so bear with me.

I have a Dell Dimension 5000, Pentium 4 (3.2Ghz) with 1Gb Ram (160Gb HD). This system is becoming slower and slower and all due to Windows. I started looking around and found Ubuntu.

Since a week or two I installed it on an older laptop of mine and really like the looks and even more, it's performance! So.. I am considering a full migration for the desktop, from Windows to Ubuntu.

My question is, if there is a best practice for such a migration. First issue I'm thinking of is partitioning the hard drive (now just one, all 160Gb in one part.). Would it be smart to split this, and make say 40Gb for a backup, and then install Ubuntu on the remaining partition? I'd like to start from scratch, so not leaving the Windows system, but wondering if that would be smart.

Also, would it be possible with the GParted tool, to add another partition with the Windows (XP) system still running on it?

Thanks, Robin

---

### Post by Phixion on 2007-06-22
You can run the Ubuntu Install CD as a Live CD, basically it acts the same way as it does when fully installed, only a little slower due to running from the CD - Just boot to the CD and you'll see.

As for partitions, if you don't have a seperate drive for backing up then it would be wise to make one for all your backups. If you want to run Windows you need to install Windows first, make a partition for Ubuntu then install Ubuntu on the continious space.

---

### Post by silverglade00 on 2007-06-22
If you are willing to give up Windows completely, then you will probably be better off creating 3 partitions. 

1st partition 20GB for /  This is your root partition. 20 GB will give you plenty of room to install all kinds of software.

2nd partition 2GB for swap This is your swap partition. It acts like virtual memory or swap file in Windows.

3rd partition the rest for /home. This is where all of your user files and configurations go.

If you are wanting to run a web site from this computer, you might want to reserve another 10GB or so for a /var partition.

If you do not want to leave Windows yet, then do not wipe it out. Leave it installed and your life will be easier. Use the Ubuntu CD to install using the option for Use Empty Space for Partitions (or something like that). Then tell the installer to create the partitions above inside that space.

The reason for making /home separate is that you can reinstall Ubuntu if you mess it up and all of your program settings and personal files will still be there. It makes it very easy to recover from problems while you are learning.

---

### Post by Robin.Muilwijk on 2007-06-22
Thanks for the replies so far.  I'll await some more advise, should it come...

Sounds good to try Ubuntu from the Live CD, I already burnt that so would give me some idea how it runs on this desktop configuration.

I like the second reply, with the advice on partitions, thanks. Sounds smart to use a separate /home, and be able to reinstall Ubuntu.

---

### Post by silverglade00 on 2007-06-22
Forgot to add the main thing you should always do. Backup your important files to another drive or CD/DVD/whatever before installing Ubuntu or any operating system. While the process is pretty near error-free, you never know. The cat can run by and knock out the power cord in the middle of partitioning or lightning could hit the house.

---

### Post by amazingtaters on 2007-06-22
> **silverglade00 said:**
> The reason for making /home separate is that you can reinstall Ubuntu if you mess it up and all of your program settings and personal files will still be there. It makes it very easy to recover from problems while you are learning.

wow wish I had known that before I installed.

---

### Post by gigaferz on 2007-06-22
search for this in the forums  

dual boot 

There is more than plenty to get you going.

Also you got to have the meantality to learn and research (hopefully it'll be a smooth case)

There are some "sticky" threads, take a look there too, and keep them in mind for future reference

There is information about installation

---

### Post by Robin.Muilwijk on 2007-06-22
I tried the Lice CD just now, to boot from the Ubuntu CD. After the system seems to be loaded, I get a message like "Unable to display this video mode". Probably the NVidia graphics card. Going to do a search on the forum for that now...

Booting the CD in safe graphics worked, but only limited screen res. with max 1024 px width which ought to be a lot better of course...

If anyone has a tip on this, I'd appriciate it.

---

### Post by bodhi.zazen on 2007-06-22
You might find the Ubuntu wiki very helpful :

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by Robin.Muilwijk on 2007-06-23
Thanks for pointing me to the Wiki, I had already checked that... as a beginner it looks like a though job to get nvidia working and configured to an optimum. I'll probably do some reading first, and setup a dual boot so I know the hardware config of the desktop will prove itself to work ok.

---

### Post by bodhi.zazen on 2007-06-23
Getting the nvidia driver up and running is a snap. Let us know if you need help :)

---

### Post by gn2 on 2007-06-23
> **amazingtaters said:**
> wow wish I had known that before I installed.

All is not lost, you can still set up a separate /home partition after installing: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Robin.Muilwijk on 2007-06-23
> **bodhi.zazen said:**
> Getting the nvidia driver up and running is a snap. Let us know if you need help :)


Thanks for the offer. I guess I first add some partitions, to get a dual boot? And install a clean Ubuntu 7.04 right? I'll have to do it in graphic safe mode because of the message and black screen I get using option 1 on the Live CD.

Once Ubuntu is running I/we can start that nvidia configuration? What I'm most interested in is getting my 1280*1024 resolution back, that will be possible?

Edit; one extra question, I would be moving to Linux/Ubuntu because of performance, this will indeed be better right? Compared to Windows XP...

---

### Post by bodhi.zazen on 2007-06-23
> **Robin.Muilwijk said:**
> Thanks for the offer. I guess I first add some partitions, to get a dual boot? And install a clean Ubuntu 7.04 right? I'll have to do it in graphic safe mode because of the message and black screen I get using option 1 on the Live CD.

Once Ubuntu is running I/we can start that nvidia configuration? What I'm most interested in is getting my 1280*1024 resolution back, that will be possible?

Edit; one extra question, I would be moving to Linux/Ubuntu because of performance, this will indeed be better right? Compared to Windows XP...

I just took someone through this today ...

[http://ubuntuforums.org/showpost.php?p=2898390&postcount=3](http://ubuntuforums.org/showpost.php?p=2898390&postcount=3)

That command "sudo /etc/init.d/gdm stop" will drop you out of X so either print the directions or be prepared.

Let me know if you need assistance :)

---

### Post by Robin.Muilwijk on 2007-06-23
Thanks, will be doing some cleanups, defrag etc. first, then create the partitions and will see how things go from there. I found another topic on the Envy tool already, so that looks like a good option. 

I just tried beryl on the old laptop, looks very nice...

---

