---
title: "Unusual Graphics issue"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by DaveT on 2007-02-22
Hi

I'm having a problem which would appear to be a very common one only on further investigation has got me completely baffled (still being new to Linux doesn't help naturally, the problem is this:-

I started off with my Sony Vaio VGN-FS115E (intel 915GM Express) by installing Xubuntu 6.10. The install went well apart from my screen resolution, which was 1024 x  768 instead of the standard 1280 x 800 widescreen.

A quick search of these forums found that lots of people has the same problem, the problem being a bad VBIOS, which i then confirmed on my system through the xorg log.

The usual work arround for this appears to be using the 915resolution. Now this is where i get confused. I can alter Xorg.conf as much as i want (manually or automatically) but it has no effect what so ever on my screen resolution. The 'Display Settings' Tab doesn't list any resolutions other than 'Default' almost as tho the laptop is grabbing its resolution settings from somewhere else other than Xorg.conf.

Im using the i810 Driver which other than this annoying problem is operating perfectly.

Has anyone seen this problem before? or could point me in the right direction in finding a solution.

I can post logs but im not sure which ones are needed and tbh i really dont want to spamm my logs all over the first post just incase there is a simple solution that i (being new) dont know yet.

If you got this far then thank you for reading, i tried to explain as best as i can, hopefully someone can make head or tail of my waffle :)

DaveT

---

### Post by ed-j on 2007-02-22
Hi !

As a Novice myself, I can only suggest that you check that you have specified your graphics adapter type and resolution in [COLOR="DarkOrange"]sudo dpkg-reconfigure xserver-xorg[/COLOR] and done a restart. Best I can do. Let me know how you get on!

---

### Post by DaveT on 2007-02-23
Hi Ed

Thanks for the reply.

Unfortunately i've reconfigured Xorg a fair few times originally it listed all the modes i would expect to find (640 480 through to 1280 800), i think my main issue is that none of these settings are(have ever)been available even tho xorg has accepted the driver, 'Display Settings' just seems to ignore the resolutions and lists the 'Default'. Either that or something goes wrong somewhere in between (dont know enough yet to figure that out).

I think i am getting somewhere tho, it appears that the 915GM has two instances (from memory this rings true with M$ OS also).

I know for sure that there is only one driver installed in xorg. could xorg be configuring the wrong one? Im sure there are two 915GM devices because they take up the address PCI 0:2:0 and 0:2:1

I think i am getting somewhere tho, it appears that the 915GM has two instances (from memory this rings true with M$).

While going through xorg reconfiguration i tried to configure 0:2:1 but this killed my Xorg system, is it  possible that im setting the resolutions for the wrong instance? and if so how do i tell xorg that i need to configure the other one?

Thanks

DaveT

---

### Post by ed-j on 2007-02-23
[COLOR="#ff8c00"][/COLOR]Back again1

Ther[COLOR="DarkOrange"][/COLOR]e is some information on PCI  configurations in a file called [COLOR="DarkOrange"]lspci[/COLOR] and another called [COLOR="DarkOrange"]lspci -X[/COLOR]  Best I can do!

---

### Post by DaveT on 2007-02-23
**_lspci output_** (just copied the graphics parts)
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

_**lspci -x output**_ (just the graphics related stuff)
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00: 86 80 90 25 06 01 90 20 03 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 b7 81
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00: 86 80 92 25 07 00 90 00 03 00 00 03 00 00 80 00
10: 00 00 08 b0 01 18 00 00 08 00 00 c0 00 00 04 b0
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 b8 81
30: 00 00 00 00 d0 00 00 00 00 00 00 00 0b 01 00 00

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00: 86 80 92 27 00 00 90 00 03 00 80 03 00 00 80 00
10: 00 00 00 54 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 b8 81
30: 00 00 00 00 d0 00 00 00 00 00 00 00 00 00 00 00

Well thats the output from the 2 commands that you gave me Ed, thanks for replying again.
Ill post my logs hopefully somebody will be able to tell whats going on in my laptop :)

Thanks again

DaveT

---

### Post by ed-j on 2007-02-23
You're welcome! Chow!

---

### Post by r4ik on 2007-02-23
Try,

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution)

Good luck !

---

### Post by DaveT on 2007-02-23
mmm i couldnt manage to post the logs because they were too big, so ive put them in a tar file. i included xorg.conf and xorg.0.log.

there are obvious errors there im just not yet competent enough with the OS to know exactly what they are or what to do about them.

if someone can help me i would be very very very grateful

DaveT

---

### Post by DaveT on 2007-02-23
TY r4ik

