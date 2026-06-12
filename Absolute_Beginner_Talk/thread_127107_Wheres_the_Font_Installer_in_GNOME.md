---
title: "Wheres the Font Installer in GNOME?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by kenweill on 2006-02-08
In KDE, i just goto the terminal and type "kcontrol' then under 'System Administration', theres that Font Installer. From there, I can add TTF fonts from a Windows Partition.

But under GNOME, where can I find the Font Installer? How can I easily install TTF fonts?

---

### Post by tageiru on 2006-02-08
System->Settings->Font->Details->Go to font folder (or something like that)

Then you drag and drop your fonts into that folder.

---

### Post by kenweill on 2006-02-08
In windows, if you install lots of fonts, some say that it will slow down your system, eating lots of memory.

What about here in Linux, does installing alot of fonts affects performance?

---

### Post by mcduck on 2006-02-08
You can also just move the font files to .fonts (to install fore one user only) or /usr/share/fonts (to install for all users.

Or you can open nautilus, type Ctrl-L to open location bar, go to fonts:// and drag-and drop font files there.

---

### Post by kenweill on 2006-02-08
Thanks alot for the info.

I installed KDE and used the Font Installer in KDE. Its just that I get used in KDE before under Red Hat 9.

I just post that question because I have no idea where to install fonts in GNOME.

Anyway, thank you all very much.

---

### Post by dschaller on 2006-02-20
[QUOTE=mcduck]You can also just move the font files to .fonts (to install fore one user only) or /usr/share/fonts (to install for all users.

Or you can open nautilus, type Ctrl-L to open location bar, go to fonts:// and drag-and drop font files there.[/QUOTE]

I can't get either of these methods to work. At least when I do them, openoffice 1.1.5 cannot find the font. I could not get the font to appear in fonts:/// even when I started nautilus as root and did the drag-and-drop methond. I've been trying for 2 hrs to get a simple .ttf to show up in openoffice. What am I doing wrong?

I've read the wiki on font installation and do not entirely understand it. The parts of it I've tried do not seem to work for me.

---

### Post by dschaller on 2006-02-20
Ok. I got it to work now when I copied to the .fonts directory from the command line. I must have been making a mistake earlier there. I'm still not sure why drag-and-drop doesn't work for me or copying to /usr/share/fonts though.

---

