---
title: "Dual Booting Operating Systems?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Stina44 on 2008-02-25
I'd like to try running Ubuntu but I don't want to lose my Windows XP either. I have an Emachines computer that runs pretty well and has Windows XP. I was talking to my stepdad about maybe using it to boot two OS's but he said I shouldn't try to mess with that because it causes too many problems and could ruin my PC. I still want to try it out because I think that as long as I don't try to load the bane of any computers existence (Vista) then XP and Ubuntu should run together just fine right? Also I'm not completly tech savvy but I am desperatly interested in learning how to install two operating systems in one computer. Any suggestions or any place I can get instruction on how to do this best?

---

### Post by hhhhhx on 2008-02-25
there are tooooons of guides on this, use google :)

---

### Post by *oPI* on 2008-02-25
Try this one. Worked fine for me...:)

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")

---

### Post by Stina44 on 2008-02-25
Ah ok. So I can use a guide I find online and if I have any problems I can just post specific questions here right?

---

### Post by hhhhhx on 2008-02-25
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)
this one will probably be the best :)

---

### Post by ispy on 2008-02-25
feel free to ask as many questions as you like, that's what we're here for...

---

### Post by hhhhhx on 2008-02-25
> **Stina44 said:**
> Ah ok. So I can use a guide I find online and if I have any problems I can just post specific questions here right?
yep

---

### Post by Stina44 on 2008-02-25
Thanks a lot you guys! I've never been to a forum where everyone was so nice. Really great! :)

---

### Post by uberlube on 2008-02-25
If you are planning to resize your partitions to make room for Linux dont forget to defragment windows. Otherwise you'll mess it up. If you would like a good tool to use for this use partedmagic.

---

### Post by graham-cracker on 2008-02-26
A quick google brought up this:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I've had lots of luck installing Ubuntu on systems with existing windows installations. I even had a triple boot at one point (Vista/XP/Ubuntu). There is always a slim chance that you'll hose your data, but I honestly think you have a better chance of doing that if you keep running windows :)

The directions on the above link look good. The basic steps are:
[LIST=1]
[*]download the ubuntu iso (from the main servers or a torrent)
[*]backup your important data
[*]defrag your hard drive
[*]boot from the ubuntu cd and run the installer
[*]resize your NTFS (windows) partition to make space for ubuntu
[*]finish installing ubuntu
[*]enjoy the freedom and fun of open source software
[/LIST]

If you run into any problems, google is your friend.

---

### Post by TrendRat on 2008-02-26
I used [Wubi]("http://wubi-installer.org/") after failing to get the LiveCD or the Alternate CD to work for me.  I installed on a distinct hard drive so that windows xp was not disturbed, not sure how it would work if you are putting it on the same drive as windows.

Please back up your windows xp drive and all files before doing this.  And good luck!

TrendRat

---

### Post by MasterAlone on 2008-02-26
To begin my migration to linux I did a lot of research and found that Ubuntu seemed to fit me the best.  I then asked pretty much the same question you asked about dual booting.  I have had several computers over the years with dual boot so I felt comfortable with the concept.

The machine I installed Ubuntu onto has 2 hard drives.  The 'windows' D: drive I hardly used so I moved what I needed off of it and installed Ubuntu on it.  This way I didn't have to worry about partitioning a single drive.  Now I have Win XP on one drive and ubuntu as a clean install on the other drive.  Haven't had any problems with either other than the grub (the little program that lets you choose Ubuntu or Win XP) is sometimes faster than I am and I wind up in in Ubuntu rather than Win but I'm getting faster at it.

Also, I recently did the same thing for a friend that was running Win ME.  She had a second hard drive so we did the same thing.  Now that her printer/copier/scanner is working in Ubuntu, she is very happy and plans to run it exclusively since she can access her files and folders on the older Win Me Fat 32.

Good luck and I think you will enjoy the experience.

---

### Post by ispy on 2008-02-26
> Haven't had any problems with either other than the grub (the little program that lets you choose Ubuntu or Win XP) is sometimes faster than I am and I wind up in in Ubuntu rather than Win but I'm getting faster at it.

you can edit your grub file to give yourself more time:
```

gksudo gedit /boot/grub/menu.lst
```

and somewhere there will be a timeout value you can change to a different number of seconds... save, close, and next time you boot up, you'll have more time to decide if you want Ubuntu or (gag)window$.

---

