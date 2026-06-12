---
title: "Problem with a new 8.10 install and yaboot"
date: 2009-02-08
forum: Apple Hardware Users
---

### Post by Halberca on 2009-02-08
I had 7.10 ubuntu on my g4 ibook but wanted to switch to 8.10 xubuntu. So I did a full new install but it wont fully boot up now. I think something didn't get changed right with yaboot because it flashes a few things but then the screen is blank.When I look at the boot info in yaboot. It says Boot: Linux     old. How do I change the yaboot to see the new install. Thanks in advance for any help.

---

### Post by Halberca on 2009-02-10
So I tried doing a full install again tonight and it resulted in the same error. The only boot option when I hit tab is linux old. When I type help it says that values are set to: device=/pci@F4000000/ata-6@d/disk@0:partition=3

Someone please help me on this.

I found a guide to yaboot at:
[http://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html](http://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html)
but I haven't figured out how to have it see the new install.

Thanks.

---

### Post by pxwpxw on 2009-02-10
> **Halberca said:**
> So I tried doing a full install again tonight and it resulted in the same error. The only boot option when I hit tab is linux old. When I type help it says that values are set to: device=/pci@F4000000/ata-6@d/disk@0:partition=3

Someone please help me on this.

I found a guide to yaboot at:
[http://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html](http://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html)
but I haven't figured out how to have it see the new install.

Thanks.

When you get to the yaboot screen the <TAB> shows  the two options
"linux"  and  "old"
you dont have an old kernel, so just enter at the boot: prompt
```
 
boot: linux nosplash single

```
( linux or Linux - whatever the <TAB> shows)
See where that gets to.

---

### Post by Halberca on 2009-02-15
Thanks for the nosplash single. I thought that might be the problem and I tried to do some combination of that before but it didn't work. This does.

So now I have 3 other problems:

1. I need to figure out how to modify my boot so I don't have to type in nospash every time.

2. The XFCE desktop doesn't work right. I tried the fix on ppclinux.info but couldn't get it to work.

3. The thunar file system isn't working right. Again I tried the fix on ppclinux.info but it didn't fix the problem.

Any help would be appreciated. I download the files for thunar fix but I am not sure how to run them from the desktop.

---

### Post by pxwpxw on 2009-02-15
> **Halberca said:**
> Thanks for the nosplash single. I thought that might be the problem and I tried to do some combination of that before but it didn't work. This does.

So now I have 3 other problems:

1. I need to figure out how to modify my boot so I don't have to type in nospash every time.

2. The XFCE desktop doesn't work right. I tried the fix on ppclinux.info but couldn't get it to work.

3. The thunar file system isn't working right. Again I tried the fix on ppclinux.info but it didn't fix the problem.

Any help would be appreciated. I download the files for thunar fix but I am not sure how to run them from the desktop.

Restart to get a text console in your installed system.
Make a backup copy of /etc/yaboot.conf
As root, use nano to edit /etc/yaboot.conf to add what worked from the boot screen (except 'single' unless you want to restart that way).

Then update the yaboot boot files by running, as root
```

# ybin -v

```

As for Xfce issues in 810, my solution on a G5 was to trash it and re-install ubuntu (with ubuntu-desktop). Or go back to 804.

But you will probably have to repeat all the yaboot fixups.

---

