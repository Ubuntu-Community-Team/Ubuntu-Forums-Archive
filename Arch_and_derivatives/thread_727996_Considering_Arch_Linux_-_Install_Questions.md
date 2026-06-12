---
title: "Considering Arch Linux - Install Questions"
date: 2008-03-18
forum: Arch and derivatives
---

### Post by Perpetual on 2008-03-18
I have been looking at Arch for awhile and am considering giving it a go for fun to see what the hype is all about.  I am a little hesitant though as I am definitely not a hardened Linux veteran.  I have some experience and have used a number of Distros and am good enough on my own to deal with Debian.

Questions are:

1.  Does hwdetect automatically find my wireless card (Intel IPW2200) and install the kernel modules, firmware, etcetera so that once Gnome is installed I will be able to get wireless working?

2.  Same question as above but regarding video card (ATI Radeon Mobility 9200).  

Both of these items work fine with Ubuntu install right out of the box.

Finally, if answers to above are 'no', is it difficult (in a noob sense) to get these items working.  I do not use compiz but I would like the ability to if I decided I wanted to.

Any thoughts would be greatly appreciated.

Landon

---

### Post by Pogeymanz on 2008-03-18
I don't have experience with your specific hardware, but I have a laptop and I followed the beginners guide and the wireless wiki and it worked fine. If you plan on using Gnome and NetworkManager, it has a good wiki which was the one that got it working for me. 

It wasn't hard to install the system at all. The wireless required me to put it away and go back to it the next day because my head started spinning after the 3 hours it took to install the system.

---

### Post by PurposeOfReason on 2008-03-18
For your wireless card, when I compiled my own kernel that was checked by default and I did hwdetect so I figure it's pretty standard.

---

### Post by Perpetual on 2008-03-18
Thanks for the responses guys.  I may give it ago tonight.  I tried last week and it failed at installing GRUB.  I was trying to set-up a dual boot with WinXP and could not get past the GRUB stage.  Gave up then.  I may just wipe the HDD and install ARCH alone.

---

### Post by Gigamo on 2008-03-18
> **Perpetual said:**
> Thanks for the responses guys.  I may give it ago tonight.  I tried last week and it failed at installing GRUB.  I was trying to set-up a dual boot with WinXP and could not get past the GRUB stage.  Gave up then.  I may just wipe the HDD and install ARCH alone.

how can you fail at that? All you have to do is uncomment the windows entry and change hd(#,#) to the corresponding numbers for your computer.

---

### Post by Perpetual on 2008-03-18
> **Gigamo said:**
> how can you fail at that? All you have to do is uncomment the windows entry and change hd(#,#) to the corresponding numbers for your computer.

Was apparently being dense.  I will try again as a dual boot.

Thanks for the response.

---

### Post by eljoeb on 2008-03-18
Configuring Network Manager and wireless on Arch took five minutes for me with the help of the wiki.  It really is that easy.

---

### Post by mips on 2008-03-18
I think you will love arch. Just follow the wiki for whatever you need.

---

### Post by MisfitI38 on 2008-03-18
> **EmosSuck777 said:**
> I don't have experience with your specific hardware, but I have a laptop and I followed the beginners guide and the wireless wiki and it worked fine. If you plan on using Gnome and NetworkManager, it has a good wiki which was the one that got it working for me. 

It wasn't hard to install the system at all. The wireless required me to put it away and go back to it the next day because my head started spinning after the 3 hours it took to install the system.
This is what I like to hear. I'm glad the Beginner's Guide got you going without much hassle. I try to make it as informative, yet as effective as possible. Enjoy.. :)

---

### Post by RedMist on 2008-03-19
> **Perpetual said:**
> I was trying to set-up a dual boot with WinXP and could not get past the GRUB stage.  Gave up then.  I may just wipe the HDD and install ARCH alone.

Hi. I have installed the AMD64 version a few times and GRUB always fails to install the first time. Just go back into the menu and reinstall GRUB again. It always works the second time. I dont know if this is a bug or if its just me :lolflag:

---

### Post by Perpetual on 2008-03-19
Thanks for all of the responses guys.  I will probably wait until this weekend as it seems time is not something I have in the near future.

Landon.

---

### Post by rye_ on 2008-03-19
I've been considering arch as well.

I'm drawn to because it's a bit geeky, and sounds fun to learn.  That aside, I'm probably gonna put much the same software that's on my ubuntu box.  is it really worth it? should I be using xfce with it?

---

### Post by Rumor on 2008-03-19
> **rye_ said:**
> I've been considering arch as well.

I'm drawn to because it's a bit geeky, and sounds fun to learn.  That aside, I'm probably gonna put much the same software that's on my ubuntu box.  is it really worth it? should I be using xfce with it?

There was a time I was dual booting Ubuntu and Arch using pretty much the same software between them. Arch had significantly more free memory at idle than did Ubuntu. More system resources are always worth it.

As to your choice of Desktop Environment or Window Manager, use what appeals to you. Install more than one and try them out.

---

### Post by MisfitI38 on 2008-03-19
> **rye_ said:**
> I've been considering arch as well.

I'm drawn to because it's a bit geeky, and sounds fun to learn.  That aside, I'm probably gonna put much the same software that's on my ubuntu box.  is it really worth it? should I be using xfce with it?

Give it a shot. It is a lot of fun, and it sort of forces you to get your hands dirty, but you'll learn a lot on the way. The Beginner's Guide is excellent (if I do say so myself ;) ) and will have you off and running in a couple hours most likely.
Arch has no default desktop, no default anything. You assemble it from the command line and choose whatever works best for you. :)

