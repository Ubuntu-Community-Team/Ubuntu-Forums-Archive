---
title: "LTSP root not found"
date: 2007-09-04
forum: Apple PPC Users
---

### Post by opapo on 2007-09-04
I have used the following web pages as a tutorial for how to get LTSP
to work in a mixed architecture environment:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup](https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup)
[http://elliot.ecowizards.com/wp/archives/2006/05/18/ltsp-booting-old-mac-hardware/](http://elliot.ecowizards.com/wp/archives/2006/05/18/ltsp-booting-old-mac-hardware/)

I am having problems booting the client.  It says it is "Please wait,
loading kernel" but just sits there.

My /etc/ltsp/dhcpd.conf file looks like this:

```
authoritative;

allow booting;
allow bootp;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.20 192.168.0.250;
  option domain-name "example.com";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;
#  if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
#    filename "/ltsp/i386/pxelinux.0";
#  }
#  else{
#    filename "/ltsp/i386/nbi.img";
#  }
  filename "yaboot.conf";
  option root-path "/var/lib/tftpboot/";
}

```

This is the /var/lib/tftpboot directory:

```
daniel at daniel-ubuntu:~$ ls -R /var/lib/tftpboot/
/var/lib/tftpboot/:
ltsp  yaboot  yaboot.conf

/var/lib/tftpboot/ltsp:
powerpc

/var/lib/tftpboot/ltsp/powerpc:
abi-2.6.17-10-powerpc         System.map-2.6.17-10-powerpc
config-2.6.17-10-powerpc      vmlinux
initrd.img                    vmlinux-2.6.17-10-powerpc
initrd.img-2.6.17-10-powerpc

```

And here is the /opt/ltsp/powerpc directory:

```
daniel at daniel-ubuntu:~$ ls /opt/ltsp/powerpc/
bin   cdrom  etc   initrd  media  opt   root  srv  tmp  var
boot  dev    home  lib     mnt    proc  sbin  sys  usr

```

Any help would be appreciated.
Thanks,
-Daniel

---

### Post by Kalif on 2007-09-07
Well, I am no expert in this matter, but:

in Gutsy, the root filsystem is _NOT_ mounted over NFS,
for performance reasons: reduce both boot time per client
and over all load on the server.

Accordingly you will then have to create a root image for your
client(s) to boot from with the command:

ltsp-update-image

if you, for any reason need to install any extra software
that is to be used from your clients, then you will have to
install that in your /opt/ltsp/i386 (the path may
depend both on your personal preferences and the
intended client architecture), then after you have
modded/installed the components that you want, you
will have to rebuild the image with the "ltsp-update-image"
command.

Then in you /var/lib/tftpboot/ltsp/i386 you can install
a custom lts.conf file so that you will not have to rebuild
the image every time you change your mind upon the contents
of the client configuration file. (yes, the path is dependent
on the client architecture in a similar way to how things
are named in your /opt/ltsp directory).

btw, i see that you are asking a PPC question, hence i think
you should go for /opt/ltsp/ppc and /var/lib/tftpboot/ppc
respectively, but there may be some upper-lower case
things with the spelling; unfortunately I am not running
any power pc boxes right now.

Please do not hesitate to tell us all about your progress.
Best,
K.A. Lif.

---

### Post by Kalif on 2007-09-07
sorry I see from your post that:

the path for your chroot files (for eventual further configuration,
if you want to) should be:

/opt/ltsp/powerpc/

and the path for your last minute changes for lts.conf is accordingly

/var/lib/tftboot/ltsp/powerpc/lts.conf

If you do not have any lts.conf in the later case, then the one
in your /opt/ltsp/powerpc/etc/lts.conf that existed when you
created your file system image is used.

Best,
K.

---

### Post by Kalif on 2007-09-07
Look at the following link and you will get the background on the new ltsp architecture:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWithoutNFS](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWithoutNFS)

/K.A. Lif.

---

