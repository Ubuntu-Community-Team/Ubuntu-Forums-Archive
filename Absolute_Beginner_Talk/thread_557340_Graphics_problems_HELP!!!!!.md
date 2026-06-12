---
title: "Graphics problems HELP!!!!!"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by JudasReanimated on 2007-09-22
I'm using Fiesty Fawn.

My problem is that when I have system color set for my panel it's fine

[http://img516.imageshack.us/my.php?image=screenshotuk3.png](http://img516.imageshack.us/my.php?image=screenshotuk3.png)

Now when I change it to solid color, or background image, or really anyway else.

[http://img516.imageshack.us/my.php?image=screenshot1fq7.png](http://img516.imageshack.us/my.php?image=screenshot1fq7.png)

I have the proper driver, and this is a relatively old computer with I810E Chipset, however this problem did not occur when I had Dapper Drake, only when I upgraded. I also had this with Edgy Elf.

Any Ideas?

---

### Post by agurk on 2007-09-22
Does the problem go away when you move the slider from Transparent to Opaque?

---

### Post by JudasReanimated on 2007-09-23
Yes when it's at 100%, any less and it's glitched looking.

---

### Post by agurk on 2007-09-23
Could you try creating and logging in as a new user to see if this problem is user-specific?

---

### Post by JudasReanimated on 2007-09-23
I've reinstalled ubuntu 3 or 4 times, and this machine is always affected by it. Other machines have no issues.

P.S. Logging in as root yields the same results. I can make a new user if you'd like, but I don't see that helping. I believe this is machine specific.

---

### Post by spur on 2007-09-23
From the pics in your earlier post it looks to me like a graphics card problem. Do you have the right driver enabled? If you are using an nvidia card you need the one for older cards I think. You may even need an older version if your card is ancient.
Try making the refresh rate a s slow as you can if you have the right driver. Also your graphics card might be on the fritz.
[IMG]http://www.cheesebuerger.de/images/more/bigs/a032.gif[/IMG]

---

### Post by agurk on 2007-09-23
Ah ok, I just wanted to make sure this wasn't related to old stuff left from previous versions or from another desktop environment installed parallel with Gnome. If you have reinstalled from scratch, that would not be the case.
The annoying thing is that I believe I have seen this once on one of my boxes, but I can't for the life of me remember what the cause or remedy was.
It's a longshot, but you could try enabling the double buffering extension in your xorg.conf (Load "dbe" at the end of the Module section):
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"GLcore"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dbe"
EndSection
```

---

### Post by JudasReanimated on 2007-09-29
The card isn't on the fritz, Dapper works just fine, and I installed it after feisty, then went back to feisty.

Also it's integrated video.

I'll try what you suggested Agurk, but keep the suggestions coming. I'd like to get this fixed. 

Also why would it work in Dapper and not Feisty? 

I assume there was a change of some kind that caused it to stop working properly.

---

### Post by JudasReanimated on 2007-09-30
Nope didn't work Agurk.

Anything else I can try?

---

### Post by JudasReanimated on 2007-10-13
Anything else I'd really like to get this fixed?

Bump

---

