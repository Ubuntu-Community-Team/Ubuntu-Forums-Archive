---
title: "installing downloaded items"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by wolfx28 on 2007-08-24
hello linux community i hope to be an acctive member very soon. i have just started looking into how linux works i've had it for a while on my hard drive and now found some help from this forum site but i have some questions

i went to add/remove programs and do i install like the majority of them and can i install things i've downloaded that way or is there another way?

Wolf

---

### Post by r4ik on 2007-08-24
See,

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Welcome to Ubuntu and good luck !

---

### Post by wolfx28 on 2007-08-24
ok so if i wanted to download kdm theme manager i would type 

sudo apt-get kdmtheme

is that correct

Wolf

---

### Post by r4ik on 2007-08-24
Use,
sudo apt-get install kdmtheme

Good luck !

Without the "install" command there is no installing. :)

---

### Post by wolfx28 on 2007-08-24
ok i did that and it went all on it's own asked me if i want to use kdm and click yea then at the end it said


Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

so does that mean it dident install because it isint in my programs or do i have to type in a command to run it

---

### Post by Dirk Lately on 2007-08-24
Wolf,

I'm new to Ubuntu as well, and I find it a lot easier to select Applications -> Add/Remove... rather than the command line. However, sometimes this doesn't work: last night I tried this method with Google Earth and it didn't find it. I was able to download just fine from earth.google.com.

(However, then a .bin file appeared on my desktop, and I had to go into the command line anyway to extract it. I wonder whether there is a GUI way to do this?)

---

### Post by wolfx28 on 2007-08-24
i also tried that for another apt and got the same message at the bottom

Wolf

---

### Post by wolfx28 on 2007-08-24
how do i use the add/remove to add files i've downloaded?

Wolf

---

### Post by r4ik on 2007-08-24
Try apt-get -f install to force an install of the files that didn't get loaded.

---

### Post by r4ik on 2007-08-24
> **Dirk Lately said:**
> Wolf,

I'm new to Ubuntu as well, and I find it a lot easier to select Applications -> Add/Remove... rather than the command line. However, sometimes this doesn't work: last night I tried this method with Google Earth and it didn't find it. I was able to download just fine from earth.google.com.

(However, then a .bin file appeared on my desktop, and I had to go into the command line anyway to extract it. I wonder whether there is a GUI way to do this?)

Try,

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

No GUI sorry.

Good luck !

---

