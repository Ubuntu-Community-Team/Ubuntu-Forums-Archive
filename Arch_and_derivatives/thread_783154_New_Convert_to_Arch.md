---
title: "New Convert to Arch"
date: 2008-05-05
forum: Arch and derivatives
---

### Post by Dr Small on 2008-05-05
Greetings there,
This morning I completely dumped Ubuntu and installed Arch. It really wasn't that hard, and now I have it setup... somewhat.

There are a few things that are annoying me at the present time, that must be delt with. First off, the Xorg fonts are horrid. If there is some package to get better fonts, I will most definitely need that.

Second, my clock is off. I checked in /etc/rc.conf and TIMEZONE is set to "Canada/Pacific". I would like to see a list of Timezones that I could possibly use, so I can find mine, and set it properly.

According to the ArchLinux Wiki, I should be able to run the following command to obtain a list of all the timezones, yet I receive the error below:
```
pacman -Ql tzdata | grep zoneinfo | grep -v posix | grep -v right | grep -v .tab | grep -v /$ | sed "s@tzdata /usr/share/zoneinfo/@ @"
```

```
error: package "tzdata" not found
```

I got Networking, Xorg, Alsa all setup, and currently only have Firefox, gFTP, GPG, SSH, and wmii.

Oh, and then there is this other problem...
I tried adding my .mozilla folder from my previous installation to my Home Folder, and it never changed any profile for Firefox. Maybe the firefox profile folder is somewhere else on Arch?

I love the fast boot time, and how lightweight my system feels right now :)
Cheers,
Dr Small

---

### Post by finferflu on 2008-05-05
As for the fonts, I suggest you to install ttf-bitstream-vera and ttf-dejavu, and ttf-ms-fonts (Microsoft's base fonts).

As for the time, I'm not sure what happened to your tzdata, however you can look up the time zones by browsing through /usr/share/zoneinfo. 

I don't know what to suggest you about Firefox.

I hope that helps so far :)

---

### Post by Barrucadu on 2008-05-05
Welcome to Arch. Sit back and enjoy the ride :popcorn:

> **Dr Small said:**
> GFirst off, the Xorg fonts are horrid. If there is some package to get better fonts, I will most definitely need that.
Look on the arch wiki for fonts - there is a big list of font packages. I recommend ttf-dejavu, artwiz-fonts, ttf-ms-fonts, and terminus-font.

> **Dr Small said:**
> I would like to see a list of Timezones that I could possibly use, so I can find mine, and set it properly.
Look in /usr/share/zoneinfo for the timezones.

> **Dr Small said:**
> Maybe the firefox profile folder is somewhere else on Arch?
I don't personally use firefox so I can't check, but as far as I'm aware the distro doesn't affect the place a program stores its settings.

---

### Post by Dr Small on 2008-05-05
Ok. I think the fonts are straightend out now. But my timezone...
Well, I set TIMEZONE to say:
```
TIMEZONE="America/New_York"
```

Rebooted and everything, and it is still saying 22:00 when it should be saying 15:00. Is there something special I have to do to change timezones?

And I really don't know what to do about Firefox and the profile directory. It just doen't read it for some reason... Hrm. That just gave me a thought :)

Most of my problems are solved, now I just need to smooth out the quirks :)

Dr Small

---

### Post by Barrucadu on 2008-05-05
Checked the permissions on the firefox directory? And to sync your time, install *ntp*, then run *sudo ntpd*. You can even add it to the daemons list in rc.conf if you want, so your clock will be synced when you boot.

---

### Post by chucky chuckaluck on 2008-05-05
that's odd about the time zone. mine changed without a problem. 

are you thinking you now have two profiles in .mozilla/firefox? if not, that might be the case.

---

### Post by Rumor on 2008-05-05
> **Dr Small said:**
> 
Second, my clock is off. I checked in /etc/rc.conf and TIMEZONE is set to "Canada/Pacific". I would like to see a list of Timezones that I could possibly use, so I can find mine, and set it properly.
Cheers,
Dr Small

The best way I know to fix the timezone thing is to use openntpd. It's quite easy:

[LIST]
[*]Install openntpd (pacman -S openntpd)
[*]Edit your /etc/rc.conf and put openntpd in your daemons array 
[*]Start the service (/etc/rc.d/openntpd start)
[/LIST]

From that point on, your computer should have the correct date / time each time you restart.

---

### Post by Dr Small on 2008-05-05
Ok, but what does ntpd or openntpd sync with to get the correct time?
Oh, and I found out my Firefox problem, after I FTPed to the server.

I got the kind of feeling when you loose your footing on a steep cliff and a sick feeling comes to your stomach as you drop.....
Apparently the Firefox folder never got backed up!!!

Oh well. It was apparently because of permissions on the files, so it never backed up any of my bookmarks (thousands...) extensions (and all of their settings!) passwords, etc. But oh well. It won't be the first time I have started over.

Lucky for me, that I have another password file for all of my passwords. :)

Dr Small

---

### Post by odiseo77 on 2008-05-05
As for your firefox problem, I'd suggest you to look for bookmarks.html and bookmarks.bak inside ~/.mozilla/firefox/your_profile_name/. I always backup these couple of files just in case (You might want to look for other profiles inside your ~/.mozilla/firefox/ directory too, who knows, maybe they're there).

---

### Post by finferflu on 2008-05-05
> **Dr Small said:**
> Ok, but what does ntpd or openntpd sync with to get the correct time?


It syncs with a [public NTP server](http://support.ntp.org/bin/view/Servers/WebHome) of your choice.

---

### Post by Dr Small on 2008-05-05
Thanks, that did the trick alright :)
I can't find anymore problems at the moment, so I'll ask this...

Where can I find that perl script that outputs that beautiful Arch logo in the terminal? I have seen that in some screenshots, and always wanted to have it :)

Dr Small

---

### Post by K.Mandla on 2008-05-05
P.S.: Welcome to the [club]("http://ubuntuforums.org/group.php?groupid=90")!

---

### Post by freduardo on 2008-05-05
> **Dr Small said:**
> 
Where can I find that perl script that outputs that beautiful Arch logo in the terminal? I have seen that in some screenshots, and always wanted to have it :)



[http://bbs.archlinux.org/viewtopic.php?id=24208&p=1]("http://bbs.archlinux.org/viewtopic.php?id=24208&p=1")
I think this is what you're looking for.

---

### Post by MONODA on 2008-05-07
welcome! I suggest you install yaourt, it is great. there should be installation instructions in the beginner guide

---

### Post by finferflu on 2008-05-07
> **MONODA said:**
> welcome! I suggest you install yaourt, it is great. there should be installation instructions in the beginner guide
Even better, there's the [official project page](http://www.archlinux.fr/yaourt-en/), which provides also a repository for it (it doesn't contain Yaourt only, but also some more updated packages).

---

### Post by kevdog on 2008-05-09
Maybe I'll join the club one day.  I'm really curious.  Guess Dr. Small has gone onto bigger and better things!!

---

### Post by elamericano on 2008-05-10
But why did he go on? A desire for adventure? or disillusionment with Ubuntu?

---

### Post by Dr Small on 2008-05-10
> **elamericano said:**
> But why did he go on? A desire for adventure? or disillusionment with Ubuntu?
Mainly adventure, and the prospect of trying something different.. Plus, ubuntu just seems to easy now anyhow, lol :)

Thanks kevdog. We're all here to help ;) ... and so is the ArchWiki :D

Dr Small

---

