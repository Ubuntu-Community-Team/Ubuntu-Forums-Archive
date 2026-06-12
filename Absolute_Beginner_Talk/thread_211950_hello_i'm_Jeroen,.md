---
title: "hello i'm Jeroen,"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Jeroen2006 on 2006-07-09
hi i'm jeroen and i'm a Unbuntu user for about 3 days... ilove it

but i keep having problems to get my mp3 and wmv files going

who would be so kind to help me out step by step to configure unbuntu?

this is what i've done already:

found in synaptics the flashplayer-mozilla (that worked)
also the w32 codecs (restricted formats)
but i dont know wich Gstreamer package i need

also the source updating thing doesn't work (i'm doing something wrong i think)

also i've updated the repository channels but do i have to edit them also?

sorry for the many questions.... i'm a complete noob and dutch:D 

thanks for the help

(i just want to play mp3's and also movie's/ streaming media)

thanks a lot

Cheers jeroen

---

### Post by bigken on 2006-07-09
install automatix this solve all your codec problems follow this guide;) [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

---

### Post by Jeroen2006 on 2006-07-09
> **bigken said:**
> install automatix this solve all your codec problems follow this guide;) [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

hi, thanks for the reply,

i've been warned about this sort of programs i don't know why
could you explain to me why it possible harm my system?

thanks a lot 

Jeroen

---

### Post by SkyNet2029 on 2006-07-09
AFAIK, yes, it is possible for Automatix to break your system, just like any other program that modifies your sources.list file, installs software from NON-official repositories, or makes system-wide modifications to the structure of your installation. In my personal experience, when I was running K/U/Xubuntu (yes, I like variety :-P  I had no issues with it. Then I reinstalled the OS, ran Automatix, and all kinds of things were hosed. 

A much smoother (and official) method is to hit this page here:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

and follow along as the Ubuntu wiki shows you the way to , umm, Ubuntu smoothness, all the way down to getting the ability to play your encrypted DVD's, .avi's, WMV's, etc. It also has some links to things like Flash and Java. Almost everything you can think to install has been tried and yes, broken on Ubuntu by now, so its always a good idea to check the wiki for pointers before using a third-party application. Incidentally, the methods in the wiki are actually less time-consuming than using Automatix.
Hope this helps.

---

### Post by Jeroen2006 on 2006-07-09
hi SkyNet2029

would you be so kind to post a list of packages?

like the gstreamer????? ( do i need those there are a lot of them)

thanks very much

greets jeroen

---

### Post by someusernoob on 2006-07-09
> **Jeroen2006 said:**
> hi, thanks for the reply,

i've been warned about this sort of programs i don't know why
could you explain to me why it possible harm my system?

thanks a lot 

Jeroen

Harm is a big word i think.

I prefer Bumps over both Automatix and Easyubuntu. Bumps doesnt change that much, it actually only installs multimedia codecs + some firefox plugins. Nothing more or less. When i used Bumps im almost ready with setting up playback for every file i want to play.

Automatix en Easyubuntu come with a big list of programs and configuration settings, if you dont look out and pay attention for what it installs it might install and configure things you do not want or do not need, and espacially for "newbies" it can be hard to ondo this.

I never used Automatix or Easyubuntu. I'd rather find out myself how to install programs. I bumped into Bumps when i allready knew how to install those things, but Bumps just makes it a little bit easier/faster for me when i reinstall, i do not need to manually install all the packages.

PS; I see that you installed flashplayer-mozilla. Can i ask you something? Would you visit this site: [http://www.planet.nl](http://www.planet.nl) and do you see any text in the middle flash section?

---

### Post by andyman on 2006-07-09
Or you could try:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

I've never had any problems with this and it doesnt modify your sources.  Seems to be a very popular way to get the initial setup working.

---

### Post by SkyNet2029 on 2006-07-09
I think this is what you meant :
(This is just cut and paste from my previous link though. That page covers just about every media format imaginable ;)  ) 

I had forgotten about EasyUbuntu..Whoops ! That actually does work rather sweetly and gives you the option as to whether or not you wish for your sources.list file to be modified. Thanks, andyman.


How to Make Things Work in a Hurry
Ubuntu 6.06 LTS (Dapper Drake) 
Install the following packages to play most proprietary formats using Totem and Rhythmbox, which both come with Ubuntu. 
Since the version of Totem that comes with Ubuntu doesn't yet play DVDs, the list below also includes packages for the GXine player, which does. 
 gstreamer0.10-ffmpeg 
 gstreamer0.10-pitfdll 
 gstreamer0.10-plugins-bad 
 gstreamer0.10-plugins-bad-multiverse 
 gstreamer0.10-plugins-ugly 
 gstreamer0.10-plugins-ugly-multiverse 
 gxine 
 libxine-main1 
 libxine-extracodecs 
 w32codecs 
Note: to enable w32codecs, see the [https://help.ubuntu.com/community/RestrictedFormats#w32codecs]("https://help.ubuntu.com/community/RestrictedFormats#w32codecs") section 
Kubuntu 6.06 
 libxine-extracodecs 
 w32codecs 
 libarts1-mpeglib 
 libakode2-mpeg

EDIT: someusernoob- > PS; I see that you installed flashplayer-mozilla. Can i ask you something? Would you visit this site: [http://www.planet.nl](http://www.planet.nl) and do you see any text in the middle flash section? I used the instructions from the wiki and all the flash (lots) shows up fine, (I use Konqueror though )

---

### Post by someusernoob on 2006-07-09
> **SkyNet2029 said:**
> 
EDIT: someusernoob-  I used the instructions from the wiki and all the flash (lots) shows up fine, (I use Konqueror though )
[SIZE="1"]Sorry for going a little off-topic. But there are 2 flash players in the repo's. They both work fine, the only problems is that flashplugin-nonfree installs automaticly the package gsfonts-x11. Flashplayer-mozilla doesnt. So i missed a lot of text on some flash sites using the mozilla one without gsfonts-x11. And gsfonts-x11 makes fonts in the menus of xmms real ugly.[/SIZE]

---

### Post by Jeroen2006 on 2006-07-09
hoi someusernoob, ( i'm writing now in dutch because he is dutch)

het gaat als een kogel met die flashplugin.. Synaptics> zoek maar op flash

Groetjes jeroen

---

### Post by someusernoob on 2006-07-09
Yes i know, see my post above you.

(Repo's = repositories = the servers that provide the stuff you find in synaptic)

My point was that if you install the mozila plugin, and have not installed gsfonts-x11 (might be automaticly installed by another program) you do not have fonts on some flash sites.

---

### Post by bigken on 2006-07-09
sorry but I have to disagree I use 3 different  boxes and 2 laptops all of different makes I have ubuntu on all of them and I have used automatix on all of them with no problems what so ever ;)

---

### Post by someusernoob on 2006-07-09
As i said, it might that another program installs gsfonts-x11. I have 3 ubuntu boxes here, all configured with the mozilla plugin and it doesnt install gsfonts-x11 it self. So there was no text in some flash sites.

If you look in Synaptic at the "properties > dependencies" of both the flashplayer-mozilla and flashplugin-nonfree, you'll find out that with the nonfree one gsfonts-x11 is depended and with the mozilla one its only recommended. When it is recommended it doenst install automaticly. But there might be more (complete other) programs that depends on gsfonts-x11, so it might be installed allready, and yes, then it runs fine without any problems.

---

