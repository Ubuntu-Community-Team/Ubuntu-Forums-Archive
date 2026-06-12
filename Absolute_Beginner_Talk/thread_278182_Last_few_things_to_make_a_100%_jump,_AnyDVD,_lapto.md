---
title: "Last few things to make a 100% jump, AnyDVD, laptop Q &amp; A"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Cornbread46 on 2006-10-15
OK I am ready to make a full time switch. I do not want to dual boot. I am an all go make it work kindof guy. I know if I leave Windows on my system.. I will be tempted to use it and not find the right way to do it so it is all or nothing for me...But here are my final concerns;

1)I only use a laptop at this time (Dell Inspiron 5100)so I am 
  wondering;
 a)what can I do for my touchpad drivers?
 b)video card drivers?
 c)power managment?
 d)other laptopy type concerns....
I haven't been able to find much dealing with laptops and this is a really big deal as this is my only system right now.


2) I use CloneDVD2 and AnyDVD a TON! I love my daughter but she ruins DVD's like acid ruins faces. I LOVE the CloneDVD interface and really would like something like it. or if this will work well in WINE or anything like it. (might be more involved but willing to figure it out for my Anydvd!)... I am mostly interested in the ability to compress and clone a whole dvd (menus/scene select/everything)with only some audio streams removed. This is a perfect solution for me and my family and I really don't want to live without it unless I find something DARN close... I know, I know, I know....not wanting to learn something new goes against this whole Linux swap... but this is one that I don't want to limit myself on.
  

Thanks in advance for any help!

---

### Post by capn_hector on 2006-10-15
check out this, [http://sourceforge.net/projects/shrinkta](http://sourceforge.net/projects/shrinkta).  in making your switch to linux, sourceforge will be your best friend.  loads of open source alternitives to do any thing you need to.  and most of the stuff is linux with windows ports.

---

### Post by Cornbread46 on 2006-10-15
that looks promising! but does it work with encrypted dvds??That is where AnyDVD shines...Most of the disks I want to back up are protected (Disney for shure!! and I don't trust my kid with those $25 two disc sets....)

---

### Post by capn_hector on 2006-10-15
id get it and try it, if not you just need to find something like dvd43 for linux  [http://www.dvd43.com/](http://www.dvd43.com/)  im sure it exists.  google would find it if shrinkta does not decrypt to.

---

### Post by d3v1ant_0n3 on 2006-10-15
"a)what can I do for my touchpad drivers?"

The default touchpad driver seems fine to me...all the buttons work and it's responsive. I still prefer using a mouse tho.
 
"b)video card drivers?"

From what I read [ here](http://reviews.zdnet.co.uk/hardware/notebooks/0,39023985,10003105,00.htm), that inspiron has an ATI video chip...I know some people have issues with ATI, and some people don't. Sorry, not much use as an answer, I know.

"c)power managment?"

Seems to work fine. suspend and hibernate work, the battery monitor works great. I can't seem to get CPU throttling to work personally, but I've not really tried.
 
"d)other laptopy type concerns...."

All my lappy buttons work. The lappy keyboard works good. All my hardware was detected off the bat. I might have been lucky tho.
I haven't been able to find much dealing with laptops and this is a really big deal as this is my only system right now.


2) I use CloneDVD2 and AnyDVD a TON! I love my daughter but she ruins DVD's like acid ruins..."
  
There is some dvd ripping software available through Automatix, but I've not given it a try yet, sorry.


Hope that was some help....

---

### Post by bodhi.zazen on 2006-10-15
For your DVD needs try [K9Copy](http://k9copy.sourceforge.net/)

For your drivers:

Did you boot with the Live Ubuntu CD? What were the results ?

You could also try contacting DELL directly.

---

### Post by BLTicklemonster on 2006-10-16
Get wine up and running using the link in my sig, so that you can use dvd decryptor, dvd shrink, and whatnot. Ignore what he says about using an older version of wine, just use the one you get from synaptic, then go get IE 6 here: [http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u](http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u) 

I used to use anydvd, but have been running into some problems with it not working on some newer dvds.

If you are running into problems with newer dvds, you will want to have [dvd decryptor and dvd shrink installed](http://www.mrbass.org/linux/ubuntu/dvdshrink/),but [read this first](http://www.ubuntuforums.org/showthread.php?t=36112&highlight=dvd+shrink) then go get this: [http://www.ripit4me.org/](http://www.ripit4me.org/) and use it to rip your dvds. START WITH RIPIT4ME, it will use dvd decryptor as needed. The instructions are on the site, so use them. 

Once you are done, you can use k3b to burn your dvd. Just pay attention to where the dvd rips to! Just drag your video_ts and audio_ts folders into the workspace on k3b and burn your dvd. One thing I have found about burning dvds, and I'm sure you have too, is to make sure you burn them slow or you will have problems with playback.

---

### Post by deeptingler on 2006-10-16
gotta say, the only reason I keep windows for duel booting is because of those programs too but have been experimenting with wine and dvdshrink too as beginning to hate going back to windows grrrrrrr

---

