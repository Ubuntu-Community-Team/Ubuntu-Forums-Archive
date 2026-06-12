---
title: "Rar programs don't support rars?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by TruthlessHero on 2007-07-28
Alright, I've been trying for at least 30 minutes to get this rar archive open. I have installed the following:
7Zip(can't find)
Ark
KArchiver
XArchiver

Messages say the following when I try in these programs:

Archive Manager - "Could not open 'file.rar'" "Archive type not supported." Didn't look at help file yet for this app.
Ark - "The utility unrar is not in your PATH." "Please install it or contact your sys admin."
KArchiver - "Compressor is not available."
XArchiver - "Sorry, this archive format is not supported: the proper archiver is not installed!"

I feel really stupid, since I've looked for how to fix each of these, but most of the stuff I found I exited in frustration. There ought to be an easy fix for at least ONE of these, no?

---

### Post by RomeReactor on 2007-07-28
Hi. You need to install **unrar** and/or **p7zip-full** so Ark and other archive managers know how to open them:
```
sudo apt-get install unrar p7zip-full
```

---

### Post by TruthlessHero on 2007-07-28
Could I interest you in my firstborn? :P Thanks much.

---

### Post by wrongo on 2007-07-29
Fix didn't work.

No go.

Still can't "unpack" .rar files.

Would anyone be willing to help me diagnose the problem?

What information do you need about my computer?

---

### Post by Endolith on 2007-07-29
Can someone explain why we have to install the other packages like unrar by hand?  Shouldn't this be included/automatic?

---

### Post by asmoore82 on 2007-07-29
because the unrar code is non-free* ...

I always use the command-line 'unrar' program to unpack rar's

```
~ $ unrar e *rar_archive.rar*
```


*Think free as in Freedom; not "Oo!! Free BEER!!"

---

### Post by Endolith on 2007-07-29
> **asmoore82 said:**
> because the unrar code is non-free

So are lots of things.   Why does non-Free --> force users to jump through hoops?

---

### Post by asmoore82 on 2007-07-29
> **Endolith said:**
> So are lots of things.   Why does non-Free --> force users to jump through hoops?

In a way, you just answered your own question. Keep in mind that it is the makers of non-free
software that are forcing you to jump through hoops and not the Linux Community.
Non-free programs in a Free OS contaminate the entire system and make it non-free as a whole.

If there were any defalt components to Ubuntu that were not freely redistributable, you would
not be able to download/burn your own install disks and/or pass them on to friends.

> **"Ubuntu Home Page"]
The Ubuntu Promise

    * Ubuntu will always be free of charge, including enterprise releases and security updates.
    * Ubuntu comes with full commercial support from Canonical and hundreds of 
          companies around the world.
    * Ubuntu includes the very best translations and accessibility infrastructure that the
          free software community has to offer.
[b]    * Ubuntu CDs contain only free software applications said:**
> 
[www.unbuntu.com](www.unbuntu.com)

---

### Post by Endolith on 2007-07-29
[I hadn't realized that unrar was proprietary.  Now it all makes sense...]

> **asmoore82 said:**
> In a way, you just answered your own question. Keep in mind that it is the makers of non-free
software that are forcing you to jump through hoops and not the Linux Community.

Not in any way, shape, or form.

It's disturbing that there was no easy way to install non-free codecs and drivers automatically until Feisty.  There's absolutely no reason why this can't be done for things like unrar, too:

"You're trying to open a .rar archive, but this requires *unrar*, which is not installed.  Would you like to download and install this proprietary package?"  (Whereupon 99.99% of users click "yes".)

> Non-free programs in a Free OS contaminate the entire system and make it non-free as a whole.

Aha.  And here we see the actual reason why this hasn't happened yet; pervasive ideological foot-dragging.  People who think that non-free software is "contamination" instead of "something that typical users want on their computer".

---

### Post by RomeReactor on 2007-07-29
I think **asmoore82** meant "contaminate" in the context of the legality of distribution for Ubuntu, not that installing proprietary software represents contamination by itself. Having a single piece of non-free software included in the installation CD would make redistribution legally impossible. However, you're right in that there should be a user-friendly dialog to aid in the installation of proprietary software required by other applications, seeing as we already have that for nVidia drivers and Totem-Gstreamer (it should probably be included in **ubuntu-restricted-extras**). I have no qualms about installing Opera, Real Player, Picasa, or Acrobat. If it works better than a free, native application--or if no free/native alternative exists--I use it.

---

