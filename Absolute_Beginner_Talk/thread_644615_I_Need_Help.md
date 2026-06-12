---
title: "I Need Help"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by dc2610 on 2007-12-19
I am trying to install Ubuntu. Where I get stuck is "you need to specify a partition for the root file system (mount point "\"). I don't know what this means or how to do it. 

I have partitioned about 20 gigs of useless space on my hard drive. Does anyone know how I can undo this?

I would like to have Windows Vista and Ubuntu running on my computer. 

I am very new to this type of stuff. I'm frustrated and about to give up. I did a search of the forums but can't find anything. Please help me.

---

### Post by BluePlum on 2007-12-19
I just selected the default partiton.

---

### Post by shadow-of-sin on 2007-12-19
First of all can you boot up the livecd, go to Applications-->Accessories-->Terminal and execute this command and post your results:
```
sudo fdisk -l
```

Also, did you resize your Vista partition yet? You should do this in Vista rather than using the Ubuntu livecd.

---

### Post by dc2610 on 2007-12-19
> **BluePlum said:**
> I just selected the default partiton.

I did that twice and it says that the partitions are unusable. And keeps telling me that I need to specify a partition for the root file system.

---

### Post by dc2610 on 2007-12-19
> **shadow-of-sin said:**
> First of all can you boot up the livecd, go to Applications-->Accessories-->Terminal and execute this command and post your results:
```
sudo fdisk -l
```

Also, did you resize your Vista partition yet? You should do this in Vista rather than using the Ubuntu livecd.

Its too late. I resized my partition about 3 times. It just keeps getting smaller. 
But I will try everything you just suggested. Thanks

---

### Post by Sef on 2007-12-19
I would merge those 3 partitions.

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by hyper_ch on 2007-12-19
And can you please edit the thread and give it a more descriptive thread title than just a generic "need help"?

---

### Post by shadow-of-sin on 2007-12-19
Also, try this guide:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
(its written for Feisty Fawn but will also work with Gutsy)

---

### Post by wormser on 2007-12-19
> **dc2610 said:**
> I did that twice and it says that the partitions are unusable. And keeps telling me that I need to specify a partition for the root file system.

I had that same problem when installing.  The gui guide is not really friendly at that point.  I just had to select the drop down bar and use /.

---

### Post by dc2610 on 2007-12-19
> **wormser said:**
> I had that same problem when installing.  The gui guide is not really friendly at that point.  I just had to select the drop down bar and use /.

I tried the drop down menu. It gives me two choices: /windows or /dos. I guess I could've typed something in but I had no idea what to type.

---

### Post by dc2610 on 2007-12-19
> **Sef said:**
> I would merge those 3 partitions.

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

Tried merging the 3 partitions. Couldn't do it.

---

### Post by dc2610 on 2007-12-19
> **hyper_ch said:**
> And can you please edit the thread and give it a more descriptive thread title than just a generic "need help"?

I have no idea how to edit this thread or any other to change the titles. If I knew things like that then I might actually know what I was doing and I wouldn't be posting at all this time of the morning cuz I'd be asleep.:confused:

---

### Post by dc2610 on 2007-12-19
Thanks for all the help and the links. Gonna read them all right now.

---

### Post by weblordpepe on 2007-12-19
Basically the short answer is that when you install more than one operating system on a hard drive, you have to break up the space into **partitions**.
By default, with one operating system, you'll have one partition covering the whole disk. Windows will assign a name to it, usually **C:**

Basically what you want to do is resize that partition to something like half of your disk (or whatever), using any software you want. On Windows you can use Partition Magic.

Linux, on the other hand is a bit of a **spazz**. It wants to have a partition where you install everything (root), and a seperate partition **just for the swap file**.

This is a screenshot of **qtparted**, a partition editor on my computer. I have three partitions there.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=53671&d=1198057293[/IMG]
The first one is where Windows XP lives (formatted to NTFS)
The second one is where Ubuntu lives (formatted to ext3)
The third one is a tiny 1Gb one formated to **Linux Swap**

When installing Ubuntu, one way or another what you want is:
[LIST]
[*]Your Windows partition taking up only a bit of the whole drive
[*]Create a new partition of a few GB to store Ubuntu, mount **root or /** to this one.
[*]Create a tiny partition after this, and format it to linux-swap.
[/LIST]

What the installer will do is do a turd on your first partition (Windows) and install the GRUB boot-loader which gives you the 'What do ya wanna boot?' menu on boot-up.

---

