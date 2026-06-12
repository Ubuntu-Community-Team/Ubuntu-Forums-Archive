---
title: "update manager issues"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by fulcrum89 on 2008-02-27
very new to ubuntu and im having trouble searching the forums for a solution so im sorry if this is a repost. whenever i try to use the update manager it is unable to download all of the package files. it gives this error or variants of it for ever separate thing that would upgrade
> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
  302 Found [IP: 91.189.88.45 80] 

im using a sager np2090 (compal ifl90), intel core 2 duo 2.2ghz, nvidia 8600m gt, 4 gigs of ram, Built-in Intel® PRO/Wireless 496,Sound Blaster Compatible 3D Audi

thanks for any help, i appreciate it a lot.

---

### Post by jonnywombat on 2008-02-27
I clicked the link you supplied and was able to download the package manually.. then click on the file and the .deb installer will do the rest for you..

Jonny

---

### Post by fulcrum89 on 2008-02-27
i did that too, when it runs it tells me i have broken dependencies and instructs me to run 'sudo synapti' or 'sudo apt-get install -f' in the terminal. i did both of these things, both of them led to the same unable to fetch error and stuck me in the same loop.

---

### Post by jan quark on 2008-02-27
just a guess
try

```
sudo dpkg --configure -a
```

---

### Post by fulcrum89 on 2008-02-27
i tried that earlier as well when i put it in the terminal nothing happens, it just pops up with the line for me to enter in a new command.

---

