---
title: "3D Desktop?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by princeroys on 2006-11-16
I was introduced to Kubuntu at LinuxWorld and as part of the demo I was shown some "Vista like" functionality with a 3D desktop. Is this Edgy functionality or can I get it from Dapper Drake? If so how? I am new to Ubuntu.

Roy

---

### Post by 23meg on 2006-11-16
It's Beryl or Compiz, which don't come preinstalled with either; you have to install them, along with appropriate drivers, and in certain cases a separate X server (XGL).

[Here]("http://www.ubuntuforums.org/showthread.php?t=272104") is how.

---

### Post by dillbertdabomb on 2006-11-16
good luck buddy...

---

### Post by turbojugend_gr on 2006-11-16
Just a suggestion, do not compare vista's aero effects with Beryl... you 'll get embarassed... or winoz will... ;)

---

### Post by jhenager on 2006-11-16
> **turbojugend_gr said:**
> Just a suggestion, do not compare vista's aero effects with Beryl... you 'll get embarassed... or winoz will... ;)

No doubt. When Vista finally does come out, it will find itself far behind what I have been running at home for over a month.

---

### Post by turbojugend_gr on 2006-11-16
Well having seen vista's aero effects, I can say it even behing the initial publication of the XGL video back in January, so there's nothing to compare, this time OSS is the Goliath... poor windoz users...paying for an imprisoned nothing.

---

### Post by Ephemeriis on 2006-11-16
> **turbojugend_gr said:**
> Well having seen vista's aero effects, I can say it even behing the initial publication of the XGL video back in January, so there's nothing to compare, this time OSS is the Goliath... poor windoz users...paying for an imprisoned nothing.

Except that Vista's Aero stuff, no matter how unimpressive or limited it may be, will work (on supported hardware) right out of the box.  Nothing special to download and install, no configuration, no plugins to grab...  It's built right in to Windows.  That's something that hasn't happened yet with Compiz/Beryl.

And given the difficulty I've had installing Compiz on my own system, that's probably a service that most end-users are willing to pay for.

---

### Post by Beej on 2006-11-16
Ephithermeriis,
        I'm in agreement generally. But as a point, I have an old PCI nvidia graphics card, and on my vista RC1 instillation I don't get the "Aero" window manager as my machine is not power full enough. On Edgy I have Beryl running like a dream.

Why can't Vista look snazzy on old hardware??

---

### Post by turbojugend_gr on 2006-11-17
> **Ephemeriis said:**
> Except that Vista's Aero stuff, no matter how unimpressive or limited it may be, will work (on supported hardware) right out of the box.  Nothing special to download and install, no configuration, no plugins to grab...  It's built right in to Windows.  That's something that hasn't happened yet with Compiz/Beryl.

And given the difficulty I've had installing Compiz on my own system, that's probably a service that most end-users are willing to pay for.

You are wrong m8 in many prospectives, sorry to say that but it is true. Here it is why:

1. In Vista you will also have to install the drivers for your card (which is part of the pain you suggested).

2. As beej just said, Vista's very limited effects are only for high end machines, which is hilarious when beryl works like a charm in a 64mb 3d nvidia.

3. Windows Vista is not officially out yet, so is beryl. But Compiz/Beryl had great pace in evolving terms (one year back there wasn't even started, around february a user could install compiz on an xgl server, late summer beryl forked, and as we are talking almost all major distros can run beryl using xorg's built-in aiglx. SO I believe that after Xmas when Vista will be out (but still only a minority on peoples PCs and most propalbly till service packs arrive it would be baggy just like XP did for over a year) beryl will install itself just by adding one repo (now you have to add 2)

4. Where's the pain m8? I installed latest beryl on my edgy, in less than 15 mins, I just added a repo for beryl, and one for nvidia (which was needed cause the drivers where beta) which won't be needed as soon as the drivers are done (actually I am not sure when that will be... any one does?). After adding the repos I just needed to download the packages (which on the contrary to windoz install themesleves, and I don't need to press no next button till it decides to do so) and add one line in my xorg.conf. If it was still May, then it would be a pain, now it's just a smoke away.

5. Yes, aero is even easier but m8 that's not cause Beryl guys want to mess with us, it's because Beryl will keep evolving and adding new stuff (as we ask them to) for a long time so a repo is needed to automatically update things. No need to mention that what Vista give with aero on February (actually january 30th, it sound like $ 9.99 trick to me) will be the same for one year at least (till someone else or M$ itself create a better one which you might have to pay for) or worst for 5-6 years till next windoz release.

I don't wish to "sound" aggressive in any way, just trying to point out the facts. I hope I did so without "sounding" aggressive.

Cheers, TJ.

P.S: I should say that adding repo's shouldn't been described as adding lines in a text file to users, cause it make them fell like hacking things, like it's a difficult thing to do. Instead users should be given an "Open software sources >> add third party repo". If that's what gives users the feeling things are difficult to understand, may be we should change that.

---

### Post by xpod on 2006-11-17
I quite agree with turbojugend_gr..

The only reason i found beryl etc difficult those first weeks was my complete ignorance and the lack of a half decent graphics card.

After leaving it all a couple of months till i was a wee bit more savvy and of course aquiring a reasonable card it was a peice of cake to install.

I got it working on dapper (gnome & kde) and on edgy with the beta nvidia drivers etc.
My only gripe is having the fire but not having the water.......to put the flames out of course;) .
Apparently the card dosent have the required pixel shading abilities or something like that.

The novelty soon wears of though and i dont even bother with it now most times.

---

