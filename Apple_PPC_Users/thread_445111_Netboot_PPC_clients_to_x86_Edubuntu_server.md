---
title: "Netboot PPC clients to x86 Edubuntu server?"
date: 2007-05-15
forum: Apple PPC Users
---

### Post by RudeIota on 2007-05-15
I've read this is possible. Using the information I've found on the net, I've mangled something together that hasn't worked for me yet.

The gist of it is I have a working LTSP Edubuntu server that boots PCs just fine. I installed Edubuntu on a PPC iMac and managed to ltsp-build-client over to the server... So I now have a 
"powerpc" directory in conjunction with my existing i386 arch directory in /opt/ltsp.

Next I configured /etc/ltsp/dhcpd.conf and it looks something like this at the moment:```

authoritative;

allow booting;
allow bootp;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.50 192.168.0.99;
  option domain-name "local";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;

  filename "yaboot";
  option root-path "192.168.0.254:/opt/ltsp/powerpc";
  }
```

The point where I'm out now is the iMac (clent) gets an IP address via BOOTP or DHCP, but it will not boot. Holding the "N" key does not work. Using Open Firmware (Apple Option O F) When I try things like boot enet: 192.168.0.1,yaboot it does not boot either, although I know it doing something since my network monitor jumps on the Edubuntu server at the exact moment I hit the enter key.

 I assume I have misconfigured something and since I don't understand the DHCPD.conf file as much as I should, maybe someone out there has some tips, resources or answers? Thanks in advance. :)

---

### Post by stmiller on 2007-05-15
I'm sure you've seen these links, but just in case:

[http://wiki.ppckernel.org/w/Mac_Netboot](http://wiki.ppckernel.org/w/Mac_Netboot)

[https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/26426](https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/26426)

And you'll have to have a yaboot.conf that looks something like

image = enet:vmlinux
label = linux
initrd = enet:ramdisk.image.gz
initrd-size = 8192

The debian ppc list archive might have more posts on this.

---

### Post by RudeIota on 2007-05-30
Thank you for the information above... Some progress (I think) has been made.

Config info:
[LIST]
[*]The Edubuntu server is 7.04. 
[*]The iMac being used is a DV400 (Indigo blue).
[*]I'm attempting to use the built-in LTSP software.
[*]iMac is connected with a PC privately, via a switch. The Edubuntu server is acting as a bootp/DHCP server.
[/LIST]

When I enter open firmware and type "boot enet:192.168.0.254,yaboot" I now get the error message (character for character):
```
CLIENT: 003065daa662
SERVER: 000f1fc93453
Transfer FILE: yaboot
TFTP ERROR response 1 File not foundload-size=0 adler32=1



LOAD-SIZE is too small
ok

```

I'm going to do some more investigative research, but I thought I'd drop this here in case anyone can identify or help me troubleshoot this sort of error. Thanks again. :)

---

### Post by RudeIota on 2007-05-31
Anyone care to share their ideas? Even the most trivial or unlikely ideas may be of great help to me.

The information I've found hasn't helped me... yet... It seems I keep getting this error and I'm unsure how to troubleshoot it. I'm relatively inexperienced with Linux (and especially ltsp.org), so it makes things all the more difficult to figure out. :)

If anyone can post the details of their *working* x86 server / ppc client configuration, that might be really helpful as well. Useful information would include any config files involved with LTSP (/etc/ltsp/dhcpd.conf, /opt/ltsp/powerpc/yaboot.conf, /etc/exports and so on...)

---

### Post by stmiller on 2007-05-31
If this is a critical situation where you are using ubuntu in a classroom, you might try contacting the official Canonical support line:

[http://www.canonical.com/support/webtolead](http://www.canonical.com/support/webtolead)

---

### Post by RudeIota on 2007-06-03
Thank you for the link. I'm waiting to hear back from someone and if I find a solution, I will post it here.

In the meantime.... It appears I'm one step closer!

I reset the PRAM and NVRAM on the iMac DV400 I'm using for testing and it now loads yaboot... sort of. It gets past the gray OF screen and displays a black screen with white text. The error message I *now* is
```
CLIENT: 003065daa662
SERVER: 00145111c630
Transfer FILE: yaboot.conf
TFTP ERROR response 1 File not foundError, can't read config file
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information

boot:

```

Any tips on why the yaboot.conf cannot be found/read?

---

### Post by Matty K on 2007-06-07
> **RudeIota said:**
> 
When I enter open firmware and type "boot enet:192.168.0.254,yaboot" I now get the error message (character for character):
```
CLIENT: 003065daa662
SERVER: 000f1fc93453
Transfer FILE: yaboot
TFTP ERROR response 1 File not foundload-size=0 adler32=1



LOAD-SIZE is too small
ok

```


Im stuck at that point there, I dont know how you cleared the PMEM etc as you described above, they annoying thing is there is no tftpd log file to watch or a config file for tftpd...

using a iMac G3 DV (Basicly same as you to build from, and have succesfully built the ltsp tree over NFS from a Live CD)

Im just stuck at this point, it looks more like either tftpd aint responding right, or the MAC is nt asking correctly!

---

### Post by RudeIota on 2007-06-07
> I dont know how you cleared the PMEM etc as you described aboveIf it helps anyone, at the open firmware prompt I typed```
http://docs.info.apple.com/article.html?artnum=42642

reset-nvram
reset-all

```
Additionally, I held down Option + Apple + P + R afterwards to clear the PRAM in case the above doesn't do that. Instead of typing reset-nvram etc.. you can also continue holding down the buttons to make the computer restart continually. After 3 times, both of the NVRAM and PRAM should be reset.

I'm assuming the issue I have now is one of configuration, since there's no longer a TFTP error. The error claims there's an issue reading my yaboot.conf.

---

### Post by jmlunning on 2007-07-02
Hi Rudelota,

Your yaboot.conf file cannot be found because the "ltsp-build-client" command puts it in the wrong directory by default.  Make a copy of it and put it in the root tftp directory.

sudo cp /var/lib/tftpboot/ltsp/powerpc/yaboot.conf /var/lib/tftpboot/yaboot.conf

I then had to remove the boot splash screen so I could see what was going on during boot-up.  Comment out the append="quiet splash" from the yaboot.conf file.

This was helpful because I had an nfs error during boot-up and had to add the entry below to /etc/exports and restart the nfs daemon on the server (sudo /etc/init.d/nfs-kernel-server restart) to get things working.

/opt/ltsp       *(ro,no_root_squash,async)


I hope this helps.

-Justin

---

