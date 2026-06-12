---
title: "What programs do I need for my Ubuntu System?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by b-rose on 2007-10-03
Alright everyone. For those who dont know, my windows computer crashed, the system restore disks didnt work and I couldnt install ubuntu. Well, it ended up being the harddrive so I bought a new one and I now have a fresh new install of Ubuntu on my computer. Thanks to everyone who helped on my previous thread. This is obviously a very active and helpful community and it has shown so far.

Now, I have been a windows guy my entire life and have a fair knowledge of computers, but I have never touched linux before. And since my windows system resource disk had an error in it, I am going solo with Ubuntu. That means I have to find some great programs to not only take over for what I used windows for, but also to get the full potential out of this wonderful operating system.

There are three main things I am looking for right now
1) Obviously when my computer crashed, all 600+ of my songs in ITunes dissapeared as well. I have them on my Ipod however. What program would I use to sync my music with my ipod back and forth and play music as well?
2) Flash, Windows media, quicktime... all media imbedded on the web. How can I get this up and running?
3) Any programs for Ubuntu that were simlar to Limewire?

And as I said previously. Any programs you would reccomend I play with to get the full potential out of my Ubuntu would be great. Thanks guys!!!!

---

### Post by nerdzero on 2007-10-03
Hi b-rose,

This website might help you:

[http://www.linuxalt.com/](http://www.linuxalt.com/)

It lists some Linux equivalents of Windows software.

---

### Post by j.bunce on 2007-10-03
iTunes - gtkpod

```
sudo apt-get install gtkpod
```

Firefox Plugins: [http://www.getautomatix.com](http://www.getautomatix.com)

Limewire - [http://www.limewire.com](http://www.limewire.com) install j2re from automatix first. Download the debian linux package and install

:)

---

### Post by gautada on 2007-10-03
> **b-rose said:**
> 1) Obviously when my computer crashed, all 600+ of my songs in ITunes dissapeared as well. I have them on my Ipod however. What program would I use to sync my music with my ipod back and forth and play music as well?

I use [Banshee]("http://banshee-project.org/Main_Page").  But you already have [Rhythm Box]("http://www.gnome.org/projects/rhythmbox/").  Either will do but I would rip all my songs off the ipod dump the drm(if any)  and them put them back on the ipod.

> **b-rose said:**
> 2) Flash, Windows media, quicktime... all media imbedded on the web. How can I get this up and running?

If you have a 32 bit machine this will be fairly straight forward.  Look at this [article]("https://help.ubuntu.com/7.04/musicvideophotos/C/index.html").


> **b-rose said:**
> 3) Any programs for Ubuntu that were simlar to Limewire?

I used [gtk-gnutella]("http://gtk-gnutella.sourceforge.net/en/?page=news").

> **b-rose said:**
> And as I said previously. Any programs you would reccomend I play with to get the full potential out of my Ubuntu would be great. Thanks guys!!!!

Be patient you  are not on windows any more and it is not that you cannot do what you want but that there is a different mindset to getting it done.  As for software the sky is the limit just make sure you don;t go completely nuts trying different software.  Try one or just afew packages at a time.  To see how easy it is to install packages just look [here]("https://help.ubuntu.com/7.04/add-applications/C/index.html").

---

### Post by multifaceted on 2007-10-03
Ubuntu comes with a ton of excellent software that rivals many proprietary software. Such as an office suite, photo editor (similar to Photoshop) CD/DVD burners, and so on... There are many more than can be installed with "Add/Remove" programs.

-You might be stuck with the songs on the iPod. It can play them right from the iPod itself when connected. Just be sure you have all of the proper **Gstream codecs** installed. That can also be done from "Add/Remove"!

-Firefox is the default web browser and is the best in my opinion. i used it long before i moved over to Linux. If there is a flash media or shockwave plug-in missing, Firefox will let you know and download the update for you.

-No, nothing similar to Limewire... which is the worst type of P2P client out there. there are P2P programs installed and that also can be obtained. they however, specifically use the **torrent protocol.** IMO, there is no better way to go, larger files and faster transfer.

---

### Post by dpar on 2007-10-03
As far as Limewire goes, theres Frostwire.

Edit: as far as Automatix is concerned, PLEASE don't use it. Read the sticky at the top of the form page.

---

### Post by rfruth on 2007-10-03
Easy Ubuntu is nice ! [http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")

---

### Post by gautada on 2007-10-03
> **j.bunce said:**
> Firefox Plugins: [http://www.getautomatix.com](http://www.getautomatix.com)

Note that automatix is not supported here.

---

### Post by Paul820 on 2007-10-03
Here is some info on restricted formats: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by b-rose on 2007-10-03
This is great guys. Thanks so much for your opinions. If anyone has any other programs that they would recommend that havent been listed here feel free to fire away. I really want to immerse myself in this thing!

Keep em coming!

---

### Post by stchman on 2007-10-03
> **b-rose said:**
> Alright everyone. For those who dont know, my windows computer crashed, the system restore disks didnt work and I couldnt install ubuntu. Well, it ended up being the harddrive so I bought a new one and I now have a fresh new install of Ubuntu on my computer. Thanks to everyone who helped on my previous thread. This is obviously a very active and helpful community and it has shown so far.

Now, I have been a windows guy my entire life and have a fair knowledge of computers, but I have never touched linux before. And since my windows system resource disk had an error in it, I am going solo with Ubuntu. That means I have to find some great programs to not only take over for what I used windows for, but also to get the full potential out of this wonderful operating system.

There are three main things I am looking for right now
1) Obviously when my computer crashed, all 600+ of my songs in ITunes dissapeared as well. I have them on my Ipod however. What program would I use to sync my music with my ipod back and forth and play music as well?
2) Flash, Windows media, quicktime... all media imbedded on the web. How can I get this up and running?
3) Any programs for Ubuntu that were simlar to Limewire?

And as I said previously. Any programs you would reccomend I play with to get the full potential out of my Ubuntu would be great. Thanks guys!!!!

Sorry to hear about your hdd.

I don't believe you can retrieve your songs off the ipod (DRM).  I have a script that will install a list of popular and useful programs.

[http://www.stchman.com/feisty_script.html](http://www.stchman.com/feisty_script.html)

Enjoy.  The script will set your PC up to do DVD, MP3, and other restricted formats.

---

### Post by multifaceted on 2007-10-03
**Inkscape **is a Vector drawing program that is very similar to Adobe Illustrator. I think it's more intuitive too. 

Another thing is I would recommend is Thunderbird as an email client. Evolution is set as default in Ubuntu but, it's got a lot of bells and whistles that I don't care for. But Evo work well too.

Rythymbox is an audio player that is similar to iTunes in it's UI. It loads by default when you plug in yout iPod...(or it does with mine at least) remember, be sure that you install the proper Gstream codecs for playing wma, mp4, aac and mpeg files as aforementioned.

---

### Post by oldos2er on 2007-10-03
1 -- I don't know; don't "do" DRM.
 2 -- sudo aptitude install ubuntu-restricted-extras (in a terminal).
 2 -- Frostwire.

---

