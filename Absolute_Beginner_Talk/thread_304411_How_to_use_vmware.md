---
title: "How to use vmware?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-11-21
Hello recently ive got in touch with vmware and i think its nice but how do i install freeBSD using an .iso file ive downloaded on my desktop to install it on vmware and use it?:-k I explain .. ive got freebsd 6.1 on .iso downloaded how do i install it on vmware so i can have my ubuntu dapper drake installation on my hdd and freeBSD in vmware?

---

### Post by LLRNR on 2006-11-21
Well it sounds to me as you'd actually need to burn the .iso to a blank CD, since through VMware you create another virtual machine which runs within your Ubuntu system (also taking up resources etc). And then you'd just need to "feed" your virtual machine the freshly burned CD, make it boot from the CD first (it should come with a generic BIOS too) and... install FreeBSD. (At least that's how I used to do in Virtual PC, I still haven't got the time to play with VMware).

EDIT: [This](http://ubuntuforums.org/showthread.php?t=183209) sounds like a good HowTo for setting up VMware (just skip the XP part).

---

### Post by haxer on 2006-11-21
But how do i install it on vmware after ive burned the .iso file to cd? Can i boot the cd inside vmware?

---

### Post by LLRNR on 2006-11-21
[quote="haxer"]But how do i install it on vmware after ive burned the .iso file to cd? Can i boot the cd inside vmware?[/quote]

When you set up your virtual machine, you get a list of parameters to choose from (for example the RAM you assign is actually taken out of your own RAM), and you will also assign your existing CD-ROM drive to the virtual machine, because you'll certainly need it for booting from the CD.

Anyway as I told you I haven't done this in VMware but in Virtual PC, but it should be the same, as they're both virtualization programs. You should check out the link to that HowTo, it should answer many of your questions.

Cheers! 

LLRNR

---

### Post by haxer on 2006-11-21
Ok thanks for that :-k

---

### Post by LLRNR on 2006-11-21
My pleasure!

I really want to start using VMware myself (when I'll finally get the time to deeply dwell into it), to make up an XP machine and FINALLY start SINGLE booting Ubuntu :KS (work stuff => XP apps, you know... and Wine just can't help enough)

Good luck!

---

### Post by haxer on 2006-11-21
But this apps you used .. virtual pc is it for linux to? If thats the case it is bether or worse? Im trying to find an easy way to use 2 os`s in my ubuntu box i want to try freeBSD and slackware i think im trying to switch i think ubuntu is really nice good apps and nice graphic but i want to try out some more "difficult" versions of linux and unix. Whats good for that ive looked at some live cd's but i think it laged really much ive tried out anonym os and thats an base of FreeBSD just like ubuntu usig an base of debian if im not totally wrong on it? And if you know any good guides of virtual pc or vmware:)

---

### Post by LLRNR on 2006-11-21
Well, besides the EDIT in my first post (for a good HowTo on these forums for VMware) I don't know others, but I'm sure they're just lurking around, since many folks use VMware very much these days (or so I heard).

The Virtual PC I used... oups... it's actually "Micro$oft Virtual PC 2004" so I don't think it has a Linux equivalent ;) I needed it to create a controlled environment in order to study some anomalies such as viruses... oh well that passed and now I'm really anxious about trying VMware myself, since I want to run XP only for work stuff and within my Ubuntu system.

Yes, it's a good thing, IMO, to install the LiveCDs for the distros you want to try, since you'll get a real feel of them only by installing. For such purposes (and many others) virtual machines are a great relief. (FreeBSD for as far as I know is the free version of UNIX... right?! I hope I'm not telling non-sense. And since Ubuntu IS Debian-based, I'll surely give it a shot someday, too.)

Yeah, I've been carefully advised to try Gentoo, Slackware and Linux From Scratch if I want some REALLY difficult distros. :D I'll wait some more... I'm still a newbie in Tux's world.

Best regards,

LLRNR

---

### Post by haxer on 2006-11-21
ok thanks 8)

---

### Post by ginkhao on 2006-11-21
You won't need to burn a CD to  get FreeBSD running in VMware - once you have VMware installed you make a new virtual machine, then set the virtual machines' CD-ROM to use the iso file you downloaded, turn the machine on and it will automatically boot from the CD and go from there.  

It really it quite easy to use, I recommend you give it a try.

---

### Post by LLRNR on 2006-11-21
> **ginkhao said:**
> You won't need to burn a CD to  get FreeBSD running in VMware - once you have VMware installed you make a new virtual machine, then set the virtual machines' CD-ROM to use the iso file you downloaded, turn the machine on and it will automatically boot from the CD and go from there.

...And yet another reason to NEVER use M$ products ever again !! (Virtual PC doesn't allow treating an .iso as an already written CD, dammit!)

---

