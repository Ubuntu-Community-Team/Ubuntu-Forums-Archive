---
title: "[SOLVED] customize vlc"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by ellalan on 2008-03-04
Hi
I am trying to customize vlc player,
when I go to the line to customize I am unable to change  from :vcdx:///dev/scd to vcd:///dev/scd.
I just want to edit x out of the line, could some one help me. Thank you.

---

### Post by herbster on 2008-03-04
Where are you going in VLC? Are you talking about File > Open Disc ??

---

### Post by ellalan on 2008-03-04
Yes herbster, 
I tried there but it wouldn't change, Thank you.

---

### Post by herbster on 2008-03-04
So you hit File > Open Disc, now at the top which do you have selected: DVD (Menus), DVD, VCD or SVCD? Are you trying to open a VCD or DVD?

---

### Post by ellalan on 2008-03-04
File>Open Disc>VCD
Then under Advaved Options I am trying to change the line from
this   vcdx:///dev/cdrom :audio-track=0
to      vcd:///dev/cdrom :audio-track=0
Sorry I was not clear enough in my previous post.

---

### Post by herbster on 2008-03-04
Hmm, that's strange. Can you delete the rest of the line? What all are the characters that will not change, or is it just the "x" ?

Try this: Hit ALT+F2, paste this:

```
wxvlc vcd:///dev/cdrom :audio-track=0
```

Hit ENTER and see if VLC launches and plays. If not, are you sure your CD-ROM is /dev/cdrom? Paste the output of:

```
cat /etc/fstab
```

---

### Post by ellalan on 2008-03-04
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b6e959a8-20cc-4f47-9da9-5257497adf2f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cef28382-cd3e-481a-8949-0aee5283f820 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0    


Hi herbster
when I pasted the first command I get the error "unable to open 'vcd:///dev/cdrom'
for the second command I get as above. Thank you.

---

### Post by ellalan on 2008-03-04
I tried to replace the whole line and it wouldn't change.

---

### Post by herbster on 2008-03-06
Do the same thing I posted above, the line "wxvlc vcd:///dev/cdrom" but change it to /dev/scd0, so it's "wxvlc vcd:///dev/scd0" That should work.

---

### Post by ellalan on 2008-03-06
When I do the change as you said I the Error:
     Unable to open"wxvlc"
     Unable to open `vcd:///dev/scdO`
Thank you for trying herbster I can live without VLC.
I have gxine working for vcd, Vlc playing the dvds so I am covered.

---

### Post by LuisGMarine on 2008-03-06
> **ellalan said:**
> When I do the change as you said I the Error:
     Unable to open"wxvlc"
     Unable to open `vcd:///dev/[COLOR="Red"]**scdO`**[/COLOR]
Thank you for trying herbster I can live without VLC.
I have gxine working for vcd, Vlc playing the dvds so I am covered.


Thats a 0, as in the number ZERO, not an O like in CheriOOO's.  Try again, :lolflag:

---

### Post by herbster on 2008-03-06
Glad you got gxine working, but you are inputting the command incorrectly. Are you running one line:

```
wxvlc vcd:///dev/scd0
```

?? It surely will work, and yes it is a zero and not an "o" (oh) :)

---

### Post by ellalan on 2008-03-07
Yes it worked herbster, I have dvd and vcd playing in VLC. 
Thanx a bunch, I like your 'never give up attitude'.

---

### Post by herbster on 2008-03-08
Glad it worked ellalan, mark the thread as SOLVED :)

---

