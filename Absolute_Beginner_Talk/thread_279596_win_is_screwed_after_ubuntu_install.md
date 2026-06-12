---
title: "win is screwed after ubuntu install"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by bobbydigital on 2006-10-18
I just installed ubuntu today on a spare IDE drive I had kicking around while keeping my win xp on its sata drive by itself. Anyway ubuntu is working fine but when I boot into win xp there is a blue tinge to everything for some reason, especially the taskbar, tops of windows, text and certain gif's. I screwed up the first ubuntu install and reinstalled it (both times in the spare HDD) and I seem to remember during the first install while i was partitioning i may have installed something into my win HDD it was along the lines of "/media". I've searched win and cant find it anywhere though. Any ideas on the blue hue?

---

### Post by rlozano on 2006-10-18
try unistalling your video driver and re-intall it in windows. it might help.

:-k

---

### Post by ReaderRat on 2006-10-18
What type of video card do you have? And, Are you using two PATA HDDs or one PATA and one SATA (This causes problems sometimes.)

---

### Post by caravel on 2006-10-18
Ubuntu can't affect your windows installation in that way.  I'm 99.9% certain this has something to do with the hardware you've installed, and not any Linux installation.

---

### Post by xpod on 2006-10-18
lol...i recently used our other kubunto`s monitor for checking another box with xp pro on it.
The old kubunto is all onboard graphics but the xp box was using a new nvida card so the monitor got plugged in via the card.All fine but...

Since putting monitor back to kubunto IT`s got some weird green tinge about it that i just cant understand.....Windows tch! messes itself up and messes everything else up...lol

---

### Post by bobbydigital on 2006-10-18
My windows was working perfectly before the ubuntu install, this is my config;

-X2 3800+ @2500MHz
-ATI x1800xt
-2x1gb OCZ Platinum
-939dual-sata2
-OCZ 450w Modstream psu
-SB audigy 2
-320gb barracuda sata2 HDD <-----windows drive
-20gb western digital pata <-----ubuntu drive

---

### Post by xpod on 2006-10-18
Sounds like you got ubunto just at the right time as apose to it actually being ubunto`s fault in anyway;) 

Did you try re-installing your graphics drivers in xp as advised??

---

### Post by bulldog on 2006-10-18
> **bobbydigital said:**
> My windows was working perfectly before the ubuntu install, this is my config;

-X2 3800+ @2500MHz
-ATI x1800xt
-2x1gb OCZ Platinum
-939dual-sata2
-OCZ 450w Modstream psu
-SB audigy 2
-320gb barracuda sata2 HDD <-----windows drive
-20gb western digital pata <-----ubuntu drive

Well I believe you.

But it isn't possible that Ubuntu and Windows are mixed up.

They are both on a different file system and are both an OS.

If you boot windows,Ubuntu does nothing and vice versa.

---

### Post by bobbydigital on 2006-10-18
> **xpod said:**
> Sounds like you got ubunto just at the right time as apose to it actually being ubunto`s fault in anyway;) 

Did you try re-installing your graphics drivers in xp as advised??

Not yet but I'll do that now. Honestly I can't see that being the culprit though.

---

