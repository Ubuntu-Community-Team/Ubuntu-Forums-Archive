---
title: "Size of your windows C drive"
date: 2013-03-30
forum: Any Other OS
---

### Post by ads2996 on 2013-03-30
Hi, 

I am in the middle of considering a hdd upgrade for my laptop and I was wondering. What sort of sizes are people's windows c drive, with there data being in a separate data drive/partition. I was also wondering what size people have for Ubuntu and for their swap.

Thanks for any advice.

---

### Post by carl4926 on 2013-03-30
I just built a setup for someone

150GB to win7
100GB Backup partition

8GB swap 
25GB /
250GB /home

YMMV

---

### Post by CharlesA on 2013-03-30
I'm lazy. On my Winy7 desktops, I have an OS drive and a Data drive. The OS lives on the OS drive and I have things like My Documents and Desktop/Downloads/etc redirected to the data drive which gets backed up to my server.

My Fedora box, I just have / on one partition and leave it at that.

---

### Post by benerivo on 2013-03-30
I've got a 250GB drive. Win7 gets 25GB, Linux gets 10GB (i don't have a swap partition), and i've got a 210GB partition for my data (i don't put any of my own stuff in /home).

---

### Post by mips on 2013-03-30
160GB and it's purely for playing games.

---

### Post by montag dp on 2013-03-30
I've got about 100 GB for Windows and 200 GB for Linux (including root and /home).  Word of caution: if you are installing 64bit Windows, plan for the installation itself to take up about 30 GB.

---

### Post by ads2996 on 2013-03-30
Thanks for your feedback, I'm currently overhauling my laptop and triple booting it with win 7, win 8 and Linux. It has a 320gb drive. I plan to use it like this
90gb win 7
60gb win 8
10gb Swap
30gb Linux
110gb Data

---

### Post by pfeiffep on 2013-03-30
10 Gb swap seems a bit excessive. If you have more than 2Gb memory there's a new equation for swap.[Full article]("https://help.ubuntu.com/community/SwapFaq")
> **Example Scenarios**

[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_Low RAM and low disk space_[/FONT] With 512 MiB RAM and 30 GB hard disk, use 512 MiB for swap since RAM is very low.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_Low RAM and high disk space_[/FONT] With 512 MiB RAM and 100 GB hard disk, use 1 GiB for swap since RAM is very low and hard disk space is plentiful.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_High RAM and low disk space_[/FONT] With 2 GiB RAM and 30 GB hard disk, use 1 GiB for swap since hard disk space is very low.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_High RAM and high disk space_[/FONT] With 2 GiB RAM and 100 GB hard disk, use 2 GiB for swap since hard disk space is plentiful.[/FONT][/COLOR]


---

