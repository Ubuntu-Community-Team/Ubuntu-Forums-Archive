---
title: "DVD Autoplay"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-07-14
I have VLC media player but when I put in a DVD it won't autoplay, it goes straight to Movie Player and then I get an error message. I've tried right clicking the cd to set it to open with VLC but there isn't an option. Does anyone know how I go by doing this? Thanks.

---

### Post by ramjet_1953 on 2007-07-14
Navigate to [COLOR="Blue"]System>Preferences>Removeable Drives and Media[/COLOR]

Click on the [COLOR="Blue"]Multimedia Tab[/COLOR]

Change the start up command for your chosen media player

Regards,
Roger :cool:

---

### Post by Bofur on 2007-07-14
Well it auto opens now but it doesn't play. I've tried running it from terminal and I get 
```
justin@linuxbox:~$ /usr/bin/vlc dvd://
VLC media player 0.8.6 Janus

(.:7673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: SG1_V5_R1_YR4
libdvdnav: DVD Serial Number: 2eb50431
libdvdnav: DVD Title (Alternative): SG1_V5_R1_YR4
libdvdnav: Unable to find map file '/home/justin/.dvdnav/SG1_V5_R1_YR4.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[00000287] main playlist: nothing to play


```

---

### Post by ramjet_1953 on 2007-07-14
It sounds like you need to install libdvdcss, to decrypt your encrypted DVD's

Follow this link for the how-to:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Regards,
Roger :cool:

---

### Post by apaz on 2007-10-04
hi, 
System>Preferences>Removeable Drives and Media >Multimedia Tab,  in DVD video Disk field simply type:
 
/usr/bin/wxvlc dvd:///dev/hda

it worked for me
bye

---

### Post by skompier on 2007-10-20
> **apaz said:**
> hi, 
System>Preferences>Removeable Drives and Media >Multimedia Tab,  in DVD video Disk field simply type:
 
/usr/bin/wxvlc dvd:///dev/hda

it worked for me
bye

For VLC to autoplay DVDs when inserted, I used

```

wxvlc DVD:///media/cdrom0
```

in Video DVD Disk field for mine. Just an FYI for people to try if hda doesn't work.

---

### Post by goatdad13 on 2007-12-23
For VLC to autoplay DVDs when inserted, I used

Code:

wxvlc DVD:///media/cdrom0


worked for me

---

### Post by omega_user on 2007-12-23
> **ramjet_1953 said:**
> It sounds like you need to install libdvdcss, to decrypt your encrypted DVD's

Follow this link for the how-to:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Regards,
Roger :cool:

This setup seems to be following instructions for Feisty. Is there a Gutsy DVD codec install that'll allow me to watch these encrypted DVDs?

---

### Post by omega_user on 2007-12-23
easy resource to explain the whole thing is here at the [Medibuntu Page]("https://help.ubuntu.com/community/Medibuntu")
hope this helps explain things

---

### Post by Dr Small on 2007-12-23
I changed mine from "totem %m" to "vlc %m"

---

