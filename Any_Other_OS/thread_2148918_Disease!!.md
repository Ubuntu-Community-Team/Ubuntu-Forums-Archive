---
title: "Disease!!"
date: 2013-05-27
forum: Any Other OS
---

### Post by excollier on 2013-05-27
Please help me. I am an incurable distro hopper since trying linux for the first time last October.
I  use, primarily, a computer with 5 distros on it, (LMDE Cinnamon, #!,  Linux Lite, Ubuntu Precise and Debian Wheezy) plus another computer with  Vista / Linux Mint 13 KDE on it.
So I have most of the desktops covered, and I really like all of them in their own way, particularly** LMDE and #!.**
I  really need to whittle it down to a triple boot at most, so which would  you choose to go along with the top two mentioned above?
Or do I keep the five partitions for tinkering with random distros? 
Distro hopping is a time consuming disease.

---

### Post by sudodus on 2013-05-27
Yes, keep the extra partitions for  tinkering with random distros, flavours and versions :-)

---

### Post by ajgreeny on 2013-05-27
I used to have 5 different distros on my old machine, just really for interest sake, as at that time I had settled on Lucid with the gnome 2 desktop.  Since getting a new machine, I have been entirely satisfied with Xubuntu 12.04 and have, probably temporarily, stopped distro hopping.

I have plenty of room on my 1TB hard disk, so fairly soon I shall probably start messing around again with more than just Xubuntu, as I do miss the fun part of seeing what else is available, though I admit I waste a lot less time now that I used to.

---

### Post by coldraven on 2013-05-27
I think you need to find a purpose for all the "tools" in your toolbox.
Try and find a project that you will find rewarding, either financially or emotionally.
So for example if you decide to do something creative with video then use the distro that works best for that.
I'm the same with programming. I cannot decide which language to master, I only actually delve into it when I have a problem to solve. This usually involves a lot of copy/paste from the internet and I end up with a javascript gadget or something.
It's like if I bother to learn Spanish but never get around to travelling if you get my meaning.
Good luck!

---

### Post by whatthefunk on 2013-05-27
Id keep a KDE one.  KDE is by far the most configurable and is my favorite to play with.  Ive been using it for nearly two years now and still discover new things all the time.

As for your disease, just stop distro hopping and find something more productive to do.  Like just about anything.

---

### Post by groggin on 2013-05-27
keep them. ;)

---

### Post by excollier on 2013-05-27
I guess I'll keep the partitions then. Just one thing, how do I edit Grub to select a default os so my wife doesn't have to navigate the minefield to get to LMDE that she has started to use.

---

### Post by rewyllys on 2013-05-27
> **excollier said:**
> I guess I'll keep the partitions then. Just one thing, how do I edit Grub to select a default os so my wife doesn't have to navigate the minefield to get to LMDE that she has started to use.
I suggest that you get a copy of [Grub Customizer]("http://linux.softpedia.com/get/System/System-Administration/Grub-Customizer-60963.shtml") and install it.  Then you can easily make your wife happier.:)

---

### Post by excollier on 2013-05-27
Tried it with LMDE, no luck though, maybe I should try from another os.

---

### Post by ajgreeny on 2013-05-27
If you want to understand more about the way grub2 works look at the grub2-basics link in my signature.

To do this manually you can copy the entry from /boot/grub/grub.cfg for LMDE from the word **menuentry** down to and including the final **}** and add it to the bottom of the /etc/grub.d/40_custom, then rename the file to **09_custom**, run sudo update-grub, and it will become the first entry in the menu.  There are other ways to do it as well noted in the link I give so read and follow,try out, but make sure you can always get back to where you were with file backups.

---

### Post by excollier on 2013-05-27
Thanks for that, really useful.

---

### Post by deadflowr on 2013-05-27
> **excollier said:**
> I guess I'll keep the partitions then. Just one thing, how do I edit Grub to select a default os so my wife doesn't have to navigate the minefield to get to LMDE that she has started to use.

You edit the /etc/default/grub file and change the line

```
GRUB_DEFAULT=0
```
To whatever number on the grub line the distro of choice is.
Like a lot of linux stuff, 0=1.
So line one is zero.

---

### Post by excollier on 2013-05-27
Won't work for me, tried it but to no avail. Not to worry.

---

### Post by deadflowr on 2013-05-27
An easy thing to set up is a custom grub menu.

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

And just make the one she wants first.

---

### Post by sudodus on 2013-05-28
> **excollier said:**
> Won't work for me, tried it but to no avail. Not to worry.

You must run ```
sudo update-grub
``` afterwards. That will make a new **[FONT=courier new]/boot/grub/grub.cfg[/FONT]** file with your change included.

---

### Post by excollier on 2013-05-28
Tried it, simply refuses to work

---

### Post by sudodus on 2013-05-28
> **excollier said:**
> Tried it, simply refuses to work

Did you edit with superuser privileges
```
sudo nano /etc/default/grub
```

And change 
```
GRUB_DEFAULT=0
```
to something else for example
```
GRUB_DEFAULT=5
```

and finally run ```
sudo update-grub
```

---

### Post by excollier on 2013-05-28
I'll try that, thanks. Do I have to do this from the last distro installed - the last distro to install and configure Grub? Which in my case is Debian Wheezy.
Edit: Thanks sudodus, I followed your instructions, from a root terminal in Wheezy, and now Grub opens at LMDE as default, and timeout upped from 5 to 10 seconds.
And thanks to all others that offered help too, I have picked up a few other useful tips for future reference.

---

### Post by Buntu Bunny on 2013-05-28
> **excollier said:**
> Please help me. I am an incurable distro hopper since trying linux for the first time last October.
I  use, primarily, a computer with 5 distros on it, (LMDE Cinnamon, #!,  Linux Lite, Ubuntu Precise and Debian Wheezy) plus another computer with  Vista / Linux Mint 13 KDE on it.
So I have most of the desktops covered, and I really like all of them in their own way, particularly** LMDE and #!.**
I  really need to whittle it down to a triple boot at most, so which would  you choose to go along with the top two mentioned above?
Or do I keep the five partitions for tinkering with random distros? 
Distro hopping is a time consuming disease.

By Ubuntu do you mean Unity? If so, then Xubuntu.

---

### Post by excollier on 2013-05-29
I have Linux Lite which is XFCE, Ubuntu based, very good it is too.
Re-cap: LMDE (Cinnamon) #! ( Open Box) Linux Lite (XFCE) Ubuntu (Unity) and Debian 7 (Gnome Classic and KDE).
So five distros and six DEs altogether, way too much choice, as if *that* were a problem, but I tend to favour LMDE and #!

---

