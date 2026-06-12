---
title: "Just did something with XGL gone wrong"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by jcr1 on 2008-04-12
Hi all,

I followed this guide:

[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

to try and get desktop effects to work with my Dell D600 ATI 9000 radeon mobility...

Now I can only login via the gnome failsafe session...

Any idea what I have done and how to reverse it?

Cheers,

Jon

---

### Post by joshrobinson on 2008-04-12
hmmm the only thing i could think of that would cause this is the changes made to the xgl.desktop file, have you tried reverting it to how it was?

```
sudo gedit /usr/share/xsessions/xgl.desktop
```
and removing this section
```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

save and close the file, now try logging in

---

### Post by jcr1 on 2008-04-13
umm...when I open that file is right that it is absolutely blank??

Cheers,

Jon

---

### Post by jcr1 on 2008-04-14
Any ideas on this please? I still haven't solved why it only boots through Failsafe mode?

I am considering backing up my home and reinstalling, but it seems silly to do that for something that must be easy to fix.

I am wondering if I should go through my startup script and comment out one by one to see if anything in there is having an effect. Any thoughts?

Cheers again,

Jon

---

