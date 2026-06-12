---
title: "Upgrade from the image?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-10-19
is it possible to get upgrades from the CD?because the servers are SLOWWW!!!
thanks:)

---

### Post by Hobo Joe on 2007-10-19
Sadly, no. At least, not that I am aware of.

I feel your pain though, my updates are going at about 5KB/s.

---

### Post by Dr Small on 2007-10-19
I do not know, as I have never done it before, but just give it a few days, and let everything die down. Alot of people, for some reason, were upgrading yesterday, and downloading Gutsy via FTP and HTTP, causing the servers to go slow.

Everything should calm down in a couple days.

Dr Small

---

### Post by hyper_ch on 2007-10-19
it is...

(1) fetch the alternate .iso

(2) mount it in the system

(3) add the "CD"-repo again in your sources

(4) upgrade

---

### Post by plinydogg on 2007-10-19
How do you "mount it in the system?"

---

### Post by hyper_ch on 2007-10-19
the simple way would be burning the image to a cd and then open/close the cd drive ;)

or you could

```

mount -o loop -t iso9660 file.iso /media/cdrom0

```

---

### Post by Hobo Joe on 2007-10-19
It would be really nice if the Ubuntu dev's could somehow make it so that the updates could come from a torrent, especially for times around the release, when everything is so bogged down.

---

### Post by Dr Small on 2007-10-19
> **Hobo Joe said:**
> It would be really nice if the Ubuntu dev's could somehow make it so that the updates could come from a torrent, especially for times around the release, when everything is so bogged down.
Yes, that would be awesome :D

---

### Post by plinydogg on 2007-10-19
Oh, so if you've already got a CD containing the image, "mounting the CD" really just means inserting it into the drive.

---

### Post by hyper_ch on 2007-10-19
pliny:

yes, it will be auto-mounted then...

Then go to synaptic and enable CD/DVD also as source...

However this works only with the ALTERNATE install cd.

---

### Post by Dr Small on 2007-10-19
> **plinydogg said:**
> Oh, so if you've already got a CD containing the image, "mounting the CD" really just means inserting it into the drive.
The cd will auto mount, if you are running a desktop and have pmount, or such.
So, yes, you just pop it in, and then uncomment the cd repositories from your sources.list

---

### Post by plinydogg on 2007-10-19
hyper_ch: Thanks for clarifying. I've got the alternate CD so I should be good to go. I'll give it a whirl as soon as I get home from work.

---

### Post by hyper_ch on 2007-10-19
good luck.

---

### Post by plinydogg on 2007-10-19
hyper_ch: since you seem to know what you're talking about, do you have any insight regarding this issue?

[http://ubuntuforums.org/showthread.php?t=581263](http://ubuntuforums.org/showthread.php?t=581263)

---

### Post by hyper_ch on 2007-10-19
I just pretend to know things ;)

---

### Post by plinydogg on 2007-10-19
I'm sure that someone with 1900+ beans knows a thing or two!

---

### Post by hyper_ch on 2007-10-19
I know how to add beans to my count ;)

---

