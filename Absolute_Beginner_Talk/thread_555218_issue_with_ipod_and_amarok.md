---
title: "issue with ipod and amarok"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Skull Kid on 2007-09-19
I have a 4th gen 20gb ipod that I've been using with Amarok for quite a while now. But yesterday when I wanted to add songs Amarok threw some error at me, and after I disconnected my ipod shows 0 songs and I lost my itunesDB. Apparently though my songs are still there, because at the settings screen it still shows theres ~400mb remaining (but 0 songs though). Whenever I reconnect my ipod amarok either doesn't recognize it or shows 0 songs. Is there anything I can do before I reload all my songs again? Thanks in advance

---

### Post by Skull Kid on 2007-09-19
bump I guess

---

### Post by Maxtorm on 2007-09-19
Not sure if this will help at all, but have you tried doing a reset on the iPod?  You may know how to do this already, but if not: turn on the iPod, hold down the Menu button and the centre button at the same time for about 10 seconds; eventually the iPod screen will go dark and then the Apple logo will appear. Try reconnecting after that.

---

### Post by simonn on 2007-09-20
After you plug in your iPod, wait 10 seconds and in a terminal:

```

$ dmesg

```

Copy the output here.

NOTE: the $ above is the prompt, do not type it! $ generally means you are a user, if # is used it means to type the commands as root.

Your ipod disk may be corrupted and may need to be fsck'ed (File System ChecK) - a bit like chkdsk in dos and windows fat. dmesg should give us more information.

Another possibility is that the itunes db on the ipod is corrupted/blanked. This can be usually be resurrected using gnupod or gtkpod.

---

