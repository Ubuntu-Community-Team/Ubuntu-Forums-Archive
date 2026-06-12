---
title: "problem with new VMware installation"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2007-03-03
I'd been wanting to install XP in VMware on Ubuntu, but didn't have the know-how or the disk space as I'm dual-booting...with 60Gig HD on laptop.

I came across this howto...to run the EXISTING XP installation with VMWare.

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

I installed VMware...firstly with Synaptic...then had errors...so uninstalled, and installed through Automatix, as suggested in the how-to.

All seemed to go ok...each time, and I followed the instructions in the how-to and ran the windows.vmx and got the same errors in VMWare-Player.

firstly: "Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded."

then: "Failed to initialize monitor device."

and in the terminal window: "/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)"

I'd love to be able to run Windows from within Ubuntu, for those odd programs I have to run in Windows and that I hate having to dual-boot for.

Any advice would be much appreciated.

---

### Post by ziggykg on 2007-03-05
I suggest installing VMWare by installing it from the vmware website.  I had problems with the synaptic version (not tried the Automatix version).

I'm running VMWare Server myself, which I installed from a .tar.gz file from the vmware website.  Running Windows 2000 and Windows 2000 server, which both run quite well.

---

### Post by tekpunk on 2007-03-06
i'm trying to install vmware, but i keep getting the error "unable to get the access rights of source file "./vmware-vix/bin" after i set up my directories.  anyone know why this is happening?

 oh yeah, and i checked the directory that i think it's talking about, and there's not even a /bin directory in there...so wtf???

---

### Post by mdsmedia on 2007-03-08
> **ziggykg said:**
> I suggest installing VMWare by installing it from the vmware website.  I had problems with the synaptic version (not tried the Automatix version).

I'm running VMWare Server myself, which I installed from a .tar.gz file from the vmware website.  Running Windows 2000 and Windows 2000 server, which both run quite well.Thanks ziggykg, I'll try that.

Wonderful to see that zero-reply threads are still being noticed :)

---

