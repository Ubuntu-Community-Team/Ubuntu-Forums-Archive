---
title: "Laptop screen resolution and other help"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by mattaklysm on 2008-04-14
Hi folks,

I have a question about my dell 700m. I love this little machine, especially now that I've loaded Ubuntu on it. The only thing is that I want to upgrade to a larger hard drive. That's my first question:

1.) For the Dell Inspiron 700m: what hard drive size would you recommend me getting? What make? I've had both Windows and Linux running on this machine and found that 40gigs doesn't cut it.

Here's the second questions about Screen Resolution:

The 700m has a 12.1" wide-aspect screen with a resolution setting of of 1280 x 800. Windows is fine on it, but Linux is having trouble adjusting to that type of size. I'm guessing because it is such a tiny screen with such a high resolution - it's hard to get that type of software support. I've already tried to go into [SYSTEM] to [ADMINISTRATION] to [SCREENS AND GRAPHICS]. After that I set the Screen Tab instead of plug n' play, set to Dell, the next field to the right is set to either 1024 x 768 Dell Laptop display panel or to 1280 x 1024 Dell Laptop Display Panel. Both of those settings doesn't even fill the whole screen even the 1280 setting. ..... So

2.) How can I get the resolution to match up to the 1280 x 800 size that I get with Windows? 


So those are my two questions. If anyone could help me out mostly with the display question I would be a happy camper. Thanks!

---

### Post by kbless7 on 2008-04-14
For a hard drive I would get a Seagate Momentus 7200.2. Thats their best line with an rpm of 7200. As for the size of it, I have a 120Gb for my dual boot and its fine.

---

### Post by pedro_orange on 2008-04-14
I believe you can add resolutions to your xorg.conf

I would be careful of doing this. Since the drivers for your graphics may not be able to support it. Look it up. 

You can reconfigure xserver (including resolutions) with the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lpkizz on 2008-04-14
1) hard drive don't matter Ubuntu unlike windows only need 1 GB of hard drive so 5 GB will do great i got mine installed on my USB stike it's only 4GB here is a pic of how it looks like but do you want to use Ubuntu only or do you want to keep Ubuntu and windows but to let you know i recommend a SATA Hard drive 

for you're  screen resolution you need to play around with you're xorg.conf i can't tell you more about x.org i don't know allot:guitar: about i t

---

### Post by mattaklysm on 2008-04-14
> **pedro_orange said:**
> I believe you can add resolutions to your xorg.conf

I would be careful of doing this. Since the drivers for your graphics may not be able to support it. Look it up. 

You can reconfigure xserver (including resolutions) with the following command:

```
sudo dpkg-reconfigure xserver-xorg
```




thank you. i did a search on that command line and found a lot. i've accidentally stumbled upon xorg before and i've gotten in trouble with my hardware not being able to recognize the display size. but i'll give it a good look-see and figure something out. thanks

---

### Post by mattaklysm on 2008-04-14
> **kbless7 said:**
> For a hard drive I would get a Seagate Momentus 7200.2. Thats their best line with an rpm of 7200. As for the size of it, I have a 120Gb for my dual boot and its fine.

hm unfortunately my options are limited with my laptop because it's so small, that it wont support anything that large and running at such a high rpm. 

i'm only used to replacing desktop hard drives. do you know of any good HD for laptops. I can only get a 60 gig. nothing higher, i'm afraid.

EDIT:/
Hey guys,

I just got a new HD for my laptop. here it is: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148128](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148128)

---

### Post by mattaklysm on 2008-06-03
> **mattaklysm said:**
> hm unfortunately my options are limited with my laptop because it's so small, that it wont support anything that large and running at such a high rpm. 

i'm only used to replacing desktop hard drives. do you know of any good HD for laptops. I can only get a 60 gig. nothing higher, i'm afraid.

EDIT:/
Hey guys,

I just got a new HD for my laptop. here it is: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148128](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148128)

hey all

so i put a new HD in my computer, maxed out my ram slots in my little dell 700m - both in the upper and lower decks of the memory sinks. she purs like a kitten. completely reformatted everything so i've got about 30 G's of space for Windows (oink oink) and around 20 for Ubuntu including the swap file and a convenient fat32 shared partition in case i want to share data between both operating systems. I've almost completed my dream machine! but not quite...

the only thing is that blasted screen display is not working properly for me. i went through xorg.conf and did some stuff on it. but it wont take me to the command screen that i want to see with all of the different screen resolution settings. (please forgive my newby idiocy). 

here's what happened: it asked me a bunch of question about my mouse and keyboard interface settings. i followed the instructions for an American keyboard layout and then skipped the setup for the 3 button mouse thing. then it exited straight to the regular terminal and out of the xserv.config blue screen and said that the setting was saved. huh?

i wasn't able to get to the different screen resolution settings in the xserv that i wanted. my laptop is running at a 1280x800 in windows, and i suspect it would do the same for "gutsy". 

it never said anything about a weird driver setting for my computer. do i have to load a special driver for my 1280x800 screen? is it some sort of a display adapter? i'm sorry for being very new at the xserv interface. maybe i'm over looking something.

if any noble souls can help out a blind dingbat like myself, i would be more than appreciative. 

thank you, kindly.

Matt

---

### Post by mattaklysm on 2008-06-16
/update

so i got my screen to work....finally. just a quick recap is that i was having trouble getting the screen of my dell 700m laptop lined up correctly. it would keep projecting at 800x600, which is the size for a default machine. but i have a 12800x800 screen on my laptop. so as you can imagine, it was really annoying using 3/4 of my screen. 

i did get in and do a reconfigure of the xserver-xorg, but that wasn't what fixed it. i just kept doing my updates, and it gutsy fixed itself. what i actually think was that someone actually added the driver support for the type of graphics card i was using. ALSO, i remember once seeing that Dell was supporting and advertising Ubuntu on their systems. maybe doing a split install of windows on one half and then linux on the other. so i guess that's what shed some light on some of the driver support. i dunno, i'm just speculating now.

anyways. i hope this helps out anyone else who was having trouble with their dell 700m.

---

