---
title: "ubuntu woes.."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by 068139 on 2008-04-13
i have vista running on my other box which i regularly use.
but i decided to change this box to run xp/ubuntu.

i love the GUI and almost everything about ubuntu from the live CD, it's a bit choppy and laggy running from the CD, so I install it. 7.10 version.

I've got all the updates and yesterday it was running fine, today I loaded the OS and everything's laggy, I try to open Firefox and the system just crashes, I try to change any settings or click anything and it's crashing. Yesterday I got a bit annoyed because I had to set up everything manually so I could stream videos online but this is really..something and I have no idea what I did wrong and how to fix this.

ps: there's no graphics card in the box with ubuntu at the moment, this is possibly the problem? but yesterday it worked fine. also im using the minimal graphics settings

---

### Post by em3raldxiii on 2008-04-13
It sounds like the system is trying to run compiz-fusion.  I know you said you have it on "minimal settings", but you have to put visual effects to "NONE".  All the other options on that page will enable compiz-fusion.

You can also open System Monitor and check which processes are eating up CPU/Memory ... that can help you find the culprit and (potentially) end the process.  If the process is still necessary for your computer use, you can also lower it's priority (higher "nice" number).  This sometimes helps if you have something like video encoding going on in the background.

---

### Post by 068139 on 2008-04-13
can you give me any instructions on how to do this? thanks

**EDIT:**Hopefully I will be able to not crash the machine when changing these settings.
also I know that it'll be in system > personalise > appearance settings but what tab should i be in? thankyou!

---

### Post by sayakb on 2008-04-13
Ubuntu does not need an extra graphics card to run and it works really well on Intel onboard graphics. See my laptop's specs.. I run Gutsy with a GMA950 onboard really well. But still, you might try disabling compiz from System->Preferences->Appearance->Visual Effects->None. You might download a good GTK theme in case you want to make it look good even without compiz :D
For themes: [www.gnome-look.org](www.gnome-look.org)

---

### Post by 068139 on 2008-04-13
Thanks

I'll try this now and if it still gives me problems I'll get back to you.

---

### Post by 068139 on 2008-04-13
okay, I've tried it..basically when i load the OS after I click anything or...interact with it at all it crashes...if i press the eject button on my cd drive, it won't open either, obviously i wasn't able to change no settings with this major problem occuring..

i tried running the live CD to install it again...the CD lags like hell anyway, I tried it several times with no success, yesterday it took me several attempts also.

im going to add a graphics card and see if it makes any difference. if none is made im thinking windows is a hell of a lot easier to use as ubuntu 7.10 is my first experience of linux..not a good first impression, sorry :(

---

### Post by Martje_001 on 2008-04-13
If you can't reach the 'visual' tab, you might want to press ALT+F2 and typ **metacity --replace**

---

### Post by 068139 on 2008-04-13
> **Martje_001 said:**
> If you can't reach the 'visual' tab, you might want to press ALT+F2 and typ **metacity --replace**

thanks, Ill try this and let you know if it crashes.

**[edit]** after i put the gfx card in (only 64mb but better than on board) and i booted it asked me if i wanted to run in low graphics mode and i selected yes, always. I havn't had a problem with crashing since then so I guess it's solved...but how can i turn low gfx mode off? after i install the driver i want to see if i can run it normally. thanks

---

### Post by Martje_001 on 2008-04-13
Go to a terminal and typ:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions.

---

### Post by 068139 on 2008-04-13
> **Martje_001 said:**
> Go to a terminal and typ:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions.

thanks.

you've all been a great help, now running 1280 x 1024 resolution and it's all working perfectly. thanks guys!

---

