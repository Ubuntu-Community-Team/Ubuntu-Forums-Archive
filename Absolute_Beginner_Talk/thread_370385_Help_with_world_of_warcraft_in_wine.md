---
title: "Help with world of warcraft in wine"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by inyolefti on 2007-02-25
I have it installed through wine but it runs super slow, ime not running it with opengl because when i try it says 

libGL warning: 3D driver claims to not support visual 0x4b

i havent installed a driver for my video card thats the problem right?

this is my video card.
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

ive been looking around trying to find a driver for it and dled one someoen said to use Xorg witch seems really complicated...

can i get some help

---

### Post by inyolefti on 2007-02-25
Bump?

---

### Post by ed-j on 2007-02-25
I am a Novice myself!

Could you please tell me which Ubuntu you are using, and if you know where to find the Terminal?

---

### Post by inyolefti on 2007-02-25
ubuntu edgy eft

yes i know how to get to the terminal: applications -> accessories -> terminal.

---

### Post by inyolefti on 2007-02-25
please i REALLY need help with this (configuring xorg i think)

---

### Post by ed-j on 2007-02-26
> **inyolefti said:**
> please i REALLY need help with this (configuring xorg i think)

Sorry about the delay.

Try typing [COLOR="YellowGreen"]sudo dpkg-reconfigure xserver-xorg[/COLOR] into the Terminal. This will give you choices of how to configure your graphics. If there are any sections of choices that look to be set ok by default, or, there are any sections you don't understand, press [COLOR="YellowGreen"]esc [/COLOR]to skip to the next. Type [COLOR="YellowGreen"]exit [/COLOR]to leave the Terminal.

Best I can do!

---

### Post by Praill on 2007-02-26
It's probably slow because you have an Integrated Graphics Controller on the board instead of an independent gpu with video memory.

Does the game run any better in Windows on that machine?

---

### Post by inyolefti on 2007-02-26
Yes it runs great in windows to be honest witch is why ime hoping to get it to work in linux.

Ima try what ed-j said thanks.

---

### Post by ed-j on 2007-02-26
Hi Inyolefti !

I'm on line again if you need any help!

---

### Post by inyolefti on 2007-02-27
i tryed to do what you told me but when i had to restart ubuntu i had a blue screen that said i had messed something up so i just reinstalled it all.

i think i just need to get that opengl thing to work.

---

### Post by Praill on 2007-02-28
Hmm. I really dont think windows will open warcraft without Direct3D acceleration.. ie. a 3D card, and it definently wont run it well.
You don't have a independent gpu in that machine? ATI? nVidia?

If youre sure, are you installing wine from the repositories?
If you are, uninstall it and download the source from [http://www.winehq.com]("http://www.winehq.com"). When you run ./configure on the source make sure you resolve ALL the dependencies. Even the ones that just say WARNING.
This means installing all openGL libraries.
Then compile wine once theres no warnings (make, make install). And try to run wow with the opengl switch (wine WoW.exe -opengl)

---

### Post by inyolefti on 2007-03-01
Actually ive gotten it to work somehow without lag in game but the graphics are pretty bad,
any idea on how i can fix this?

---

### Post by inyolefti on 2007-03-01
i installed wine using automatix... ile try that.

---

### Post by Slychilde on 2007-03-01
Hello there,

Have you looked at [this part of the Ubuntu wiki]("https://help.ubuntu.com/community/WorldofWarcraft") yet?  It contains quite a bit of helpful information.

It has been my experience that if I want WoW to run well in Linux, then I have to run it under OpenGL.  It made a huge difference for me.  However, I'm not using an onboard card, and that may make a difference (doubtfully).  But, like the others said, that is really going to hurt your performance.  Invest in a new video card if you can - Nvidia is much more linux friendly imo.

Do you know if direct rendering is enabled?  I ask because I had that problem - just a shot in the dark.  Type

```
   glxinfo | grep direct
```

and paste the results for us (if that  command works, period).  It should say yes.  Also, could you tell us what your system specs are if you happen to know them?  Thanks!

---

### Post by ccw127 on 2007-04-27
Actually, you should see better performance in Wow using OpenGL when you are using wine. This is because wine doesn't implement D3d as well as the native libs by microsoft. Like someone else said, are you using the latest version of wine? Try the directions on [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
Also, check your xorg.conf and see if you are using just the basic vesa server. That is defiantly NOT the best bet if it turns out to be the case.
Finally, keep in mind that you will likely never see as good of performance under wine (configured ANY way) as you would playing wow natively. I speak from experience.... having a brand new, built by myself, compy with the latest and greatest hardware.
Oh, and I have found that you can set most of the settings in game to what you would use in windows... EXCEPT, turn off 'Vertical Sync' and turn down the 'Terrain Distance'. I am able to get a rather respectable frame rate. If you need more help/suggestions, feel free to email me,

[email]hololight@gmail.com[/email]
Chris

---

