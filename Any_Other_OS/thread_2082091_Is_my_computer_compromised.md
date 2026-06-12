---
title: "Is my computer compromised?"
date: 2012-11-08
forum: Any Other OS
---

### Post by Henzor on 2012-11-08
On my computer I've had random input from mouse (movement), keyboard (up, down, left, right) and scroll (haven't got a mouse with scroll so its a bit weird). I use Linux Mint (don't like the Unity interface, but its basically ubuntu) so I don't get the regular update reminder I used to get using ubuntu and it had been a long time since last update. After the update I decided to check with RootKit Hunter and I got a few warnings:

```
[14:52:36] Info: Starting test name 'filesystem'
[14:52:36] Performing filesystem checks
[14:52:36] Info: SCAN_MODE_DEV set to 'THOROUGH'
[14:52:36]   Checking /dev for suspicious file types         [ Warning ]
[14:52:36] Warning: Suspicious file types found in /dev:
[14:52:36]          /dev/.udev/rules.d/root.rules: ASCII text
[14:52:36]   Checking for hidden files and directories       [ Warning ]
[14:52:37] Warning: Hidden directory found: '/etc/.java'
[14:52:37] Warning: Hidden directory found: '/dev/.udev'
[14:52:37] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
```

So I wonder if I still got viruses and if I could get an advise of how to fix it?

---

### Post by Soul-Sing on 2012-11-08
would you please take a look at this documentation: [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)
And "run" rkhunter again.

---

### Post by teward on 2012-11-08
> ```
[14:52:36] Warning: Suspicious file types found in /dev:
[14:52:36]          /dev/.udev/rules.d/root.rules: ASCII text
[14:52:37] Warning: Hidden directory found: '/dev/.udev'
```

These can be ignored, most if not all Ubuntu systems have that hidden directory.  The data inside that directory is therefore to be ignored, because the /dev/.udev directory is included in the "What to Ignore" list.

> ```
[14:52:37] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
```
This one should also be fine, that's a common one I see on a lot of Ubuntu systems.

> ```
[14:52:37] Warning: Hidden directory found: '/etc/.java'
```
I've not checked my system, but that may be a problem directory.  I"ll get back to you about this dir, i'm checking on Ubuntu 12.04.

And mint is not Ubuntu by the way.  Sorry, have to say it.  It may be a derivative, but its not truly Ubuntu.

---

### Post by nothingspecial on 2012-11-08
*Thread moved to **Other OS/Distro Talk**.*

---

