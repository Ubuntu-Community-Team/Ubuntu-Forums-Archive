---
title: "Totally newbie looking for assistance."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Badmagic on 2006-08-25
I have been reading ream after ream of help posts and linked documentation for a few hours now but so far everything I have read is using terminology that frankly is beyond me, I used DOS then different versions of widows from 3.1 jumping to ME then the different versions of XP so I really need information in plain English.

I downloaded and burned the ISO for ubuntu (AMD64) I am using an fx-53, when I try to boot from CD I get an initial screen that prompts items such as ‘Install, check disc for errors etc’, on using the install or run from cd option it shows a form of boot up sequence where its loading up the drivers etc, after a couple of minutes the screen goes black, I hear whats apparently a ‘Welcome to ubuntu’ sound file play but my monitor never re-activates, it behaving like it does not exist.

Any tips (in very plain English) on how to get it functioning would be very welcome, I am presuming I need to install a compatible 64 bit video card driver for ubuntu to use but the only information I could find on this was talking in code and obviously not for a beginner.

The components that are concerned are as follows:

Video Card:  ATI X800 Pro
Monitor:  Viewsonic VX910

I should probably also mention I have two partitions on the HDD, one at 90 GB for XP Home (fresh install with all updates and monitor/video/sound drivers nothing else yet) and one at 23 GB which is empty at the moment for trying out ubuntu.

As I say, I would be happy to help myself if I could even follow the conversation posted on some of the ‘Install Help’ threads.

Thanks in advance for your time.

---

### Post by benfindlay on 2006-08-25
I've had that exact problem in the past; it turned out to be the resolution and refresh rate on my monitor. If you plug another monitor in it may well work ok (I'm assuming you or someone you know has a spare/can lend one to you for a few minutes), then you can sort out getting your to work in teh display settings under SYSTEM>>ADMIN>>SCREEN RESOLUTION

---

### Post by gn2 on 2006-08-25
As a fellow noob, I sympathise with your plight.

Two things that will ease your Ubuntu woes:

1: If using 64-bit Ubuntu put it away for later, and use 32-bit for now.

2: If you have an Nvidia card plug it in now.

ATI drivers are a nightmare, best to use Nvidia hardware.

---

### Post by Bachstelze on 2006-08-25
Hi Badmagic and welcome on board :)

I recommend using the text-based installer on the alternate CD instead of the dektop one. Anyway, after the "Welcome" sound, does Ctrl+Alt+F2 get you a command line prompt ?

---

### Post by Badmagic on 2006-08-25
Thanks for the responce everyone.

> **HymnToLife said:**
> Hi Badmagic and welcome on board :)

I recommend using the text-based installer on the alternate CD instead of the dektop one. Anyway, after the "Welcome" sound, does Ctrl+Alt+F2 get you a command line prompt ?

Hi HymnToLife, just a quick question, I had to wait a week to get a cd burner so I downloaded two files, the first was the basic amd 64 version I have been trying but I also downloaded the other one with the filename:

"ubuntu-6.06.1-alternate-amd64.iso"

Is this the one you are refering too?  I need to get some sleep but I will burn this to a cd tomorrow and test the Ctrl+Alt+F2 thing.

Thanks again.

---

### Post by Bachstelze on 2006-08-25
Yep, that's the one. It has a text-based installer, so it's less pretty but also less likely to die on you. In your case, I don't think it will make much difference though. 

If Ctrl+Alt+F2 gets you to a commant prompt, log into the system and look in your xorg logs if there are some errors (lines starting with EE). To see the log, run the command

```
nano /var/log/Xorg.0.log
```

---

