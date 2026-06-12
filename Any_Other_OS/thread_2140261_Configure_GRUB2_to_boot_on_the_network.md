---
title: "Configure GRUB2 to boot on the network"
date: 2013-04-29
forum: Any Other OS
---

### Post by sb19 on 2013-04-29
Hi,

I'm Looking for a way to configure grub2 to boot on the network.
I've already done the way by installing a dhcp server , a tftp server and it works fine when I choose to boot on the network card.

Now I want to add an entry in my grub.cfg  which says to boot on the network.

In fact when I boot on normal mode I want an entry which says "Reboot on the network"

I think the following link shows what I want to do but it does not work for grub2

[http://wiki.linuxmce.org/index.php/GRUB_PXE_network_boot#Configure_GRUB_to_boot_from_the_network](http://wiki.linuxmce.org/index.php/GRUB_PXE_network_boot#Configure_GRUB_to_boot_from_the_network)

for example the dhcp command is not available.



Thx for your help

---

### Post by oldfred on 2013-04-29
I have not done it, but grub2 has lots of pxe commands.

[URL="https://www.gnu.org/software/grub/manual/grub.html#Network"]https://www.gnu.org/software/grub/manual/grub.html#Network

[http://wiki.osdev.org/Diskless_Booting](http://wiki.osdev.org/Diskless_Booting)
[/URL]

---

### Post by sb19 on 2013-04-30
Thx,
Ok I'll try it soon.

i just have download [http://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz](http://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz) to understand how the directories lib/ bin/ share/ ...are made.
i'm executing the following commands : ./configure --prefix=/tmp/grub/ ; make ; make install and in  /tmp/grub/ there are all the directories.
When I check in lib/grub/i386-pc/ there are some *.mod and *.module
I don't understand what are these *.module because if I check on my PC in /usr/lib/grub/i386-pc there are only the *.mod

I'm looking at this because when I execute grub-mkimage which generate a core.0 for the pxe boot it only work if I do it from /usr/lib/grub/i386-pc.

---

### Post by sb19 on 2013-05-02
I do not have the net_pxe commands only some net_commands like for example net_ls_dns.
This command only works when i've already boot on the netcard. (net_ls_dns returns the adress of the dhcp server)

---

### Post by sb19 on 2013-05-02
Ok I do have the net_pxe variables only if I boot on the network card, not if I boot on the disk which seems logical

---

