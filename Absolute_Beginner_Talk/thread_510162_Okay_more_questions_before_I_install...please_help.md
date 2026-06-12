---
title: "Okay more questions before I install...please help."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Carn Thorn on 2007-07-26
I'm about to try to install Xubuntu and I need to know what to do about these problems...

I've got the alternatecd and I wanted to know does it have a livecd desktop environment?  The first option on the bootup screen is to install in text mode...

---

### Post by maldojr88 on 2007-07-26
you can install it in text mode with no problems
graphic mode is only a little more user friendly

---

### Post by w4ett on 2007-07-26
The alternate cd is a text based install.....the Live CD can be obtained here:

[http://cdimage.ubuntu.com/xubuntu/releases/7.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.04/release/)

---

### Post by Carn Thorn on 2007-07-26
But does the alternate cd have a desktop environment I can try out before I install?  Never used Linux before so I want to try it before I install.

---

### Post by NESFreak on 2007-07-26
> **maldojr88 said:**
> you can install it in text mode with no problems
graphic mode is only a little more user friendly

though it requires lots of ram to run. Which you since your installing xubuntu probably don't have.

---

### Post by Carn Thorn on 2007-07-26
Okay so I'm just gonna install and try it out after I'm done...now here's the big question.

I've got a 130gb hardrive with about 16gb being used right now.  I want to install Xubuntu into a 20gb partition without erasing any of my other data...what options do I chose to get this desired effect?

---

### Post by wpshooter on 2007-07-26
> **NESFreak said:**
> though it requires lots of ram to run. Which you since your installing xubuntu probably don't have.

Yes, that is my question.  Does the poster really need and want to use/install Xubuntu ?

Does your computer not have enough resources to run Ubuntu/gnome or Kubuntu ?

---

### Post by w4ett on 2007-07-26
> **Carn Thorn said:**
> But does the alternate cd have a desktop environment I can try out before I install?  Never used Linux before so I want to try it before I install.

To get the UI Desktopt Environment, you'll have to get the Live CD....the Alternate Install CD does not contain the Graphical Environment.

---

### Post by Carn Thorn on 2007-07-26
> **wpshooter said:**
> Yes, that is my question.  Does the poster really need and want to use/install Xubuntu ?

Does your computer not have enough resources to run Ubuntu/gnome or Kubuntu ?

Well my computer only has a pentium 3 processor and mismatching sticks of ram that equal up to I think 384...so I just thought Xubuntu would run better and since I can use all of the programs that Ubuntu can (well it says it can on it's site...) then this would be the way to go for me.

Oh and does the alternate cd have a graphical install setup on it?  I can use the text one it's just really ugly.

---

### Post by Carn Thorn on 2007-07-26
Please I need help soon...does the alternate cd have a graphical installer and also what settings do I use to make a partition for Xubuntu while not deleting the data on the hardrvie?

---

### Post by NESFreak on 2007-07-26
The alternate will install a graphical desktop. The installer itself is the only text based thing about it. And yes you can resize your windows partition and install ubuntu next to it. When booting it allows you to choose which one to boot (windows or ubuntu)

---

### Post by alex_anthony on 2007-07-26
so you don't lose your data, defragment your drive first then back up!

---

### Post by wpshooter on 2007-07-27
I believe with 384mb of RAM I would give Ubuntu a try before I decided to use Xubuntu.

No I do not believe the Alternate has a Graphical installation method.

I think you need to use the MANUAL partitioning choice.  If you have some other O/S on this computer I believe that it is highly recommended that you run chkdsk and defrag on the drive multiple times before attempting to install Ubuntu.

Good luck.

---

### Post by hyper_ch on 2007-07-27
Well, there are users that have enough ram to run gnome or kde but just prefer xfce because it's simple and straight forward...

as NESFreak said already, the alternate install cd does install the same stuff as the desktop CD... the only difference is, it's not a live cd and not as pretty... however if you can "read" then the text installer will be of no problem for you..

Regarding the 20gb partition: That one will be earsed/wiped... Xubuntu will require at least 2 partitions (although 3 are recommended). When you arrive at the partitioner, make sure you select the correct partition and delete it.
After that create in the empty space a new partition with around 1 GB and set as type "SWAP"
After that create about a 6-7 GB partition. use as file system EXT3 and set the mounting point to "/" and make it bootable (should be checked by default I think)
With the rest create another partition, use again EXT3 and set the mounting point to "/home"...

The three partitions above don't need to be a primary ones (you can only have 4 primary partitions on a harddisk). So you may need to create a logical one with extended partitions in there.

---

