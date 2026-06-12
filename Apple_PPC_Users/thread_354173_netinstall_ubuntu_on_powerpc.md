---
title: "netinstall ubuntu on powerpc?"
date: 2007-02-05
forum: Apple PPC Users
---

### Post by tonyr on 2007-02-05
I'm trying to figure out network installation for ubuntu.  I'm using Dapper
on a pc as the tftp server, and the target is an iMac G3/350.  The dhcp server
is a LinkSys router.  The installation media is a loop mounted alternate-powerpc
iso image of feisty/herd3.

I have gotten as far as having the first few steps of the installation dialog
succeed, but when it gets to the part about detecting the CD, the dialog fails,
because, of course, there is no CD in the drive.   I can skip that step, but then
the dialog fails to find the preseed file, and the process goes back into a loop
trying to detect the CD.

I'm not sure if this is one problem or two.  I'm pretty sure I have missed
something about specifying that there is no CD, but that the installation
source the tftp host, and I'm not sure whether solving this would affect
the yaboot.conf kernel boot parameter that specifies the preseed file
location.

What I've done so far has been cobbled together from various articles
in forums and wikis, mostly aimed at i386.  iMac netboot is started
successfully from OpenFirmware with "boot enet:<host-ip-address>,yaboot".

Any suggestions?


More detail:
1. tftp host uses xinetd in inetd_compat mode; tftp service is specified in
/etc/inted.conf

2. tftp root is /srv/tftp (tftpd installation provided that)

3. yaboot and yaboot.conf are in /srv/tftp on the host

4. the iso is loop mounted on /srv/tftp/cdrom on the host

5. So /srv/tftp looks like this:
  dr-xr-xr-x 11 root root      2048   2007-02-01    01:08 cdrom
  -r--r--r--       1 root root  153056  2006-07-25    07:02 yaboot
  -rw-r--r--     1 root root       4072 2007-02-05    11:58 yaboot.conf

6.  This yaboot.conf  got me this far.
## This yaboot.conf is for CD booting only, do not use as reference.
## Ubuntu PowerPC (feisty)

default=install


message=cdrom/install/boot.msg

# PowerPC subarch
image=cdrom/install/powerpc/vmlinux
       label=install
       alias=install-powerpc
       initrd=cdrom/install/powerpc/initrd.gz
       append="file=cdrom/preseed/ubuntu.seed quiet --"
       initrd-size=8192
       read-only

image=cdrom/install/powerpc/vmlinux
       label=expert
       alias=expert-powerpc
       initrd=cdrom/install/powerpc/initrd.gz
       append="file=cdrom/preseed/ubuntu.seed priority=low --"
       initrd-size=8192
       read-only

---

### Post by pxwpxw on 2007-02-10
The problem may be the install kernel images as well the 
yaboot.conf. I have not used the tftp install, 
and cant comment on the tftp configuration, but similar situation recently with a netboot. Netboot images give you the option to select the install package source, cd images look for a cd device.

Ubuntu Installation Guide
 4.5. Preparing Files for TFTP Net Booting.
 right down in the small print at end of page in 4.5.4:

< For net booting, use the yaboot-netboot.conf. Just rename this to yaboot.conf in the TFTP directory.> 
 (I think it means netboot/yaboot.conf)

The Guide does not say so, but you also need the netboot vmlinux and initrd.gz - get them all from:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-powerpc/current/images/powerpc/netboot/)

The install vmlinux and initrd.gz go in the same directory as yaboot and yaboot.conf, those from the cd iso are not used.

I used that configuration for a netboot installation.

---

