---
title: "GRUB splash screen problem"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by saxplaya on 2007-06-03
I was trying to add a new splash screen to the grub menu but apparently I did not configure it correctly.

When I boot up my computer it says :

"Failed to read splash image ((hd1, 0)/boot/grub/blu.xpm.gz)
Press any key to continue..."

Next, the regular grub menu comes up and shows:

Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems
Microsoft Windows XP Home Edition

When I try to boot into any of these the computer just restarts and nothing happens. I think that my problem is I didn't set the (hd1,0) correctly. I am running  Feisty Fawn 7.04. Any suggestions?

---

### Post by jonward0690 on 2007-06-03
Reinstall grub

---

### Post by khardbored on 2007-06-03
Boot from live cd, mount / - fix grub?

---

### Post by Herman on 2007-06-03
It's a very common thing to happen when trying out a new splashimage for the first time.
The best thing to do is get yourself a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") for CD, floppy or USB and then when you make it, use that to boot your Ubuntu with to fix the problem.

You can also use any Ubuntu LiveCD to mount your Ubuntu partition and fix your menu.lst file. You should check with a partitioner that your Ubuntu is really in partition 2, (hd0,1) . If it  isn't, then that's probably what's wrong.  
```
 splashimage=(hd1,0)/boot/grub/blu.xpm.gz
```>  Change the (hd1,0) if you have a different setup.Also, check that you did copy your splashimage to your /boot/grub directory. You can leave it in your /home/saxplaya directory if you want and grub will still see it, but if you do that you'll have to tell grub where to look for it by typing in the correct file path, for example,```
 splashimage=(hd1,0)/home/saxplaya/blu.xpm.gz
```Here's how to mount your Ubuntu system in the LiveCD and it also tells you the code you can use to open certian vital files like menu.lst, /etc/fstab and xorg.conf from the LiveCD to edit them, 
[                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000].

Here is some more help about splashimages in Grub too, just in case you find something there, [/COLOR][/COLOR][Add a splashimage to the GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#splash")

I just added some new info about [Setting the foreground, background and border colors]("http://users.bigpond.net.au/hermanzone/p15.htm#Setting_the_Foreground_Background_and")for your grub menu there too, which really makes your splashimage look even nicer! ;)

I'll be back in a whlle, if you still have trouble please post your menu.lst file here and your output from sudo fdisk -lu and seomone will be able to help you, if not I will when I get back. :D

Regards, Herman  :D

---

### Post by Herman on 2007-06-03
P.S. Thanks,  saxplaya, for letting me know about blu.xpm.gz, I Googled it and downloaded one for my wife's computer, it's a perfect  match for her theme, she loves blue things, thanks again. :D

I also added [GNOME-Look.org]("http://www.gnome-look.org/?xcontentmode=160&PHPSESSID=981a82a9e6ffdebfd3801ffee1352143") to my Grub page, thanks to you, so you have helped everyone a lot, but you didn't know it. Thanks. :D

Regards, Herman
Bye now.

---

### Post by saxplaya on 2007-06-04
Thanks so much Herman!

I ended up just booting to the liveCD and fixing the "(hd1,0)" to "(hd0,1)" and everything works perfectly.
Oh, and you're welcome for helping you find the website, I do what I can. :-P 

Again, thanks very much, you're help is greatly appreciated.

-saxplaya

---

### Post by Herman on 2007-06-04
Hello saxplaya,
I'm finally back! I'm glad you were able to solve your problem, very good! It's worth a little trouble to have a nice grub splash and you learn some things about computers that way too eh? Good work and thanks for letting me know you did it okay,
Regards, Herman :D

---

