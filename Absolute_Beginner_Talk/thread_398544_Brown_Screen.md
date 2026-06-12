---
title: "Brown Screen"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by GCDB on 2007-04-01
Hi ,
Hope someone can help.
Installed ubuntu 6.10 dual booted with xp on same drive.Grub boot.
Worked fine for a few weeks. Tried to boot 6.10 recently and got to login screen and after that just gave me a blank brown screen with a mouse pointer.
Decided to re-install 6.10 by removing the grub boot,(so it just boots to windows) then reformatted the linux partitions.Put the live cd of 6.10 back in to re-install and just runs to the blank brown screen again. Can get a cmd line by ctrl alt f1 but dont know what to do next??
Thinking hardware fault?? but all ok in device manager in xp so puzzled??
Please help
Ta Gav

---

### Post by mills on 2007-04-01
apparently this has solved similar problems for others but iam a bit of a noob
so dont take my word for it

```
sudo apt-get install ubuntu-desktop
```

hope it helps

---

### Post by nonewmsgs on 2007-04-01
when that happend to me i did the rest xorg comand in terminal

sudo dpkg-reconfigure xserver-xorg

and then everything is all fine 'n' dandy.

---

### Post by GCDB on 2007-04-01
Hi,
Thanks, got little further as it displayed the nautilus? window then went to the blank brown screen again.
The configuring of xorg is what exactly as a lot of questions came up and never had to do this before to get the live cd working.Is it a problem with my nvidea 32mb tnt pro 64 graphics card?
Thanks for reading but i am a novice and this is losing me.
Gav

---

### Post by nonewmsgs on 2007-04-01
yeah it's supposed to do that to make sure all the settings are correct.  i've mucked things up a few times and had to do that so often that i have written down my horizontal and vertical frequencies.

even if the settings you type in are more conservative but gnome starts, that means you can adjust those numbers some more to find the perfect settings and know that the problem is being fixed.  have you finished the wizard or did you just panic and close it?  if so were there any differences?

---

### Post by GCDB on 2007-04-01
Hi,
got it going and re-installed it. In xorg setup i picked the vi..? driver, cant remember the name but read it somewhere on here to use other than the nv one and it worked. Just want to find out where i went wrong now so i dont have to re-install it all again. Maybe it was an updated nvidea driver?? anyone any insight?
Thanks Gav

---

### Post by nonewmsgs on 2007-04-01
there are 2 nvidia drivers the nv and the nvidia.  i recomend the nvidia (as long as you're on the supported nvidia card list).  the reason i think the nvidia one is better is because when i was using the nv (open source driver) beryl said that i wasnt using an  a GL visual (open gl).  now if beryl says i dont have opengl support, then otherthings are probably slowing down too.  so try the nvidia one first (it's right below nv on the list).

---

### Post by nonewmsgs on 2007-04-01
here mate

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by trowa116 on 2007-04-05
can anyone help me? I have the latest ubuntu 6.10 i386 and trying to install it on a voodoo envy machine. I get to the brown screen after choosing the first option and nothing happens, sometimes a empty white box will come up on the top left corner of the brown screen and make a noise but it stays there.

I tried doing the following from the top post "typing sudo dpkg-reconfigure xserver-xorg in the terminal" 
But all i got was a bunch of questions that i thought i answered to the best of my knowledge and after i install all of them it brought me back to the terminal, i then reboot the machine and same thing again.

Please if anyone can help i would really appreciate it....

---

