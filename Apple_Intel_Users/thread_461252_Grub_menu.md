---
title: "Grub menu"
date: 2007-06-01
forum: Apple Intel Users
---

### Post by andrewbossie on 2007-06-01
i have a mac book core duo and was wondering if you could edit what kernel grub boots into. i dont want to use the latest kernel ( .16), i want to use .15. every time i want to boot i have to go into the grub menu and select the desired kernel manually, is there a was to maybe take the undesired kernel off the menu or set which kernel to boot?

---

### Post by buschi on 2007-06-01
> **andrewbossie said:**
> ... edit what kernel grub boots into...

that's done in /boot/grub/menu.lst

sebastian.

---

### Post by pbw on 2007-06-01
Sure, just take a look at /boot/grub/menu.lst and either remove the latest kernel from the list or set the other one to be default.

Better fix to what you'd like however, is to put your kernel version on hold so it doesnt get upgraded automatically on you again in the future.

just remove the newer kernel and run ```
echo kernelpackage hold | dpkg --set-selections
```

And if later you'd like to have it auto upgrade when there is a newer kernel release, just run ```

echo kernelpackage install | dpkg --set-selections
```

--pbw

---

### Post by mority on 2007-06-01
Yeah, just edit the file /boot/grub/menu.lst.

There you have for every kernel installed on your system lines like this:

```

title   Ubuntu, kernel 2.6.20-16-386
root    (hd0,4)
kernel    /boot/vmlinuz-2.6.20-16-386 root=UUID=d39fc2f5-0df4-4728-9eec-de5942d3b370 ro quiet splash
initrd    /boot/initrd.img-2.6.20-16-386
savedefault

title   Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root    (hd0,4)
kernel    /boot/vmlinuz-2.6.20-16-386 root=UUID=d39fc2f5-0df4-4728-9eec-de5942d3b370 ro single
initrd    /boot/initrd.img-2.6.20-16-386

```
You can remove the lines for the kernel you don't want to boot.

And at the top of the file you have one line saying:
```

default   0

```

The number is saying that (in this case) the first entry should be default.

In Ubuntu, the file is pretty good commented, so just read the comments for more information.

Hope that helps :)

---

### Post by andrewbossie on 2007-06-01
thank you al or your help!!

---

### Post by ivesjd on 2007-06-01
You dont have to remove them either, you can just put a "#" in front of the line and that will comment it out.

---

### Post by Dougie187 on 2007-06-01
Yeah I would suggest not removing them. Just incase you ever need to get into it later.

---

### Post by pbw on 2007-06-01
Honestly, i dont see why he should even need to touch grub. It's good to know how, but as i said in the above post - Just remove the new kernel package you dont want and put the one you do want on hold. Simple. Then it wont update on you, you wont have to bother in the future, and you don't have a fairly big package on your system that you aren't going to use.

---

### Post by ronocdh on 2007-06-01
> **pbw said:**
> Honestly, i dont see why he should even need to touch grub. It's good to know how, but as i said in the above post - Just remove the new kernel package you dont want and put the one you do want on hold. Simple. Then it wont update on you, you wont have to bother in the future, and you don't have a fairly big package on your system that you aren't going to use.
Tsk tsk, don't criticize one's preference for configuration! That's what Linux is all about, no? Anyway, I think the primary motivation to edit the GRUB list is that by commenting out the "undesirable" kernels, he can sample different builds and revert to a previous one in case anything goes wrong. Also, he can edit the countdown timer on the boot screen. Isn't that handy? :D

---

### Post by pbw on 2007-06-01
If you know you don't want a certain kernel, then why keep it on your system. That makes no sense at all - that's why i'm criticizing, i'm by no means criticizing keeping multiple kernels on a machine to be able to fall back on, or to test out. That'd make me hypocritical since i have 3 atm.

I didn't say to remove his previous one(s), i said to remove the newer one he stated he doesnt even want to use.

Thanks for the countdown timer tip..

-- pbw

---

### Post by eldepeche on 2007-06-09
The problem seems to be more with the "linux-image" metapackage being installed by default. I've read a ton of stories about problems with kernel upgrades that were completely unnecessary, but done automatically. Why does Ubuntu do this?

---

### Post by mority on 2007-06-10
> **eldepeche said:**
> The problem seems to be more with the "linux-image" metapackage being installed by default. I've read a ton of stories about problems with kernel upgrades that were completely unnecessary, but done automatically. Why does Ubuntu do this?

Example?

---

### Post by eldepeche on 2007-06-10
> **mority said:**
> Example?

[This thread](http://ubuntuforums.org/showthread.php?t=469557&highlight=kernel), and [this one](http://ubuntuforums.org/showthread.php?t=468525) linked in it.

Unless there are security flaws in the last kernel release, it wasn't necessary for most users to upgrade, but Ubuntu is set up to do it by default.

---

### Post by mority on 2007-06-11
Well, that's just a guess: Let's say the current kernel has a serious bug (maybe even security related) but this bug only occurs on ThinkPads for example. Should the kernel maintainers now let the many ThinkPad users alone because they don't want to bother the rest of Ubuntu users with a kernel update?

You can always pin your kernel version via /etc/apt/preferences. That's what I did on one of my Debian systems where I don't want to install kernel updates:
```

gort:~# cat /etc/apt/preferences 
Package: linux-image-2.6.18-4-k7
Pin: version 2.6.18.dfsg.1-12
Pin-Priority: 1000 

Package: linux-headers-2.6.18-4
Pin: version 2.6.18.dfsg.1-12
Pin-Priority: 1000 

Package: linux-headers-2.6.18-4-k7
Pin: version 2.6.18.dfsg.1-12
Pin-Priority: 1000 

```In Ubuntu it's working the same way. You'll find more info on how to use pinning in the [APT Howto]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin").

Cheers.

---

