---
title: "I want to make the switch, but..."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by tommyhat on 2008-01-06
I've tried making the ubuntu switch a few times now and it never sticks. It's been a few months and now Feisty is out and my interest is back again.

I'm now faced with the task of backing up, getting ready, setting aside the time and all that. Everytime i switch over, I come crawling back to windows because it will play my games. My wide array of consoles isn't enough there's still some games I just can't live without (Civ 4, portal, oblivion mainly.)

Someone please tell me there is a way for me to have my cake (ubuntu) and play games too!

---

### Post by kellemes on 2008-01-06
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by Joeb454 on 2008-01-06
You could always try dual booting with Windows.

[Check Here]("http://www.psychocats.net/ubuntu/installing") for more details on that :)

---

### Post by tommyhat on 2008-01-06
I did this before and it was good except:

1. The boot loader ubuntu had wouldnt let me switch the default and would load windows unless i was there to tell it otherwise. Eventually I stopped caring

2. I split an 80g drive between windows and ubuntu and the games on windows suffered due to the small OS partition.

---

### Post by Joeb454 on 2008-01-06
Ok I see your point about the drive sizes...but if you're just using Ubuntu for your every day stuff...and if you use 7.10, which has built in NTFS read/write support, you could just have the Ubuntu partition size at 15-20Gb, and the rest Windows.

And to edit the bootloader, you have to run ```
gksu gedit /boot/grub/menu.lst
```

and put in your password, to edit it with privileges :)

---

### Post by tommyhat on 2008-01-06
Whoa, thanks! Very helpful

My 'everyday' would probably just be coding with music/videos. is that too much to run on 20g?

---

### Post by PeterJS on 2008-01-06
One of the options in the grub config option that joeb mentioned is which entry is the default.

As to disk size I started off with a 10 gig linux partition on a 60gig drive. Back when ntfs write support was lacking (I feel like a crotchety old man, now get off my lawn). You can get away with a pretty small linux partition these days, 10 gigs would be ample, and just push all your data storage off on the ntfs parition.

---

### Post by Joeb454 on 2008-01-06
Not really, depends how much music and video's you have :) When you've installed Ubuntu post back here and I'll help you change the bootloader if you like. And for what it's worth, the bootloader is called GRUB

---

### Post by Joeb454 on 2008-01-06
PeterJS, I've done that with my music...because I need to dual boot with Windows for Uni software, I manage my iPod with iTunes, so just pointed Rythmbox to load the iTunes Music folder and check for new files :) Saved me having the same 8gb of music twice :D

*Sorry for hi-jacking the thread :)*

---

