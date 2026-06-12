---
title: "How do I repair a HD?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by OffHand on 2006-04-30
hi
I got errors on my /home directory. Also it says I got 7% something (I forgot the word). How can I try to fix this partition?
The automated check checks it, but doesn't fix it.

---

### Post by NiceGuy on 2006-04-30
Is the word "Non-contiguous"? If it is then that just means its fragmented (think windows). It freaked me out [when I first saw it]("http://ubuntuforums.org/showthread.php?t=72392") but its nothing to worry about.

I'm my case the reason it didn't fix its self straight away was because my HD was nearly full! In fact I did end up filling it up and I started getting error messages about not being able to write logs! The reason it took a while to twig was that if that had happened in windows it wouldn't have booted at all but in ubuntu I didn't realise there was a problem!

In short try checking the amount of free space you have and if its very low, delete some stuff you don't need and try rebooting.

ps. Nice signature - but you spelt linux wrong! (intentionally?)

---

### Post by OffHand on 2006-04-30
[QUOTE=NiceGuy]Is the word "Non-contiguous"? If it is then that just means its fragmented (think windows). It freaked me out [when I first saw it]("http://ubuntuforums.org/showthread.php?t=72392") but its nothing to worry about.

I'm my case the reason it didn't fix its self straight away was because my HD was nearly full! In fact I did end up filling it up and I started getting error messages about not being able to write logs! The reason it took a while to twig was that if that had happened in windows it wouldn't have booted at all but in ubuntu I didn't realise there was a problem!

In short try checking the amount of free space you have and if its very low, delete some stuff you don't need and try rebooting.

ps. Nice signature - but you spelt linux wrong! (intentionally?)[/QUOTE]
yes it was non-contiguous  :) I ended up popping in a live cd and run fsck. It said the volume was clean. So I suppose it's ok now. My hd has about 8.5 GB left out of 30GB so that should be ok. About my sig: I found it on a funny website about hacking. I suppose the writer made it intentionally. It's not the only typo and the article was funny as hell. Thanks for your reply.

---

### Post by patrick295767 on 2006-04-30
I use e2fsck daily, and I would think this can fix mb ur prob, no ??

Greetz

---

