---
title: "replace cdrom with dvdrecorder?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Horza on 2007-02-24
I installed ubuntu dapper (LTS) with a cdrom drive, but wish to replace it with a dvd recorder; if I just plug in the recorder, the old and removed cdrom appears to show up as cdrom 1, alongside of the new dvdrecorder; how do I effect complete replacement, especially removing the icon of the old cdrom?

---

### Post by mgmiller on 2007-02-24
Take a look in /etc/fstab and see if there is still an entry there for the old drive.
If there is, just comment out or delete the line, log off, restart x and log back on.  It should be gone.

First, back up the old file:
```
sudo cp /etc/fstab fstab.backup
```

Then open the file for editing:
```
sudo gedit /etc/fstab
```

Here is what my fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=5a835667-ffe7-484e-8788-88159f8ee87b / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=306fffe5-ebb4-4458-bc60-58bcb120bf28 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto  0       0


You will notice the last 2 lines refer to cdrom0 and cdrom1 (even thought they are both DVD drives)  
If you are not sure which is the one you want to remove, just put a # at the start of one of the lines, save it and see if it worked.  If not, reopen the file and put the # in front of the other one.  Putting a # at the start of a line, comments it out, so it does not execute.  Once you are sure of the one you want to remove, just delete the whole line.

After you comment out or remove the line, save the file.

Next, log off.
Next, restart x by hitting ctrl/alt/backspace

Log back in.

Should be fixed.

Edit:
You may have to restart the computer if just restarting x doesn't work.

---

### Post by Horza on 2007-02-25
My fstab has only one relevant entry, and looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm assuming that the cdrom0 is the original cdrom, no longer in the system.

commenting out the last line causes the cdrom 1 to be removed from the places|computer menu item, but I still can't mount a CD in the drive as a repository under synaptic, so presumably there's some additional step to make the drive fully functional in the system.

---

### Post by mgmiller on 2007-02-25
> I'm assuming that the cdrom0 is the original cdrom, no longer in the system.

Not true.  It only shows one optical drive attached to the second IDE controller and jumpered as the slave.  (/dev/hdd)

I would try removing the comment and then changing the the hdd to hdc.

change this:
```
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
```

to this:
```
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Then, shut off the computer, open the case and **change the jumper on the DVD drive from slave to master, making sure it is _not _on the same ide cable as your hard drive.**

Each ide controller has 1 cable with 2 drive connectors on it.

The way the letters work is:
/dev/hda is master on first ide controller (cable 1)
/dev/hdb is slave on first ide controller (cable 1)
/dev/hdc is master on second ide controller (cable 2)
/dev/hdd is slave on second ide controller (cable 2)


So your fstab is telling me you have a hard drive with 2 partions on the master of the first controller (the 2 /dev hda entries)  and one optical drive set as slave on the second ide controller (/dev/hdd)

If you have both the hard drive and the dvdrom on the same cable, then, the line for the dvd should read /dev/hdb, and the jumper should be set to slave.  (This is not the best way to do it for optimal performance)

The preferred way to do it is to have the optical drive on a seperate cable on the second ide controller jumpered as the master.

Most DVD drives ship today with the jumper set to CSL (cable select)  You need to look carefully on the back, or bottom or top of the drive near the back for the diagram that shows the different jumper settings.  Sometimes it's just engraved in the metal, sometimes it's printed on a label.  You should make sure the jumper is in the master position  (sometimes referred to as MA on the label)

I hope this isn't too confusing.

---

### Post by Horza on 2007-02-26
Yep, that did it :)  - I knew about jumpers etc in the Windoze world (where they have very little effect on anything), but forgot about how they relate to fstab.  Good explanation, in any event!

---

