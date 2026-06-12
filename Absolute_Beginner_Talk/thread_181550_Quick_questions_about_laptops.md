---
title: "Quick questions about laptops"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by kimlatraductrice on 2006-05-24
I am planning to make the switch from Windows to Ubuntu this weekend, but I have some very basic questions first that I was hoping someone could help me with. 

I'd like to install Ubuntu on a 4-yr-old HP laptop. It only has a 20 gb
hard disk. It also has Windows XP Home Edition installed.

1. Is there enough space for Ubuntu to run without any problems?
2. Obviously I won't be dual-booting. Will Ubuntu just erase Windows XP
automatically? (I don't want to keep it, and I don't want it to take up
space for nothing either.

Many thanks in advance!

---

### Post by skippy81 on 2006-05-24
10gb is enough room for a decent linux installation.  With 20gb you could dual boot if you wanted, as long as you have a fairly slim windows installation.   

Assuming you don't want to dual boot, the easiest thing is just to tell ubuntu installer to erase and repartition the whole disk.  Obviously you will want to make backups of your movies, photos, music and documents first.  You can then copy them back on with CDs or memory stick once linux is installed.   

Since your using a laptop I also recommend you try the live CD to make sure your hardware is supported.

Just to clarify, linux uses a different filesystem (EXT3) to windows (NTFS).  For that reason you would have to delete your NTFS partition and all the data in it.   You can't install Linux over Windows as such, you have to delete the partition windows lives on and replace it with an ext2 formatted partiton for linux. The installer will do all of this for you if you want it to.

---

### Post by kimlatraductrice on 2006-05-24
Perfect! Thanks, that's exactly what I wanted to know. 

Thanks again!
Kim

---

### Post by costoa on 2006-05-24
Skippy is right so backup everything you want to keep. BTW, the laptop support (acpi and wireless stuff) on Dapper is IMO much better than before so you might want to give it a spin.

Dapper runs get on my Sharp MC-24 (cheapo depot machine but small).

---

### Post by youthforlinux on 2006-05-24
i have a Dell Inspiron 1000
do u think that ubuntu dapper will support my keyboard shortcuts?

---

### Post by aysiu on 2006-05-24
kimlatraductrice, this link should help you out:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

It explains how to download and burn the Dapper live CD.
You can play around with the live CD for a while--see if you really think it's worth installing.

Then, the instructions go on to tell you how to install it over Windows (it's a lot easier if you don't want to dual-boot).

At this point, eight days away from the official release, it's probably a good idea to use the upcoming Dapper (6.06) release instead of Breezy (5.10).

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/)

You can play with the live CD for a week. Then install it on June 1.

---

### Post by aysiu on 2006-05-24
[QUOTE=youthforlinux]i have a Dell Inspiron 1000
do u think that ubuntu dapper will support my keyboard shortcuts?[/QUOTE] Did Breezy? If Breezy did, Dapper will, too.

---

### Post by joshrobinson on 2006-05-24
[QUOTE=youthforlinux]i have a Dell Inspiron 1000
do u think that ubuntu dapper will support my keyboard shortcuts?[/QUOTE]

i havent had probles with the standard shortcuts, volume, brightness (although i think brightness isnt attached to ubuntu, not sure)

as for other ones im not sure what else you have or use, i never really used the play buttons

---

### Post by youthforlinux on 2006-05-24
[QUOTE=aysiu]Did Breezy? If Breezy did, Dapper will, too.[/QUOTE]

Unlike my other computers, i havent installed ubuntu on it at all
but now i want to install it
should i use the Dapper live CD to check it out?

P.S. will the touchpad work too?

---

### Post by aysiu on 2006-05-24
[QUOTE=youthforlinux]Unlike my other computers, i havent installed ubuntu on it at all
but now i want to install it
should i use the Dapper live CD to check it out?

P.S. will the touchpad work too?[/QUOTE] Use the live CD for at least a week. I'd advise two weeks, actually, before you install Ubuntu. You can never be too cautious.

It pains me to see people rushing into installing Ubuntu and then realizing they have no idea what they're doing. With a live CD, you can familiarize yourself with the interface, how to install programs, and how to manipulate configuration files--all within the safety of a fake session running in your computer's RAM.

Once you reboot, you're back to Windows or your native OS.

The live CD also lets you know things like... whether or not your touchpad will work.

---

### Post by kimlatraductrice on 2006-05-24
Thanks for the helpful responses and the link Aysiu, you've been a great help.

The (small) problem is that I already ordered the Breezy CDs, thinking that I'd better stick with a version that's already been tested etc. Do you really think it's worthwhile installing Dapper? Or are there going to be many bugs? I've never installed Linux before, so I'd like to avoid any possible glitches.

If you strongly feel that Dapper is the way to go, then I'll use that instead, the cds only cost me $5 (I'm in Canada), so it's not the end of the world if I don't use them.

---

### Post by kimlatraductrice on 2006-05-24
Oh, and I'll definitely play around with the live cd first! That seems to be the most logical (and safest) thing to do.

---

### Post by youthforlinux on 2006-05-24
[QUOTE=kimlatraductrice]Thanks for the helpful responses and the link Aysiu, you've been a great help.

The (small) problem is that I already ordered the Breezy CDs, thinking that I'd better stick with a version that's already been tested etc. Do you really think it's worthwhile installing Dapper? Or are there going to be many bugs? I've never installed Linux before, so I'd like to avoid any possible glitches.

