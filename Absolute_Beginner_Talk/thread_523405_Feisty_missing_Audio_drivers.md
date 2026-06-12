---
title: "Feisty missing Audio drivers ?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-08-11
I just installed a brand new motherboard, as I was rebuilding a computer, and then I installed Feisty on the new hard drive. But sound doesn't work period.

So, here is the information on the audio for the motherboard, from NewEgg, where i bought the motherboard:
Audio Chipset  -  Realtek ALC861VD / ALC883

So, how would I get the right drivers or whatever to get my audio to work?
By the way, this computer is not hooked up to any sort of internet (wireless, ethernet, modem), so I'll have to transfer anything over to it via USB Flash drive.

Many thanks,
Dr Small

---

### Post by Dr Small on 2007-08-12
I have resolved my problem, so I write unto you, to explain how I fixed it, incase someone else may peradventure the same problem, and also need a remedy.

I found that Feisty was *not* missing any drivers/codecs. I had to access the bios (Basic input / output system) and set my audio to the onboard sound card. Then I booted up in Ubuntu and everything worked.

Dr Small

---

### Post by shakma on 2007-08-15
Dr Small, you da man!  :) This may be the least likely fix ever, but I had exactly the same problem.  I had had a soundblaster installed in this machine, so I guess I turned off onboard audio then.  I took it out to put in another machine, and have been soundless ever since.  Couldn't figure out why ubuntu wasn't detecting it!

Thanks, again!

Peace.
shakma

---

### Post by Dr Small on 2007-08-17
I'm am now glad I replied and left an answer to how I fixed it :D
Cheers!

Dr Small

---

### Post by armandh on 2007-08-17
only the very old and the most unusual or newest are unsupported
otherwise suspect hardware

---

