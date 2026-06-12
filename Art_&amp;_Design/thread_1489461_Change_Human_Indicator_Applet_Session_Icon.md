---
title: "Change Human Indicator Applet Session Icon"
date: 2010-05-21
forum: Art &amp; Design
---

### Post by klausner on 2010-05-21
Using the Human icon set for the Gnome desktop, how can I change the _Indicator Applet Session_ icon? There isn't a "properties" option. It uses a orange terminal icon that bugs me. I've gone through several other icon sets, but they each seem to use different named icons for this applet. Searching through /usr/share/icons/human, I found a computer.svg icon that matches the one used, but changing that for another image doesn't work.

Is there some sort of reference file that says "Applet X uses Icon Y" for an icon theme?

---

### Post by klausner on 2010-05-24
Bump

---

### Post by dzon65 on 2010-05-25
You can always change it in usr/share/icons/gnome.You might wanna look it up though,could be in pixmaps.

---

### Post by klausner on 2010-05-25
> **dzon65 said:**
> You can always change it in usr/share/icons/gnome.You might wanna look it up though,could be in pixmaps.

Look it up *where*? I've tried going through the share images and changing the candidates I found, without success.

---

### Post by dzon65 on 2010-05-26
That's the path.System/usr/share/icons or system/usr/share/pixmaps.

---

### Post by klausner on 2010-05-26
> **dzon65 said:**
> That's the path.System/usr/share/icons or system/usr/share/pixmaps.

As I said in the initial post, I've been all through /usr/share/icons/human, and changing the icon there has no effect.

/usr/share/pixmaps seems used by applications, not the desktop.

---

### Post by dzon65 on 2010-05-26
You say you're using the human icon set?Then the indicator applet session icon isn't a terminal.It should look like this.

---

### Post by dzon65 on 2010-05-26
Oops,sorry about that,wrong file extension.

---

### Post by dzon65 on 2010-05-26
I changed that icon once.It's located in usr/share/libindicator/icons/hicolor/16X16/system-shutdown-panel

---

### Post by klausner on 2010-05-26
> **dzon65 said:**
> I changed that icon once.It's located in usr/share/libindicator/icons/hicolor/16X16/system-shutdown-panel

Thanks for the suggestion. I tried changing the icons in that directory, logged out, and then  back in, but it had no effect.

---

### Post by dzon65 on 2010-05-27
Well,running out of ideas.You seem to have a weird hard time changing icons.I even installed the human theme to check it out cause that terminal icon as standard indicator icon is weird.Anyway,I managed to change it in 5 minutes.Did you get that icon theme from synaptic?What's shown if you install another theme,does it remain a terminal?

---

### Post by mike4ubuntu on 2010-09-01
does anybody know if there is a command line to popup the system-shutdown-panel?  I'd like to assign a shortcut key to it.

---

### Post by Sciesch on 2010-09-16
I also want to change the Logout Icon, atm I am trying to use the green running man from Crux, but i cannot seem to replace the actual one (a Monitor from the 'Human' theme). 
The strange thing is that there seems to be no indication on where the theme gets it's icon from, not in the index.theme nor in the folders, at least as far as I looked.

It seems not every theme uses the same locations for their icons ):P

&#8364;: I got it now.
Seems like for 'Human' Icon theme the responsible piece is /usr/share/icons/Human/24x24/devices/system.png. Now I got the little green man :D

---

### Post by Topazgb on 2010-10-10
It changes with the theme, I have a similar problem and trying to find the location.

---

### Post by graha1994 on 2010-10-14
How about the default theme, dust theme ? can everyone tell me the exact location ?

---

