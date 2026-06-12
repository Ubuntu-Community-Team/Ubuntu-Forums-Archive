---
title: "My options?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by kristalsoldier on 2007-02-23
Hi...

I have been test running Dapper and Edgy off their respective live cds.

I have a relatively new Sony vaio VGN FE-28B laptop running xp, which I want to configure in a dual boot mode.

Here is the problem. As my posts indicate...in Dapper the wireless works, the printer - for some reason does not. Additionally, power management in Dapper - as far as i can tell - is absent. I read some posts and thought the printer did not work because I was running the live cd. But...

In Edgy, the printer works (bam! like that! and that too off the live cd!), power management works! But wireless does not! :( 

I have one laptop (wife has appropriated the 2nd!). Internet access - for a variety of reasons has to be wireless in the house and at work. I write...so I need to print! So, printer MUST also work!

From what I gather, Edgy does not recognize the wireless on my machine. There are patches etc. that I can probably configure (with a lot of help from you folks) to get the wireless working in Edgy. But this will mean that I need to be on the net to download the relevant drivers etc (I hope I am right in this).

One confession - for some unknown reason, I seem to have an implicit confidence in Edgy - I have no reason to be confident - I know NOTHING about linux - edgy, dapper or otherwise!

So, where does that leave me? I am guessing I can download the driver(s) onto an external USB drive and then run Edgy and upload from the external? Does this work?

What I don't understand is - if the wireless is recognized in Dapper, why will the same device not be recognized in Edgy? :confused: 

Or, am I left with the option of looking at some other distro?

If you have a moment, please share your insight and experience with me.

Thanks in advance.

---

### Post by tgalati4 on 2007-02-23
I would start with Dapper.  It's stable and it will receive bug fixes and updates for the next three years.  HP printers are well supported in Ubuntu.  Wireless driver architecture changed from Dapper to Edgy.  Power management is turned off by default in Dapper.  Go into the menu and turn it on.

Search Sony Viao in the forums to see what problems folks are having and proposed work-arounds.

If you have a second machine for experimenting put Edgy or Feisty on that machine.

Better yet, buy a large notebook drive, partition it smartly, and put all three distro's on there.  After 6 months, delete the distros that you don't want and use the partitions for media and personal data storage.

Don't do what most noobs do.  Start with Feisty.  Crash and burn.  Always some critical function that is not working.  Then try Edgy.  Play with the eye-candy and neat desktop features.  Still broken or annoying stuff.
Wipe it and install Dapper.  After all you still got to surf the net and check email.

We need you in the fight.  Come join us.  Viva La 'Buntu!

---

### Post by kristalsoldier on 2007-02-23
Thanks! Will do! And, will keep reading and updating!

Again, thanks!

---

### Post by MetalMusicAddict on 2007-02-23
I would _NOT_ go with Dapper. It will get bug fixes and security updates yes but not fixes that make things work better from one release to the next.

---

### Post by tgalati4 on 2007-02-24
You're right!  With a new Sony Vaio, Edgy would run fine.  However the Vaio's quirks may be better handled in Dapper.  Install both and test.

---

### Post by kristalsoldier on 2007-02-24
> **tgalati4 said:**
> You're right!  With a new Sony Vaio, Edgy would run fine.  However the Vaio's quirks may be better handled in Dapper.  Install both and test.

Probably because I am a novice, Dapper seems more friendly', simply because Edgy refuses to recognize my wireless - compounded by the fact that at the moment, I am running both off the Live CD. Installation program is set for Sunday (tomorrow:) )

---

### Post by igknighted on 2007-02-24
> **kristalsoldier said:**
> Probably because I am a novice, Dapper seems more friendly', simply because Edgy refuses to recognize my wireless - compounded by the fact that at the moment, I am running both off the Live CD. Installation program is set for Sunday (tomorrow:) )

The thing is, of all the things you mention, wireless is the easiest to configure if it doesn't work.  Plus, Edgy boots faster, has a lot more room for upward mobility as you get more comfortable, and allows you to upgrade to fiesty should you choose when it goes stable (end of April), which could in the end solve all your issues.  I don't think you will ever get the power management solved.  Wireless, while it might be tedious depending on your hardware, is very doable.  The printer could probably be made to work with either, but not knowing anything else about it I don't know for sure.

What type of wireless chip do you have?  We can point you to a how to you could look at before you make up your mind.

---

### Post by kristalsoldier on 2007-02-24
> **igknighted said:**
> The thing is, of all the things you mention, wireless is the easiest to configure if it doesn't work.  Plus, Edgy boots faster, has a lot more room for upward mobility as you get more comfortable, and allows you to upgrade to fiesty should you choose when it goes stable (end of April), which could in the end solve all your issues.  I don't think you will ever get the power management solved.  Wireless, while it might be tedious depending on your hardware, is very doable.  The printer could probably be made to work with either, but not knowing anything else about it I don't know for sure.

What type of wireless chip do you have?  We can point you to a how to you could look at before you make up your mind.

Hardware profile indicates the foll:
Intel Pro 3945 ABG Network Wireless

My machine is:
Sony Vaio VGN FE-28B (Core Duo)
100GB HDD
IGB RAM

Printer Epson Stylus DX3850

---

### Post by igknighted on 2007-02-24
> **kristalsoldier said:**
> Hardware profile indicates the foll:
Intel Pro 3945 ABG Network Wireless

My machine is:
Sony Vaio VGN FE-28B (Core Duo)
100GB HDD
IGB RAM

The recommendations I see for that chip say to use ndiswrapper.  If you follow the tutorials it is very easy to use ndiswrapper, but it can be tedious.

---

### Post by kristalsoldier on 2007-02-24
Yes, I read that too and its taking me time (and courage) to work this. If I mess up my machine (in any way) my work is seriously compromised! But, yes, I will keep plodding away. Thanks for your help.

---

### Post by kristalsoldier on 2007-02-24
I managed, without any major disasters to install Edgy onto my machine. Somehow the wireless issue also seemed to resolve itself. Thanks to all who helped and encouraged! I would also like to acknowledge the help a particular friend who also materially assisted.

Again, thanks!

---

