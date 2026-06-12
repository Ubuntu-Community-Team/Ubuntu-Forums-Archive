---
title: "Thunar and Xcfe 4.4"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Wangsta on 2006-09-22
Hey, I've been wondering why xubuntu doesn't intstantly install the newest version of applications.
:confused: :confused: 
For example, Gaim is still at version 1.5.0 while the newest version is 2.0.0. Also, Thunar is supposed to be version 0.4.0 while (after I checked the updates) it said the current version is Thunar 0.3.1.

Also, I heard Xcfe 4.4 is out. Do I have to manually install it or will it come in an update?

---

### Post by jamesr on 2006-09-22
Hi,

I am also interested in the answers. Although by some of the upgrade woes associated with Thunar, I am not surprised of the delay.

---

### Post by sawjew on 2006-09-22
If you want the latest versions in Ubuntu you need to use the testing version which is currently Edgy Eft (I really don't know where they come up with these names).  I currently use Dapper on my desktop and Xubuntu Edgy on my laptop.  Edgy has some obviously unfinished features but seems to be stable enough, and I am currently using xfce 4.4 beta 2 and thunar 4.0 I think ( I am currently on my Ubuntu desktop so I can't check).

Edgy intends to use the completed xfce 4.4 when it is released.  Ubuntu does not update software after release except for security or stability issues.  You can get some updated software by using the backports repository.

---

### Post by jamesr on 2006-09-22
Hi,

Thanks for quick reply. After reading your reply, I will probably stick with current Xcfe. I am using it on a server so the stability is fairly important, therefore as a consequence using Edgy not an option. I am using Xubuntu to make my life easier especially when copying and moving files, in addition I find the cd burn gui easier. For most uses I am using the CLI.

---

### Post by Wangsta on 2006-09-23
so does that mean i can't use THUNAR 4 until i change my xubuntu dapper to edgy?  or is there some way to put Thunar 4 on a dapper xcfe 4.2?

---

### Post by Cartwheels4amile on 2006-09-23
I don't have any specific answers here, but let me say one thing. STICK WITH THE VERSION OF XFCE THAT CAME WITH XUBUNTU. Xfce 4.4 RC1 (the newest version) still has some BIG issues to be worked out. I found this out the hard way.

---

### Post by Wangsta on 2006-09-23
Well, i guess i can stay with the older, more stable versions. But thanks for the help.

---

### Post by sawjew on 2006-09-23
> **Wangsta said:**
> so does that mean i can't use THUNAR 4 until i change my xubuntu dapper to edgy?  or is there some way to put Thunar 4 on a dapper xcfe 4.2?

You could go to [http://thunar.xfce.org/download.html]("http://thunar.xfce.org/download.html") and download the thunar installer and try it for yourself.  I tried the upgrade to xfce4.4rc1 using their graphical installer and it completely stuffed up my system and I had to reinstall.  I really like some of the new features though so I decided to take the risk and upgrade to Edgy and so far so good, no problems at all.

If you do decide to try and upgrade thunar it's probably better to uninstall the old thunar first which will also uninstall xubuntu-desktop.  If you hunt around you may be able to find a thunar0.4 deb somewhere as an easier alternative.  You could also just enable the Edgy repositories, install thunar and its dependencies, then disable the edgy repository again.

---

### Post by detyabozhye on 2006-09-23
Xubuntu 6.06 (Dapper Drake) uses Xfce 4.4 Beta 1 (with a lot of patches to make it stable). Xubuntu 6.10 (Edgy Eft) will use the RC or the full release. Generally, we don't use Beta/unstable software in our releases, especially with a release that will be supported longer than a regular release (6.06 LTS). That's why gaim is still at 1.5 for example. Ubuntu 6.10 will have a lot of cutting edge technology and therefore will not be supported for a period as long as and may be somewhat less stable than 6.06.

---

### Post by Cartwheels4amile on 2006-09-24
So how in the world do I get back to the version of Xfce I was running when I first installed Xubuntu?

If that isn't possible, I need to be able to mount USB devices so my music can be transferred off of here and I can do a fresh install of Xubuntu.

Thanks in advance for the help.

---

### Post by Cartwheels4amile on 2006-09-24
[IMG]http://img124.imageshack.us/img124/872/bumpir5.jpg[/IMG]

---

### Post by detyabozhye on 2006-09-24
Um, my guess would be to mark all the xfce packeages for reinstall in Synaptic.

---

### Post by Cartwheels4amile on 2006-09-24
> **detyabozhye said:**
> Um, my guess would be to mark all the xfce packeages for reinstall in Synaptic.

Thanks for the suggestion... I tried it though, and I'm still stuck with RC1. :(

---

