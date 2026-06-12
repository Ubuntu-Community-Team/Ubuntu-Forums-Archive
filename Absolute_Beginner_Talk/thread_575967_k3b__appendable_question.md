---
title: "k3b / appendable question"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by not_yet on 2007-10-14
I'm trying to back up my home folder before the next upgrade

I have an LG supermulti burner, and dvd-r disks

seems to burn fine with K3B

when I try to read the disk later, it won't show up in Nautilus

when I have the disk in and open K3B, it says the disk is appendable

I can see whats  on the disk, but can't do anything with it?

thanks

---

### Post by e_james on 2007-10-14
I am not familiar with your specific situation but I have some knowledge which may be helpful.

There are 2 different ways of creating CDs and DVDs which allow for adding further data to a partly filled disc.

1. Packet writing. This requires special software and makes the disc behave approximately like a floppy disc except you may not be able to delete. The procedure is often used in DVD recorders and discs must be "finalised" by the software used to write them before they are generally readable by other machines.

2. Multi-session. I believe this idea became popular via Kodak for creating CDs with photo collections. You could add a new set of photos several times until the disc was full. I discovered that I could make multi-session DVDs using XP but the burning software also warned me that only XP would be able to read them. They probably weren't taking linux into account but the limitation definitely applies to my DVD players.

My initial impression is that your k3b discs are multi-session. There should be a setup option to say "no multi-session" and / or "finalise disc, no further writing possible"

---

### Post by Squizzle on 2007-10-14
I had this same problem just today with k3b and an external LG multi burner (backing up the home directory also)...  it just wouldn't recognise the data disc straight after burning.

I use the external burner at home as it's faster and to minimise wear and tear on the fixed internal drive on the laptop... strangely though the burnt disc loaded fine in my internal laptop dvd drive.
 
When I burned a downloaded dvd image file (non multi-session obviously) on the external burner with k3b it loaded fine immediately after burning... so yeah, I agree that it's likely a multi-session thing.

---

### Post by e_james on 2007-10-14
In my limited experience, multi-format burners will read just about anything they can write but DVD-rom drives are much more picky. I have a personal preference for writing DVD+R discs and I have found that some makes of DVD+R are readable in some makes of DVD-R drives. I don't know about the other way around. I have also been told that burning DVDs at maximum speed (16X?) can create discs which are unreadable in other drives. Apparently you can sometimes see the speed changes on the disc dye layer. It is important to me to have a reliable disc first time, if possible, so I usually stick to 4X. A few minutes saved in the burn is normally the least of my time concerns. 

For the same reason I always prefer to verify discs after burning and I was looking for linux software which would do this.
[http://ubuntuforums.org/showthread.php?t=566495](http://ubuntuforums.org/showthread.php?t=566495)

---

### Post by Pumalite on 2007-10-14
For backup and restore:

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

---

