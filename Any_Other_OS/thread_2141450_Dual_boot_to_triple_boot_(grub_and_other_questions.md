---
title: "Dual boot to triple boot (grub and other questions)"
date: 2013-05-02
forum: Any Other OS
---

### Post by cincinnatus13 on 2013-05-02
So I've researched a bit and found a few threads...
[http://ubuntuforums.org/showthread.php?t=2127821&highlight=triple+boot+grub](http://ubuntuforums.org/showthread.php?t=2127821&highlight=triple+boot+grub)
[http://ubuntuforums.org/showthread.php?t=2006475&highlight=triple+boot+grub](http://ubuntuforums.org/showthread.php?t=2006475&highlight=triple+boot+grub)
[http://ubuntuforums.org/showthread.php?t=2132112&highlight=triple+boot+grub](http://ubuntuforums.org/showthread.php?t=2132112&highlight=triple+boot+grub)
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Right now my 128GB SSD has Windows 7 (~60GB) and Ubuntu 12.10 Gnome (about the same size) on it. I'm looking to one- probably upgrade to the new Ubuntu LTS or some other Linux distro.
That makes my first question- when I install the new OS over top of that (formatting all the Linux partitions to start fresh of course) will it prompt me to update the GRUB menu?
Second, I'd like to (after that) do a triple boot with OpenELEC on the side. It'd be small and when formatting the partitions for the above, I'd clear out a smaller partition for this. This again leads me to wonder if OpenELEC has an option to automatically append itself to GRUB or if I will have to go into the other Linux and add it manually. It's not a big deal but I am not exactly clear on where I'd add it and what it would have to point to to boot up OpenELEC.

The reason for all of this is that it is a travel laptop along with an HTPC when I'm not traveling. It is much easier and lighter on the system (an old Dell i3) to have OpenELEC and remove all that unnecessary overhead when just using it as an HTPC.
Thanks in advance for any help. Mainly it's just the GRUB modifying that is making me pause before doing all of this.

---

### Post by oldfred on 2013-05-02
When you install a new system it installs grub2's boot loader to the MBR and runs os-prober to find all other systems to add to the grub menu.
If installing to existing partitions and you have backed up everything you want to save including a list of installed apps and all of /home, you just use manual install or Something Else and choose the existing partition as / (root) and format as ext4. It will auto find an existing swap.

Do not know about openElec. Some give options on where to install grub and the option not to install. Ubuntu does not give an option not to install and the only thing you can do if you want another system to be in charge of booting is to choose to put grub2's boot loader in the PBR or partition boot sector as a throw away or not to be used. Never install grub to  a NTFS partition's PBR as that has to have Windows.

---

### Post by cincinnatus13 on 2013-05-03
Thanks for the advice. As a caution to others, OpenELEC seems very different with regards to installation. Normal Linux distros at least give you a warning and then a custom install option but OpenELEC just merely will write over everything (at least it would have for me.) Custom install only lets you select a different device.
I happened to find this link- [http://blog.jordanhopfner.com/2013/01/10/triple-boot-windows-7-linux-openelec/](http://blog.jordanhopfner.com/2013/01/10/triple-boot-windows-7-linux-openelec/) which helped immensely. Followed the instructions on that and it worked like a charm. Just make sure to set your hd0,* and /dev/sda* partitions correctly to your computer.

Thanks again. Hope this helps someone in the future.

---