i tried following that how too thread, i had already tried most of it already but i hadnt tried mode 30, ive just tried that but my desktop is still default with no resolutions listed in the display settings tab :(

Thanks for trying though.

Dave

ps my logs are attached to my last post if your up for the challenge of helping me figuring it out :)

---

### Post by r4ik on 2007-02-23
I am sorry but i ran out of options.
The only advice i can give now is bump the thread if nobody else jumps in.
Hope you find a solution.

---

### Post by DaveT on 2007-02-23
awe well, it was worth a try.

thanks for trying, 

Hopefully somebody will either know the problem or understand my logs well enough to get me through this, im pretty sure that i could sort this out myself if i had a little more experience with Linux but i dont so atm its kinda like reading a foreign language, you get the general idea of whats happening but not the finer details.

on a brighter note, ill know Xorg inside out by the time ive got this figured:)

DaveT

---

### Post by ed-j on 2007-02-23
> **DaveT said:**
> awe well, it was worth a try.

thanks for trying, 

Hopefully somebody will either know the problem or understand my logs well enough to get me through this, im pretty sure that i could sort this out myself if i had a little more experience with Linux but i dont so atm its kinda like reading a foreign language, you get the general idea of whats happening but not the finer details.

on a brighter note, ill know Xorg inside out by the time ive got this figured:)

DaveT

I could tell you a tale of "87 Total Novice Days" before I managed to poke the dreaded Xorg in the eye. Aye! Between bouts of deep breathing, I used to reinstall from a bootable CD,  very, very..................slowly. And eventually, all the very slowly bits worked?

Q for you: What's a Feisty Fawn Tester? I've heard there's a whole *herd* of people doing it. Can anyone have a go?

---

### Post by DaveT on 2007-02-23
heheh, i think im just coming out of the re install 3 times a day stage :)
" what happens if i do this!...........'#$%£££" puts the Xubuntu CD back in.

Fiesty is the next version that is effectively in development, new features but more chance of bugs. i only really updated because i wanted to see if it would auto solve my screen problem.

I wouldn't consider myself a tester. If i hadn't had the display issues i would still be using Edgy. That said its working fine on this machine so i will stick with it.

needless to say it didn't but its running flawlessly on my machine (with the exception of the screen size).

I have to say tho im really impressed with Xubuntu, ive got one of my Desktop PCs running Sabayon (Gentoo based), i wanted Beryl to work out of the box and couldnt manage it on Dapper (that was my very first Linux install so no doubt the problem was me and not Beryl.
i guess ill be re installing that desktop to xubuntu aswell soon

---

### Post by ed-j on 2007-02-23
> **DaveT said:**
> heheh, i think im just coming out of the re install 3 times a day stage :)
" what happens if i do this!...........'#$%£££" puts the Xubuntu CD back in.

Fiesty is the next version that is effectively in development, new features but more chance of bugs. i only really updated because i wanted to see if it would auto solve my screen problem.

I wouldn't consider myself a tester. If i hadn't had the display issues i would still be using Edgy. That said its working fine on this machine so i will stick with it.

needless to say it didn't but its running flawlessly on my machine (with the exception of the screen size).

I have to say tho im really impressed with Xubuntu, ive got one of my Desktop PCs running Sabayon (Gentoo based), i wanted Beryl to work out of the box and couldnt manage it on Dapper (that was my very first Linux install so no doubt the problem was me and not Beryl.
i guess ill be re installing that desktop to xubuntu aswell soon

Knock me down with-a-fetha! Someone mentioned KDE, I downloaded it with instructions from _[www.psychocats.net/ubuntu/index](www.psychocats.net/ubuntu/index)_ a couple of days ago. Indeed. *Very *impressive. Especially the ease of switching between KDE and Edgy; which helps my learning.

I've got an old 6.4 drive here that's got dapper on. I think it's time for a rasher of Feisty!

---

### Post by DaveT on 2007-02-24
KDE was quite nice looking but it just didnt feel 'right' for me. XFCE on the other hand suits me down to the ground.

---

### Post by DaveT on 2007-02-24
mmmmm

my screen is 1280x800 this morning when i booted up!! now im over the moon :)))))

i guess something i did yesterday fixed the problem but restarting x didnt apply the settings while a restart did... strange

for reference Display Settings now displays 1024 x 768 and Default. Default being 1280 x 800. I only hope it remembers the settings it has atm :)

thanx

DaveT

---

### Post by ed-j on 2007-02-25
> **DaveT said:**
> KDE was quite nice looking but it just didnt feel 'right' for me. XFCE on the other hand suits me down to the ground.

I've got a better idea what you mean now: Gnome, KDE and Xfce. AKA: Ubuntu, Kubuntu and Xubuntu. I'm getting there! =D>

---

