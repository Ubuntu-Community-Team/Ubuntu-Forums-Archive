---
title: "GCC missing"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by CurlyBlue on 2006-08-31
Hi

can anyone help me

Am in the process of installing a HP 2600n Color Laserjet and when I try and run make I get the following:

#
# Dependencies...
#
      ***
      *** Error: cc is not installed!
      ***
      *** Install Software Development (gcc) package
      ***:confused: 
make: *** [all-test] Error 1

Any ideas how I fix / resolve this.

Thanks

---

### Post by jpeddicord on 2006-08-31
Install the package build-essential. You can do this from System > Administration > Synaptic, or you can type```
sudo apt-get install build-essential
```in the terminal.

---

### Post by spin2cool on 2006-08-31
I can't remember if build-essential includes gcc as a dependency.  If not, also do 

```

sudo apt-get install gcc

```

---

