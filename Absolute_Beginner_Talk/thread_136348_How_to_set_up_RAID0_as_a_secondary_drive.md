---
title: "How to set up RAID0 as a secondary drive?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by derspiess on 2006-02-25
I need to salvage some data from a RAID0 array (two 80GB SATA drives).  I connected them to to my secondary computer (which is running Ubuntu), but it is recognizing them as separate secondary drives.  

Is there a tool or app I can use to get Ubuntu to mount them as a single RAID0 drive, without formatting them?

FWIW, the RAID controller on the motherboard is VIA, not sure which version.

---

### Post by derspiess on 2006-02-26
After some fumbling around looking for an answer, I saw some references to dmraid.  I downloaded an .rpm file to my desktop.  Can anyone tell me how to install it?

Thanks!

---

### Post by z3r0-c0d3r on 2006-02-26
To install fist type
```
alien <file_name>
```
then it will generate a .deb file
```
sudo dpkg -i <deb_file>
```

if the first command doesnt work
```
sudo apt-get install alien
```

---

### Post by derspiess on 2006-02-26
Thanks.  I get "command not found" for alien, though.

---

### Post by z3r0-c0d3r on 2006-02-26
Like I said before
> if the first command doesnt work
```
sudo apt-get install alien
```


---

### Post by derspiess on 2006-02-26
Doh- I'm slow today.  Thanks-- that got it installed.  Now I need to read up on using it :)

---

