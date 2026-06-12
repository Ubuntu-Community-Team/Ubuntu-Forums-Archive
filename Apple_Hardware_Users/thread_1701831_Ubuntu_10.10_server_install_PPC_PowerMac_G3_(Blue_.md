---
title: "Ubuntu 10.10 server install PPC PowerMac G3 (Blue and white)"
date: 2011-03-07
forum: Apple Hardware Users
---

### Post by tallthom on 2011-03-07
(Actually very *faded* blue and white G3, but still going!)

Currently running 8.04.1 server.  Wanted to upgrade to a newer LTS or even 10.10 (new php/mysql etc).  The install disk doesn't seem to contain the old IDE driver for my G3.  

During the install when it tries to detect the disk drive, it comes up with a list of drivers from which I must choose.  None appear to be the correct driver.  Rebooting back to 8.04.1, I do an LSMOD to show the loaded modules:

```
thomw@eorl:~$ lsmod
Module                  Size  Used by
iptable_filter          3136  0
ip_tables              15624  1 iptable_filter
x_tables               17604  1 ip_tables
ipv6                  311048  12
snd_powermac           50336  0
snd_pcm                87844  1 snd_powermac
snd_timer              26820  1 snd_pcm
snd                    70612  3 snd_powermac,snd_pcm,snd_timer
soundcore               9028  1 snd
snd_page_alloc         12040  1 snd_pcm
loop                   22116  0
pmac_zilog             21448  0
serial_core            25600  1 pmac_zilog
af_packet              26052  2
pcilynx                21384  0
ieee1394              108864  1 pcilynx
evdev                  14400  0
ext3                  163304  1
jbd                    57716  1 ext3
mbcache                 9632  1 ext3
usbhid                 35748  0
hid                    48420  1 usbhid
***ide_disk               19872  3***
generic                 4804  0 [permanent]
cmd64x                 11516  0 [permanent]
ide_floppy             22560  0
ide_cd                 36996  0
cdrom                  47196  1 ide_cd
bmac                   17744  0
mesh                   26492  0
***ata_generic             8324  0***
ehci_hcd               42572  0
ohci_hcd               40976  0
libata                182776  1 ata_generic
usbcore               174088  4 usbhid,ehci_hcd,ohci_hcd
scsi_mod              193108  2 mesh,libata
windfarm_core          14544  0
fuse                   57684  1
```

Any ideas how I can proceed?

---

### Post by linuxopjemac on 2011-03-07
This is a known problem for years which Ubuntu does not want to address. The problem is that the kernel which Ubuntu uses has no module for your type of drive. It's really amazing how simple to solve this is and the lack of interest from Ubuntu. That's for me the reason I don't do Ubuntu on PPC anymore. I recommend Debian Squeeze, it will install without all this hassle.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131)

workaround:
[http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0](http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0)

---

### Post by tallthom on 2011-03-07
Well, I guess that explains it.  Thanks for your response.

---

### Post by viper250 on 2011-03-08
also debian will give you a better server in the long run.
debian uses a text based installer but is very easy to use.

---

### Post by tallthom on 2011-03-08
> also debian will give you a better server in the long run.
debian uses a text based installer but is very easy to use. 

Thanks for your response.  I don't have a problem with the text-based installer (actually Ubuntu uses the same one with a few less options unless you enable the expert mode).  

I just like how Ubuntu decides a few of the security options for me for example not allowing root to have a password and so on.  I'm not the most technical guy, so playing around under the hood is something I try not to do too much of with regard to the operating system and security.

One thing I like is that when I install Webmin on Ubuntu, the users are already configured by default.  In Debian, I've got to step through some hoops* to get the Webmin user and login user to work properly.  That worries me because I'm never sure if I've opened up something of a security hole when I touch Webmin configuration files.

I do like the Debian "simple server" approach, though.  If I don't need it it isn't installed by default.  I'll keep studying...  thanks again for your response.

-T

*hoops - If I have no root password defined, then I can't log in to Webmin even with my authorized user.  The user isn't a member of the right groups or something I've not yet figured out just yet. I will keep checking the forums.

---

