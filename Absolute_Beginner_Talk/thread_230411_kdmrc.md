---
title: "kdmrc"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-08-05
After the most recent update, Synaptic said that my kdmrc had been modified by me or by a script, and did I want to keep the original or install the package maintainer's version.

I chose the former, figuring it was safer. As it is, my wallpaper has disappeared from my system, and Konqueror (as file browser) is acting funny. Maybe more is broken, I haven't explored it all yet.

I have a "differences" file, which I won't post because it's *very* long, and I can't attach it because it's an "invalid file" (too big?).

I have no idea how to read it. If I decide to install the maintainer's version later, can I? 

And I'd *really* like to get my wallpaper back. It was debian-kde_default.png which is no longer on my hard drive.

---

### Post by editrix on 2006-08-07
Anybody? I've now discovered that root's fonts are grey and blurry, although my own are fine. And I can't get new wallpapers from the Get New Wallpapers gizmo in Configure Desktop.

Also, the fonts for Gnome programs, like Synaptic, are almost as bad as root's.

---

### Post by kaveraj on 2006-08-18
```

cd /etc/kde3/kdm
ls -l

-rw-r--r-- 1 root root 21580 2006-08-03 15:42 kdmrc.dpkg-dist
-rw-r--r-- 1 root root  1490 2006-08-06 06:51 kdmrc.original


```

You should see a file kdmrc.original which is about 10 times smaller in size than the new updated kdmrc.dpkg-dist file. The file kdmrc is your current config file. You can take a backup and then 

```
mv kdmrc kdmrc.backup
cp kdmrc.original kdmrc
```

Now logout and login.. You should have your old configuration. In case you face any problem, restore the backup (using CTRL+ALT+F1 to type the commands, if the gui does n't show up).

I am not sure what your problem is, but the new config file works for me.

---

### Post by editrix on 2006-08-18
> **kaveraj said:**
> ```

cd /etc/kde3/kdm
ls -l

-rw-r--r-- 1 root root 21580 2006-08-03 15:42 kdmrc.dpkg-dist
-rw-r--r-- 1 root root  1490 2006-08-06 06:51 kdmrc.original


```

You should see a file kdmrc.original ... [/CODE]
<...>
I am not sure what your problem is, but the new config file works for me.

Thanks for the reply, kavera. I don't have a kdmrc.original. Here's the entire output:

-rw-r--r-- 1 root root   348 2006-07-05 09:33 backgroundrc
-rw-r--r-- 1 root root   181 2006-05-22 14:41 kdm.options
-rw-r--r-- 1 root root  1497 2006-07-05 09:33 kdmrc
-rw-r--r-- 1 root root 21580 2006-08-03 06:12 kdmrc.dpkg-dist
-rw-r--r-- 1 root root  1921 2006-05-22 15:48 Xaccess
-rwxr-xr-x 1 root root   484 2006-05-22 15:48 Xreset
-rwxr-xr-x 1 root root  1396 2006-08-03 06:12 Xsession
-rwxr-xr-x 1 root root   160 2006-05-22 15:48 Xsetup
-rwxr-xr-x 1 root root   643 2006-05-22 15:48 Xstartup
-rwxr-xr-x 1 root root   285 2006-05-22 15:48 Xwilling

As it turns out, I was able to fix the fonts using a tweak I found elsewhere--just change the fonts and change them back. And I got a friend of mind on Debian to send me the wallpaper.

But, it's very odd that a file like a wallpaper should have been erased.

---

