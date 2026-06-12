---
title: "The last few steps"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by qebab on 2007-03-06
At the time I'm writing this, I'm (hopefully) only a few hours away from booting up ubuntu. However, being the absent-minded person I am (frequently searching for things that I carry in my pockets and such), I'm sure that I have forgotten some things, not prepared well enough and that this whole thing will blow up in my face.

If you're not interested in reading my story, jump down a few paragraphs, I'll make a list of what worries me, remedies I have thought of, and things like that.

The story starts wednesday last week. A friend of mine has been contemplating going over to ubuntu for a while. On wednesday, he finally managed to convince me to join him, and yesterday we agreed to "see each other on the other side". Whether both of us will show up has yet to be shown. Thursday morning, I brought a couple of Ubuntu Live CDs that I had burned to the university, and we decided to test it over the course of the weekend and make our decision on monday. I was well prepared to tell him that it was a no-go, after all, linux is not user-friendly, it has limited software and whatnot! (That's what I thought. So much for stereotypes.) On sunday when I went back to xp for a while, I actually found myself missing Ubuntu a bit. I mean, I've grown out of computer games - I hardly use anything that is present only on windows and not on linux, and even if I did, there's still Wine, so it's possible to use it.

So we discussed it yesterday, he had the same experiences as I do, and we're both going to change. However I'm a bit nervous of nature, so I don't want to cross over completely, I want the option to boot up XP if I want to. I need a dualboot, and I want to keep the hidden partition with the system recovery tools on my pc. I consulted another friend who studies computer science and use Ubuntu and asked if this could cause any problems.
He asked me if I had checked how well Ubuntu supported my laptop. And well, the only things it doesn't support are things that I would never know how to use (A camera? Fingerprint stuff? Do I even have those things?. I said it looked fine, and he grew thoughtful for a while, before blurting out with this: "You do know that Grub overwrites the MBR, right?"

My reaction was surprise and astonishment! And the phrase "What the hell is a MBR and why does the Grub dislike it?" I'm pretty sure I caused some laughter right there. So I got a basic explanation, basically, unless I found a way to bypass this, I would be unable to boot the system recovery tools. Which doesn't leave me any way of going back if this blows up in my face. He couldn't tell me how to do this, so he said "Forums, google, search for it." And I did. 

And here comes the gem. I found *nothing* the first *3* hours. And then I hit the jackpot and located everything I needed in a timespan of five minutes. I have forgotten how this came to pass, but I still have the links, so I should be alright.

[This is my computer. From the little I understand of that page (Mind you, I know nothing about hardware), there doesn't seem to be any problems that would be very hard to solve?](http://www.thinkwiki.org/wiki/Category:Z61t)

[This is the "Rescue and Recovery" partition that I want to keep, and presumably how to achieve that.](http://www.thinkwiki.org/wiki/Rescue_and_Recovery)

[This is a relevant blog entry for someone who has done something similar with SUSE.](http://sharadware.com/2005/07/11/suse-linux-winxp-access-ibm-on-the-thinkpad-t43/)

[This is err... The official Lenovo support which is also relevant.](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-46088)
On the same page I found an image that will recover the MBR to factory defaults, allowing me to access the system tools on the hidden partition if I want to reset the entire laptop to factory defaults.

Other preparations I have made:
Backups, doing that as I'm writing this. 
CD Integrity Check.
[Reading this.](https://help.ubuntu.com/community/WindowsDualBoot)
[And this.](https://help.ubuntu.com/community/MigratingFromWindows)

I have considered what software I need, so over the course of the aforementioned weekend, I've spent some moments thinking about what exactly I use.
When I'm using my laptop, the following programs are likely to be used:
Winamp, utorrent, IDLE (Shell/Code editor), mIRC, Firefox, thunderbird, some word processor, pdf-document handler of some kind, and... that's it, I think. From what I've understood, running that kind of apps should be cause no problems for me in linux, and it didn't when I used the Live CD. 

What I am most worried about:
This whole installing thing will blow up in my face and my computer will explode! (Well, I know it won't explode...) - Remedy: that CD to fix the MBR and let me access the hidden partition, reset to factory defaults.
All my stored data will be lost! - Remedy: Backups are being taken.
I might have an important program that won't run in linux! - Remedy dualboot/wine.
I lose my hidden partition! - Remedy: I'm going to kill myself.
Some hardware isn't supported! - Remedy: Important hardware, try to locate drivers, non-important hardware, ignore it.

And that's really all that I can think of. But now I'm back at me being absentminded.
What I want you to help me with is; Help me found out what I have forgotten to do/check, warn me of things that could go wrong while I'm doing the process I've described, give me a few pointers to start out with. 

Any help is greatly appreciated, and with a bit of hard work and luck I'll be finished by tonight. :)

---

### Post by lyceum on 2007-03-06
First off, welcome aboard. Ubuntu is very user friendly and you should be okay. The best advice, don't panic :)

It sounds like you are doing everything right, and have firgured most things out. You should know that wine does not run every MS based program. You may want to look [here](http://www.codeweavers.com/compatibility/browse/rank/) for the list of programs [crossover linux](http://www.codeweavers.com/products/cxoffice/) offers, it is wine based with a nice gui. You do not have to buy it, as there is wine, but it does make things easier.

Also, my signature (below) has some good websites with new-to-Ubuntu info in the first line. I recomend psycocat's page if you look at nothing else. It also sounds like you may want to check out the "install anything" page too.

Good luck, and feel free to ask questions !

:)

---

### Post by buuntuu! on 2007-03-06
i think you covered it all
i've got a thinkpad myself and am absolutely happy with lenovo's hardware support. seems they built their boxes especiallyfor ubuntu :) (tried ark-linux but that was a no-go)
i even took the penultimate step and killed the hidden partition after burning the backup cds, five gig simply seemed too much space to waste. (don't  worry, the partition is safe, it will not be touched by the installation if you don't decide to do so) 
i still dual-boot, but just because i am too lazy to kick window$ off my drive, there was no need whatsoever to boot it since i got ubuntu, and essentially i'm doing the same stuff you are planning to do.
so, if you've made your backups do not fear!
have fun in the linux-world!

---

### Post by qebab on 2007-03-06
Ohh, that's simply beautiful. :)

Only a couple of more things to check before kickoff now. I've burnt out about 7 DVDs now, so I nearly hope it crashes, all this effort just to be on the safe side. 

So there's not really anything else I need to know?

---

### Post by lyceum on 2007-03-06
I am sure there is lots more for you to know, but you really won't need to know it until you have the question :)

As far as needing to know, your hard ware worked with the live disk (I am guessing your wifi worked as well)

There are gobs of programs to chose from in add/remove, and I have you a link you the MS programs you can still use with wine ot crossover.

MP3's will not work out of the box and neither will playing movies on comercial DVD's, but [Easy Ubuntu](http://easyubuntu.freecontrib.org/) or [Automatix](http://www.getautomatix.com/) can fix that if you want the easy way out.

:-k can't think of anything else off hand. Again, you may want to read psycocat's ubuntu info, you coould do that while you are burning your DVD's to see if there is anything else....

---

### Post by qebab on 2007-03-06
Yeah I am reading it right now. Waiting for a computer to finish writing DVDs, just to start writing another isn't really very exciting, but reading that page is. Thanks again!

I already visited Automatix, and will probably get it once I'm done. It might sound childish, but I'm getting excited about this now, and only a couple of hours until it's done. I also figured out that I need an external hdd, this is the last time I back up an entire drive to DVDs. :(

---

### Post by jhenager on 2007-03-06
The external HDs are so cheap now, they make a lot of sense.

---

### Post by lyceum on 2007-03-06
> **qebab said:**
> Yeah I am reading it right now. Waiting for a computer to finish writing DVDs, just to start writing another isn't really very exciting, but reading that page is. Thanks again!

I already visited Automatix, and will probably get it once I'm done. It might sound childish, but I'm getting excited about this now, and only a couple of hours until it's done. I also figured out that I need an external hdd, this is the last time I back up an entire drive to DVDs. :(

I felt the same way, and still do every time a new releace come out, I guess we never grow up :)

---

### Post by yanqui on 2007-03-06
Wow--for someone who is "absentminded" and "knows nothing" about hardware, you seem to have taken care of business before you got started. YOu're the sort of person I'd want to do business with.

---

### Post by qebab on 2007-03-06
> **yanqui said:**
> Wow--for someone who is "absentminded" and "knows nothing" about hardware, you seem to have taken care of business before you got started. YOu're the sort of person I'd want to do business with.

I know nothing about hardware, but that doesn't mean I don't know anything about software. I'm a hobby programmer, and one of the things I've learnt from programming is that thinking through things beforehand, and planning is very important when dealing with software in general. It's always done me good. I'm absentminded, so I have to write lists and such for all these things though, I never remember it unless I don't. :P

---

### Post by qebab on 2007-03-06
Just thought I'd say that I got it working easily, and have been playing with Ubuntu for a few hours now. :)

---

### Post by lyceum on 2007-03-07
> **qebab said:**
> Just thought I'd say that I got it working easily, and have been playing with Ubuntu for a few hours now. :)

:guitar:

---

