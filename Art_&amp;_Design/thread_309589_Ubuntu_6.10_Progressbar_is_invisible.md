---
title: "Ubuntu 6.10 Progressbar is invisible"
date: 2006-11-29
forum: Art &amp; Design
---

### Post by Thumper322 on 2006-11-29
Hello all,

I just installed Ubuntu 6.10, my first Linux distro, and I'm quite impressed (fast install, detected all my hardware properly, etc). Unfortunately, the progressbars seem to be broken. While I was installing, the progressbar was invisible, and the text slowly turned grey; the volume control (Fn-F[1|2|3]) doesn't display properly, and other progressbars are also kaput.

If I change to a different theme, everything works like a charm. Is there some way to fix this in the default Human theme? If not, can someone recommend a nice theme for me? (I'm used to Royale; I used to use it under Windows XP Professional, and I thought it looked quite nice.)

Thanks for any help anyone can offer.
~Thumper322

---

### Post by reacocard on 2006-11-29
> **Thumper322 said:**
> Hello all,

I just installed Ubuntu 6.10, my first Linux distro, and I'm quite impressed (fast install, detected all my hardware properly, etc). Unfortunately, the progressbars seem to be broken. While I was installing, the progressbar was invisible, and the text slowly turned grey; the volume control (Fn-F[1|2|3]) doesn't display properly, and other progressbars are also kaput.

If I change to a different theme, everything works like a charm. Is there some way to fix this in the default Human theme? If not, can someone recommend a nice theme for me? (I'm used to Royale; I used to use it under Windows XP Professional, and I thought it looked quite nice.)

Thanks for any help anyone can offer.
~Thumper322

I don't know about fixing the problem, but there are *tons* of themes available on [www.gnome-look.org]("http://www.gnome-look.org")

---

### Post by Thumper322 on 2006-11-30
> **reacocard said:**
> I don't know about fixing the problem, but there are *tons* of themes available on [www.gnome-look.org]("http://www.gnome-look.org")

Thanks reacocard; are there any themes you could recommend?

~Thumper322

---

### Post by reacocard on 2006-11-30
> **Thumper322 said:**
> Thanks reacocard; are there any themes you could recommend?

~Thumper322

My current favorite is MurrinaAquaIsh: [http://cimi.netsons.org/pages/murrine/themes.php](http://cimi.netsons.org/pages/murrine/themes.php) (3rd one down)

You'll need to install the Murrine GTK engine to use it: [http://malteo.homelinux.net/pool/edgy-malteo/extras/gtk2-engines-murrine_0.31-1_i386.deb](http://malteo.homelinux.net/pool/edgy-malteo/extras/gtk2-engines-murrine_0.31-1_i386.deb)

---

### Post by Thumper322 on 2006-11-30
> **reacocard said:**
> My current favorite is MurrinaAquaIsh: [http://cimi.netsons.org/pages/murrine/themes.php](http://cimi.netsons.org/pages/murrine/themes.php) (3rd one down)

You'll need to install the Murrine GTK engine to use it: [http://malteo.homelinux.net/pool/edgy-malteo/extras/gtk2-engines-murrine_0.31-1_i386.deb](http://malteo.homelinux.net/pool/edgy-malteo/extras/gtk2-engines-murrine_0.31-1_i386.deb)

Thanks! Looks pretty good.

Can I **sudo apt-get install gtk2-engines-murrine**?

---

### Post by reacocard on 2006-11-30
> **Thumper322 said:**
> Thanks! Looks pretty good.

Can I **sudo apt-get install gtk2-engines-murrine**?

If you add this line to your /etc/apt/sources.list you can:
```
deb http://malteo.homelinux.net edgy-malteo extras
```

You'll also need the GPG key for this repo:
```
wget http://malteo.homelinux.net/B54820BC.gpg -O- | sudo apt-key add -
```

---

### Post by reacocard on 2006-11-30
But it's easier to just download and install the .deb I linked to above. That way you don't have to worry about your theme breaking if Murrine is updated.

---

### Post by Thumper322 on 2006-12-01
Well, I installed the .deb and tried out the theme.

I'm afraid I don't really like it; OpenOffice and Firefox don't quite fit in the theme, and overall it's too pale grey. I've already tried a few themes from gnome-look, but I haven't found anything I really like.

Can anyone recommend a theme that
[LIST]
[*]blends into Firefox and OpenOffice.org
[*]isn't too pale (it's hard to see on my LCD)
[*]and doesn't use the ubuntulooks engine (which isn't rendering progressbars correctly)?
[/LIST]

Thanks for your help...

---

### Post by swamytk on 2006-12-02
Try default human theme with different default color depth in /etc/X11/xorg.conf. It should work

[http://ubuntuforums.org/showthread.php?t=284713](http://ubuntuforums.org/showthread.php?t=284713)

---

