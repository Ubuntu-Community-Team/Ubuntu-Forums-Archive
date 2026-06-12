---
title: "Clean Install Question"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by AcademyKP03 on 2007-10-24
I just installed Ubuntu 7.10 from the Live CD on my desktop.  Then restarted the system as it asked. Then during boot up, the orange loading bar only got to about 1/7th of the way across before it just frooze.  Its been like that for the past 10 minutes.  Any suggestions?

---

### Post by az on 2007-10-24
Hit CTRL-ALT-F1 and see if you can see any error messages.  Try CTRL-ALT-F3, as well.

---

### Post by jenhsun on 2007-10-24
> **AcademyKP03 said:**
> I just installed Ubuntu 7.10 from the Live CD on my desktop.  Then restarted the system as it asked. Then during boot up, the orange loading bar only got to about 1/7th of the way across before it just frooze.  Its been like that for the past 10 minutes.  Any suggestions?

I got this kind of problem before. Did you overclock your pc?
If don't, next time you boot the system, press esc to bring the recover-mode.
And take a look at which steps is freeze.

---

### Post by AcademyKP03 on 2007-10-24
Yeah, good idea .... trying it now ...  couldn't do it from where it previously frooze ... so I restarted system and just as it as loading hit contral/alt/F1 .... right now its been sitting for 2 minutes at LOADING HARDWARE DRIVERS ..... 

okay, now it's been about 3 minutes ....

Any ideas?

---

### Post by AcademyKP03 on 2007-10-24
> **jenhsun said:**
> I got this kind of problem before. Did you overclock your pc?
If don't, next time you boot the system, press esc to bring the recover-mode.
And take a look at which steps is freeze.

No, I don't overclock my computer ..... well, it's frozen right now at "loading hardware drivers...." after I hit control/alt/F1 .....

i'll restart and hit escape during loading and see about going into recover mode ....

---

### Post by AcademyKP03 on 2007-10-24
Here's what I get - when I hit escape and select recover mode:

* Starting kernel event manager    [ OK ]
*Loading Hardware Drivers

[59.711642] hda: dma_timer_exprity:  dma status == 0x21
[69.704258] hda:  DMA timeout error
[69.704318] hda timeout error: status = 0x50 {DriveReady Seek Complete}
[69.704481] ide: failed opcode was: unknown
[89.697487] hda: dma_timer_expiry: dma status = 0x21
[99.690105] hda: DMA timeout error

Next step?

---

### Post by jenhsun on 2007-10-24
> **AcademyKP03 said:**
> Here's what I get - when I hit escape and select recover mode:

* Starting kernel event manager    [ OK ]
*Loading Hardware Drivers

[59.711642] hda: dma_timer_exprity:  dma status == 0x21
[69.704258] hda:  DMA timeout error
[69.704318] hda timeout error: status = 0x50 {DriveReady Seek Complete}
[69.704481] ide: failed opcode was: unknown
[89.697487] hda: dma_timer_expiry: dma status = 0x21
[99.690105] hda: DMA timeout error

Next step?

I am no good at hardware issue. It's looked like you have the hardware problem at the beginning. open your box and take a look at the connection. By the way, check your motherboard manufacture about your bios update (IMPORTANT: very danger, be careful about it.)

STEPS:
1. Motherboard bios-> hardware connection/dust remove ....
2. download ubuntu alternative Desktop ISO, install in text mode. (Don't worried, it as easy as desktop)
3. Report your result here.

---

### Post by az on 2007-10-24
> **AcademyKP03 said:**
> Here's what I get - when I hit escape and select recover mode:

* Starting kernel event manager    [ OK ]
*Loading Hardware Drivers

[59.711642] hda: dma_timer_exprity:  dma status == 0x21
[69.704258] hda:  DMA timeout error
[69.704318] hda timeout error: status = 0x50 {DriveReady Seek Complete}
[69.704481] ide: failed opcode was: unknown
[89.697487] hda: dma_timer_expiry: dma status = 0x21
[99.690105] hda: DMA timeout error

Next step?

Go into your bios (setup at boot time) and see if you can disable DMA for that hard drive.

If there are several options, post them here.

Don't worry about playing around with your BIOS.  You usually can exit without saving if you are unsure...

---

### Post by usererror on 2007-10-24
Weird, unless you've got some special bios settings you could also try restoring them to the defaults.

I'd also try the Alternate CD.  I, for one, prefer the Alternate text based install over the live CDs.  But its my preference, too.  I feel I have less if not any issues when using the text based installers!

---

### Post by AcademyKP03 on 2007-10-24
Well, I tried the text based option just now ... and it froze at detecting hardware ....

I'm going to look at the adjusting the bios option and see what that does ..

---

### Post by usererror on 2007-10-27
That is strange.  Do you have a home built PC?

---

### Post by mdpalow on 2007-10-27
Make sure you disk is clean and scratch free.

Always the last thing one thinks of after hours of issues. My install didn't work once because of a smudged up disk. Had to clean it and it worked great.

unplug / take out any hardware that's not critical and go bare bones just to rule out everything you can.

Good luck,

---

