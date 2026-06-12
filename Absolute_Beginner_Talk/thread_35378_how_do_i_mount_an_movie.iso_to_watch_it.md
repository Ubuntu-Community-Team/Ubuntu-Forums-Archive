---
title: "how do i mount an movie.iso to watch it ?"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by NoTiG on 2005-05-18
I need to watch a file called foo.iso . But how do i mound it ??

and where do i mount it too ? /mnt ???

EDIT: NM 

 sudo mount -t iso9660 -o loop,ro /home/notig/Desktop/foo.iso /mnt

---

### Post by dave9191 on 2005-05-18
I was just about to look it up for you :) Just subscirbing to this so I can have the cmd at hand :)

---

### Post by Moobert on 2005-05-18
mplayer can play files like that directy also

---

### Post by bro on 2007-04-27
I happen to stumble upon this. Just tried. Mplayer did not play my dvd-iso. VLC however did.

---

### Post by bogdarnet on 2008-06-27
Got the movie running in Totem Movieplayer, but the subtitles aren't there and the menu isn't available... any suggestions?

---

### Post by JacoLouw on 2008-06-27
Download Gmount-iso.

Synaptic Packet Manager should find it for you.

---

### Post by bogdarnet on 2008-06-28
Okay, tried gmount, but I'm still not seeing menus or subtitles - any suggestions?  (Also I wasn't sure whether to continue using Totem after gmount or some other viewer?)

---

### Post by BennBuntu on 2008-06-28
Here's a script for nautilus (I didn't make them, somewhere else on these forums). If you forget to unmount it will leave folders in your /mnt/ directory, but you can always delete them.

I've since realised that VLC can play them directly, menus work fine for me. If you choose DVD-simple in vlc it skips them.

For the script, make 2 text files in 
~/home/yourUser/.gnome2/nautilus-scripts/
And copy this into each one, one for mount_iso, one for unmount_iso.

Then make them executable (right click, permissions etc.)


```
#!/bin/bash
#
# nautilus-mount-iso

gksudo -u root -k /bin/echo "got r00t?"

sudo mkdir /media/"$*"

if sudo mount -o loop -t iso9660 "$*" /media/"$*"
then
        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted.
        
        Open Volume?"
        then
                nautilus /media/"$*" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$*"
        zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
        exit 1
fi
```

```
#!/bin/bash
#
for I in "$*"
do
foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`

sudo umount "$I" && zenity --info --text "Successfully unmounted /media/$I/" && sudo rmdir "/media/$I/"
done
done
exit0
```

---

### Post by bogdarnet on 2008-06-29
VLC did it - thanks!

---

### Post by ene_dene on 2008-06-29
> **bogdarnet said:**
> VLC did it - thanks!
Yes, the best combination is mounting iso with gmount and then using VLC player for playing video. The same goes for DVDs (you don't need gmount then).

---

