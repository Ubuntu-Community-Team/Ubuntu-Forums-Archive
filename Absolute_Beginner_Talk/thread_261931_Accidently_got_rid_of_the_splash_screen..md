---
title: "Accidently got rid of the splash screen."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by TwilightVampire on 2006-09-20
Ok, heres the story of my stupidity. I accidently installed one of the Kubuntu packages when updating things with the Synaptic Package Manager. This changed my splash screens to the Kubuntu ones. I managed to remove it, but it only fixed the exit screen. The starting splash was still the Kubuntu one. I attempted to fix the problem using [this]("https://help.ubuntu.com/community/USplashCustomizationHowto") how-to, but now I have no splash screens at all. Just the lovely gray-ish blue classic command line text. Any idea how to help? I tried to undo that guide when I found out what it did, but that didnt help.

---

### Post by Najand on 2006-09-20
Try to reinstall:
```

sudo aptitude install usplash

```

---

### Post by TwilightVampire on 2006-09-20
Text indicates it didnt do anything and restarting didnt do anything either.

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

---

### Post by Najand on 2006-09-20
Check it out the splash is in:
/usr/lib/usplash
(output of "ls -l" is useful.)

try to reinstall usplash again and  see the result:
```

sudo aptitude reinstall usplash

```

---

### Post by TwilightVampire on 2006-09-21
This is the output of ls -l in the /usr/lib/usplash directory.

```
total 28
lrwxrwxrwx 1 root root    36 2006-09-17 11:59 usplash-artwork.so -> /etc/alternatives/usplash-artwork.so
-rw-r--r-- 1 root root 25368 2006-05-18 02:43 usplash-default.so

```

When I go there in the file browser theres 2 files there, usplash-default.so and usplash-artwork.so.

I'll try a reinstall momentarily.

edit: Heres the output from the reinstall operation. It didnt help.

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  usplash
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upg raded.
Need to get 0B/35.8kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 83498 files and directories currently installed.)
Preparing to replace usplash 0.2-4 (using .../usplash/usplash_0.2-4_i386.deb) .. .
Unpacking replacement usplash ...
Setting up usplash (0.2-4) ...
cpio: ./usr/lib/usplash/usplash-artwork.so: No such file or directory

```

---

### Post by David Corrales on 2006-09-21
Why don't you try completely removing usplash first? As long as it doesn't uninstall a whole bunch of other stuff, you should be able to install it completely after.

---

### Post by TwilightVampire on 2006-09-21
I removed the usplash directory and then tried to reinstall usplash but I recieved the same error as before.

I think I may have accidetnly edited something the wrong way when attempting to follow that tutorial.

---

### Post by TwilightVampire on 2006-09-21
Anyone have any ideas?

---

### Post by TwilightVampire on 2006-09-21
I came up with the idea of installing the edubuntu splash screens with Synaptic to see if that would at least bring back a splash screen, but it didnt.

I've searched these forms and google for a few hours to see if theres a way to fix this and came up with nothing. And I'm afraid to expariment on my own anymore.

---

### Post by canadianwriterman on 2006-09-27
Just an idea, but check GRUB when you boot and see what the default kernel that your system boots up into. It should be 2.6.15-26.47. If there is a different version then your KDE download may have created a kernel update to the wrong kernel. It happened to me when I accidentally installed the Mepis version of Automatix and the system immediately updated to a Mepis kernel and wiped out my usplash.

---

