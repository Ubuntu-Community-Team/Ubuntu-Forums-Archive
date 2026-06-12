---
title: "ReFind boot loader: How to choose default OS?"
date: 2016-01-16
forum: Apple Hardware Users
---

### Post by wessenu on 2016-01-16
Hello there! I installed Ubuntu as a dual boot system on my MacBook Air with the refind boot loader to try out Linux for fun for the first time. Everything's fine and nice, but as my printer doesn't work properly I want to change back to OS X. And here´s my problem: How can i change the default OS to boot? 
On the first startup refind let me choose if I wanted to boot to Ubuntu or OS X. Now it just boots Ubuntu. I guess it is just a key to hold during the startup, but a google search and a forum search didn´t tell me which one...
So maybe someone can help me out?

---

### Post by este.el.paz on 2016-01-16
> **wessenu said:**
> Hello there! I installed Ubuntu as a dual boot system on my MacBook Air with the refind boot loader to try out Linux for fun for the first time. Everything's fine and nice, but as my printer doesn't work properly I want to change back to OS X. And here´s my problem: How can i change the default OS to boot? 
On the first startup refind let me choose if I wanted to boot to Ubuntu or OS X. Now it just boots Ubuntu. I guess it is just a key to hold during the startup, but a google search and a forum search didn´t tell me which one...
So maybe someone can help me out?

@wes:

rEFInd seems to "remember" your last choice, and offer that as default.  Try booting with the option key held . . . that should take you to the OSX boot loader . . . and then pick OSX . . . .  I have a triple boot set up, so the default is OSX1 . . . but lately I'm running OSX2, so if I want that on cold boot, I hold the option key, goes to OSX boot loader, I select OSX2, since I have rEFInd installed on OSX2, then rEFInd opens . . . which has "remembered" my last selection (OSX2) . . . and it loads OSX2 . . . .

You possibly could read the rodbooks wiki on rEFInd . . . and how to "set" the default . . . but, I think it will "figure it out."

Also, you could try to get the printer issue figured out; I do see people posting on the lubuntu-user list serve asking questions about getting printing going . . . I don't do much printing these days . . . but, it does seem to happen in the linux-world . . . ???
e
...

---

