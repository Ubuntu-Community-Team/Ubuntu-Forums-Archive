---
title: "Boot Help for iBook G4 PPC 8.04"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by rwATR on 2008-07-10
I've only become familiar with Linux in the past couple of weeks. I ideally I would like to install Hardy on an External Hard Drive (Firewire) because my laptop hard drive is rather small. 

The problem:

I downloaded the ISO for PPC and burned it to a CD at 8x. I booted with OpenFirmware by pressing Apple key, Option, o, and f. At the "ok   0> prompt, I entered boot cd:,\install\yaboot. At which point the screen changes and at the top it reads something to the effect of "Cannot allocate region 0 from device". If it is important to know the exact wording/code I can write it down.

I am not very computer savvy, but would *love* to Linux on my Mac. Thanks for any help!

-Frustrated and Confused-

---

### Post by pxwpxw on 2008-07-10
**rwATR**

" Cannot allocate region 0 from device .... "

That message is ok, not fatal,  I get it on my iBookg4 1GHz,  hardy 8.04 works  well. 

This is probably the fix:

After you boot yaboot from Openfirmware, you should see the yaboot prompt
```

boot:

```

Then press the [tab] key for a list of options,
choose live-nosplash, that skips graphics initially.
```

boot: live-nosplash

```

That should get you a Ubuntu desktop in a minute or so (assuming you are using the Desktop CD). You need to have an ethernet cable network connection for internet access from the the desktop cd if you want to try it out  (recommended)  before installing (but wireless is fine after install). 

You should  also be able to boot the cd just by holding down the option key and selecting the cd icon, slower but easier.

Also make sure you read the PPC Sticky at top of this forum before you install,
some external firewire drives are easier to install than others, you should be able to check this out from the desktop cd before trying the install, you may need a small boot partition on your internal dive.

---

### Post by rwATR on 2008-07-11
I tried that and it tried to load the kernel, then this line appeared:

live-nonsplash:2,/vmlinux: Unable to open file, Invalid device

I typed "check-powerpc" because I think I recall reading on another forum to make sure your CD burned correctly. When I did this I just got a black screen with no activity.

---

### Post by pxwpxw on 2008-07-11
> **rwATR said:**
> I tried that and it tried to load the kernel, then this line appeared:

live-nonsplash:2,/vmlinux: Unable to open file, Invalid device

I typed "check-powerpc" because I think I recall reading on another forum to make sure your CD burned correctly. When I did this I just got a black screen with no activity.

That is a typo, it should be live-nosplash, but you need to be seeing the yaboot message and prompt
```
boot:
```
for it to makie any sense, you shold also be seeing the list of options when you hit the TAB key.

---

### Post by helencollier on 2008-07-12
> **pxwpxw said:**
> That is a typo, it should be live-nosplash, but you need to be seeing the yaboot message and prompt
```
boot:
```
for it to makie any sense, you shold also be seeing the list of options when you hit the TAB key.


Yes I too feel this that see the list option when you hit the TAB key.


[www.slashedpricetag.com](www.slashedpricetag.com)

---

### Post by stream303 on 2008-07-14
Have you just tried booting the install disk by holding down the C-key when powering up?

As for an external firewire, it is pretty simple.  You go through the installation steps to the firewire drive, but upon completion, you'll need to boot your install disk again in rescue or single user mode, and edit your /etc/yaboot.conf file manually.

See this for details:
[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

You may not need the ofboot line, as this thread may be getting a bit old.  It still worked with Hardy 8.04 for me however.

And, thanks to pxwpxw for helping me out numerous times.  I really need to rewrite that thread somehow..

---

### Post by rwATR on 2008-07-16
pxwpxw:

Thanks for the help. It was just a typing error, woops. 

stream: 

I haven't gotten around to using your external HD thread. I'm testing Ubuntu out on a PC, where it was much easier to install. The process looks a little complicated and I want to make sure I'm actually going to use it (I've never used Linux before) before I take the time to do that. 

Again, thank you both for your help.

---

### Post by lukerz8 on 2008-07-16
were did you find a ppc version of ubuntu 8.04? i cant seem to find it anywhere....

---

### Post by stream303 on 2008-07-17
rwATR - no problem, just know that firewire install is possible.  It looks hard, but after you do it once, should be no problem.  Welcome to Linux - keep it fun..

lukerz8 - lots of good stuff in the sticky faq. :)  You can get Ubuntu PPC here:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

