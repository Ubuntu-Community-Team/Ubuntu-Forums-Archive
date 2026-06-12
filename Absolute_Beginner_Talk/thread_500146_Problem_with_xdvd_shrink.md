---
title: "Problem with xdvd shrink"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-07-13
Trying to migrate from windoze to a linux  only system. Installed ubuntu a couple of weeks ago (dual boot). 
Attempted to install xdvd shrink. Converted rpm file OK, but when I tried to open xdvdshrink a message appeared telling me I was missing mjpegtools, transcode and subtitleripper. I obtained them and converted them (at least I think I converted them) from rpm to deb. Problem is that now subtitle ripper and  transcode are stuck on my desktop and tell me I don't have permission to move them or delete them. How does one do this?
Also, can find an installed xdvdshrink in synaptic, but can't migrate it to applications menu nor desktop.
Any help from knowledgable people would be much appreciated.

---

### Post by p_quarles on 2007-07-13
Re: the missing dependencies, you could try searching for those titles in Synaptic and installing them from there.

To get it in the menus, you should be able to right-click on "Applications" and choose "Edit Menus." If that doesn't work, you can always add a custom launcher there by typing in the BASH command for the application (probably "xdvdshrink").

Finally, depending on what features you need, you may be able to get by with K9Copy or DVD95. If you haven't tried those (both available via Synaptic), you might want to see if they meet your needs.

---

### Post by bumanie on 2007-07-13
I am very new to ubuntu. What is a bash command?
I will consider trying k9 or dvd 95, but really need to get these files off my desktop if it is possible to do so.

---

### Post by p_quarles on 2007-07-13
BASH is the command line interface (terminal) that is installed with Ubuntu.

I'm not exactly sure what you did to "convert" the RPMs to Debian packages, though, so if you could describe that, someone might be able to help solve the desktop issue.

In general, though, avoid manually downloading anything you want to install until you are more familiar with the system. The Synaptic Package Manager works very well, and has just about anything you might want to install.

---

### Post by bumanie on 2007-07-13
I converted rpm to deb files with alien. 
The reason I wanted xdvdshrink was because it worked well under windoze. I guess I am fairly ambitious and don't mind trying things - unfortunately this did not work.
Also, anyone know how to get rid of shrink? I will give native programs a go first. Only learnt they existed last night.

---

### Post by p_quarles on 2007-07-13
You said it's listed in Synaptic, right? You can mark it for uninstallation there.

As for the files on your desktop, you might be able to delete them normally after you uninstall shrink. If it still doesn't work, you can open a terminal and type ```
gksudo nautilus
```

In the new Nautilus window, look for the "desktop" folder in your home directory, and then delete them. Just be sure to close this window after you finish. 

Note: I'm assuming you're running the default edition of Ubuntu. If you're using Kubuntu or Xubuntu the command would be different.

---

### Post by bumanie on 2007-07-13
Thanks I will try that. Hopefully it will work. I am using the default ubuntu.
I did uninstall through synaptic but still could not remove the desktop items, so i re-enabled it. Didn't know about getting into desktop programs with nautilus at that point. Presently am at work so can't try until later.

---

### Post by SyberKowboy on 2007-07-13
Right click on the desktop and run the the script "root-nautilus-here" and then you can delete what ever you want. DVD backup was a critical thing for me when I switched and K9 copy is one of the best programs I've found. Works beautifully.  Plus I think there are deb packages for xdvd shrink in Synaptic and under Add/Remove under the Applications menu.

---

### Post by p_quarles on 2007-07-13
I looked, and didn't find it in Synaptic (all the normal repos + Medibuntu enabled). If you have it, would you mind letting me know what repo it's in?

---

### Post by bumanie on 2007-07-13
I will let you know where it is. I am at work at present. Won't be home for another 2hours or so. 
I think it is only in synaptic due to the work I did converting the rpm to deb file with alien. I did a search in synaptic when I could not find it in add/remove and it came up with a green square indicating it was installed, but as I said I suspect it is there only because of the rpm file conversion. Anything I have read indicates there is no debian xdvd shrink package, that is why it gets compiled via rpm files.

---

### Post by p_quarles on 2007-07-13
@bumanie: Actually, that question was intended for SyberKowboy. He said he thought it was in one of the repositories, and I was just wondering which one. You have the file in Synaptic only because you installed it manually.

Good luck getting everything to work. 

By the way, K9Copy is absolutely all you need if you just want to copy shrink a disk image so that you can back it up. DVDShrink offers other features, like copying selected chapters or audio tracks, but if you don't need all that, the native app will be good.

---

### Post by bumanie on 2007-07-13
Xdvdshrink is in a section named "converted from rpm by alien." It is clear that is the only reason I have xdvdshrink is due to the conversion, Anyway I will try what you have suggested.

---

### Post by bumanie on 2007-07-13
Thanks p_quarles that worked. I uninstalled xdvdshrink, plus mjpegtools, transcode and subtitleripper. Now everything is back to  normal as far as I can tell.
Thanks again.

---

### Post by bumanie on 2007-07-13
Should have added that I will try the native applications. Didn't use shrink much anyway, I guess when I read it was available on linux, I looked for it as it was familiar. From now on I will check out native applications first. Thanks again for your help. In the meantime I will keep trying things out. Hopefully I won't get into too many problems again. I will try k9copy and see what else ubuntu has re native apps. that are similar.

---

