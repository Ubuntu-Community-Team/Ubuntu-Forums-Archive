---
title: "How to Rip DVDs with Ubuntu?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Tachions on 2008-01-05
I like backing up my recently purchased dvds. I switched to Ubuntu and was wondering what a great dvd ripping software there is available? I used DvD shrink for windows. any ideas???? thanks

---

### Post by LowSky on 2008-01-06
AcidRip is a good one

---

### Post by wheredidrealitygo on 2008-01-06
K9Copy is also really good, if you want to rip to .ogg then Thoggen works really well too.

---

### Post by BLTicklemonster on 2008-01-06
I've found that if you install k9copy and k3b from synaptic or terminal, either one, then set up k9copy like so, settings, configure k9copy, dvd, check "burn with k3b": and "autoburn", with the size as 4300 (maybe 4400 will work, I don't know), then copy it to a directory as an iso image, then when it's done, k3b will take over and viola, archived copy.

---

### Post by mkquist on 2008-01-10
wow, that was easier than i thought would be... thanx :lolflag:

---

### Post by BLTicklemonster on 2008-01-11
Took me two years to find that out by accident one day.

---

### Post by HemiGTX on 2008-01-11
if you used DVDShrink.. try xdvdshrink.. :)

```
http://dvdshrink.sourceforge.net/
```

---

### Post by Tachions on 2008-01-22
> **HemiGTX said:**
> if you used DVDShrink.. try xdvdshrink.. :)

```
http://dvdshrink.sourceforge.net/
```

How do you install xdvdshrink?

---

### Post by chris200x9 on 2008-01-22
if you want to transcode you could try handbrake but it's on a cli on linux

---

### Post by Dr Small on 2008-01-22
> **wheredidrealitygo said:**
> K9Copy is also really good, if you want to rip to .ogg then Thoggen works really well too.
+1
K9cpy is the way to go ;)

---

### Post by oldos2er on 2008-01-22
> **Tachions said:**
> How do you install xdvdshrink?

 [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Tachions on 2008-01-23
> **Dr Small said:**
> +1
K9cpy is the way to go ;)

How come when I seem to backup my dvd with k9copy, this is my first time ever using this software by the way, i can not burn it. 

I see the iso and then select burn to disc it doesnt work, an error comes up. should i get a new burning software or anything else, doing something wrong...? 

thanks ahead of time

---

### Post by Tachions on 2008-01-23
bump

---

### Post by Hallvor on 2008-01-23
What burner do you use?

---

### Post by stchman on 2008-01-23
> **Tachions said:**
> I like backing up my recently purchased dvds. I switched to Ubuntu and was wondering what a great dvd ripping software there is available? I used DvD shrink for windows. any ideas???? thanks

I use K9Copy.  It does a great job.  I would use the version(1.1.3) from [www.getdeb.net](www.getdeb.net) over the one in the repos.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)  Look in the Software section

It has a few more features than the previous version.

---

### Post by JohnnyC44 on 2008-01-23
Well, I learn something every time I enter this forum.  But a little learning is a dangerous thing, they say.  This is in response to BLTicklemonster's post (#4 above).  Sounded good: I did the K9copy rip just fine.  The rest of the post says "K3b will take over and viola, archived copy."

Not so for me.  I got a K3b screen and tried to hack it.  Clicked "Burn" and Start is grayed out.  No amount of finnagiling will light up the Start button to begin the burn.  What am I missing in the "viola?"

FYI, I am an 8-month noob -- only an egg where linux is concerned, but I'm educable.  Any help in getting K3b to burn what I've ripped will help.  Thanks!

P.S. I have backed up DVD copies on Windows many times, so I know the process.  But I've just forced myself to use Ubuntu exclusivily for the past several months.  I wouldn't have to fire up my Windows machine at all IF Intuit would get off their **** and come out with a QuickBooks version for Linux.  I know the litenay about the alternatives, but 85% of Americans use some form of QBs! 

Thanks in advance.  Every time I've posted here I've gotten the right answer....

---

