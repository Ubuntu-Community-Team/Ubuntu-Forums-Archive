---
title: "[SOLVED] Why Ubuntu is so slow on old Computers??"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by blooboy on 2007-12-12
I have an AMD Sempron 2500+ system at my home with 256 MB RAM. I have used it for testing various distros but sadly I've found that Ubuntu, SUSE, Mint(Ubuntu clone) have all worked quite slow on my system. In fact I could not even install Ubuntu 7.04 on my system through live installer. It was sooooo slow to load up that I pulled my hair. Surprisingly in the same pc and under same configuration Mandriva and PClinuxOS both installed fine even through live installer !!!

So that means Ubuntu is unusuable in older systems? Am I wrong in this assessment? Any easy answer from many would be to increase the RAM, but BUT my question is, why PClinuxOS and Mandriva are working smoothly?

---

### Post by kpkeerthi on 2007-12-12
See [Minimum Requirements]("http://www.ubuntu.com/getubuntu/releasenotes/710")

You are better off with Server Edition + XFCE or Xubuntu setup with that hardware.

---

### Post by subs on 2007-12-12
> **blooboy said:**
> I have an AMD Sempron 2500+ system at my home with 256 MB RAM. I have used it for testing various distros but sadly I've found that Ubuntu, SUSE, Mint(Ubuntu clone) have all worked quite slow on my system. In fact I could not even install Ubuntu 7.04 on my system through live installer. It was sooooo slow to load up that I pulled my hair. Surprisingly in the same pc and under same configuration Mandriva and PClinuxOS both installed fine even through live installer !!!

So that means Ubuntu is unusuable in older systems? Am I wrong in this assessment? Any easy answer from many would be to increase the RAM, but BUT my question is, why PClinuxOS and Mandriva are working smoothly?

minimum requirements for the live cd is nearly 390mb of ram and  4gb of unused disk space.... with 256 mb.... u really cant expect it to be very fast....

btw.... once u hav installed ubuntu... the ram usage will drop substantially..... so try installing it from the text based installer

---

### Post by shadow-of-sin on 2007-12-12
If you have less than 384MB of RAM then you will need to use the alternative CD installer.

Ubuntu can work fine on old computers, but to get it to work faster you might want to consider installing an lighter Window Manager such as Fluxbox.

Alot of people have run Linux on old systems (see this thread: [http://ubuntuforums.org/showthread.php?t=478237](http://ubuntuforums.org/showthread.php?t=478237) )

---

### Post by hyper_ch on 2007-12-12
and having a 2.5 ghz processor with only 256mb ram is IMHO a waste of cpu power as you hardly can ever make full use of your processor. Another 1 GB ram stick will do wonders on your computer.

---

### Post by MerlinX420 on 2007-12-12
Actully I run a p3 450 desktop and laptop with ubuntu. They run great compared to win xp.
The Desktop has 256 mb ram and the laptop has 128 mb. I was able to do a live install on the desktop. (I did my fisrt text based ubuntu install on the laptop last night)

But thats just my 2 cents...

---

### Post by philinux on 2007-12-12
Runs fine on mine. See known bugs for slow boot up.

---

### Post by Whiffle on 2007-12-12
Sounds more to me like something in his hardware isn't being detected correctly by ubuntu, possibly hard drive controller or something, which could really really slow things down. (especially if he's having to swap alot w/ 256 mb of ram)

---

### Post by HermanAB on 2007-12-12
The problem is the attrocious window managers used by the KDE and Gnome projects.  

You should run IceWM or Xfce on old machines.  Note that you can make a hybrid system and replace GDM with IceWM, while keeping the rest of Gnome.  That will result in a very fast Gnome, but in my experience it is not worth the bother - just install Xubuntu - zero hassle and blazing speed.

Cheers,

H.

---

### Post by lespaul_rentals on 2007-12-12
Ubuntu is made to run on mid-grade computers and better.  You can't expect a full-bore distro to run smoothly on a system like that, especially with Gnome, which is the most resource-demanding of all popular desktop enviroments/window managers.  In fact, maybe that's why Mandriva and PCLinuxOS did run, as they are KDE-based.  I'm surprised, to be honest, but it works, so that's cool.

For an older system like that, I would recommend Wolvix Cub 1.1.  It's one of the most awesome distros I have ever used.  Plus, it's Xfce -- very lightweight.  You might also try Fluxbuntu, which is Ubuntu with Fluxbox window manager.

---

### Post by rgeddes on 2007-12-12
My system is borderline... P3, 512MB RAM, 300 GB disk space....  can any other window manager (eg Fluxbox) be installed side-by-side with Gnome so I can try before I commit?  Like dual booting, except, it would be dual-window managers.

Thanks

---

### Post by t0p on 2007-12-12
> **shadow-of-sin said:**
> If you have less than 384MB of RAM then you will need to use the alternative CD installer.


This is not true, though many people believe it because the published system requirements to use the Live CD is "at least 384 MB of RAM".

My box has 256 MB RAM.  The Live CD *did* run slower than I'd prefer - but I was still able to use it to install Gutsy to the hard drive.

Now I'm running Gutsy Ubuntu and it's fine.

---

### Post by Whiffle on 2007-12-12
So a 2500+ is old now eh? Hmm.

I guess my computer is a freak then, because it runs KDE with all the bells and whistles with no problems at all, and its only a 1.6GHz Pentium 4 overclocked to 2.23 GHz... maybe its the 1 gb of ram.  I dunno.

---

### Post by louieb on 2007-12-12
> **rgeddes said:**
> My system is borderline... P3, 512MB RAM, 300 GB disk space....  can any other window manager (eg Fluxbox) ...
Sure - Fluxbox in Gutsy has a small menu problem that easy to fix. Heres a couple of how tos.
[HOWTO: get a Fluxbox menu (and customization) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox")
[Fluxbox - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Fluxbox")

---

### Post by subs on 2007-12-13
> **hyper_ch said:**
> and having a 2.5 ghz processor with only 256mb ram is IMHO a waste of cpu power as you hardly can ever make full use of your processor. Another 1 GB ram stick will do wonders on your computer.




:lolflag::lolflag::lolflag:


btw... u can try xubuntu... its supposed to go easy on the required hardware

---

### Post by rockinlinux on 2007-12-13
how do you keep it cool?? water cooling? just curious..... :)

---

