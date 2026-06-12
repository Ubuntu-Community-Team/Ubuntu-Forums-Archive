---
title: "Ubuntu on my Laptop !!!"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by ervyxx on 2006-12-01
Hi!

Downloaded Ubuntu and booted my Laptop through the live CD.

My Laptop Specs are as follows:

Compaq Presario 2100 (2113AH)
[LIST=1]
[*]Intel Celeron 2.4 GHz
[*]512 MB RAM
[*]ATI Radeon IGP 340M
[*]Hitachi 40 GB HDD[/LIST]Additional Hardware attached:
[LIST=1]
[*]Microsoft Wireless Optical Notebook Mouse
[*]Iomega USB Predator CD-RW[/LIST]Here is the surprise!

Everything (including graphcis/sound) worked when I booted through the Live CD except the Touchpad.

Now, it didn't matter much coz I never use the touchpad. I always use the Microsoft Mouse.

I also attached my Transcend 1 GB USB Flash Drive and voila it was immediately detected and I could see the files.

Now, this my best experience with Linux till date.

I was sceptical as by base is ATI based mobo and graphics and I have read people nightmares with it.

So, either am Lucky today or Ubuntu is great.

Now, this is not my story.

**My Query is whether all my devices which were detected flawlessly in the LiveCD will be detected out of the box when I install Ubuntu on the HDD?**

If yes, what do I do to the Current 3 NTFS partitions I have?

Also, I have to login to a Windows 2003 Domain at my office.

Is there a way to do the same through Ubuntu? I've heard of Samba but, couldn't find anything on the LiveCD.

Also, last but, not the least, is there a way to make the Touchpad work?

---

### Post by renzokuken on 2006-12-01
You can do what you like with the 3 NTFS partitions, if your keeping windows and wanting dual boot i would suggest clearing one of your partitions (not the one with windows installed) and using that for ubuntu. the installation will format it for you.

Samba is not on the CD but is freely available in the Ubuntu repos. Either search for it in Synaptic or do ```
sudo apt-get install samba
```
there are some excellent guides in the forums and in the wiki on how to use samba.

there is usually a way to make touchpads work but no guarantees. search the forums for people who have similar problems, they mat shed some light.

EDIT: according to here [https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresario2100?highlight=%28laptop%29](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresario2100?highlight=%28laptop%29) your touchpad should work. it may be that it doesnt work on the livecd but will do once installed to the harddrive

---

### Post by ervyxx on 2006-12-01
Thanks for that link and the advice.

I'll try it as soon as am ready to install Ubuntu on my lappy. ;)

---

### Post by princemackenzie on 2006-12-01
Generally nothing changes if it works on the LiveCD to when you put it on the HD.  I would be confident nothing will change when you install it.

---

