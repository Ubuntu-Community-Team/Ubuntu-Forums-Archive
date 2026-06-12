---
title: "After Ubuntu installation Windows CD not recognizing Hardrive"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by moragos on 2007-02-11
Hi, 
I've formatted my laptop using the Ubuntu installation and splitted the HardDrive to linux partition and NTFS partition.

Everything went great with the linux but after I finished installation - when I wanted to reinstall my Windows on my other partition the windows Boot CD did not recognize any HardDrive connected to my PC. 
I attempted to reformat and repartition in various ways and with various distributions but with no success - anything but a low level format of the drive.

any one has any idea?

---

### Post by shareMenaPeace on 2007-02-11
You could try install gparted with synaptic

System -> Administration -> Synaptic package Manager
seach for gparted and install.

Than run gparted and set NTFS partition flag for "boot".
from terminal gparted or in System -> Administration m-> Gnome partition Manager

Or run windows with vmware.

---

### Post by Madmoose on 2007-02-11
Hello, 

Is this the same issue? I have another hardrive installed that has all my files on it like .docs, .pdf, and others. When I used windows it was my backup hardrive (Slave), anyway now Ubunto isn't seeing that drive. 

I went ahead and tried to download the gparted just incase, and this is what I got:

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cairomm/libcairomm-1.0-1_1.2.0-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cairomm/libcairomm-1.0-1_1.2.0-0ubuntu1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.12.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.12.2-0ubuntu1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.10.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.10.2-0ubuntu1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.2.5-1.1ubuntu11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.2.5-1.1ubuntu11_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'


---

### Post by taurus on 2007-02-11
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all repos/lines.  Save it and run

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by Madmoose on 2007-02-11
Thanks!

That worked, but ummm where does gparted live? I can't find! it :-k 

In fact I can't find a lot of the stuff that gets downloaded...

zsnes
wine
sound card stuffs

---

### Post by taurus on 2007-02-11
Gparted is in System -> Administration.

---

### Post by Madmoose on 2007-02-11
Found it!

Thanks, now I just need to search for some other lost programs. 

Take care, 

Moose

---

### Post by moragos on 2007-02-14
Thanks for all the replies. I put the recovery disk in and recoved my Windows OS. I'll probebly ghost it down and reinstall a linux of sorts and then ghost the windows image onto it.

---

