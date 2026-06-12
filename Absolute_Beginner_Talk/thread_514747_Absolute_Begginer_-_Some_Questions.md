---
title: "Absolute Begginer - Some Questions"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by DampCat on 2007-08-01
Morning all.

I've heard of linux and a lot of my old friends have used it in the past, however, i've never really taken the plunge. I've seen an awful lot of press recentley regarding Ubuntu so have popped over to ask some questions, to see if it is possibly something i can get into.

I'm worried about software support. I dont play many games anymore but the ones i do i enjoy playing a lot. World of Warcraft for example. CSS. Is it possible to run these on a Ubuntu system? Is it a simple case of install and play, or do i need an XP emulator? or do i need to play around with the WoW/CSS system files?

I'm currently building a Carputer. It's a low-powered low voltage mini-itx PC to be used solely for MP3 and DVD playback. Perhaps if i get sad/desperate enough it'll eventually support Wi-Fi for internet browsing. Would Ubuntu be suitable for this? This is relevant as OS's such as XP and Vista are huge monsters and take a LOT of ram to make them work. Apple is out of the question for me. I'm limited to 512mb ram here to keep hibernation times low and not drain my car.

Generally, how easy is it to make a fully working Ubuntu system? Do i need to spend hours coding my own programs a la Slackware or is there a rather large pre-installed package or easy to access community created programs?

How large/system intensive is Ubuntu? 

I'm really sorry if this information is sitting on the site easy to find, but i'm at work and a lot of sites are unavailable to me. Thanks a lot for any help you can provide.

---

### Post by 505 on 2007-08-01
If you play games a lot, Linux is not really suited. These games need Windows. And although there is the Windows emulator (Wine), games remain problematic. However, if you want to try Ubuntu you can set up a dual boot system, so you can choose to boot Windows or Linux.

For a car computer Linux could be ideal. It is free an you can make it lightweight. For example, you could install Ubuntu without the GUI, relying only one the command line. There are command line MP3 players. This sure would fit on 512 MB ram.
To install and run Ubuntu you don't have to code anything yourself. It is an automated process, much like the Windows setup. After the basic setup, you can install new packages for extra software. This is as simple as selecting it and clicking apply. I think the system requirements are about the same as XP for the full GUI system. Although I also have a server running Ubuntu (no GUI), and that stays beneath 1GB for the total installation.

---

### Post by atomkarinca on 2007-08-01
> **DampCat said:**
> I dont play many games anymore but the ones i do i enjoy playing a lot. World of Warcraft for example. CSS. Is it possible to run these on a Ubuntu system? Is it a simple case of install and play, or do i need an XP emulator? or do i need to play around with the WoW/CSS system files?

you can play these games perfectly fine using a software called wine. and these are the howtos:

wow: [http://ubuntuforums.org/showthread.php?t=312482&highlight=wow+howto](http://ubuntuforums.org/showthread.php?t=312482&highlight=wow+howto)

css: [http://ubuntuforums.org/showthread.php?t=304528&highlight=css+howto](http://ubuntuforums.org/showthread.php?t=304528&highlight=css+howto)

---

### Post by atomkarinca on 2007-08-01
> **DampCat said:**
> 
I'm currently building a Carputer. It's a low-powered low voltage mini-itx PC to be used solely for MP3 and DVD playback. Perhaps if i get sad/desperate enough it'll eventually support Wi-Fi for internet browsing. Would Ubuntu be suitable for this? This is relevant as OS's such as XP and Vista are huge monsters and take a LOT of ram to make them work. Apple is out of the question for me. I'm limited to 512mb ram here to keep hibernation times low and not drain my car.

512mb ram is more than enough to get ubuntu working and you can play mp3 or dvd files using gui.

> Generally, how easy is it to make a fully working Ubuntu system? Do i need to spend hours coding my own programs a la Slackware or is there a rather large pre-installed package or easy to access community created programs?


it's as easy as one click. if you don't have very brand-new hardwares, you won't have a problem. you can check it using the livecd. if you can do everything fine using the livecd, you're good to go.

(sorry for the double post :))

---

### Post by DampCat on 2007-08-01
Ah, brilliant thanks guys. Looks like i might be looking into Ubuntu for my Car PC then. I might stick to windows on my desktop for now though, until i've looked into WINE stability a bit more.

Thanks for the excellent replies :)

---

### Post by jombeewoof on 2007-08-01
I don't know what CSS is, but i had WoW running at a solid 70 fps with a P4 2.8 Nv6800. 
wine is a bit of a pain, but that was better than I had it running in xp by about 30 frames.

you can get the games running, but you have to follow the guide exactly.

---

### Post by DampCat on 2007-08-01
In that case, if i was to move over to Ubuntu and use WINE for the games... what about hardware support? IE. My crappy Nvidia card requires all sorts of lame updates to keep going. These are only ever released in Apple and Windoze, so would i have to somehow run these drivers through WINE? Or is there a community hiding somewhere that takes these drivers and makes them Ubuntable?

I'm really sorry, i really do know nothing :P

---

### Post by Steveway on 2007-08-01
There are Linux-drivers for your card.
On a standard-install it uses nv wich gives you good 2D-Acceleration but no 3D.
Then you can install the nvidia-driver wich can be installed via one click in the restricted-driver-manager.
It gives you full support for 2 and 3D.
There is also a project called nuveau wich tries to give us an fully open-source 2 and 3D cappable driver for Nvidia-cards, but it's really unstable at the moment, I tried it on Fedora 7.
And one or two more things:
1. **W**ine **i**s **n**ot an **E**mulator
2. If you just want a Multimedia-box for playing music and Dvds I'd recommend Geexbox, it's a Distribution especially created for this task but Ubuntu would work equally well.

EDIT: Forgot one important thing: Welcome to the free world!

---

