---
title: "Problems using Ipod"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-05-27
I was trying to use my ipod with the KDE desktop on Ubuntu 7.04. I couldn't get Amorak to pick up my ipod so I installed gtkpod. I have figured out the command to mount my ipod, gtkpod opens and displays the music but when I try adding music it will add but then when I click save, it comes up with 'permission denied' and will not let me add music to my ipod. What am I doing wrong / not doing?? How do I get Linux to add music to my ipod??:confused:

---

### Post by spartan777 on 2007-05-27
you need to run gtkpod with admin permissions. you can try opening the command prompt and running
```
sudo gtkpod
```

---

### Post by ENN0 on 2007-05-27
Be careful..i got a nasty virus from gtkpod onto my ipod!!

---

### Post by spartan777 on 2007-05-27
a VIRUS? how is that possible? do you mean a windows virus? I don't know how that's possible without putting the virus on yourself, whether it was intentional or not.

---

### Post by ENN0 on 2007-05-27
> **spartan777 said:**
> a VIRUS? how is that possible? do you mean a windows virus? I don't know how that's possible without putting the virus on yourself, whether it was intentional or not.

When i used it it deleted all my songs and i was left with a blank ipod!i then hooked it up to my itunes on vista and it said there was a corrupt file so i had to format the ipod!

---

### Post by k1001001 on 2007-05-27
That's not a virus. Your iPod just freaked out and dumped its database file. It most likely happened because you unplugged the iPod while it was writing data. Also, if your iPod is getting older, the hard drive may be going bad. It happened quite often to my iPod mini. To fix this problem, all you have to do a factory reset on iTunes. You will lose your music though.

I did hear there were some iPod shipped with Windows viruses on them at one time though.

This reminds me, if anyone knows of a way to factory reset an iPod using Ubuntu, that'd be great if you could pass along that information. It's rather annoying to be stuck with a dead iPod until you can find someone with a Windows machine.

---

### Post by stewvmusic on 2007-05-29
> **k1001001 said:**
> This reminds me, if anyone knows of a way to factory reset an iPod using Ubuntu, that'd be great if you could pass along that information. It's rather annoying to be stuck with a dead iPod until you can find someone with a Windows machine.

Not sure what you mean by a dead iPod.  What do you mean by factory reset?  Do you want to start from scratch?

I plug mine (5G - 30Gig) into the USB port and it charges right up in Ubuntu Feisty.  

Also, if your iPod screen is stuck and it won't respond, hold the center button and the menu button simultaneously for 10 seconds and it should reset itself without losing any data.  Because the buttons are small be careful not to accidentally press one of the other buttons too.

Hope that helps...

---

### Post by Dragonbite on 2007-05-31
I just updated my iPod (Shuffle) through Banshee last night and everything worked fine except the database got messed up so the iPod wouldn't play.

I had to read the ipod in gtkpod and then resynch-ed in order to have gtkpod fix the database (didn't have to reload all of the songs because they were already present).  Gtkpod did, though, throw an error at me about the database being corrupt ( or something ) and was going to try and fix the meta-data.

I don't think I pulled the iPod while it was writing, but now that the database is corrected I'll have to see if Banshee will be able to run things without messing up the database again.

---

