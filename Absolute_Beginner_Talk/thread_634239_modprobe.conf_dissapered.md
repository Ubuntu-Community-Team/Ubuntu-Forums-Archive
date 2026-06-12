---
title: "modprobe.conf dissapered"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by funky_beak on 2007-12-07
Odd as this may sound and a likely case of fat fingers, i seem to have lost the original version of modprobe.conf. ```
find / - name modprobe.conf
``` nor```
 slocate modprobe.conf
``` find the ******* file.  

I had successfully configured my TV card to use the correct tuner and card by setting the appropriate parameters and was feeling quite smug.  My TV card worked from login with no command line effort.  A few days weeks? passed a few scheduled managed  updates later my TV card no longer works.

Oh i think what where those settings i stored in modprobe.conf, god knows cos its disappeared!!  I cannot think where its gone, I have not compiled or tried  anything quite so ambitious and i expect it'll remain a mystery.

Where can i get the version that shipped with feisty, to restore the settings i had?  there seemed to be quite alot in there.

Also mysql now cannot connect to its socket and although i haven't tried fixing this i suspect it may be todo with this problem as i did have mysql running as i dabbled with myth TV and got it working.

Are these issues related ? Where do i get the original?  any ideas?

---

### Post by p_quarles on 2007-12-07
I'm not sure how much help I can offer here, since I don't have a TV tuner myself, but I can explain the modprobe.conf thing. Ubuntu 7.10 doesn't use such a file. Instead, it stores the information in the files in /etc/modprobe.d/ -- these files work exactly the same way as modprobe.conf. 

Additionally, modprobe.conf/modprobe.d don't actually controls the modules that are loaded, but control the behavior of the modprobe command. The module settings are stored in /etc/modules. 

If you know the name of the module that drives the TV card, you should be able to find a reference to it in /etc/modprobe.d/ and work from there. 

Hopefully someone who uses a TV card will see this, though, and provide a more definitive answer.

---

### Post by funky_beak on 2007-12-08
mmm OK, thanks for that but now that begs the question what actully loads the kernel modules on bootlup.  i'd assumed that there was a load of modprobes in some start up script which took its behaviour from modprobe.conf.  Which definitely used to exist.  My TV card uses the Saa7134 chipset and the V4l drivers do work with it.

This is the annoying thing is that it was all hunkydory...

However ive grepped in /etc/modprobe.d and there nothing pertaining to saa7134 (i guess that this is the problem) i can probs work out what the .conf for the saa7134 driver should contain, you'd think that as the saa7134 driver is loader (according to dmesg) that it woul already have created a default setup.

I wish i'd spelt disappeared correctly!

thanks for you input, im none the wiser!  I guess i need to do more reading.....

---

### Post by p_quarles on 2007-12-08
Well, like I said, it's the file /etc/modules that actually loads the modules at boot time. The modprobe command loads them manually, on a session-by-session basis. If you can find the exact name of the module, you should simply be able to add it to /etc/modules, and it will run when you boot.

---

### Post by funky_beak on 2007-12-10
Ah got it!! Ive put the correct command line arguments in /etc/modules against the desired module and hey presto, would you believe it it works.!!!  Slowly the mist clears.  Thanks for your help,  Now on to  amarok and mysql !!

---

