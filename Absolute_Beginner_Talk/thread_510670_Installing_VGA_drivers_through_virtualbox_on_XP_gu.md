---
title: "Installing VGA drivers through virtualbox on XP guest"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Bazirker on 2007-07-26
OK there are a million threads on using VirtualBox but I haven't found one that helps yet...

I got VirtualBox going with Windows XP Pro as a guest on my laptop (specs in sig.)  Everything is awesome (can't wait to delete my XP partition off my hard drive and run straight Ubuntu) but I can't get my VGA drivers to install, and as a result I'm stuck with crappy resolution and doubt I can get any games running without the VGA drivers and the ATI drivers that will follow.  Has anyone else experienced this and could they fix it?

---

### Post by felicity on 2007-07-26
As far as I know, it's not possible to install the drivers in the guest because the virtual machine software is emulating all the hardware itself. And playing games through a virtual machine, that doesn't sound like it would work very well to me. But I don't know much about this stuff, perhaps someone else with more knowledge will be able to help more.

---

### Post by be4truth on 2007-07-26
> **bodhi.zazen said:**
> Yes. First install the so called addons (Install the addons on the guest OS NOT THE HOST).

Then in a terminal :

```
VBoxManage controlvm "Guest" setvideomodehint "1440" "900" "24"
```


Where :

[list][*]"Guest" is the name of the Guest OS.
[*]"1440" and "900" are the desired resolution.
[*]"24" is the desired color depth (8,16,24)[/list]

For further information : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Did you see this thread?

[http://ubuntuforums.org/showthread.php?t=372285]("http://ubuntuforums.org/showthread.php?t=372285")

---

