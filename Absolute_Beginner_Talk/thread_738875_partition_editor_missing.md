---
title: "partition editor missing?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by New2Linux0319 on 2008-03-29
hi,
i have Linux 7:10 and i want to resize my partition smaller.
i originally wanted to have windows xp with 60gb and linux with 20gb (hdd total 80gb)
but somehow i got linux with 55gb...  hhmm  

so i want to resize my partition smaller and add  a /home partition.
my book says use GNOME partition editor but i cannot find it.
it is not on the drop down list. i looked all over for it
any ideas?

---

### Post by New2Linux0319 on 2008-03-29
hhhmmm,
ok, i went to synaptic package thing and download GPARTED and istalled it.
but it is taking like forever "scanning all devices"
is this normal?

---

### Post by New2Linux0319 on 2008-03-29
how do i delete my posts after i figure it out?

---

### Post by Jareth on 2008-03-29
You could mark it as solved with THREAD TOOLS at the top.

I think it does take it a while if it has to look at a large drive. I noticed one time that I had an external drive plugged in that was 250GB and that slowed it down because it wanted to scan everything plugged into it.

---

### Post by ramjet_1953 on 2008-03-29
There is not a lot of point in downloading a partition editor onto a HDD that you want to edit, as you can't re-size a drive that is mounted.

Your best bet is to download the GParted Live CD, burn it to a CD slowly as an iso image and then boot from this CD.

You can get the GParted Live CD from here:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Regards,
Roger :cool:

---

### Post by New2Linux0319 on 2008-03-29
hhmm,

yeah, now i realize that all three of these partitions (windows,swap, ext3)  have a lock symbol and it does not give the option to resize.

my book said that i could add partions later after install.   or did i read it wrong?

if i want to creat a /home partition   do i need to reinstall everything and redo the partitions from the beginning?

---

### Post by ryanhaigh on 2008-03-29
You can edit the partitions using gparted from the ubuntu livecd, because you won't have the partitions mounted you will be able to resize them and create the home partiton, this will however change the uuid of the partitions so you may need to edit/reinstall grub and change /etc/fstab. If you haven't done anything major yet then it may just be easier to reinstall, you could copy everything from your existing home folder and /etc if you want to keep any config files or data.

---

### Post by luceerose on 2008-03-29
> **New2Linux0319 said:**
> hhhmmm,
ok, i went to synaptic package thing and download GPARTED and istalled it.
but it is taking like forever "scanning all devices"
is this normal?

Gparted will hang on 'scanning all devices' if you have (for example) a floppy drive enabled in the bios but no floppy drive attached to the computer. Because it is trying to look for something that is not there.

---

### Post by New2Linux0319 on 2008-03-29
hhmm,  could not find gparted on the ubuntu live cd.  weird.   
i put the cd in,  restarted comp booted from cd.

so now i'm downloading the iso image of gpated from the link above and gonna burn it.  see what happens.

---

