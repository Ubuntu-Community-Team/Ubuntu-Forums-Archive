---
title: "Dual Boot Issue"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Biscuitpie on 2007-04-06
I'm having trouble with Windows, but Linux is working great. I have a thread here: [http://ubuntuforums.org/showthread.php?t=402150&highlight=Installation+trouble](http://ubuntuforums.org/showthread.php?t=402150&highlight=Installation+trouble) that had a ton of issues of mine and I've got most of them worked out. If you follow through it I think on the last page is my problem and what louieb asked me to do, but he is at work, so he cannot help me. I made a new thread as a 5 page post will probably not attract as much attention. =/

---

### Post by Biscuitpie on 2007-04-06
I also have another question. Is there a way for me to use my Logitech G15 keyboard's macro keys with Linux?

---

### Post by Biscuitpie on 2007-04-06
:(

---

### Post by confused57 on 2007-04-06
I glanced over page 5 in your thread & noticed you don't have an entry to boot Windows in your menu.lst...see the 3rd link in my signature for how to edit your /boot/grub/menu.lst.
Also, there's an example entry in your menu.lst that should boot your Windows install if it's on the first partition...just add it to the bottom of your menu.lst

louieb will definitely be able to help you, but you might want to try this until he gets back.

Added:  If Windows is on your 2nd hard drive, see the entry in the link I gave you.

---

### Post by Biscuitpie on 2007-04-06
> **confused57 said:**
> I glanced over page 5 in your thread & noticed you don't have an entry to boot Windows in your menu.lst...see the 3rd link in my signature for how to edit your /boot/grub/menu.lst.
Also, there's an example entry in your menu.lst that should boot your Windows install if it's on the first partition...just add it to the bottom of your menu.lst

louieb will definitely be able to help you, but you might want to try this until he gets back.

Added:  If Windows is on your 2nd hard drive, see the entry in the link I gave you.

Sorry if I was confusing, but I can't even install windows. IE, it loads all of it's crap for a few minutes then says Starting Windows... and never ends. Same disc worked on my dad's laptop. So... I know something is wrong.

---

### Post by confused57 on 2007-04-06
I misunderstood & thought you already had Windows installed on sda1 & was just trying to get it to boot...I've installed Linux countless times, but I've installed Windows only one time.  Might possibly be a problem with your cd drive correctly reading your Window's disc or maybe you could try disconnecting the other hard drive that you're not going to install Windows on...

You probably should wait on louieb, he should be able to get you up & running.

---

### Post by Biscuitpie on 2007-04-06
I've tried it without my external. =/ It's not going to have Windows on it, it's just my music and T.V. shows/movies.

But thanks for trying. :D

---

### Post by Biscuitpie on 2007-04-06
Well, he says everything looks fine. But it's not working that way. :( Really frustrated.

---

