---
title: "Installing over XP in Safe Mode"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-08-31
So, here's the long and the longer of it:
   I have a pirated version of Windows XP Pro on my work compootor. Several years ago, I turned off the automatic updates, then the years flew by and I completely forgot why I had done that. A week or so ago I turned Automatic Updates back on, and the thing starts downloading like it's going out of style. At the end of a week of this, my desktop informs me at startup that I am the victim of piracy or terrorism or some such crime, and that I need to get a legit version of XP to resolve the issue. Fairly quickly the comp starts crashing and burning, or needing to restart to get out of whatever jam it's in, until finally it will only run in Safe Mode.
   So, fine... I take it as a sign to move on away from Windows, I download Ubuntu on a friend's comp, burn the desktop dick, load it into my work comp (which, again, is only running in Safe Mode) and then... nothing. Well, not exactly nothing. I can run the apps perfectly well - Firefox, Gaim, Abiword, etc... - from the disk or I can (and did) install them on the hard drive. But I'm not seeing anything at all related to an OS kernel, GNOME or Nautilus. Zip. I'm not even sure what I'm supposed to be looking for.
   I'd appreciate questions right now just as much as answers. TIA.

---

### Post by jordanmthomas on 2006-08-31
> burn the desktop dick,
pretty funny typo.

Anyway, you need to boot off the CD instead of running it in Windows.
This will vary by computers, but you will need to get your BIOS to boot off your CD.

Typically, hitting F2 as your computer is starting to boot will let you in to the BIOS settings.  On mine, tapping F12 as it starts to boot will allow me to choose to boot off a CD.  You'll need to figure out how to do that on your particular computer, but it's not usually too tough.

After that, you will be running Ubuntu off the CD and should be able to install from there.

Good Luck!

---

### Post by cwaldbieser on 2006-08-31
> **ricardisimo said:**
> So, here's the long and the longer of it:
   I have a pirated version of Windows XP Pro on my work compootor. Several years ago, I turned off the automatic updates, then the years flew by and I completely forgot why I had done that. A week or so ago I turned Automatic Updates back on, and the thing starts downloading like it's going out of style. At the end of a week of this, my desktop informs me at startup that I am the victim of piracy or terrorism or some such crime, and that I need to get a legit version of XP to resolve the issue. Fairly quickly the comp starts crashing and burning, or needing to restart to get out of whatever jam it's in, until finally it will only run in Safe Mode.
   So, fine... I take it as a sign to move on away from Windows, I download Ubuntu on a friend's comp, burn the desktop dick, load it into my work comp (which, again, is only running in Safe Mode) and then... nothing. Well, not exactly nothing. I can run the apps perfectly well - Firefox, Gaim, Abiword, etc... - from the disk or I can (and did) install them on the hard drive. But I'm not seeing anything at all related to an OS kernel, GNOME or Nautilus. Zip. I'm not even sure what I'm supposed to be looking for.
   I'd appreciate questions right now just as much as answers. TIA.

You need to burn the ISO as a bootable CD, then you boot your computer from the CD ROM drive.  Windows never really comes into the picture at that point.  The system initially runs off the CD.  You choose to install it to the hard drive, and you can pretty much erase the Windows partition in the process, if you choose to do so.

---

### Post by ricardisimo on 2006-09-01
> **jordanmthomas said:**
> pretty funny typo.

Anyway, you need to boot off the CD instead of running it in Windows.
This will vary by computers, but you will need to get your BIOS to boot off your CD.

Typically, hitting F2 as your computer is starting to boot will let you in to the BIOS settings.  On mine, tapping F12 as it starts to boot will allow me to choose to boot off a CD.  You'll need to figure out how to do that on your particular computer, but it's not usually too tough.

After that, you will be running Ubuntu off the CD and should be able to install from there.

Good Luck!

That's not a typo... I burned by weewee during the whole process. Doesn't everyone?

Anyhow, I think I know what I did wrong; what I'm seeing on the disc is "ubuntu 6.06.1 i386" instead of "ubuntu-6.06.1-desktop-i386.iso". In other words, I unzipped it onto the desktop and burned the results, rather than just the iso. Does that sound probable to you guys? TIA

---

### Post by jordanmthomas on 2006-09-01
That certainly sounds possible.  
In case you don't know how to burn an ISO, here's a good small program for it.

[http://www.deepburner.com/?r=download](http://www.deepburner.com/?r=download)

You don't have to pirate it, there's a free version ;)

---

### Post by ricardisimo on 2006-09-01
> **jordanmthomas said:**
> That certainly sounds possible.  
In case you don't know how to burn an ISO, here's a good small program for it.

[http://www.deepburner.com/?r=download](http://www.deepburner.com/?r=download)

You don't have to pirate it, there's a free version ;)

OK. F8 on startup gets me a "Please select boot device" with four options, one of which is clearly the CD/DVD. This isn't my BIOS screen, though, or is it? Anyhow, selecting the CD/DVD doesn't install Ubuntu. I mean, there's a lot of whirring and green lights flashing, but it eventually loads XP in Safe Mode, same as it ever was.

---

### Post by L_o_N_e_R on 2006-09-01
then your cd isnt bootable

reburn it again as a bootable cd

---

### Post by confused57 on 2006-09-01
Here's how to burn an iso:
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

Burn the iso to cd "as an image", not as a data cd, nor as a bootable cd option.  Burn it at a lower speed...8x or less.

Edit:  Since you're using a Mac:

[http://www.psychocats.net/ubuntu/maciso.html](http://www.psychocats.net/ubuntu/maciso.html)

---

### Post by ricardisimo on 2006-09-01
> **jordanmthomas said:**
> That certainly sounds possible.  
In case you don't know how to burn an ISO, here's a good small program for it.

[http://www.deepburner.com/?r=download](http://www.deepburner.com/?r=download)

You don't have to pirate it, there's a free version ;)

Perhaps it's because I'm on a Mac currently, but deepburner doesn't seem to be installing, and i didn't see an option for a Mac version anywhere on the website. Any other recommendations?

---

### Post by ricardisimo on 2006-09-01
The app this guy has here on his Mac is Roxio Toast Titanium 6, which has under "Advanced" an option called "ISO 9660". Is that what I'm looking for?

---

### Post by ricardisimo on 2006-09-01
I think I've got it... "Copy Disc" > "Image File". Hopefully. If it works, you'll never hear from me again, since I'm clearly so adept at these things... [eyes rolling into back of head]

---

