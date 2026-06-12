---
title: "Mount iso image on Edgy"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by apokalipto on 2006-12-01
Hi Everyone!!

Im having a problem. I want to mount an iso image. I used the following comand:

```

sudo modprobe loop
sudo mount some.iso /media/iso/ -t iso9660 -o loop

```

I made the necessary directories and everything. I get the folowing message:

```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Any Ideas on how to solve the problem?

---

### Post by agustin.g on 2006-12-01
make sure the /media/iso directory exists... the syntax seems to be wrong though... try this

```
sudo mount -t iso9660 -o loop ~/some.iso(complete path) /media/iso/ 
```

---

### Post by apokalipto on 2006-12-03
Hey thanks Agustin...

that worked fine...

but well I couldnt do what I wanted. Lets see... I have a .bin/.cue file... which I cant play with VLC nor Kaffeine. So well I thout that I could convert it to an Iso and then mount the iso Image ande then play it. But it didnt worked.

any Ideas how could I play that file??

Thanks

---

### Post by taurus on 2006-12-03
Mplayer can play .bin directly...

```
gmplayer filename.bin
```

---

### Post by po0f on 2006-12-03
apokalipto,

For generic, non-multimedia BIN/CUE pairs, there is [CDemu](http://cdemu.sourceforge.net/) as well.

---

### Post by CatKiller on 2006-12-03
Did you try [bchunk]("http://packages.ubuntu.com/edgy/otherosfs/bchunk")?

---

### Post by apokalipto on 2006-12-04
Hey thanks guys.... everything worked just fine.... I solved everything.... thanks a lot for your time..

---

