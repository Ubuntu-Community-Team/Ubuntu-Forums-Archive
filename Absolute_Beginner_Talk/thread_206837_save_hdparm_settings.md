---
title: "save hdparm settings"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-30
I followed this site's directions: [http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=2), but when it gets to here:
"Be sure to add the above line (not the test line with -tT flags!) to your /etc/rc.d/* scripts once you're sure the system is stable"

How can I do that?

---

### Post by hda on 2006-06-30
You don't need that. If hdparm is installed on your system just edit your hdparm.conf. This will make sure the settings are applied to your drives on every startup.
> sudo gedit /etc/hdparm.conf
For further help type 'man hdparm.conf' or read the comments in hdparm.conf.

hth,
_hda_

---

### Post by WADemosthenes on 2006-06-30
[QUOTE=hda]You don't need that. If hdparm is installed on your system just edit your hdparm.conf. This will make sure the settings are applied to your drives on every startup.

For further help type 'man hdparm.conf' or read the comments in hdparm.conf.

hth,
_hda_[/QUOTE]
What exactly do I do to the file, do I add the lines "-c3" and "-m16" etc., becuase that didn't work :D

---

### Post by hda on 2006-06-30
Insert the following lines to set these parameters on your first IDE drive:
```
/dev/hda {
        mult_sect_io = 16
        io32_support = 3
}
```

---

### Post by WADemosthenes on 2006-06-30
[QUOTE=hda]Insert the following lines to set these parameters on your first IDE drive:
```
/dev/hda {
        mult_sect_io = 16
        io32_support = 3
}
```[/QUOTE]
sry, what about -X34, -d1, and -u1?

---

### Post by hda on 2006-06-30
You will find a near perfect description of all options if you type```
man hdparm.conf
```in a terminal window. ;-)

---

