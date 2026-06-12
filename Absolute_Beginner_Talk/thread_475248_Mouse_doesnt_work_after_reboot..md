---
title: "Mouse doesnt work after reboot."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by phr0ze on 2007-06-15
My mouse (Razer Copperhead) will work fine on a cold boot. But if I do any reboot, the mouse will not work. If I unplug and replug the mouse it will start to function again. Any ideas? (This is an Ubuntu Dell, but the mouse didn't come with it.)

---

### Post by Cappy on 2007-06-16
```

gksudo gedit /etc/modules

```

Add these two lines onto the end:
```

-r usbhid
usbhid mousepoll=1

```

I'm thinking it is because usbhid isn't starting when you reboot. This code will also have the effect of increasing your mouse polling rate (makes it smoother) to the maximum your mouse supports (which is 1000hz aka 1ms).

---

### Post by phr0ze on 2007-06-16
Ohh, thanks. Maybe this will help my mouse speed problem in Unreal. I read that I have to modify the kernel to fix my UT problem.

---

### Post by phr0ze on 2007-06-16
woo hoo!!! It worked for my reboot problem. It also fixed my keyboard problem on a reboot. I used to have to type a key to 'wake' the keyboard up.

Thank You again.

---

### Post by Cappy on 2007-06-16
If someone sees this thread, don't use mousepoll=1 unless you KNOW your mouse supports it. I use mousepoll=2 because I have a G5. Setting it to 1 when your mouse doesn't support it can ruin your mouseses.

---

### Post by phr0ze on 2007-09-02
Ok, today I just installed the latest update through the update manager which appeared to be some sort of minor kernel updates. 

Now my mouse doesn't work on reboot again. I have rechecked the file edited above and the original changes are still there.

Any help would be appreciated.

---

### Post by Cappy on 2007-09-02
Well you can resume using the older kernel when booting by selecting it in GRUB.
-or-
you can try a different method here: [http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)

You can try the second method listed on the page.

---