### Post by ReaderRat on 2006-10-18
> -320gb barracuda sata2 HDD <-----windows drive
-20gb western digital pata <-----ubuntu drive
Did you know this about mixing PATA & SATA drives?....[http://ubuntuforums.org/showthread.php?t=204428](http://ubuntuforums.org/showthread.php?t=204428)

---

### Post by bulldog on 2006-10-18
> **bobbydigital said:**
>  and I seem to remember during the first install while i was partitioning i may have installed something into my win HDD it was along the lines of "/media". I've searched win and cant find it anywhere though. Any ideas on the blue hue?

I can asure you Ubuntu will install nothing on a NTFS file system.

Think you have seen your window partitions are mounted in your Ubuntu /media folder.

But try to write to a NTFS disk in Ubuntu,and you'll see it's denied.
You can read and copy from it,but writing is out of the question by default.
[It is possible though]

---

### Post by bulldog on 2006-10-18
> **ReaderRat said:**
> Did you know this about mixing PATA & SATA drives?....[http://ubuntuforums.org/showthread.php?t=204428](http://ubuntuforums.org/showthread.php?t=204428)

Hmmm,don't know what you mean with this link.

It's all about windows want's to be the on the first hdd and if not you can map your hdd's in GRUB.

Has nothing to do with this issue,seems Windows boot fine but is faulty after booting.

---

### Post by xpod on 2006-10-18
I aint sure why it would be either....
Theres always a logical answer to strange things when they happen though..
that is one thing i have learned in my short time on a pc.

My kubunto pc is still the same but i KNOW that it was`nt really just cause i borrowed its montior for an xp pc....weird coincidence it only being since plugging the monitor into the xp box....but that would be silly:D 

Go to device manager in xp and have a look what it says about your video driver...other than that i aint got too much of a clue im afraid

---

### Post by ReaderRat on 2006-10-18
??

---

### Post by bulldog on 2006-10-18
> **xpod said:**
> I aint sure why it would be either....
Theres always a logical answer to strange things when they happen though..
that is one thing i have learned in my short time on a pc.

My kubunto pc is still the same but i KNOW that it was`nt really just cause i borrowed its montior for an xp pc....weird coincidence it only being since plugging the monitor into the xp box....but that would be silly:D 

Go to device manager in xp and have a look what it says about your video driver...other than that i aint got too much of a clue im afraid

Using a monitor on a fifferent computer doesn't change anything.

It's possible however that by unplugging the device you moved your graphic's adapter if it's not properly placed and tied with a screw.

---

### Post by bobbydigital on 2006-10-18
Ok , I re-installed my video drivers(6.10 beta's) and everything is all good. I'm still at a loss as to how they were effected during the ubuntu install though? Wel I'm happy now, cheers and thank you[=

 Now I'm just finding out that the ubuntu version I installed, the 64bit version, is unsupported](*,)

---

### Post by xpod on 2006-10-18
No mate ...they all screw in fine.Kubuntos just got a green hue aboot it:D 

It`s weird as the initial big red "COMPAQ" screen that comes up is it`s fine red but the blinking curser i have for a sec in the top corner is green-ish
then all the kubunto install info and then desktop is the same awful color.

Ive messed about with the display settings and checked another monitor on it but still the same...all i did was put the monitor from one pc to another and back..no pulling,yanking or hammering involved.........this time

The kids are using another pc as we`ve just discovered we`re still getting our old set top box internet as well as my recent modem connection so we`re not really too fussed but i`d like to sort it.

Cant have them using m.e surely:twisted:

EDIT Glad YOU got sorted mate....im green with envy...lol:mrgreen:

---

### Post by xpod on 2006-10-18
> Now I'm just finding out that the ubuntu version I installed, the 64bit version, is unsupported

You might find you`ll need a bit of support if using the 64 bit as apparently it still has lots of issues..
Most newcomers are advised to use the x86 to begin..

This was the advice 3ish months ago that i got

---

### Post by bobbydigital on 2006-10-18
> **xpod said:**
> You might find you`ll need a bit of support if using the 64 bit as apparently it still has lots of issues..
Most newcomers are advised to use the x86 to begin..

This was the advice 3ish months ago that i got

I'm going to tough it out with the 64bit, I've seen some work arounds, and I always wanted to try a 64bit os.

Good luck with your green hue mate, and did you try re-installing your video drivers?

---

### Post by Mimsy on 2006-10-18
> **bobbydigital said:**
> Good luck with your green hue mate, and did you try re-installing your video drivers?

:-D !

As for why Windows drivers act up and do what they do, I've got a personal, completely unofficial and unsupported theory that they fall apart gradually, a bit like radioactive compounds, so they have a set half-life, andwhen it expires you need to reinstall them or update them.

And of course the fallout contaminates everything around them, that why you ned to defrag the harddrive and clean up gunk to free up hard drive space so often. It's not the OS, it's the decomposing drivers.

/Mimsy

---

### Post by xpod on 2006-10-18
lol.........good stuff.
The pc in question has some onboard thing that just worked out the box.
So im not sure about that but i will certainly look into it.

Ive been having plenty fun on my main pc with all the 3d stuff and the wee ones have got another with the internet now ....but they would prefer the kubunto rather than the m.e me thinks....me KNOWS:D

EDIT:good luck with the 64bit btw

---

### Post by Mimsy on 2006-10-18
Well... duh? WinME is U.G.L.Y. 

And contaminated. [-( 

/Mimsy

---

### Post by bobbydigital on 2006-10-18
> **xpod said:**
> lol.........good stuff.
The pc in question has some onboard thing that just worked out the box.
So im not sure about that but i will certainly look into it.

Onboard gfx chips have drivers aswell, you should be updating fairly regularly tbh. Find out what your onboard gfx are and go to the site for an update and I'll bet you your problem will be solved.

---

### Post by nickpaton on 2006-10-18
@ Xpod: Is the colour OK on Kubu but green tinge on ME?

I can't work out from the posts, but have you tried another monitor with the same probs?

In general, I don't really suggest removing or connecting a monitor with the PC switched on, since in times past you could blow the PC's graphics video amps - If only one of the Red - Green - Blue amps goes, you end up with a funny coloured display.

Now they add buffer amplifiers to prevent this, but if the prob is both Kubu and ME, then this could be a possibility.

The same is also true of the amps in the monitor with the same results.

Finally, do you have a detachable video lead to the monitor, since it is quite easy to break one of the wires, again with the same result colour-wise.

---

### Post by xpod on 2006-10-18
> @ Xpod: Is the colour OK on Kubu but green tinge on ME?

Unless you eaten something bad mate it must be our kubunto thats a funny shade.The m.e`s fine.If you can call any m.e "fine".

Im not that bad that i dont turn the power off on the pc`s first m8....honestly:D 

I`ve just done some more monitor swapping to check and it seems it`s the actual monitor....It`s the same horrid colour if i put it on this ubunto pc but ubu pc`s monitor is fine on kubunto pc...with me;) 

I was sure id tried m.e`s monitor on kubunto when it first happened the other day and it had been green-ish......leaving me to believe it was kubunto itself.positive i did:-k 

It`s really not a problem though..i had only mentioned it as a comparison to the first mad point about xp being messed by ubu.
The monitor is an old one mate and their ten a penny.
I`ll swap the pc`s over tommorow so they`ve got their kubunto back upstairs and m.e can go in the cupboard till transplant time:twisted:

EDIT:Glad to see you back in the land of the "not so" living m8

---

### Post by nickpaton on 2006-10-18
> **xpod said:**
> 
I was sure id tried m.e`s monitor on kubunto when it first happened the other day and it had been green-ish......leaving me to believe it was kubunto itself.positive i did:-k 

EDIT:Glad to see you back in the land of the "not so" living m8

Sounds like one of your Rabby Burns stories - The Tale of Mad Greeny Screen :p :p 

Saying no more since I don't want to highjack this excellent post!

---

