---
title: "Why Won't It Install?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-09-26
I have a daa file that i need to unzip, but, to do so i need to install a program called acetone ([http://www.acetoneteam.org](http://www.acetoneteam.org)). I downloaded the .deb file, but whenever i try installing it, it says that libqt 4-core is not satisfiable. When i check in synaptic, though, it says that libqt 4-core has been installed. Is there a work around for this or a suitable alternative?

---

### Post by reckless2k2 on 2007-09-26
it probably means that version on the machine currently is not high enough...ie...you have version 3 and it requires version 5. you'll have to look into it a little farther.

---

### Post by reckless2k2 on 2007-09-26
hhmm..i just looked and there's a fiesty deb for this program so it should work out of box. what version of ubuntu are you running?

there's 2 versions, have you tried them both?

---

### Post by intense.ego on 2007-09-26
I'm running feisty so it should work.

---

### Post by wpshooter on 2007-09-26
Have you checked to see if the Acetone program is available in Synaptic for installation ?

---

### Post by intense.ego on 2007-09-26
no acetone is not on synaptic. should i try a version designed for a previous release of ubuntu?

---

### Post by Majorix on 2007-09-26
Try poweriso instead. They are the masters of .daa. It has a linux executable available for download.

Download that, extract it to /usr/bin or some similar folder which is in your $PATH variable (echo $PATH to see whats on there) and then run it.

I used it with my previous Feisty installation and it worked fine.

From their site:
> PowerISO for Linux -- This is a free utility for linux which can extract, list, and convert image files (including ISO, BIN, DAA, and other formats).  Type " poweriso -? " for detailed usage information.  File Size: 286KB

So you know you have to type
```
poweriso -?
```
to get usage information.

Hope it helps.

---

### Post by intense.ego on 2007-09-26
thanks for the help. i'm going to install poweriso right now

---

### Post by intense.ego on 2007-09-26
when i try extracting the file there, it says that i do not have permission to write to the folder. i found out that only root can do that. so, how do i use root?

---

### Post by intense.ego on 2007-09-26
I've managed to get the exe file into the /usr/bin folder, but can't open it.

---

### Post by mcduck on 2007-09-26
> **intense.ego said:**
> I've managed to get the exe file into the /usr/bin folder, but can't open it.

You just downloaded the Windows version instead of the Linux version.. Linux doesn't run .exe files.

On the bottom of PowerISO's download page there's the Linux version, in a -tar.gz package. Download that and extract it into correct place.

---

### Post by crjackson on 2007-09-26
> **mcduck said:**
> You just downloaded the Windows version instead of the Linux version.. Linux doesn't run .exe files.

On the bottom of PowerISO's download page there's the Linux version, in a -tar.gz package. Download that and extract it into correct place.

Is this a GUI or only cli for Linux?

---

### Post by mcduck on 2007-09-26
I've never tried it, but it looks like CLI only.

But the instructions seem simple enough, and if needed it should be pretty trivial to create a nautilus action to use it without opening a terminal..

---

### Post by Majorix on 2007-09-27
```
sudo poweriso -?
```

---

### Post by intense.ego on 2007-09-28
does anyone have any idea of what to do?

---

