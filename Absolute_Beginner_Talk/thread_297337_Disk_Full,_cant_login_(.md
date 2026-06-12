---
title: "Disk Full, cant login :("
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by online14230 on 2006-11-11
Hi there. I broke Ubuntu. Again :(

This time, i was a bit trigger happy, with the trigger being Synaptics Apply button :(

I installed very many apps, and games, and oh well .. everything. Then I shutdown. Then I startup. Then I cant login cos It says it cant write to my x-config (Im sure its that one) file. Now, I have JUST re-installed, because of problems with dbus system not starting, which results in HAL not starting. Wasnt getting much help, so I reinstalled. Incidentally, I have the repositories on DVDs... a great many of them, so its not a problem re-installing (I have to download wine again, though). Any ideas how I can get into the system without installing from scratch ... again? Ive tried recovery mode AND just booting into console. nothing. Please help me here... Im lost.
one more thing: this Ububox has no connection to the internet. I have Kubuntu (installed from DVD, Mandriva 2006(from DVD) and Ubuntu (from shipit) installed. The DVDs I got from the Freedom toaster. Dont ask.

---

### Post by HareBall on 2006-11-11
Check out this thread. [http://ubuntuforums.org/showthread.php?t=282805](http://ubuntuforums.org/showthread.php?t=282805)
I hosed my desktop and this is what I did to get it back.

---

### Post by online14230 on 2006-11-11
Thanks Hareball, but thats not it. Ive been there, done that. This time, Ive installed too many apps, and its filled up the HDD. Thats why it wont let me in. No space to write log files. What Id like to know is, how do I fix it? I cant even log in!!!
B.

---

### Post by warbread on 2006-11-11
I recently had this problem on my laptop.  The way I solved the problem was to log in under command line (interrupt GRUB and tell Ubuntu to boot in recovery mode), logged in from there and then type in

```
cd /var/cache/apt/
```

```
sudo rm *.deb
```

Note that there is **not** a space in between * and .deb!

All of the .deb files in that folder are redundant and you don't need them and they're unnecessary.  Deleting them will give you plenty of space.

---

### Post by pandu.rs on 2006-11-11
```
cd /var/cache/apt/
```

It should have been

cd /var/cache/apt/archives

---

### Post by online14230 on 2006-11-15
Thank You so much people, it was a MAJOR help. I knew therre was a cache that I could clean out, but I didnt know where to find it... Mandriva searched on the Ubuntu partition but couldnt find it. I have Ubuntu up and running again, no problem.

Once again, thank you...

---

