---
title: "Did I load Ubuntu twice?? (Solved)"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by surlysteve on 2006-10-22
I finished loading ubuntu and when the grub comes up I get this.

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
 

I am a nood to linux and don't know if this is right. It appears as though there are two installs?? The install went without a hitch.
Thanks

---

### Post by divague on 2006-10-22
No you didn't.

It's ok, you have two kernel images installed, 2.6.15-26-386 and 2.6.15-27-386.

Just use the 2.6.15-27-38 which is the latest for ubuntu dapper.

If you want you can uninstall the 2.6.15-26-386 image.

---

### Post by GStubbs43 on 2006-10-22
You have two kernel images installed... You can remove the 2.6.15-26-386 one... wait for instructions because I'm going to sleep. ;)

---

### Post by aysiu on 2006-10-22
Those are just the new kernel and the old kernel--same installation.

If you don't want the old kernel any more, just boot into the new one (27) and uninstall the old one (26) by searching in Synaptic or Adept for *linux-image* and marking it to be uninstalled.

---

### Post by surlysteve on 2006-10-23
Can someone walk me through the uninstall? I have only had Ubuntu installed for about an hour now.

---

### Post by aysiu on 2006-10-23
> **surlysteve said:**
> Can someone walk me through the uninstall? I have only had Ubuntu installed for about an hour now.
Read this--you'll learn a lot about installing and removing software:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by ewl1217 on 2006-10-23
Really, there's no need to uninstall it. Unless you're cramped for disk space, there's no pressing reason to do so. All it does is just take a bit more disk space (you wont free up memory or get a performance boost from uninstalling it). Personally, I suggest that you keep it. It is there so that if, for whatever reason, you have troubles with the newer, updated kernel, that you have a back-up plan. Also, since you're unfamiliar with Ubuntu, there's always the possibility that you could mess something up (no offense, it's just something new to you). Of course, you can go ahead and uninstall it if you want, but that's just my two cents.

---

### Post by localuser on 2006-10-23
> **aysiu said:**
> Read this--you'll learn a lot about installing and removing software:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

That's a great resource.

surlysteve, you should definitely go through that document and pay close attention to the Synaptic section.  That's one of the sections that aysiu was referring to in the following

> If you don't want the old kernel any more, just boot into the new one (27) and uninstall the old one (26) by searching in Synaptic or Adept for linux-image and marking it to be uninstalled.

You can get to the Synaptic Package Manager at System | Administration | Synaptic Package Manager.  Then search for "linux-image" and you'll see all the different images that are installed.  You can remove the one(s) you don't want from there.

---

### Post by surlysteve on 2006-10-23
what package would that be under?

---

### Post by surlysteve on 2006-10-23
How can I tell which kernnel I am in right now?

---

### Post by aysiu on 2006-10-23
Paste this command in the terminal: ```
uname -r
```

---

### Post by encompass on 2006-10-23
type...
> uname -a

---

### Post by ewl1217 on 2006-10-23
To find out what kernel version you are currently using, open a terminal and enter the following command:
```
uname -r
```

**EDIT:** I must say, I've never seen a triple post like that before...

---

### Post by surlysteve on 2006-10-23
I thank everyone for their help.
That kernel is outta here!! There is quite the learning curve with linux. That seemed simple enough though:rolleyes:  
Thanks again!

---

