---
title: "[SOLVED] System Reboots At Startup"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by MelL on 2007-06-28
Alas, here I am, the new Ubuntu person. I recently installed Ubuntu 7.04 Server Edition on an older pieced together system with 256mb of RAM and sporting a way speedy K6-2 500 CPU. 

So here's the run down on what occurs. When the machine starts, it goes through the normal memory test and hardware detection, no problem there. It then gets to the following:

GRUB loading stage 1.5

GRUB Loading, please wait... [    ]
Press ESC to enter the Menu

If I don't do anything, the system reboots in a few seconds. Over and over it reboots, with no sign of surrendering to my Ubuntu needs. So when I do hit Esc, I come to the following menu:

ubuntu, kernal 2.6.20-15-server
ubuntu, kernal 2.6.20-15-server (recovery mode)
Ubuntu, memtest86+

If I select the top two, the reboot cycle begins anew. The memory test just looks neat. For a few seconds, anyway. :p

Any thoughts? Win98 used to be on the system, so might it be possible there was a corruption of Ubuntu by the wicked Win98?

---

### Post by Digitallysick on 2007-06-28
It sounds corrupt, maybe a bad harddrive? might want to just reinstall it

---

### Post by MelL on 2007-06-29
I tried re-installing, but to no avail. The loop simply occurs again and again. :(

---

### Post by molly_001 on 2007-06-29
If it's an old Compaq or HP Pavilion, you have to coax Xorg to interface with the graphics properly.  If possible, please post as much info as you can about your system.  Model, crack open the case and see what graphics chipset seems to be present (ask for help if needed) and the motherboard name and model .  Thanks!

---

### Post by weresheep on 2007-06-29
Hello,

I had a similar sounding problem when I tried to install the Server edition onto my old computer. I eventually found out that the Server edition doesn't use a i386 Kernel but defaults to a i686 one (my computer has a i586 CPU). I can't remember if a K6-2 is compatible with i686 or not, but it might be worth checking out.

-weresheep

---

### Post by MelL on 2007-06-29
> **molly_001 said:**
> If it's an old Compaq or HP Pavilion, you have to coax Xorg to interface with the graphics properly.  If possible, please post as much info as you can about your system.  Model, crack open the case and see what graphics chipset seems to be present (ask for help if needed) and the motherboard name and model .  Thanks!

It's an old Gateway2000 system where pretty much everything has been replaced. It now has an FIC AN19E Mainboard with a Diamond Viper V550 for the video card. It has a K6-2 500 for a CPU and 256mb of RAM.

Also, to the poster just before this, a messageboard I found indicates the K6-2 is i586 as opposed to i686 and that using it for such will result in illegal operations. Might the loop be a result of such?

---

### Post by weresheep on 2007-06-29
Hi again,

It certainly sounds like the same thing I was seeing when I installed the 'Server' edition on my old i586 computer. The computer would start to boot, I would see some Grub messages and then it would reset and start booting again.

When I found out about the i686 limitation I installed a server from the 'Alternative' Ubuntu CD instead of the 'Server' CD. I didn't need the automatic LAMP installation so it didn't really bother me.

Perhaps that would be worth a try for you too?

-weresheep

---

### Post by MelL on 2007-06-30
I will definitely check into that right away! By chance, were you able to set up the same services that you would have had you used the 'Server' cd?

Edit: By alternative Ubuntu cd, what do you mean? I apologize for the dumb question. Do you mean a variant like Xubuntu?

---

### Post by molly_001 on 2007-07-01
> **MelL said:**
> MeIL wrote ....

 By alternative Ubuntu cd, what do you mean?

.

.

.




If you ask me, using the Alternate Install CD is the way to go for any installation of any flavor of Ubuntu.  What is it?  Well, you know how posters are always referring to the "LiveCD" -- and it's probably the one you downloaded.  The LiveCD is bootable and allows you to experience Ubuntu (from the CD, with all tasks loaded into RAM as you implement them) without actually installing Ubuntu.

The Alternate Install CD is the same Ubuntu version but doesn't have the "Live Environment" on it.  It only allows you to install -- just like any Windows installation CD gives you only an install option.

What I like about the Alternate Install CD is that it gives you much more hands on control over how the installation proceeds.  It's also a great way to learn more about how Ubuntu installs on your computer, instead of just clicking a "Install Now!" button and having it do all the work for you.

I encourage you to go ahead and download the Alternate Install CD for Ubuntu 7.04 on [this page]("http://tinyurl.com/2gp9ca") (third section down).  Burn that (.iso) to a CD, and fire it up and install Ubuntu the working man's way.  There are some great guides to take you visually through it step-by-step, most notably [this one]("http://users.bigpond.net.au/hermanzone/p14.htm").  Note that those instructional pages literally show you what is on the screen while you are looking at it-- you can't go wrong.

---

### Post by weresheep on 2007-07-03
Oops. Sorry, I forgot to check back on this thread.

Thanks to molly for picking up the slack for me :)

Just to confirm, I did mean the official Ubuntu alternative install CD. It is still Ubuntu (not Kubuntu, Xubuntu etc) but just does basic installing. On the Ubuntu website download page, there is a checkbox that you can select to download the alternative install CD instead of the normal LiveCD. Here is a picture that shows the checkbox you'll need to check before downloading the ISO.

Click the image for a larger version.
[[IMG]http://www.grassfield.co.uk/data/alternative_sm.jpg[/IMG]](http://www.grassfield.co.uk/data/alternative.jpg)

By default the alternative install CD will install the same Ubuntu as the normal LiveCD, with GUI desktop and OpenOffice etc. If you don't want any GUI stuff installed then you have to tell it to do a 'server' install. I think there should be instructions on the screen that tell you how to do this, but if I remember correctly you type in 'server' at the CD boot prompt. This will install the basic operating system without any GUI stuff.

Once installed you'll have a fairly minimal Ubuntu system. The actual Server CD has the option to install LAMP (Linux, Apache, MySQL and PHP) as part of the operating system install but all these things can be installed in any version of Ubuntu. So, if you need MySQL database installed then you can do that via apt-get...

```
sudo apt-get install mysql-server
```

To search the repositories for avalable software, for instance if you can't remember the exact package name you need, you can do this...

```
apt-cache search foo
```

This returns a list of packages that mention 'foo' in their descriptions so you can use that to find the specific packages you need.

Again, sorry for the delay.

Hope that helps.

-weresheep

---

### Post by MelL on 2007-07-03
Well, gents, I write this response from my newly installed Ubuntu system using the Alternate Install CD. :D And after scanning her at Steve Gibson's website for security flaws, I am very happy! Now I just have to learn how to install software and various other little things. It does seem well worth learning,though.

Thank you for the patience to see me through to my goal, a working Linux box! :D

---

### Post by weresheep on 2007-07-04
Good to hear you got it working :D

Old computers forever!

-weresheep

---

