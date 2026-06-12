---
title: "Updates changed my menu.lst!"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by nbeerbower on 2007-09-03
I'm really screwed now. I'm talking to you through my Wii. The kernel updates changed my menu.lst. Neither ubuntu nor xp is accessible. I got to Ubuntu by changing the partiton it booted from but it won't login. It says it couldn't write to the authorization file! I made a backup of menu.lst before I made Xp default booted os. Could I maybe delete some files on the ubuntu partition with some sort of boot disk so Ubuntu can write to the authorization file and I can change menu.lst? Or do I have to reinstall Xp or Ubuntu or something? All help is really apperciated. Excuse my spelling Like I said I have to type on my Wii.

P.S. I think the updates filled up my 3 gig ubuntu partition so please try and find a way I can delete files off that partitijn by making some sort of boot disk! I don't want to yank my hard disk or reinstall XP. Does any else think this is the problem? cause my ubuntu partition was running very low. Like it didn't let me install a small game one time!

---

### Post by sumguy231 on 2007-09-03
The "cannot write to authorization file" think usually happens when the disk is full or you don't have write permission to your home directory. Do this:
Press Ctrl+Alt+F1, and try to log in.
Run 'df -h'. Look and see if any of your filesystems are 100% used. 
If not, do an 'ls -l ~' and see if you see your username twice for the files. If root or something else is listed as the owner, try doing 'sudo chown -R /home/<your username here>'

---

### Post by nbeerbower on 2007-09-03
Thanks SumGuy. (Haven't tried it yet just saying thanks for the quick response)

I'm now talking to you via Ubuntu Live CD. (Thank God! :P) I'll check that out and get back to you guys on it. Thanks! I'm so happy I have the Live CD!

---

### Post by nbeerbower on 2007-09-03
Well turns out the Ubuntu partition is full and my backup menu.lst still exists. Should I now just remove unnessacary files using the Live CD? (I'm on the Wii again) :P

EDIT: Or should I just reinstall Ubuntu? I mainly just use it as a backup OS it wouldn't be a big deal if I lost the files on that partition.

---

### Post by Nigmah on 2007-09-03
[COLOR=DarkOrange]**How big is you hdd? Seriously 3 gig?**[/COLOR]

---

### Post by nbeerbower on 2007-09-03
That partition is. (I wasn't thinking. :P) My hdd is really 200 gigs

---

### Post by sumguy231 on 2007-09-03
No need to bother reinstalling, seems like a lot to do for what isn't a huge issue.*

You can clear up a little space by doing the following:
sudo apt-get clean

If you still need more, try deleting /tmp:
```
sudo rm -r /tmp/*

```
(Be very careful here - make sure it's exactly this, with no extra spaces or bad things could happen!)

Once you can log in again, run the very handy 'baobab' utility to find out exactly what is taking up all of your disk space - it will show your disk as a radial chart with the area of largest disk usage appearing largest.

***Edit: Just kidding, I just read that you have 3 gigs. It might really be best if you reinstall it and give it a lot more space. But if you ever run out of space again, keep this in mind.**

---

### Post by nbeerbower on 2007-09-03
Well, it worked I'm talking to you again with Ubuntu! I fixed my boot menu and I will consider reinstalling to make my partition bigger. lol :P

Thanks! I REALLY REALLY appreciate it.

---