---

### Post by Perpetual on 2008-03-20
Thanks for the responses.  I haven't made the leap yet, honestly, still rather intimidated.  I was once intimidated by Debian though and am comfortable with it now so, will be installing Arch this weekend.

---

### Post by Pogeymanz on 2008-03-20
Good luck. It's not really that hard, so don't sweat it. It does take a long time, though. I like Arch a lot and if I could finish all the tweaks on my laptop, I'd clear Ubuntu off of it and dedicate it to Arch.

---

### Post by Perpetual on 2008-03-20
> **EmosSuck777 said:**
> Good luck. It's not really that hard, so don't sweat it. It does take a long time, though. I like Arch a lot and if I could finish all the tweaks on my laptop, I'd clear Ubuntu off of it and dedicate it to Arch.

The more I read in the documentation the clearer things are becoming.  I have run into something I don't understand in the Beginners Guide.  It says:

```
pacman -S gnome gnome-extra
```

However, when I search all [Repositories]("http://www.archlinux.org/packages/search/?repo=all&category=all&q=gnome-extra&limit=50") there is no gnome-extra.  Furthermore, same for gtk-engine-murrine.

I haven't tried installing yet so not sure what will happen when I reach that point.

Will see soon though!

---

### Post by PurposeOfReason on 2008-03-20
> **Perpetual said:**
> The more I read in the documentation the clearer things are becoming.  I have run into something I don't understand in the Beginners Guide.  It says:

```
pacman -S gnome gnome-extra
```

However, when I search all [Repositories]("http://www.archlinux.org/packages/search/?repo=all&category=all&q=gnome-extra&limit=50") there is no gnome-extra.  Furthermore, same for gtk-engine-murrine.

I haven't tried installing yet so not sure what will happen when I reach that point.

Will see soon though!
I just checked for you, it exists. :) Easier to check here.
[ftp://ftp.archlinux.org](ftp://ftp.archlinux.org)

---

### Post by rye_ on 2008-03-20
I think I'm sticking with ubuntu;

It may not be i686 optimised but its pretty snappy on my core 2 duo.
I'm a gnome user (Gedit is unparalleled).  kde is too cluttered, xfce is nice though.
apt-get is great, could I want anything else?

Most Importantly, Canonical stands for freedom.  I don't fear the inclusion of propriatry apps.  The system they produce is really excellent, and it does mean a lot to me to have everything work.

May try arch on a secondary laptop/pc though.

---

### Post by PurposeOfReason on 2008-03-20
Gedit is really nothing compared to vim. ;)

---

### Post by aeto on 2008-03-20
The fact that this type of questions get asked is proof of the lack of confidence and/or competence.

However, if you could get down and dirty with Debian, then you won't have much problem here.

---

### Post by Perpetual on 2008-03-20
> **aeto said:**
> The fact that this type of questions get asked is proof of the lack of confidence and/or competence.

I would have to agree, that's why I am interested in learning it.

---

### Post by mips on 2008-03-20
> **rye_ said:**
> I think I'm sticking with ubuntu;

It may not be i686 optimised but its pretty snappy on my core 2 duo.
I'm a gnome user (Gedit is unparalleled).  kde is too cluttered, xfce is nice though.
apt-get is great, could I want anything else?

Most Importantly, Canonical stands for freedom.  I don't fear the inclusion of propriatry apps.  The system they produce is really excellent, and it does mean a lot to me to have everything work.

May try arch on a secondary laptop/pc though.

Good for you.
With arch you choose your own DE so it has nothing to do with kde, gnome, xfce etc.
pacman is actually better than apt, really go read up on it.

Canonical just takes from Debian and contributes back. It is no better any other linux distro if you ask me.

Yeah throw more processing power at it.
Out of the box it is a OK distro, mint is probaly a better ubuntu.

---

### Post by Pogeymanz on 2008-03-21
I like the Ubuntu philosophy (which is pretty much the same as all "big" Linuxes), however I've always been a tweaker at heart, even if I don't consider myself a power-user, and that's where Arch wins.

But the Arch philosophy of "Keep It Simple, Stupid" is great. I love the transparency and how the devs made it easy to find and interpret the system configurations.

The ONLY downside for me is the leniency for proprietary apps. I like how Ubuntu will let you play mp3's, but the documentation reminds you that ogg's exist, and stuff like that. Arch doesn't do that. Oh well, nobody's perfect. :)


I usually install XFCE and install gedit anyway. It is really good!

---

### Post by Perpetual on 2008-03-22
Well, took about 4 hours but got "everything" going.  Learned more in 4 hours than I did in the past 3 years.

A lot more to do still...

---

### Post by MisfitI38 on 2008-03-22
> **Perpetual said:**
> Well, took about 4 hours but got "everything" going.  Learned more in 4 hours than I did in the past 3 years.

A lot more to do still...

Congratulations and...
Welcome to Arch!

---

### Post by Perpetual on 2008-03-22
> **MisfitI38 said:**
> Congratulations and...
Welcome to Arch!

Thanks for the [Beginners Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide").

---

