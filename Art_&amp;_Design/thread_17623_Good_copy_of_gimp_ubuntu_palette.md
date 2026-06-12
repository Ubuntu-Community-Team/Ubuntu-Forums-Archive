---
title: "Good copy of gimp ubuntu palette?"
date: 2005-03-01
forum: Art &amp; Design
---

### Post by lordofkhemenu on 2005-03-01
Anybody have a good copy of the ubuntu palette for gimp?
The [one from the Wiki](http://www.ubuntulinux.org/wiki/UbuntuArtwork/ubuntu-palette.gpl)  returns a 'magic header' error when trying to refresh the  palette list.
Or am I missing something painfully obvious?

---

### Post by uc50_ic4more on 2005-06-11
[QUOTE=lordofkhemenu]Anybody have a good copy of the ubuntu palette for gimp?
The [one from the Wiki](http://www.ubuntulinux.org/wiki/UbuntuArtwork/ubuntu-palette.gpl)  returns a 'magic header' error when trying to refresh the  palette list.
Or am I missing something painfully obvious?[/QUOTE]

I just ran into this issue, too... Anyone have any ideas?

---

### Post by kostkon on 2005-06-12
Yeah, I got the same error! Temporarily to solve the problem I've downoaded the png image version of the palette.

---

### Post by AgenT on 2005-06-12
Glad I am not the only one with this problem :???:

---

### Post by kassetra on 2005-06-12
I've fixed the ubuntu gimp palette - try the one I have attached.

The one from the site seems to have some encoding issues.

---

### Post by AgenT on 2005-06-12
[QUOTE=kassetra]I've fixed the ubuntu gimp palette - try the one I have attached.

The one from the site seems to have some encoding issues.[/QUOTE]

Imported into GIMP with ease. Thank you.

---

### Post by uc50_ic4more on 2005-06-12
[QUOTE=kassetra]I've fixed the ubuntu gimp palette - try the one I have attached.

The one from the site seems to have some encoding issues.[/QUOTE]

kassetra -

Thank you so much! Would you mind sharing with the class what you did, assuming it is not terribly complex? The error message that the GIMP had returned prior to this version said something to the effect of "does this file need to be converterted from MS-DOS?"...

---

### Post by kassetra on 2005-06-12
[QUOTE=uc50_ic4more]kassetra -

Thank you so much! Would you mind sharing with the class what you did, assuming it is not terribly complex? The error message that the GIMP had returned prior to this version said something to the effect of "does this file need to be converterted from MS-DOS?"...[/QUOTE]

Well, knowing gimp and some of it's funkier error messages, I assumed that the person had built the palette file from within a specific version/platform of gimp, possibly, and then just uploaded that file.

In order to fix it, I copied the actual palette contents in gedit, created a new file and wrote the header information myself - making sure that the "Name" field in the file and the actual file name followed the conventional gimp gpl naming schemes.

(leaving out the column info)

*poof* fixed gimp palette.

---

### Post by uc50_ic4more on 2005-06-12
[QUOTE=kassetra]*poof* fixed gimp palette.[/QUOTE]

I did notice that the original, non-functioning version had Columns=0 (or something to that effect) in it. The palettes that came with the GIMP did not have that line, so I tried removing it, but to no avail... Then I tried kicking and yelling at my computer; finally resting in a fetal position under a warm pile of blankets, figuring that the issue would resolve itself.  :)

Anyway, thank you again kassetra. The more you folks stick around bailing us out of trivial problems, the less we'll have to count on you to move the community and the OS forward!  \\:D/

---

### Post by lonetree on 2005-06-13
Hi people,

just wanna check if anyone has made py-slice work in gimp. Been searching around but seems no luck. So, has anyone of you made py-slice work with your ubuntu, I have upgraded mine to 2.2.7.

Thanks

any suggestion appreciated

---

### Post by ubuntu_demon on 2005-07-04
thnx kassetra!

---

