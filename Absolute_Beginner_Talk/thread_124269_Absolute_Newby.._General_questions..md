---
title: "Absolute Newby.. General questions."
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-01
I tried the live cd and i gotta say i love this os..


MOST IMPORTANTLY:
how do i set up a dual boot?


im an absolute newbie when it comes to linux so i know NOTHING... 

Why should i choose linux..
Why should i choose Ubuntu?
Whats the dif between kde and the other one.


I REALLY want to set this up on my thinkpad r52.. but the screen resolution only goes to a certain size.. I like LOTS of space and everything to look very tiny. Does anyone know a way to do this? 

My ethernet doesnt work..

How do i scan for wireless networks? (my wifi works straight out of the box! :-D )

What is the best c++ ide for linux? 


Thank you guys.. Im pretty excited about ubuntu, but help me make this a more realistic migration (namely the screen res and ethernet)..:cool: 


Also, how do you get to the console and what are some basic commands?

---

### Post by systemintheglitch on 2006-02-01
Also: Any free firewalls for linux?
Any free virusscans?

Are there cool utilities as in windows (defrag, system restore)..

So why should i not choose red hat?

---

### Post by Jason_25 on 2006-02-01
[QUOTE=systemintheglitch]

So why should i not choose red hat?[/QUOTE]
For one, Ubuntu is free.  Red Hat is commercial software.

> 
How do i scan for wireless networks?

```

iwlist scan eth0

```
Replace eth0 with whatever your wireless adapter is named.  You can also do System > administration > networking in gnome.  Then click your wireless card and choose properties I think.  I'm not using wireless on ubuntu at the moment.


For your screen res, you will need to edit your xorg file to include the resolutions you want.
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by alamba on 2006-02-01
1. Dual boot - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
2. Why use linux/ubuntu - U'll need to figure out your own reasons. Mine's pretty trivial - I like the ability to look at the original code (even if I don't always understand it)
3. KDE & GNOME (the other one) are basically GUI to linux. Try both and see which you prefer. As a base rule, GNOME is cleaner and good for newbies, KDE has much more options
4. Screen resolution - Once you have ubuntu installed come back here and someone will help you with the screen resolution. Should'nt be too much of a problem with thinkpad.
5. Not sure about your ethernet.
6. Easy way to connect to wireless networks. Just search the forum.
7. Firewall - IPtables. Fronend - Firestarted. Very user friendly.
8. Anti-virus: You typically don't need one but a number of them are easily available. ClamAV for one.
9. Cool utilities - As a rule you can customize linux much more primarily due to the way its structures (kernel design) etc. You won't need to defrag linux.
10. Redhat - Go ahead and try it. I used it for 6 years and dumped it for ubuntu mainly for apt-get as against rpm.

Akshay

---

### Post by Jimmey on 2006-02-01
Dual booting couldn't be simpler.

The installer, for 5.10, loads everything like the liveCD does, infact the first difference you see is when it loads the partitioner. 

When it does, the first option it offers is to resize the largest partition on your hard drive to make room for Ubuntu. All you have to do is set the amount of disk space you want to assign to Ubuntu, and mash enter a few times....I'm not even kidding. It's that simple.

Choose Ubuntu, because It's the best. (lol)

I mean, not just the operating system, but these forums aswell, make Ubuntu one of the easier going Linux operating systems. If everything doesn't work, there's amost definately people on here who will know how to help you to get it to work...And will have no hesistation in helping you.

To be honest, I'm pretty sure that the desktop environment you choose now will be the one you learn to love...If you start with KDE, you'll probably then prefer it to Gnome, and vice versa. It's down to personal preference - Your choice :)

Choose Linux because it's friendly. Choose Linux because it's free :)

---

### Post by xmastree on 2006-02-01
[QUOTE=Jimmey]When it does, the first option it offers is to resize the largest partition on your hard drive to make room for Ubuntu. All you have to do is set the amount of disk space you want to assign to Ubuntu, and mash enter a few times....I'm not even kidding. It's that simple.[/QUOTE]
It should be mentioned at this point, to back up any valuable data on the partition you want to resize. :rolleyes: 

> Whats the dif between kde and the other oneKde has more features, and uses more resources. Gnome is lighter, so better for slower systems. Even slower ones should use xfce/fluxbox/icewm. It's **your** choice, that's the beauty of linux.

---

### Post by Bartender on 2006-02-01
As far as dual-boot, I second alamba.  The link he provides was crucial to my successful dual-boot just a week ago.  On the one hand, yeah, you could probably just wing it but I wouldn't suggest.  If you can, set yourself up next to a second computer with access to internet and use the connected machine to walk thru the steps one by one.  
Prior to doing it that way, I tried printing out the "Ubuntu + NTFS" guide and got just text, none of the graphics.
xmastree is also right on the money.  Back up everything that you would miss if something goes wrong.  Do you have everything you need to re-install Windows?  You don't have to look hard to find posters who are quite disconcerted that "Ubuntu wrecked my Windows!" but I have to wonder how many of them woulda been able to pull off a Windows/Windows dual boot?  Anybody doin' major brain surgery oughta have Plans B, C, and D ready to go.

---

### Post by MartinJ on 2006-02-01
You may want to have a look at [http://www.thinkwiki.org](http://www.thinkwiki.org)
Or more specifically: [http://www.thinkwiki.org/wiki/Category:R52](http://www.thinkwiki.org/wiki/Category:R52)

---

### Post by xmastree on 2006-02-01
Found this:
[http://video.google.com/videosearch?q=linux+dual+boot](http://video.google.com/videosearch?q=linux+dual+boot)
Whilst googling around. They're starting from zero, so they don't resize an existing windows partition. But it could be useful.

---

### Post by saubz on 2006-02-01
here is a site that helped me out as well.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by systemintheglitch on 2006-02-01
Thanks for the help everyone..

How do i access the command prompt? 
 
Also.. With that screen resolution command, is it possible to set my screen resolution larger than windows will allow me to?

---

### Post by xmastree on 2006-02-01
Depending what version, (with my 5.04 it's in applicationx>system tools but I believe it may be different in 5.10) look in the menus for **Terminal** to open one on your desktop. Or, try Ctrl-Alt-1 and log in there.
The first option is similar to a DOS box in windows, the second is more like booting into DOS, big and ugly.

---

