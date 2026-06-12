---
title: "Only 640 x 480 and other newbie probs"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by Major Matt Mason on 2005-11-13
I don't think you can get much newer than me. I've come straight from Windoze and the learning curve is steep, nay vertical.

I'm running a Tosh Tecra PII.

I can only get 640x480 resolution and I've been reading the posts and people are talking about typing stuff into sudo and then there is loads of code and, well, I'm still none the wiser. (I didn't get a choice of resolutions when Ubuntu installed).

I've also got a Linksys Wireless-B Notebook adapter 2.4 GHz and don't know where to start with getting that up and running in Breezy Badger.

These two questions probably don't have a short answer, but any clues would be helpful from any of you wonderful people.

Ta

Matt

---

### Post by Wangsta on 2005-11-13
i have exactly the same problem, so i would also like to know how to fix this.

---

### Post by frodon on 2005-11-13
To allow higher resolutions you will need to specify the horizontal and vertical refresh rates of your screen.
All is in this guide : [http://www.ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate](http://www.ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate)
Feel free to ask for more details here.

---

### Post by Major Matt Mason on 2005-11-13
Thanks Frodon

But when I said I was a real newbie, I wasn't joking. How do I get a terminal/console to run in Ubuntu?

Matt

---

### Post by salva on 2005-11-13
Go to Applications->Accessories
there you will find a menu shortcut to your terminal.
If you want you can right click and select - add to panel. This will place an icon in your top panel for easy access to your terminal.
And dont worry, after a couple of tries with different terminal commands you will quickly get the hang of it, sudo and all. ;)

---

### Post by Major Matt Mason on 2005-11-13
Thanks mate. Getting there...

---

### Post by az on 2005-11-13
Some older cards with small amounts of video memory are misconfigured and the 24-bit color depth by default results in poor resolution.  You can try 16-bit or even 15-bit mode...

---

### Post by Major Matt Mason on 2005-11-13
Yes, I got given this laptop, so thought I would try Linux for the first time. Bit of a project, that's turning into an obsession...

How do I switch to 16- or 15-bit mode?

---

### Post by Major Matt Mason on 2005-11-16
[QUOTE=frodon]To allow higher resolutions you will need to specify the horizontal and vertical refresh rates of your screen.
All is in this guide : [http://www.ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate](http://www.ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate)
Feel free to ask for more details here.[/QUOTE]

It worked! Cheers, you're a star.

Matt

---

### Post by patrick295767 on 2005-11-16
[QUOTE=Major Matt Mason]I don't think you can get much newer than me. I've come straight from Windoze and the learning curve is steep, nay vertical.

I'm running a Tosh Tecra PII.

I can only get 640x480 resolution and I've been reading the posts and people are talking about typing stuff into sudo and then there is loads of code and, well, I'm still none the wiser. (I didn't get a choice of resolutions when Ubuntu installed).

I've also got a Linksys Wireless-B Notebook adapter 2.4 GHz and don't know where to start with getting that up and running in Breezy Badger.

These two questions probably don't have a short answer, but any clues would be helpful from any of you wonderful people.

Ta

Matt[/QUOTE]

did you try : 
dpkg-reconfigure xserver-xorg
  
  
  
----------------
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)

---

### Post by patrick295767 on 2005-11-16
[QUOTE=Major Matt Mason]It worked! Cheers, you're a star.

Matt[/QUOTE]
  
Nice !!
  
Enjoy Linux !

pat'

---

