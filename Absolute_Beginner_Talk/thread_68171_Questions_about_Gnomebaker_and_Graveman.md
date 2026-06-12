---
title: "Questions about Gnomebaker and Graveman"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by xavierh on 2005-09-22
I have several questions regarding Gnomebaker that I hope somebody can help me with. Hee we go:

**Finished CD/DVD Volume Name (GnomeBaker)**: Is there a way to change the volume name of a CD/DVD rather that sticking with the defaul name of CDROM.

**Burning Folders (GnomeBaker)**: Is there a reason why, when you add folders to be burned, they get flattened and only the files get burned.

**Graveman:** In grave man it appears htat I have all the optiosn that I need (volume labeling, maintaining folder structure, etc.) but when I click on the write files button it tells me to insert blank media in the drive and it just sits there, even though the blank media is inserted in the drive.

Thanks in advance for your help

---

### Post by Wolki on 2005-09-22
[QUOTE=xavierh]**Finished CD/DVD Volume Name (GnomeBaker)**: Is there a way to change the volume name of a CD/DVD rather that sticking with the defaul name of CDROM.

**Burning Folders (GnomeBaker)**: Is there a reason why, when you add folders to be burned, they get flattened and only the files get burned.[/quote]

On Breezy, it burns folders correctly, and you get to choose the volume name immediately before it starts to burn.

Can't tell you if it's already in hoary, I used k3b there.

**Graveman:** In grave man it appears htat I have all the optiosn that I need (volume labeling, maintaining folder structure, etc.) but when I click on the write files button it tells me to insert blank media in the drive and it just sits there, even though the blank media is inserted in the drive.[/QUOTE]

I had a similar problem on hoary, didn't try on breezy yet.


I suggest using k3b for the next month, gnome-baker after you switch to breezy.

---

### Post by xavierh on 2005-09-22
thanks for the quick answers. The version in the current release is version 0.3.10 According to the changelog for graveman... version 0.3.11 will have better ddvd-r detection. do you know which version of graveman will be inlcuded in breezy?

I do want to go to KDE just yet so i'll wait for the next release to see what new functionality comes with gnomebaker.

When breezy should come out?

---

### Post by idn on 2005-09-22
Early next month I believe, not too long to wait :)

---

### Post by xavierh on 2005-09-22
[QUOTE=idn]Early next month I believe, not too long to wait :)[/QUOTE]

Now that we are talking about Breeze, what is hte recommended method for upgrading to breezy?

---

### Post by Wolki on 2005-09-22
[QUOTE=xavierh]Now that we are talking about Breeze, what is hte recommended method for upgrading to breezy?[/QUOTE]

Either completely reinstall or change the instances of "hoary" in your /etc/apt/sources.list with "breezy".

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
is currently the only active line in my sources.list.

Then, dist-upgrade with synaptic or apt-get.

---

### Post by patrick295767 on 2005-09-30
Hi, 

Is there a way to add folders in the gnomebaker ?
How ? cos it's not either on the right click or in the menu of the program ?

Like nero, u do right click and u can find 'add folders' ... 

is there a way, a solution ?

thank you very much 

Pat('

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=xavierh]
I do want to go to KDE just yet so i'll wait for the next release to see what new functionality comes with gnomebaker.
[/QUOTE]

You don't need all of KDE to use K3B. I use it in Gnome ALL the time:

[https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29](https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29)

---

