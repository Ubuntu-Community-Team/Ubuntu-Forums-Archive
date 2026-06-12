---
title: "Rhythmbox crashes when iPod mounts"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Aholiab on 2008-01-02
I have a new iPod Nano (3rd gen.) that is crashing Rhythmbox whenever it mounts. The iPod has a FAT32 format with iTunes 7.5. This crashing hasn't always happened, but I cannot tell what made the change.

Can someone help? :(

---

### Post by galvheim on 2008-01-02
I can not help, but I can help by letting people know that I have the exact same problem. When mounted and trying to start Rythmbox it just crash after displaying Rythmbox for one second.

For now, I have to use Windows to deploy files on it.

Have also tried a bunch of other software, but none of them seem to work with this version of the iPod, yet....

---

### Post by CCNA_student on 2008-01-02
I would suggest that you use gtkpod. I did not even know that Rythmbox could manage an 
iPod. You can easily download gtkpod from the package manager. I hope my solution works for you.

         Sin Cere,

         CCNA

---

### Post by Aholiab on 2008-01-03
When I start gtkpod, I get this error:

Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.

When I click through, gtkpod wants to put the mountpoint at /media/disk, but my iPod is at /media/[ipodname], and gtkpod knows this from the preferences.

Rhythmbox works some/most of the time with iPod. It just inexplicably crashes other times when I mount the iPod.

---

### Post by jeffus_il on 2008-01-03
I've seen it happen, Don't know the solution but there can be two attempts in parallel to mount the ipod, Gnome will try to mount according to the definition in System>Preferences>Removable Drives and Media and Rhythmbox does its own  MTP. Cancel the gnome auto mount and see if the situation improves.

---

### Post by metalpancake on 2008-01-03
You could also consider using an open source firmware replacement for ipods called Rocbox.
[http://www.rockbox.org]("http://www.rockbox.org")
It allowas you to use a drag-and-drop interface with your music and can play sound formats not previously compatible with aplle software.
It also dual boots with the apple software so that you have the freedom to use wichever system you want.:)

---

### Post by dark_harmonics on 2008-01-03
> **Aholiab said:**
> I have a new iPod Nano (3rd gen.) that is crashing Rhythmbox whenever it mounts. The iPod has a FAT32 format with iTunes 7.5. This crashing hasn't always happened, but I cannot tell what made the change.

Can someone help? :(

Yes I had this same issue (i have the 8gb black one).
First you should make sure that "Portable Players - iPod" is the only portable players plugin that is checked in rythmbox's plug-ins.

 Try the following instructions at this link:
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

I would not recommend custom firmware. This will void your brand new iPod's warranty. 

I got the information from this forum thread. You'll see the post Ii thanked (5th post). 
[http://ubuntuforums.org/showthread.php?t=650094](http://ubuntuforums.org/showthread.php?t=650094)

---

### Post by metalpancake on 2008-01-03
> would not recommend custom firmware. This will void your brand new iPod's warranty. 

Yeah, I guess not. You can probably try uninstalling if you need waranty....
The package comes with a gui that installs it on your ipod. I think it can uninstall files too.

---

### Post by dark_harmonics on 2008-01-03
> **metalpancake said:**
> Yeah, I guess not. You can probably try uninstalling if you need waranty....
The package comes with a gui that installs it on your ipod. I think it can uninstall files too.

Yea if you can remove it cleanly then its an option. I just know that apple would use any excuse to not support it. I would consider open source custom firmware after my warranty expires.

---

