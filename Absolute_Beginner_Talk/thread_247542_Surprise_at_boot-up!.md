---
title: "Surprise at boot-up!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-08-30
Everything was working OK last night. I shut down as usual, and it went as usual. When I booted up this morning, I got nowhere...
```


Uncompressing Linux... Ok Booting the kernel 
mount: Mounting /root/sda1 /root failed: No such device 
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory mount: 
Mounting /sys /root/sys failed: No such file or directory mount: 
Mounting /pro /root/pro failed: No such file or directory 
Target filesystem doesn't have /sbin/init 

Busybox v1.01 (debian 1:1.01-4ubuntu3) Built-in shell (ash) 
Enter 'help' for a list of built-in commands /bin/sh:
can't access tty; job control turned off
#
```

I have a Dell Lattitude C610.
Edit:
I searched on some of the keywords here, but didn't find anything that worked. I found the exact same code, but his issue was fixed in a way that had no effect on my system?!? (see post #4 for details.)

---

### Post by AntiFlash on 2006-08-30
is your SATA disk showing up in the BIOS?  I have had issues with my SATA drive not getting detected there after which it will not be detected by Linux...

---

### Post by Papa-san on 2006-08-30
When I go into my bios, I can only select time and date. I cannot go 'down' to my drives, etc. So I don't know...

I'm running in a 'live' state right now, and "Places --> Computer:
It shows up there, but I cannot mount it.

---

### Post by Papa-san on 2006-08-30
I tried:
```
sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev
```

Results:
```
Fetched 60B in 1s (33B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
udev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/#

```

What happens if I re-install?

---

### Post by Papa-san on 2006-08-31
Is there a way to re-install that won't overwrite my info?

Help, PLEASE!

---

### Post by Dramist on 2006-08-31
Why is it when one user gets an error everyone else starts to get it..

Add me to the list of pissed off not mounting..

The thing that pisses me off most is i didnt have a camera.. I wrote all that on the inside of an unfolded box of goldfish...

EDIT: MY error is similar but different enough to have a different solution. will start new thread

---

### Post by Papa-san on 2006-08-31
The only thing I can figure is that something happened with the last update I did. Everything was perfect. I got the little icon on the top taskbar letting me know there was an update. Everything went OK for the rest of the night. When I turned it back on the next morning, my error showed up. I didn't do anything different, and I didn't install anything else. Just the update.

---

### Post by Carbonfish on 2006-08-31
Hi,

This may or may not be helpful, but I had a boot problem right after the update yesterday as well. The thing that may have saved me is that just by chance my machine auto-ran fsck (due to the 30 boot cycle thing) when I restarted immediately after the update. While I had some problems that required some fiddling, everything now works.

Question. Are you able to boot to a console and manually run fsck?

Again, I don't know if that would help or not and if I am getting my foot close to my mouth, I am confident that someone will jump in.

KC

---

### Post by Papa-san on 2006-08-31
I can only get to the busybox shell. I don't know if that is a console or not. I also wouldn't know how to run it from there. (What the commands would be)Since it isn't finding the hd, I don't know if I can make any changes from there.

---

### Post by Carbonfish on 2006-08-31
Do you have a prompt? If so, try:

fsck

and hit return.

If you have no prompt, I am not sure.

KC

---

### Post by Papa-san on 2006-08-31
Rats... Nothing. When I tried to boot again, it gave me error after error, then I got the splash screen. Entered my user and pw. Kept bumping me back to splash. I played this game about five times and decided I need to re-install it again.

This is the last opportunity I have to save my data, If someone can help, I would like it please! LOL

---

### Post by Sterkenburg on 2006-08-31
Edit: Hahaha...  I'm stupid.

---

### Post by Carbonfish on 2006-08-31
Sorry Papa-san,

I'm afraid that's the only suggestion that I had in me.
I hope that somebody comes along who has your answer, and that you are able to save your data.

KC

---

### Post by Papa-san on 2006-09-01
Hey,
Thanks for at least trying!

I went ahead and re-installed. No resolution to this problem was found...

---

