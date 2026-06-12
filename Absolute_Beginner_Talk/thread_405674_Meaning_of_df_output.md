---
title: "Meaning of df output?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2007-04-10
Hi,

 I have consulted Google + these forums but I cannot work out the meaning of the output of df on my computer:

```
andrew@ilium:~$ df -m -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              38G  2.2G   33G   7% /
varrun                502M   80K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  120K  9.9M   2% /proc/bus/usb
udev                   10M  120K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm

```

/dev/hda1 is obviously by HDD but could someone help me out with the others?

                Thanks,

                    Andrew

---

### Post by justleen on 2007-04-10
to be honest, im not sure what they exactly mean.
the rest of the output is some internal OS stuff 

But the output is correct. you will always see the others /devs and /var

---

### Post by LaurelLynn on 2007-04-10
Dear andrew.46,

Those are resources for system processes.  Linux/Unix treats a lot of things such as hardware as if they were files. One common interface makes them easier for programmers to work with.

So, just because they are listed by the ¨disk free¨ program ¨df¨ does not mean that they are necessarily on a harddrive.

For example, I change the size of /dev/shm when I run the PC emulator ¨Qemu¨ so that that I can allocate 256Meg of memory for it. (defaults to 221Meg on my system).

Laurel Lynn

---

