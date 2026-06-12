---
title: "Battle with Drivers"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by TheNetStrider on 2006-09-05
Hi, I have a question :confused: ...

I've been trying to install my nVidia drivers (which I've downloaded the latest one from nVidia's site). I've done this numerous times in Suse, but can't seem to get it right in Ubuntu. My main problem ](*,) is that I can't get into "super-user / init 3" mode to install the driver. I've tried everything. Ctrl+Alt+F1 / gdm stop and so-on. But everytime I run "sh NVIDIA.... -q" it tells me that X-server is still running. Which it is NOT.

How dow I go about installing the nVidia driver, could someone PLEASE help!!! Without it, I can't use XGL and Cedega...

Thanks

---

### Post by jd65pl on 2006-09-05
You could try booting your system in recovery mode so X doesn't start. I dont have an nVidia graphics card so couldn't help more than that.

---

### Post by yota on 2006-09-05
Hi,

the nvidia drivers are in the ubuntu repositories (search for nvidia-glx package), so you don't have to download them unless you absolutely need the latest&greatest version.
Once installed nvidia-glx run this command to enable the driver:
```

sudo nvidia-glx-config enable

```

If the driver in the repositories doesn't suit your needs look at these threads on how to install latest.

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

Finally if you want to go to single user mode do a:
```

init 1

```
or boot selecting "recovery mode" from the boot loader list (eventually press esc to see it).

Hope this helps!

---

