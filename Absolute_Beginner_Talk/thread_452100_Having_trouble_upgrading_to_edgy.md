---
title: "Having trouble upgrading to edgy"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by etotehpii on 2007-05-23
I'm getting the following error when trying to upgrade to edgy.

 Failed to fetch [http://metascape.afraid.org:13666/apt/dists/sid/main/binary-i386/Packages.gz](http://metascape.afraid.org:13666/apt/dists/sid/main/binary-i386/Packages.gz) 301 Moved Permanently

This is after I run

```
gksudo "update-manager -c"
```  

and click to update to edgy.

I also can't even check if I'm updated as when I check for the verison under system>about ubuntu I get this error message.

Could not launch menu item

Details: Failed to execute child process "yelp" (No such file or directory)

Can do I an upgrade via cd?

Thanks

---

### Post by ronocdh on 2007-05-23
I'm sorry if it's discouraging, or even off-topic, but I always do version upgrades by reinstalling from a CD. It's only once every six months, which to me is totally reasonable, but I've just had too much trouble trying to actively update without reinstalling from a disc. On top of that, I usually use the alternate installer discs, FWIW.

---

### Post by etotehpii on 2007-05-23
> **ronocdh said:**
> I'm sorry if it's discouraging, or even off-topic, but I always do version upgrades by reinstalling from a CD. It's only once every six months, which to me is totally reasonable, but I've just had too much trouble trying to actively update without reinstalling from a disc. On top of that, I usually use the alternate installer discs, FWIW.

As in just installing over my current Ubuntu partition?

I have no problem doing that, if no other solution presents itself.

Thanks

---

### Post by Ek0nomik on 2007-05-23
I personally do a clean install myself.

What you can do is boot up the Live CD or Alternate CD and delete the partitions than create new ones, and install from there.  If you backup your important information, it will be hassle free.  But, you can continue to look for a solution if you wish.  ;)

---

### Post by etotehpii on 2007-05-23
The one gripe I just remember with a fresh install is gmail and Thundarbird.

I'll need to go through the process of setting that up again?

---

### Post by Ek0nomik on 2007-05-23
You can backup your Thunderbird account and put it on a USB Thumbstick or an FTP Server or whatever it is you do.

~/.mozilla-thunderbird

Inside there is probably a   xx123xx.default   folder or something.  That is what you will want to backup your profile.  Than upon the fresh install, you can port over that folder, or if you have troubles jut download Thunderbird Profile Manager and it can handle it for you.

---

### Post by Roasted on 2007-05-23
Question for those of us who dual boot in regards to upgrading distros...

You folks say installing from the CD is the best option. Okay fine. But the rule of thumb is to install linux after windows. Okay fine. That's what we're doing, right? Would doing so make any changes to grub? Should windows freely boot without issues after doing a full distro upgrade to linux?

And for the record, what if windows failed and you had to reinstall. Would you be screwed in reinstalling linux after the new windows re-install?

---

