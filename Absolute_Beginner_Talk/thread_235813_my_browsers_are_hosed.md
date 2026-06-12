---
title: "my browsers are hosed"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-08-13
ever since i messed with this xgl stuff, my browsers keep closing without warning. i've gotten rid of as much xgl and compiz stuff as i could find, though this might not even be the problem. it may be just a coincidence. any ideas?

---

### Post by nalmeth on 2006-08-13
Still sorting things out eh?

Post the output of:
cat /etc/X11/xorg.conf
cat /etc/apt/sources.list
cat /etc/gdm/gdm.conf-custom

Perhaps in text files as the output will be rather long for all three. You may still be running the XGL session, but without the effects, or maybe there is still unnecessary junk in your xorg.conf.

---

### Post by fuscia on 2006-08-13
> **nalmeth said:**
> Still sorting things out eh?

Post the output of:
cat /etc/X11/xorg.conf
cat /etc/apt/sources.list
cat /etc/gdm/gdm.conf-custom

Perhaps in text files as the output will be rather long for all three. You may still be running the XGL session, but without the effects, or maybe there is still unnecessary junk in your xorg.conf.

i got rid of a bunch of stuff earlier. i used *locate* to try to sniff out any leftover xgl or compiz stuff. there was one beerokid entry left in the sources list and i just got  rid of it. attached are the other two things.

---

### Post by enopepsoo on 2006-08-13
:KS backup your files andd reinstall the OS.:KS

---

### Post by DSn0wMan on 2006-08-13
I was having the same problem. I think? Anyhow there is some "feature" of XGL/Compiz wich causes windows to disappear on specific mouse movements.

To get rid of this "feature" I did the following:

run gconf-editor

apps>compiz>plugins>showdesktop>allscreens>options and cleared entries from initiate_edge.

Then just to be sure I got rid of the entries for initiate_edge in apps>compiz>plugins>scale>allscreens>options

---

### Post by fuscia on 2006-08-13
> **DSn0wMan said:**
> I was having the same problem. I think? Anyhow there is some "feature" of XGL/Compiz wich causes windows to disappear on specific mouse movements.


i saw your thread. when i went to the compiz plugins, it was empty. i've been trying to purge all that junk and i don't know if those plugin entries were ever there or not.

---

### Post by nalmeth on 2006-08-14
I see you're running the nvidia driver. Do you need 3D at this point for anything else? If not, try to reset your X settings (after cp a backup):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.xglbackup
sudo dpkg-reconfigure xserver-xorg
```
You'll have a backed-up copy called xorg.xglbackup. Running the dpkg-reconfigure command will automatically back one up for you, but it's easier to find it this way.
Try the open-source nv driver just for now. You won't get 3D if you play games, but it's a start to see if there's any improvement. I'm not a wizard with X configging, but there seem to be some extra spices in your xorg.conf, and hopefully this will clear things up and get you back to normal. 

BTW, the defaults will be acceptable for most everything as you go through the wizard. Go with them unless you know you need certain settings, like extra screen resolutions.

You shouldn't have to reinstall after something like this.

---

### Post by fuscia on 2006-08-14
i ended up re-installing. it was quite simple and now i have a clean, shiny system. thanks to all of you for your help.

---

