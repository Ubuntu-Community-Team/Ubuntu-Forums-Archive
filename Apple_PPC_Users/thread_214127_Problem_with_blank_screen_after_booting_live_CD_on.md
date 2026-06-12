---
title: "Problem with blank screen after booting live CD on iMac G3"
date: 2006-07-12
forum: Apple PPC Users
---

### Post by tobydwhite on 2006-07-12
Hi!

Ok, this is the situation:

Have inserted and booted from CD on my iMac G3 350Mhz with 192MB/7GB. To view specification: [http://lowendmac.com/imacs/350.html]("http://lowendmac.com/imacs/350.html")

Blank screen appears after booting, although from reading other posts this can be corrected.

Had found a post by '[COLOR="Red"]twongkee[/COLOR]' which stated that you must change the frequencies in monitor section in the '[COLOR="Red"]X config file[/COLOR]'.

This has been saved and changes made although when restarting [COLOR="Red"]X[/COLOR] using:

[COLOR="Red"]sudo /etc/init.d/gdm restart[/COLOR]

I get the following two errors:

[COLOR="Red"]Stopping GNOME Display Manager OK
Starting GNOME Display Manager Fail[/COLOR]

I then restarted by typing [COLOR="Red"]'ctrl' + 'alt' + delete'[/COLOR]. I booted from the CD again but no change: still the same blank screen as before.

Thanks in advance and any help is much appreciated.

Toby.

---

### Post by 3rdalbum on 2006-07-12
Is it a black screen, where your monitor has turned off, or a dark brown screen?

---

### Post by linear on 2006-07-12
When using the Desktop CD, use:

**sudo killall -HUP gdm**

to restart Gnome.

In addition to changing monitor frequencies in xorg.conf, disable dri.

---

### Post by tobydwhite on 2006-07-13
> **3rdalbum said:**
> Is it a black screen, where your monitor has turned off, or a dark brown screen?

It is indeed a black screen.

Thanks for your help,

Toby.

---

### Post by tobydwhite on 2006-07-13
> **linear said:**
> When using the Desktop CD, use:

**sudo killall -HUP gdm**

to restart Gnome.

In addition to changing monitor frequencies in xorg.conf, disable dri.

Thanks - I'll attempt this now.

Toby

---

