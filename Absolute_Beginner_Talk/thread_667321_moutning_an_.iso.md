---
title: "moutning an .iso"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-14
how do i mount an .iso image? I used aptoncd to make a meta package and i need to just get the package off the .iso it made so i can put it with other files.

thanks :)

---

### Post by fiddledd on 2008-01-14
you can use "mount -o loop -t iso9660 filename.iso /mnt/" in the Terminal, or tou can install a GUI for it. Look here:

[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

You could also install nautilus-actions from Synaptic, that adds right click option to Nautilus Menu to mount isos, amonst other things
Nautilus Actions website contains scripts to download for this:

[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)

---

### Post by taurus on 2008-01-14
```
sudo mkdir /media/iso
sudo mount -t iso9660 *filename.iso* /media/iso -o loop
ls -la /media/iso
```

---

### Post by machoo02 on 2008-01-14
```
mount -o loop -t iso9660 foo.iso /mountpoint
```
There is also a neat little PyGTK program in the repos called gmountiso that is basically a GUI front end to this command.

---

### Post by hyper_ch on 2008-01-14
there are also plugins for nautilus and konqueror which will let you mount ISOs.

---

### Post by quandary on 2008-01-14
See:
[http://ubuntuforums.org/showthread.php?t=647833](http://ubuntuforums.org/showthread.php?t=647833)

---

### Post by rockinlinux on 2008-01-14
well i downloaded that gui one but im trying to get nautilus actions to work. I followed the insructions but it still oes not give me the options...ideas?

---

### Post by FuturePilot on 2008-01-14
```
sudo apt-get install gmountiso
```
This is a little graphical tool for mounting .iso files.
Applications>System Tools>Gmount-iso

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-22
> **rockinlinux said:**
> well i downloaded that gui one but im trying to get nautilus actions to work. I followed the insructions but it still oes not give me the options...ideas?

Hi rockinlinux, 

Have you solved your problem yet?
I just wrote a tutorial (script) to easily mounting/unmounting ISO through nautilus actions, the script will then creates a desktop shortcut for the mounted ISO.

You might want to see the thread or tried my suggestion there, here's the link:
[http://ubuntuforums.org/showthread.php?t=704350]("http://ubuntuforums.org/showthread.php?t=704350")

PS: You can also see how to creating the "action" for the nautilus-actions there.

---

### Post by mgranet on 2008-02-22
> **rockinlinux said:**
> how do i mount an .iso image? I used aptoncd to make a meta package and i need to just get the package off the .iso it made so i can put it with other files.

thanks :)

I'm confused. Normally in APTonCD, you create the iso, then on the new system, run the APTonCD program, and click "Restore", pointing to the iso. The metapackage will automatically appear in your package manager as aptoncd-metapackage. You click that to install all the archived debs as dependencies. You don't need to manaully pull anything out of the iso, nor should you need to add anything in.

---

### Post by uhappo on 2008-02-23
First post here...

Ok, GMountISO working very well here.

Just 1 problem/Q about a dvd-iso:

It opens it up in audio_ts and video_ts, what plaeyer plays it back as a "normal dvd", including starts up as a normal dvd with menus etc???




P.S. I've been using Ubuntu Gutsy for a week. Never before anything linux-related, Windows all the time. But now... Gooosh, no more MS for me

---

### Post by asmoore82 on 2008-02-23
> **uhappo said:**
> First post here...

Ok, GMountISO working very well here.

Just 1 problem/Q about a dvd-iso:

It opens it up in audio_ts and video_ts, what plaeyer plays it back as a "normal dvd", including starts up as a normal dvd with menus etc???




P.S. I've been using Ubuntu Gutsy for a week. Never before anything linux-related, Windows all the time. But now... Gooosh, no more MS for me

for a dvd image on hard disk, you don't even need to mount it:
mplayer and vlc can definitely "play the iso;" and I would assume xine can too.
VLC is "user-friendly," so you can just click and drag the iso to it.
For mplayer the command is something like this:
```
mplayer -dvd-device */path/to/file.iso* dvd://
```

---

### Post by uhappo on 2008-02-23
VLC works like a champ!!! Thanks!!!

---

