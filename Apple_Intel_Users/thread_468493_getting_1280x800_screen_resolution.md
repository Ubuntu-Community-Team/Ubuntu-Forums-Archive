---
title: "getting 1280x800 screen resolution?"
date: 2007-06-08
forum: Apple Intel Users
---

### Post by LieToPurify3 on 2007-06-08
I just installed Xubuntu on my Macbook using parallels, but I only have two resolutions I can use, and one is unusable because it just makes my screen go crazy.  Is there anyway to set Xubuntu so that it can run 1280x800 resolution?  How do I do this?  If not, what would you suggest as the best resolution to use, and how do I "install" that resolution?  Thanks!

---

### Post by ronocdh on 2007-06-08
> **LieToPurify3 said:**
> I just installed Xubuntu on my Macbook using parallels, but I only have two resolutions I can use, and one is unusable because it just makes my screen go crazy.  Is there anyway to set Xubuntu so that it can run 1280x800 resolution?  How do I do this?  If not, what would you suggest as the best resolution to use, and how do I "install" that resolution?  Thanks!
I do not use Parallels, so proceed with some caution, but I believe the command you're looking for is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will allow you to set a video driver and also manually add certain resolutions. When running natively, the old MacBook Pros require the fglrx ATI driver, and the MacBooks I believe needed the 915resolution package, which can be added via Synaptic. You might want to investigate these first.

---

### Post by kzm. on 2007-06-09
more or less every tutorial starts with that:

sudo software-properties -e universe
sudo apt-get update
sudo apt-get install 915resolution

---

### Post by LieToPurify3 on 2007-06-09
When I typed in sudo software-properties -e universe, it said "sudo: software-properties: command not found
And when I typed sudo apt-get install 915 resolution, it went through a bunch of stuff and then told me that it did not work with my chipset.

---

### Post by LieToPurify3 on 2007-06-09
For ronocdh's post, what do I do after that?  Is it asking for my chipset?  I'm not sure what chipset a macbook has or if thats even what it is asking for

---

### Post by ronocdh on 2007-06-09
> **LieToPurify3 said:**
> For ronocdh's post, what do I do after that?  Is it asking for my chipset?  I'm not sure what chipset a macbook has or if thats even what it is asking for
Maybe watching [this thread]("http://ubuntuforums.org/showthread.php?t=465221") would also be beneficial for you.

---

### Post by kspn on 2007-06-24
> **ronocdh said:**
> I do not use Parallels, so proceed with some caution, but I believe the command you're looking for is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That worked Perfectly for getting my system to recognize that the screen was better than 1024x768.

I may have not been running parallels but it is simple and it worked as well as not being driver specific.

Thanks (I was setting up 1280x1024 but same difference :))

---

