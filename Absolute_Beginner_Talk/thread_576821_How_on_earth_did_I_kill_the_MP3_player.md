---
title: "How on earth did I kill the MP3 player?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-10-15
This is horrible!
I borrowed my father's MP3 player, an Asono with 512MB. When I plugged it into my computer to transfer the three songs I wanted to, it was auto-mounted read-only. So I tried to mount it manually.
```
sudo mount -o umask=0777 /dev/sdb /media/USB
```
Okay, it mounted, but trying to enter /media/USB resulted in "Access denied". Not too much familiar with Linux-hyper-nerd-codes yet, I simply typed
```
sudo cp /home/joakim/Music/* /media/USB
```
To copy the three songs inside the Music directory, and then
```
sudo umount /media/USB
```

And this is where it happened. Or didn't. Well, the drive unmounted, but that's the last thing it did. Now it doesn't auto-mount anymore, I'm not able to mount it manually, it doesn't show up in gparted and it doesn't even turn on!! HOW did this happen, and HOW do I fix it? PLEASE help! And yes, I tried changing the batteries :p

Thanks so much in advance!
Joakim

---

### Post by MatthewPlanchard on 2007-10-15
Have you tried using the mp3 player's reset function? On an iPod you can press and hold the select and menu buttons for ten seconds to perform a reset. If an Asono has the same ability that might do the trick.

If that doesn't work, well, I'm as lost as you are.

---

### Post by Daveth on 2007-10-15
I guess the most critical question to ask here is how long will it be before your dad asks for his player back.....? But I'm with Matthew- try a player reset and if that fails-leave home!:)

---

### Post by Joakim Stokland on 2007-10-16
> **Daveth said:**
> I guess the most critical question to ask here is how long will it be before your dad asks for his player back.....? But I'm with Matthew- try a player reset and if that fails-leave home!:)

And sacrifice free meals? Are you insane?? ;)

I tried menu + play for 10 seconds, but no change (there are only play, volume, skip, previous, menu and hold buttons). You haven't by any chance got an Asono AB-200 manual lying around? :p Can't find any on the net, and as you might guess, the bundled one is missing...

I guess i'll have to buy a new one if I can't revive it. Fortunately it's not an expensive player!

Any idea how those poor commands could create such a disaster?

Thanks for your help!
Joakim

---

### Post by Daveth on 2007-10-16
OK, so your mum is an excellent cook!
I wonder if it is player-side rather than Ubuntu side? A firmware upset perhaps? Have you ever moved songs from your computer to this device before? What does your long-suffering father use to download songs to it? Though it uses usb, it does have some sort of firmware "operating system" onboard, so is not just a passive storage device. Does it support the file format of the songs? I'm making this up, by the way! Pleased it is not a top of the range player:)

---

### Post by Joakim Stokland on 2007-10-16
Well, I just can't understand that transfering songs should destroy the firmware. It's not like I've overwritten or deleted anything (I didn't force the transfer, only performing it as root). The files I transferred were MP3s, just like the ones previously transferred to it.
Actually, my sister bought it a while ago, and replaced it with an Ipod after some time. So she gave it to my father, who actually has not used it yet, as he recently discovered the possibilities of MP3. Lately he has mentioned to start using it though, so I feel I do have to repair/replace it as soon as possible.
Anyway, my sister runs WinXP, and until now all transfers has been performed on her computer. This is the first time on any other computer at all. That's why I even speculate about whether my computer has caused this error or not.
No matter how I twist or turn, I simply can't find a logical explanation why Ubuntu should have caused this. I guess it's just coincidence - maybe it just was our beloved Asono's time..

Any thoughts to add?

---

### Post by argie on 2007-10-16
Maybe you accidentally unplugged it before it was done? If you have windows and this player uses some proprietary app to transfer files, trying it there might help to reset it. If all fails, put it back in and check with fdisk if it has a partition table.

 Also, the last time a USB device did that to me it was starting to die, but it was a poor quality pen drive anyway.

---

### Post by Joakim Stokland on 2007-10-16
This player is simply drag-n-drop. Works just like a thumbdrive, so no special software is available. And I'm 100% sure that it was successfully unmounted before I removed it. Furthermore, I've tried dmesg, but Ubuntu doesn't seem to discover it at all...
I'm starting to realize that it's really really dead...

Thanks anyway! Still, further suggestions will be appreciated! :)
Joakim

---

### Post by jay767 on 2007-10-16
Have you tried removing the battery for a few seconds? It worked on my Lyra when it went into a coma (actually it did that twice)

Also, is there a lock button on it somewhere? Maybe it's on and won't let the buttons do anything

---

