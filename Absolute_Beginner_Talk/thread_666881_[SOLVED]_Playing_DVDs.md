---
title: "[SOLVED] Playing DVDs"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by rissie on 2008-01-13
I can't watch DVDs :( 

I tried to use Totem, which was installed previously. No good! 

The error message I got: 
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

So I went to [Movies, DVDs and videos]("https://help.ubuntu.com/7.10/musicvideophotos/C/video.html") documentation page and followed the instructions. 

I put in a DVD and gxine opened but it didn't load the movie. I got another error:. 
No demuxer found - stream format not recognised

I've also tried VLC which I used in Windows without issue, but it won't load movies. In fact it loads for a second then closes right away with no error messages. 

Please help?

---

### Post by jrusso2 on 2008-01-13
Those instructions don't tell you that you need libdvdcss2 which I think is in the mediabuntu repository.


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Udaho on 2008-01-13
Try installing the ubuntu-restricted-extras package.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Open a terminal and type

sudo aptitude install ubuntu-restricted-extras

---

### Post by meanburrito920 on 2008-01-13
go to Add/Remove and search for Ubuntu Restricted Extras. Install it and it should fix all your problems.

---

### Post by rissie on 2008-01-13
jurusso2: I have no idea what to do from that page. the /pool directory is all kinds of crazy. 

Everyone else: Ubuntu Restricted Extras is already installed. 

:(

---

### Post by philinux on 2008-01-13
Follow the instructions below 

medibuntu

---

### Post by rissie on 2008-01-13
Ok, to get a little more specific: 

The medibuntu page says to open a URL and pick the distribution I'm using. But there isn't an option. If I go up to the parent directory then I can select my distro. Cool. Then it asks that I select free or non-free. I'm not sure? Then it asks my architecture? 

I have no idea. :(

---

### Post by jrusso2 on 2008-01-13
> **rissie said:**
> jurusso2: I have no idea what to do from that page. the /pool directory is all kinds of crazy. 

Everyone else: Ubuntu Restricted Extras is already installed. 

:(

Scroll down to where it shows how to add the mediabuntu repository.

Once its added do sudo apt-get update

then sudo apt-get install libdvdcss2

That should fix it if you already installed libdvdread

---

### Post by rissie on 2008-01-13
> **jrusso2 said:**
> Scroll down to where it shows how to add the mediabuntu repository.

Once its added do sudo apt-get update

then sudo apt-get install libdvdcss2

That should fix it if you already installed libdvdread

Right, it's getting to the sudo apt-get update part that I'm lost at. 
I don't know if I need free or non-free or what my architecture is.

---

### Post by rissie on 2008-01-13
OK, I finally figured it all out but when I get to the part of the instructions when i put i ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-get add && sudo apt-get update
```

I get an error in terminal saying: 

gpg: can't open `': No such file or directory

---

### Post by rissie on 2008-01-14
Bumping this in hopes of help.

---

### Post by crjackson on 2008-01-14
nikoPSK usually beats me to these but here you go.  Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by nikoPSK on 2008-01-14
here you go:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```(if in gutsy replace from "fiesty" to "gutsy".) that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. 

Regards,
nikoPSK

---

### Post by nikoPSK on 2008-01-14
> **crjackson said:**
> nikoPSK usually beats me to these but here you go.  Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``````
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```You probably won't have any trouble after this.

LOL, well I got beat this time, we all benefit :p

EDIT: I shouldn't leave post boxes open for 20 minutes...

---

### Post by rissie on 2008-01-14
WOOO

I HAVE MOVIE!!! 

Thank you SOOO much.

(I have the most boring job ever and I work 10 hour shifts with nothing to do. The lack of movie watching has been killing me.)

You both get thanks!

---

### Post by nikoPSK on 2008-01-14
> **rissie said:**
> WOOO

I HAVE MOVIE!!! 

Thank you SOOO much.

(I have the most boring job ever and I work 10 hour shifts with nothing to do. The lack of movie watching has been killing me.)

You both get thanks!

:lolflag: no problem man.

---

### Post by Wharf Rat on 2008-01-14
Guys,
Thanks for the help.. It will solve the same problem for me.

However, when I input the line:
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
 
I this response asking for my Ubuntu Alpha disk.

After unpacking 48.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823)'
in the drive '/cdrom/' and press enter


Is there a way around it?

---

### Post by nikoPSK on 2008-01-14
> **Wharf Rat said:**
> Guys,
Thanks for the help.. It will solve the same problem for me.

However, when I input the line:
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
 
I this response asking for my Ubuntu Alpha disk.

After unpacking 48.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823)'
in the drive '/cdrom/' and press enter


Is there a way around it?

System->Administration->Software Sources

Then at the first tab uncheck the cd.

Best,
nikoPSK

---

### Post by Wharf Rat on 2008-01-14
Thanks nikoPSK!

Got it.

---

### Post by nikoPSK on 2008-01-14
> **Wharf Rat said:**
> Thanks nikoPSK!

Got it.

No problem. :)

Best,
nikoPSK

---

