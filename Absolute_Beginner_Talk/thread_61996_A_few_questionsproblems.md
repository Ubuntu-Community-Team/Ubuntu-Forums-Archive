---
title: "A few questions/problems"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by Rasson on 2005-09-02
Hi, I just installed Ubuntu on my asus Z71V laptop ([http://www.istnc.com/store/products.php?cat=90)](http://www.istnc.com/store/products.php?cat=90)), and im having a few problems.  Ive never, ever, worked wtih linux before, but im pretty tired of working with windows, so I decided to make the switch.  Here are some of the things that have gone wrong for me so far...

I got it up and running, but I dont seem to have any sound.  Are there any drivers that I might need to install?  The name "Realtec" rings a bell...

Another problem Im having is with my external hard drive.  Do I need to do something before I plug it in?  When i do plug it in, my gui disappears and im faced with a command line, and its telling me what its doing, but then it just stops and sits there.  Ill refrence exactly what it said and get back to this one....If i restart the computer at that point though, it reads the drive when its booted up agian.

Another problem i'm having is when my hard drive IS recognized, it works VERY slow.  It could take minutes to pull up a folder....

The system itself seems to be sluggish also, when i know it shouldnt be.  Im running a pentium m 770 2.13ghz, 1gig pc4200, nvidia geforce 6600go...

One more quick thing, is there a way to turn off my mousepad when i have my usb mouse plugged in?  I keep brushing by it with my hand while typing...

Thanks guys, and be gentle  :)

---

### Post by poofyhairguy on 2005-09-02
[QUOTE=Rasson]Hi, I just installed Ubuntu on my asus Z71V laptop ([http://www.istnc.com/store/products.php?cat=90)](http://www.istnc.com/store/products.php?cat=90)), and im having a few problems.  Ive never, ever, worked wtih linux before, but im pretty tired of working with windows, so I decided to make the switch.  Here are some of the things that have gone wrong for me so far...

I got it up and running, but I dont seem to have any sound.  Are there any drivers that I might need to install?  The name "Realtec" rings a bell...

Another problem Im having is with my external hard drive.  Do I need to do something before I plug it in?  When i do plug it in, my gui disappears and im faced with a command line, and its telling me what its doing, but then it just stops and sits there.  Ill refrence exactly what it said and get back to this one....If i restart the computer at that point though, it reads the drive when its booted up agian.

Another problem i'm having is when my hard drive IS recognized, it works VERY slow.  It could take minutes to pull up a folder....

The system itself seems to be sluggish also, when i know it shouldnt be.  Im running a pentium m 770 2.13ghz, 1gig pc4200, nvidia geforce 6600go...

One more quick thing, is there a way to turn off my mousepad when i have my usb mouse plugged in?  I keep brushing by it with my hand while typing...

Thanks guys, and be gentle  :)[/QUOTE]


Are you using Hoary?

You need to install that Nvidia card to speed things up:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

And install prelink:

[http://www.ubuntuforums.org/showthread.php?t=1971](http://www.ubuntuforums.org/showthread.php?t=1971)

---

### Post by Rasson on 2005-09-03
Thanks for your quick response!  Im doing that now.

---

### Post by Rasson on 2005-09-03
Im having troble installing prelink.  How do I log in as root so i have the nessessary permissions to edit the sources.list file?

Thanks agian!

---

### Post by aysiu on 2005-09-03
[QUOTE=Rasson]Im having troble installing prelink.  How do I log in as root so i have the nessessary permissions to edit the sources.list file?

Thanks agian![/QUOTE] There's no root. Just type

*sudo gedit /etc/apt/sources.list*

---

### Post by Rasson on 2005-09-03
Besides this, can you help me with my sound and external hard drive problems?

Thanks agian.

---

### Post by aysiu on 2005-09-03
[QUOTE=Rasson]Besides this, can you help me with my sound and external hard drive problems?

Thanks agian.[/QUOTE] Doubtful, since I didn't have sound or external hard drive problems with my Ubuntu install. I did have screen resolution problems, so I'm pretty good at fixing that!

What I generally find helpful is searching on Google for stuff and just prefacing the search with *site:ubuntuforums*. For example, [this is the search I'd do for sound problems.](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+sound&btnG=Google+Search)

---

### Post by Rasson on 2005-09-03
Alrighty, ill look around.  Heres the exact error i get when i plug in my hard drive, btw.

sda: asssuming drive cache: writing

FAT: utf8 is not a recomended IO charset for FAT filesystems, filesystem will be case sensitive!


It then proceeds to lock up untill i reboot.

---

### Post by poofyhairguy on 2005-09-03
[QUOTE=Rasson]Besides this, can you help me with my sound and external hard drive problems?

Thanks agian.[/QUOTE]

This:

[http://resonance.org/~josh/laptop.html](http://resonance.org/~josh/laptop.html)

Says to use alsa.

Do that this way:

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by aysiu on 2005-09-03
[QUOTE=Rasson]Alrighty, ill look around.  Heres the exact error i get when i plug in my hard drive, btw.

sda: asssuming drive cache: writing[/quote] Oh, that reminds me. Another good way to Google stuff is to search for the exact error. For example, [this search](http://www.google.com/search?num=100&hl=en&safe=off&lr=lang_en&q=sda:+assuming+drive+cache:+writing&spell=1) may help you out for that error.

> 
FAT: utf8 is not a recomended IO charset for FAT filesystems, filesystem will be case sensitive! And this isn't an error--it's a warning. I get that warning every time I boot up as well.

> 
It then proceeds to lock up untill i reboot. That's an error. Don't know why it's there.

---

