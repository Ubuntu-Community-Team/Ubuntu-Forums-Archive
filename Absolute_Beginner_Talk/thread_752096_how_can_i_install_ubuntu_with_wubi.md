---
title: "how can i install ubuntu with wubi"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by ~L~ on 2008-04-11
cam anyone tell me how to do it, step by step ? I am experienced with PC .
I do not wish to delete my current windows installation .thanks

---

### Post by wormser on 2008-04-11
The best way to get step by step directions is to find a blog or howto with directions.  [Here is one]("http://www.herroflomjapan.com/2007/09/28/major-geek-fun-playing-with-ubuntu-gutsy-gibon-risk-free/").

---

### Post by philinux on 2008-04-11
Comes from the horses mouth.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by Lazy-buntu on 2008-04-11
If you're looking for a real dual boot here's a nice link: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

This is for vista of course, but I don't see why it wouldn't work with XP, etc.

---

### Post by sub2007 on 2008-04-11
It's not much different except with with XP you have to use Grub, there's no way to add Ubuntu to XPs bootloader.

Wubi's really good for trialling Ubuntu. It's what pushed me to in the end move away from Windows, prior to that I was experimenting a lot with virtualisation but never really felt brave enough to partition. After using Wubi for a while (and it consequently breaking) I felt like I had to go ahead and partition. If you want any kind of permanent installation then you should probably partition and go for the full dual boot as Wubi is inherently more unstable.

This guide is also quite good for setting up a dual boot: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

For what it's worth I had more problems with getting Wubi to work than for getting a dual boot to work. But I'm glad I did try Wubi because it gave me the confidence to know that Ubuntu was definitely for me.

Bear in mind that before doing a Wubi installation you must ensure that your Windows is formatted in NTFS. If you have Vista it should be but if you have XP then by default it will be FAT32. FAT32 only supports 4GB files and so you will use up your virtual Wubi hard disk very quickly.

---

### Post by ~L~ on 2008-04-11
thanks all i will try it ^_^

---

### Post by hums07 on 2008-04-11
> **sub2007 said:**
> It's not much different except with with XP you have to use Grub, there's no way to add Ubuntu to XPs bootloader.

Of course THERE is! I am using it.
[http://ubuntuforums.org/showthread.php?t=755782](http://ubuntuforums.org/showthread.php?t=755782)

---

### Post by ~L~ on 2008-04-14
i want to ask some questions about linux ubuntu

can i use peer to peer software for legal torrents etc
can i use any movie editing software (im pretty sure no on that one, and i think i can live without it)
can i burn discs
can i use itunes for my ipod
can i chat with my msn address

i dont play games, what i usually do is chat on msn, browse the web on youtube, google, and mainly listen to music to relax from life's anxiety

thanks

---

### Post by hums07 on 2008-04-14
> **~L~ said:**
> i want to ask some questions about linux ubuntu

can i use peer to peer software for legal torrents etc
can i use any movie editing software (im pretty sure no on that one, and i think i can live without it)
can i burn discs
can i use itunes for my ipod
can i chat with my msn address

i dont play games, what i usually do is chat on msn, browse the web on youtube, google, and mainly listen to music to relax from life's anxiety

thanks

point 2. there are one or two software for it such as [Kino]("http://www.kinodv.org/"), PiTiVi. Dont expect the ability as powerful as paid software tho'. (at least at this moment).
point 3. Of course
point 5. Yes!
I dont know about other questions.

---

### Post by ~L~ on 2008-04-14
it says searching drives and it is stuck at 46% for EVER whats wrong

---

### Post by ~L~ on 2008-04-14
bump?

---

### Post by rev7 on 2008-04-14
> **~L~ said:**
> can i use peer to peer software for legal torrents etc
can i use itunes for my ipod

Yes on torrents, if you download one of the many torrent clients available for Linux.  No on iTunes-- However, quite a few programs will allow you to sync iPods.  Ubuntu comes with Rythmbox, which is very iPod friendly.


As to what is wrong as of your last post, there is too little information there.  Please let us know your hardware info, etc.  You may have to try the alternative installation CD.


Cheers!

---

### Post by ~L~ on 2008-04-14
i am posting through the hardy installation :)
finally.
now if you can show me a program to sync my ipod with ubuntu, and a program to use torrents with..I will change to ubuntu for ever :KS

---

### Post by sub2007 on 2008-04-14
You can get BitTorrent, Azeureus, KTorrent (very nice program), Deluge... there are plenty of torrent clients you can try in the repositories. You can even install UTorrent through Wine if you so wish.

For syncing iPods I don't know as I don't have one, many people recommend GTKPod or Rhythmbox. As I said, I'm nowhere near an expert on iPods.

---

### Post by ~L~ on 2008-04-14
thanks :)
as i wait for someone to tell me about the ipod sync issue..
Can anyone explain to me what GNOME is? Is it another distribution of linux or an upgrade? If I install ubuntu will I have to delete it to install GNOME? 
> You can even install UTorrent through Wine if you so wish.
Does using wine have any disadvantages ? Is it just a program ? 
:confused:
Thanks :)

---

### Post by Mazza558 on 2008-04-14
Go to add/remove programs and search for "Amarok". This music program will let you access your iPod. You can also try Exaile and Rhythmbox (Rhythmbox is already installed).

---

### Post by Mazza558 on 2008-04-14
> **~L~ said:**
> 
Can anyone explain to me what GNOME is? Is it another distribution of linux or an upgrade? If I install ubuntu will I have to delete it to install GNOME? 

GNOME is just the desktop for Ubuntu. You're using it now.

> **~L~ said:**
> 

Does using wine have any disadvantages ? Is it just a program ? 
:confused:
Thanks :)

It can be tricky to set up. Try Deluge instead (search in add/remove programs), this is a very good Bittorrent program.

---

### Post by sub2007 on 2008-04-14
GNOME is a desktop environment, it's what controls the graphical user interface. More info: [http://www.gnome.org/](http://www.gnome.org/) Ubuntu uses GNOME as it's desktop environment, but there is also KDE, the K Desktop Environment (Kubuntu) and the XFCE Desktop Environment (Xubuntu) as well as other Window Managers like Enlightenment and Fluxbox. One of the great things about Linux is that you can choose the desktop environment that you like the best. 

So basically, GNOME isn't a Linux distro but it's a shared project that many distros utilise to provide the graphical interface for their distros.

Wine is a program that allows you to run some Windows programs through Linux. It's far from perfect and generally speaking we'd advise against using Wine if there is a good Linux alternative as Wine is no where near native efficiency. However if you absolutely HAD to use UTorrent as you used it on Windows and it had features that you'd like that the Linux native clients didn't have then you could do that. I do use Wine for the odd thing that I want to run on Linux. It also allows you to run some games on Linux. Again it's not perfect but it's better than nothing.

---

### Post by ~L~ on 2008-04-14
thanks ^_^ it works
thanks sub2007 too

---

### Post by ~L~ on 2008-04-14
Ok here I have some more issues. Well one.
Sometimes my internet stops and I have to type sudo dhclient to have it again. What do I have to enable to have web permanently?
(windows is unaffected)

---

### Post by halitech on 2008-04-14
wireless or wired connection?

---

### Post by ~L~ on 2008-04-14
wired, ethernet

---

### Post by halitech on 2008-04-14
when you are not able to browse, can you open a terminal and ping any websites?

---

