---
title: "Terrible Firefox icon theme!"
date: 2005-04-13
forum: Art &amp; Design
---

### Post by basse1989 on 2005-04-13
OK, Now I want a strait answer, is the icon theme a bug or what?
Please tell me you are gonna fix this and make the theme look like gnome.
Please Please Please!

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=basse1989]OK, Now I want a strait answer, is the icon theme a bug or what?
Please tell me you are gonna fix this and make the theme look like gnome.
Please Please Please![/QUOTE]

I'm pretty sure that Ubuntu's Firefox uses the *default* Firefox theme. I'll admit that it could be better.

---

### Post by localzuk on 2005-04-13
Take a look at the list of themes at: [https://addons.update.mozilla.org/themes/?application=firefox](https://addons.update.mozilla.org/themes/?application=firefox)

if you don't like the default one.

---

### Post by basse1989 on 2005-04-13
There's no point in changing themes on my own in firefox, the point was that it change accordingly to the gnome theme currently in use. That is why it was such a great patch.

---

### Post by Nis on 2005-04-13
[QUOTE=basse1989]There's no point in changing themes on my own in firefox, the point was that it change accordingly to the gnome theme currently in use. That is why it was such a great patch.[/QUOTE]
 I guess the patch was too unstable for inclusion in Hoary.  Here's hoping it will make it into Breezy.  In the meantime the [GNOME-Fx](http://gnomefx.mozdev.org/) themes will have to do (even if you do have to change the Firefox theme when you change you're gtk theme.

---

### Post by basse1989 on 2005-04-13
I though the patch worked nicely. I can't think of anything about that patch that was bad.  :-?

---

### Post by SKLP on 2005-04-13
Maybe it didn't work with the latest firefox and when they updated to it they were just going to release hoary and didn't have time to fix an updated version of the patch.

---

### Post by basse1989 on 2005-04-13
Well probably, but that's so sad. :(

---

### Post by Nis on 2005-04-13
[QUOTE=basse1989]I though the patch worked nicely. I can't think of anything about that patch that was bad.  :-?[/QUOTE]
 The only bug I can remember about the patch was sometimes the forward and back arrows would disappear while a page was being loaded.  But other than that I thought it was great.  Maybe SKLP is right.  Le sigh. :(

---

### Post by ssam on 2005-04-13
and is it just me that gets a blue globe as the firefox icon in the applications menu?

surely after all the work mozilla have done with the firefox branding it should have a proper firefox icon.

---

### Post by Glanz on 2005-04-13
[QUOTE=ssam]and is it just me that gets a blue globe as the firefox icon in the applications menu?

surely after all the work mozilla have done with the firefox branding it should have a proper firefox icon.[/QUOTE]
I believe that was one of Debian-Legal's decisions because they didn't approve of the purety of the creative-commons or other licensing of the icon...... Sheeeeessssh!!!!
=================here's the skinny==============
from:: [http://lists.debian.org/debian-devel/2004/02/msg01877.html](http://lists.debian.org/debian-devel/2004/02/msg01877.html)
Hello all, 

I received a rather disturbing email from Andre Dahlqvist (quoted
below with URLs) today that I'm having trouble with, and I'd like
opinions and advice on how to proceed. debian-legal might be a better
forum for this, but I think it has some deep ramifications for not
just firefox.

I included the official icons in my latest mozilla-firefox package,
thinking that the developers had perhaps rushed to get the release
done forgot to include it. Unfortunately it seems these icons and even
the name "Firefox" (and Mozilla even) are trademarked and can't be
used except with the official builds or permission of the Mozilla
Foundation (see [http://mozilla.org/foundation/licensing.html]("http://mozilla.org/foundation/licensing.html") and
[http://forums.mozillazine.org/viewtopic.php?t=50876]("http://forums.mozillazine.org/viewtopic.php?t=50876")). Now I feel
confident I could get said permission, but it would be pointless since
it would likely violate point 8 of the DFSG.

Now not being able to use the artwork is annoying, but not the end of
the world (people will whine as to why we don't have the pretty
icon). However, not being able to use the name would really be a
shame, not to mention confusing. 

So, how should I approach the Firefox developers (or branding team)?
or should I merely rename the browser in Debian to something like
Icerabbit (you get the idea) to skirt these thorny legal issues. It
seems OpenOffice.org has similar restrictions on their logo
([http://www.openoffice.org/about_us/summary.html]("http://www.openoffice.org/about_us/summary.html")), how were they
handled?

---

### Post by mostwanted on 2005-04-14
If that patch must come back, please don't remove the default theme. Some people here actually like the default theme a lot, and you can't download and install it, so you're dependant on getting it from the Ubuntu package (or download Firefox from mozilla.org and run it separately from the ubuntu package-system).

---

### Post by SKLP on 2005-04-14
[QUOTE=mostwanted]If that patch must come back, please don't remove the default theme. Some people here actually like the default theme a lot, and you can't download and install it, so you're dependant on getting it from the Ubuntu package (or download Firefox from mozilla.org and run it separately from the ubuntu package-system).[/QUOTE]
agreed.
(still prefer the gnomeized theme :P)

---

### Post by endoscient on 2005-04-14
Is there anyway to change the icon to the default one?

Also is it possible to install the patch on hoary.

---

### Post by Glanz on 2005-04-14
[QUOTE=endoscient]Is there anyway to change the icon to the default one?

Also is it possible to install the patch on hoary.[/QUOTE]
 You could add the original icon to /usr/share/pixmaps (as sudo) giving it the samenameand format as the current after renaming the current for starters.
And you can hack the Firefox libs and configs in much the same way but it is a bit more complicated.

---

### Post by thechitowncubs on 2005-04-27
[http://www.ubuntuforums.org/showthread.php?t=30133](http://www.ubuntuforums.org/showthread.php?t=30133)

---

### Post by TravisNewman on 2005-04-27
The original firefox theme can't be redistributed with custom builds. Since most distributions have custom firefox builds, they have to use the logo mozilla made for custom builds. Not a choice by debian, but by mozilla. They want people to know whether they're running default firefox or not.

EDIT: when I say "theme" above, I mean the branding theme-- the icon, the about dialog, etc.

---

