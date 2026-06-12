---
title: "Trying to get DVD's working.....different problem to all"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by tx1138 on 2006-07-15
Hi everyone. I've tried searching for my problem, and tried some possible solutions, however, when I tried to download the correct codecs, synaptic package manager sees it as installed (I'm assuming a green-coloured box means it's already installed). If so, how come I can't get DVD's to play? I've tried EVERYTHING.

Failing that, can someone please tell me how to watch DVD's in VLC, because I cannot run the dvd, it asks me for the device or something and being a complete noob, I'm in over my head.

Thanks for any help guys, I guess becoming insane is all part of the learning experience right? :mrgreen:

---

### Post by ovimunt on 2006-07-15
Hi,

I'm not sure what you've installed but you might be better off removing the stuff from Synaptic and then doing it in the old fashioned way... at the command line.

In any case, have a look here [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") This should provide you with all the answers.

EDIT: Let me know if you need help with the command line.

---

### Post by Sonic Alpha on 2006-07-15
> **tx1138 said:**
> Failing that, can someone please tell me how to watch DVD's in VLC, because I cannot run the dvd, it asks me for the device or something and being a complete noob, I'm in over my head.

I've actually just figured this out for myself.

It'll take a little work from you, however.

Pop in your DVD, and figure out what the drive is called (this really only applies to having more than one DVD drive).

1.  Open up VLC
2.  Click Settings
3.  click Preferences
4.  Click Input/Codecs
5.  Click General
6.  Scroll down to "DVD Device"
7.  Enter either "/media/cdrom0" or "/media/cdrom" (Without the quotes).

Then when you choose to open a disk, the path should be filled in correctly (you may need to restart VLC).

Oh, I also had to do all the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") stuff, but just take it a step at a time, and it should be fine :)

---

### Post by tx1138 on 2006-07-15
hahah wow I just logged out as a last resort and it appears everything seems to be working fine now :) Thanks for the interest anyway mate, much appreciated :)

---

