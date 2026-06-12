---
title: "Can I install Fiesty Now?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-04-11
Hi guys, my laptop just got formatted. Its an ATI vid card that ran the proprietary drivers from A.TI and Beryl. If I install Fiesty now, can I update using normal update tomorrow to the RC1? and then can i do subsequent updates to get the final full release working? or is it just going to bork up? Are the updates going to update to a full release or just a working copy of RC1?

The reason I ask is because I need to get some work done on it and I don't want to install Edgy, then reformat to install Fiesty.

Thanks in advance.

---

### Post by angkor on 2007-04-11
> **Bagboy23 said:**
> If I install Fiesty now, can I update using normal update tomorrow to the RC1?

Yes

>  and then can i do subsequent updates to get the final full release working?

Yes

>  or is it just going to bork up?

 Who knows...it's still beta :)

> Are the updates going to update to a full release or just a working copy of RC1?

In the end, you'll be running the full release.

> The reason I ask is because I need to get some work done on it and I don't want to install Edgy, then reformat to install Fiesty.

When you need to get some work done....I'd install Edgy. You know edgy works on your laptop, who knows what problems feisty will give you in beta stage. You can always upgrade edgy to feisty after the final release.

---

### Post by finferflu on 2007-04-11
You don't need to reformat in order to install Feisty, you can just [upgrade]("https://help.ubuntu.com/community/FeistyUpgrades"). I suggest you to stick with Edgy if you want a stable system.

---

### Post by Bagboy23 on 2007-04-11
Does anyone have a direct link to an ISO, the upgrade method I cannot do because I don't have an OS on my lappy.

---

### Post by pppetter on 2007-04-11
Edgy(6.10) or Dapper(6.06):
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Feisty:
[http://www.ubuntu.com/news/Ubuntu704Beta](http://www.ubuntu.com/news/Ubuntu704Beta)

---

### Post by LookTJ on 2007-04-11
you can find the torrent [here](http://linuxtracker.org/torrents-details.php?id=3788&hit=1).

---

### Post by IndyBob on 2007-04-11
For my $.02 worth, wait on the final release.  I tried the upgrade from Edgy to Feisty and it "borked" as you said.  I went back to Edgy and will give Feisty time to settle down before I try it again.

---

### Post by bodhi.zazen on 2007-04-11
My 2c ~ Fresh install Feisty

FYI there is a Feisty Forum : [http://ubuntuforums.org/forumdisplay.php?f=179](http://ubuntuforums.org/forumdisplay.php?f=179)

---

### Post by macogw on 2007-04-11
Most of the problems have been smoothed out.  There's a few little wrinkles, but they're nothing major, and there's workarounds for a lot of them.

---

### Post by dhtechs on 2007-04-11
:D  I upgraded to the Feisty Beta as you were wondering about....with no problems...had an issue with swiftfox locking up, but it seems to have been ironed out with the daily updates......However, IMHO, a clean install is ALWAYS preferrable to an upgrade.

---

### Post by IndyBob on 2007-04-11
Maybe I had an older Desktop CD of Feisty or it could just be my 'puter won't handle it.  I have a Dell Dimension XPS R400 that I bought in 1998 that I have upgraded from Windows 98 to XP Pro and to an Intel Pentium III 850 mgh processor with 384 MB ram and two 40GB WD hard drives.  I still am going to wait just a while after the release before I upgrade.

---

### Post by ayenack on 2007-04-11
Hey all. I would say not to upgrade just yet. I've been testing Feisty on my test PC and have had a few problems with some of the different pieces of kit I've tried on it e.g. wireless adapter that works fine on Edgy, sound card and monitor that also work fine on Edgy but not on Feisty. So I say if it ain't broke don't fix it. Not yet anyway.

Best of luck. ayenack.

---

### Post by Bagboy23 on 2007-04-14
Guys when I try the latest CD, what happens is that I get a quad-screen effect. My screen splits up into 4 sections all showing the same desktop. I can't use safe-mode or whatever the second option is called because that gives me problems. Any ideas?

I have a ATI Radeon x700 Mobility Card.

---

### Post by igknighted on 2007-04-14
> **Bagboy23 said:**
> Guys when I try the latest CD, what happens is that I get a quad-screen effect. My screen splits up into 4 sections all showing the same desktop. I can't use safe-mode or whatever the second option is called because that gives me problems. Any ideas?

I have a ATI Radeon x700 Mobility Card.

Now THAT is weird... try switching to tty1 (ctrl+alt+F1) and changing your xorg.conf to use the vesa driver.  Then restart X and see if it works.  The you can install fglrx again and be happily on your way.  Once its figured out, file a bug report too so the devs know.

---

### Post by Seisen on 2007-04-14
You can always do this with the older computers to be able to run the newer version of Ubuntu.

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