### Post by mr_ed on 2008-01-23
I assume that your burner is selected (and detected!) and that you've inserted a disc.

Under "Burn Medium" what does it say?

Sorry if I'm being Captain Obvious here.  Usually though when the "burn" button is greyed out it means something is missing.  You're burning an ISO file, right?

---

### Post by TeaSwigger on 2008-01-24
Warning that I'm not expert... I do use k3b though. I think it's the best burning app features-wise, but it's far from the only good one.

First, let me point out that once the ISO is made, you could try burning it with ubuntu / Gnome's native programs. Maybe they'd work. For instance, try burning it from Nautilus, I seem to recall it has some burning options? The best Gnome burner in my opinion is Gnomebaker; you could try installing it (easy as pie via Synaptic) and under tools you'll see "burn DVD ISO" or something like that, and go to it.

If you do want to use k3b, or if the above options don't work either, then see Cap'n Obv... er, ed's post above ;)

---

### Post by JohnnyC44 on 2008-01-24
mr_ed & TeaSwigger: Thanks for the speedy replies.  So I tried TeaSwigger's alternate path - using Ubuntu's CD/DVD Creator GUI.  It didn't like my generic DVD disks - couldn't recognize them.  So, the problem is obviously not with k3b afterall, it's my cheesy, cheap disks.  I tried several and Ububtu flatout doesn't want to play with them.  Same disks work fine in my Win machine.  So I'll go out and buy some name brand disks and see what happens.  Stay tuned....

---

### Post by TRANQU111TY on 2008-01-25
I'm ripping and burning with k9copy and it just works but I must say I didn't find it as user friendly as DVDFab for Windows.

---

### Post by asnd16 on 2008-01-28
K9copy is awesome . . . Thank You!  :guitar:

---

### Post by BLTicklemonster on 2008-01-28
> **JohnnyC44 said:**
> Well, I learn something every time I enter this forum.  But a little learning is a dangerous thing, they say.  This is in response to BLTicklemonster's post (#4 above).  Sounded good: I did the K9copy rip just fine.  The rest of the post says "K3b will take over and viola, archived copy."

Not so for me.  I got a K3b screen and tried to hack it.  Clicked "Burn" and Start is grayed out.  No amount of finnagiling will light up the Start button to begin the burn.  What am I missing in the "viola?"

FYI, I am an 8-month noob -- only an egg where linux is concerned, but I'm educable.  Any help in getting K3b to burn what I've ripped will help.  Thanks!

P.S. I have backed up DVD copies on Windows many times, so I know the process.  But I've just forced myself to use Ubuntu exclusivily for the past several months.  I wouldn't have to fire up my Windows machine at all IF Intuit would get off their **** and come out with a QuickBooks version for Linux.  I know the litenay about the alternatives, but 85% of Americans use some form of QBs! 

Thanks in advance.  Every time I've posted here I've gotten the right answer....

Not sure what could be causing the problem other than the obvious stated earlier.

If that wasn't what the problem was, there's certain stuff you need to already have installed to burn dvds. For the life of me I can't remember exactly which ones you need. I'm in kde4 right now, and have no idea what I'm doing, so I can't look and see what all I have to see if I can help. 

Perhaps some of the real heavy duty gurus here can post exactly what you will need to be sure you can burn dvds?

sorry

---

### Post by ediblestarling on 2008-05-23
I've tried both DVD::Rip and K9copy and imho k9 is far more user friendly (read:dummy proof) and easy to use, while dvdrip offers a much larger degree of customization but is harder to use. 

I'll be sticking with k9copy. hope that helps a little with making a choice!

---

### Post by xjgnsdof on 2008-05-23
I use Brasero to copy CDs and DVDs, but for copyrighted media, I use DVD Decrypter in WINE; nothing else gets around the protection. If you PM me, I can post instructions.

---

### Post by stinger30au on 2008-05-23
this may help
[http://ubuntuforums.org/showthread.php?t=781429](http://ubuntuforums.org/showthread.php?t=781429)

---

