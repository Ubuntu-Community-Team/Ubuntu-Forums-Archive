---
title: "Fonts in Ubuntu/Linux?"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by Leadherent on 2005-11-29
Hi,

I have a program in Ubuntu 5.04, that uses lesstif2 as a front-end. I need to be able to use a certain ttf font in this program. What do I have to do to install the font so that it is correctly recognised?

Thanks,

L

---

### Post by Manny C on 2005-11-29
Can you be a bit more specific? What ttf font and what is/does lesstif2 do?

---

### Post by GTvulse on 2005-11-29
[QUOTE=Leadherent]Hi,

I have a program in Ubuntu 5.04, that uses lesstif2 as a front-end. I need to be able to use a certain ttf font in this program. What do I have to do to install the font so that it is correctly recognised?

Thanks,

L[/QUOTE]

Motif is rather primitive when it comes to fonts[1] and only knows about fonts installed in the X server, that is, the fonts you can get at with [FONT="Monospace"]xlsfonts[/FONT] and [FONT="Monospace"]xfontsel[/FONT]. If you have to configure the fonts by hand you'll need the X fonts names those applications show to you. Can't tell you exactly how to setup a Motif options file as I have blissfully forgotten how it works already. :-)

You'll notice that the fontpaths defined in [FONT="Monospace"]/etc/X11/xorg.conf[/FONT] do not contain a directory where you can add fonts easily to your X server. But Ubuntu already has one, [FONT="Monospace"]/usr/local/share/fonts[/FONT]. What you need to do is to add the following line to the Files section in [FONT="Monospace"]xorg.conf[/FONT] (use "[font="Monospace"]sudo <your editor> /etc/X11/xorg.conf[/font]"):
```

FontPath        "/usr/local/share/fonts"

```
Copy your truetype fonts to that directory, change directories to it and type:
```

sudo mkfontcache .
sudo mkfontdir .
sudo fc-cache .

```
in that order and notice that I typed a dot/period at the end of each command. Do as well.

Now, log off your session. Hit "<ctrl-alt-backspace>" watch X Windows reboot and log in again. The fonts will be availabe to your Motif/Lesstif applications.

[1] Sometime ago I reacquainted myself with Solaris (a.k.a. SunOS 10) after 10 years of not touching the thing (SunOS 5.4 was my last stint at it) and when CDE showed up in its glorious and ugly late 80's style, I told myself: "CDE!!! I thought you was dead, maaaan!".

---

### Post by Leadherent on 2005-12-01
Thanks for your reply. I followed your advice but the lesstif/motif application still does not see the font. GIMP, on the other hand, seems to be able to recognise it but xlsfonts does not. (?)

Still confused but on a higher level... ;-)

L

---

### Post by Tosa on 2005-12-01
Hi,
I've just installed some ttf and it worked in openoffice. I followed Help > Ubuntu 5.10 Starter Guide.
I copied fonts to

/usr/share/fonts

and then typed in terminal

sudo fc-cache -f -v

It worked for me.
HTH.

---

