---
title: "The location is not a folder."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by AuToFiRE on 2007-09-25
Has anyone got this error before and how do i solve it?    (im so sorry for being such a n00b)

---

### Post by lisati on 2007-09-25
What were you trying to do when you got the error?

---

### Post by Dr Small on 2007-09-25
Use cat instead of cd...

---

### Post by AuToFiRE on 2007-09-25
im getting the error on the desktop for  instance:

Couldn't display "/home/omega/Desktop/ati-driv...staller-8.40.4-x86.x86_64.run".

The location is not a folder.

---

### Post by Maestro23 on 2007-09-25
> **AuToFiRE said:**
> im getting the error on the desktop for  instance:

Couldn't display "/home/omega/Desktop/ati-driv...staller-8.40.4-x86.x86_64.run".

The location is not a folder.

Navigate to your Desktop:

> cd /home/omega/Desktop

then

ls (lists all files on Dekstop)

Then you can install the driver.

---

### Post by aktiwers on 2007-09-25
Its not a folder..
To install open terminal and type:
```
cd /home/omega/Desktop/
```
```
sudo ./ati-driv...staller-8.40.4-x86.x86_64.run
```

Remember to change the .run files name to the real one

---

### Post by AuToFiRE on 2007-09-25
ok i will try that i just find it weird that when i double click things it does that

---

### Post by antofthy on 2008-01-14
I just had the same thing happen to me.  Though I have used Ubuntu, I was not using that system at this time, but using Fedora Core 8.  In any case the solution will probably be the equivelent to what I did.

Basically something stuffed up the meta-data for nautilus, and it is a real pain.  So I downloaded the nautilus package and re-installed it, and after a logout and in all was fine.

For Fedora (redhat type) systems I installed a RPM package using
    rpm -Uhv --replacepkgs nautilus-2.20.0-6.fc8.i386.rpm

The version number was the same as what was installed previously.  BUt it fixed the problem for the new login, even when reboots previously didn't.

Nautilus is crappy as it stuff up regularly, this was the simplist fix I have yet to find, and it did not involve wiping out my gnome setup!

---

