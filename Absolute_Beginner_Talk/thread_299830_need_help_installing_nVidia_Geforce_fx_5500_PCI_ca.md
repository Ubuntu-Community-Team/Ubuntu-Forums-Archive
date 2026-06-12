---
title: "need help installing nVidia Geforce fx 5500 PCI card in 6.10"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by ryodoan on 2006-11-14
Hi, I just downloaded and installed Ubuntu 6.10 and I have been trying to install the nVidia graphics drivers.  It is a PCI card, not PCI express.

I followed the guide [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

but when i run the command, **sudo apt-get install nvidia-glx nvidia-kernel-common**

I get the error, "Package nvidia-glx is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source."

When I went onto part two of the help, for what to do when the first part doesnt work, there was no reference to "nv" in /etc/X11/xorg.conf

I have an onboard graphics card by intel, but it is a POS and I would rather use the PCI card.  Any help would be much appreciated, thanks.

---

### Post by joshsherman on 2006-11-15
That's bizarre.  I'd attempt a ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` and try it again.

If that doesn't work you may want to use the nVidia beta drivers (they allow you to run Compiz without an Xgl server)  Great directions are available here:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA")

-j

---

### Post by dannyboy79 on 2006-11-15
first step I am sure is to update your repositories so it knows where to look, did you do this? it appears as though you didn't per the error message. check this out about updating your /etc/apt/sources.list

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
it's in section 1.4.1

good luck.

---

### Post by ryodoan on 2006-11-15
I am currently at school, so I have not gotten a chance to try updating the repositories, but I just wanted to give some more information, dunno if it really helps.

I found this site to download the package manually, but the download link is broken: [http://packages.ubuntu.com/dapper/x11/nvidia-glx](http://packages.ubuntu.com/dapper/x11/nvidia-glx)

---

### Post by dannyboy79 on 2006-11-15
i would strongly suggest NOT doing it manually, that's the whole reason that we have apt-get and or aptitude! do it correctly, update your sources.list and do the update and then the upgrade. otherwise, you're right, that link is dead, but all I did was remove the last part of it and it took me to the page with all the nvidia-glx files and much more, here ya go: [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/)

but again, I would do it the right way if you want your system to be stable etc etc. also, follow this thread to ensure you are doing this all correctly: [http://ubuntuforums.org/showthread.php?t=233241](http://ubuntuforums.org/showthread.php?t=233241)

---

### Post by ryodoan on 2006-12-17
Well, a super delayed update to anyone that might be interested.

After looking into all of the advice here in this thread I kept running into problems.  Finally I thought I was making progress, but I ended up somehow royally screwing up the drivers for the graphics in all cases and Linux wouldn't boot anymore, it kept giving me errors.

Thoroughly frustrated I just let it drop for a month or so.  Finally the call of exploration went out to me again and I decided I would do a complete reformat of my computer and do a clean install of Ubuntu 6.10.  I did that, followed the instructions again from the wiki and POOF, it works fine.

No idea why it didn't work fine earlier, but its working now, so thank you everyone for your help.

---