If you strongly feel that Dapper is the way to go, then I'll use that instead, the cds only cost me $5 (I'm in Canada), so it's not the end of the world if I don't use them.[/QUOTE]

I thought that the CDs were free?!

---

### Post by aysiu on 2006-05-24
[QUOTE=kimlatraductrice]
The (small) problem is that I already ordered the Breezy CDs, thinking that I'd better stick with a version that's already been tested etc. Do you really think it's worthwhile installing Dapper? Or are there going to be many bugs? I've never installed Linux before, so I'd like to avoid any possible glitches.

If you strongly feel that Dapper is the way to go, then I'll use that instead, the cds only cost me $5 (I'm in Canada), so it's not the end of the world if I don't use them.[/QUOTE] When are the Breezy CDs supposed to arrive? If it's within the next eight days, you can use the Breezy live CD to play around and just get familiar with Ubuntu--see how it works on your hardware, for example.

Do you use your computer every day for serious productivity (in other words, you earn a living off of the programs you'll be using in Ubuntu)? 

If so, I wouldn't install Dapper before June 1 (though, you can certainly use the live CD before that).

If not, install away. It's technically beta, but it's come a long way since a couple of months ago (when it was crashing so often it was almost unusable).

---

### Post by aysiu on 2006-05-24
[QUOTE=youthforlinux]I thought that the CDs were free?![/QUOTE] They are if you want to wait two months for them to arrive. If you pay someone $5 for them, you probably get them more quickly.

---

### Post by youthforlinux on 2006-05-24
how long do u think itll take to get to the US????

---

### Post by aysiu on 2006-05-24
[QUOTE=youthforlinux]how long do u think itll take to get to the US????[/QUOTE] I live in the US. The Hoary CDs took about two months to get to me last year.

---

### Post by youthforlinux on 2006-05-24
did u order breezy cds????

---

### Post by joshrobinson on 2006-05-24
[QUOTE=youthforlinux]did u order breezy cds????[/QUOTE]

my breezy cd's came in just under a month.. my dapper cds claimed to have shipped, but im thinking they just sent me more breezy cd's when i thought i would be getting dapper.. who knows!

---

### Post by aysiu on 2006-05-24
[QUOTE=youthforlinux]did u order breezy cds????[/QUOTE] No, but I haven't heard any murmurings on the forums indicating that Breezy CDs ship more quickly than Hoary ones did.

---

### Post by youthforlinux on 2006-05-24
well i hope the cds come quickly for me

---

### Post by joshrobinson on 2006-05-24
[QUOTE=youthforlinux]well i hope the cds come quickly for me[/QUOTE]

if you have a cdburner i would just download them for now if you need to use them.. dialup or not it will download before they are shipped to you

---

### Post by aysiu on 2006-05-24
[QUOTE=joshrobinson]dialup or not it will download before they are shipped to you[/QUOTE] Downloading an ISO on dial-up would probably take about four days. Waiting for the ShipIt CDs will probably be sixty days.

joshrobinson's right.

---

### Post by youthforlinux on 2006-05-24
ok seems good to me

---

### Post by kimlatraductrice on 2006-05-24
[QUOTE=aysiu]When are the Breezy CDs supposed to arrive? If it's within the next eight days, you can use the Breezy live CD to play around and just get familiar with Ubuntu--see how it works on your hardware, for example.

Do you use your computer every day for serious productivity (in other words, you earn a living off of the programs you'll be using in Ubuntu)? 

If so, I wouldn't install Dapper before June 1 (though, you can certainly use the live CD before that).

If not, install away. It's technically beta, but it's come a long way since a couple of months ago (when it was crashing so often it was almost unusable).[/QUOTE]

The Breezy CDs should arrive today or tomorrow. (I ordered one week ago.)

I do use my desktop computer every day, but not my laptop, which is why I'm planning on using it as a starting point. That's also why I don't mind erasing Windows and doing a complete install. If I like Ubuntu enough (I hope so!), then I plan on dual-booting my desktop (which already has partitions; although I may have to change some of them as I've been reading about FAT32 partitions... anyway, we'll see about that when the time comes.). For now, I'll start by playing around with the live CD. It'll probably be simpler to just use the CD that I have; when I'm ready to install, then I'll download Dapper, if you think it's stable enough.

Thanks again for all your help.

---

### Post by aysiu on 2006-05-24
Dapper's already pretty stable, so I'm pretty confident it'll be stable on June 1.

If you want to be sure, post here on June 1 and ask, "Is Dapper's final release working the way it should, or are there still bugs even though it's been officially released?"

---

### Post by kimlatraductrice on 2006-05-24
Sounds good to me. 
I'm so excited to try it out now, yay!

By the way, your website is awesome. You write really well, and everything is extremely clear and easy to follow.

---

### Post by youthforlinux on 2006-05-24
just wondering, since ubuntu say that a new release will come out every six months, will a new one come out in december????????????

---

### Post by aysiu on 2006-05-24
[QUOTE=kimlatraductrice]
By the way, your website is awesome. You write really well, and everything is extremely clear and easy to follow.[/QUOTE] Thanks. I'm adding more stuff to it as I have time to create the screenshots...

---

### Post by youthforlinux on 2006-05-24
[QUOTE=aysiu]Thanks. I'm adding more stuff to it as I have time to create the screenshots...[/QUOTE]
 wat is ur website??

---

### Post by aysiu on 2006-05-24
[QUOTE=youthforlinux]wat is ur website??[/QUOTE] [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

