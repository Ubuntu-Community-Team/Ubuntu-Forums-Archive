---
title: "[SOLVED] Netboot install on Dell PowerVault 725N"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by dstew on 2008-02-07
*After languishing 24 hours on the Installation and Updates forum with no replies, I am re-starting this thread here. Any comments/mocking/non-profane abuse appreciated.*

My son pulled this beast out of a dumpster. It is a "headless" NAS (network-associated storage) device. It actually works, and from the BIOS I can tell it has 2 GB RAM and 4 x 120 Gb IDE drives that seem OK. The current OS is Windows Server 2003, but I am locked out by password protection.

I want to try a netboot installation of Ubuntu using its BIOS PXE facility. It has no floppy drive or connector, no CD-ROM or connector, and apparently cannot boot from its USB ports. I have looked at HowTos for doing this type of installation, and am basically ready to go. I am going to use my Ubuntu desktop as the netboot server.

Does anybody have any experience with this kind of installation, or with this particular machine? Thanks.

---

### Post by wiseguyxp on 2008-02-07
[Here]("http://www.debian-administration.org/articles/478") is a good place to go to figure out how to install the proper servers and do the setup.  Basically, you download and install a tftp server and dhcp server, then set them to access certain files in the /var/lib/tftpboot directory (could be different depending on programs).  I use tftpd-hpa and dhcp3-server and it works great.

---

### Post by dstew on 2008-02-08
Thanks wiseguyxp. That link looks excellent. I am looking at all the various HowTos and am getting a good idea of what to do. I am planning to use dhcp3-server and tftpd-hpa as you suggest. I will post my progress here. Thanks again.

---

### Post by dstew on 2008-02-10
I was successful! The Netboot installation went without a hitch. I used these three pages to figure out the setup:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[http://www.debian-administration.org/articles/478](http://www.debian-administration.org/articles/478)
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

I installed dhcp3-server and added this to the /etc/dhcp3/dhcpd.conf file:```
subnet 192.168.2.0 netmask 255.255.255.0 {
        range 192.168.2.100 192.168.2.200;
        filename "pxelinux.0";
        next-server 192.168.2.101;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.2.255;
        option routers 192.168.2.1;
}
```I set my Ubuntu machine to use the static IP address 192.168.2.101, with the subnet mask and gateway as above (routers = gateway) using the Network graphical tool. I disabled the DHCP service on my router, and made sure I could get on the internet, and made sure my Ubuntu dhcp server was providing IP addresses to computers on my network.

I installed tftpd-hpa, tftp-hpa, and xinetd as directed. I checked to see if the directories and binaries were in the places they were supposed to be.

I downloaded the Feisty netboot archive netboot.tar.gz and unpacked into /var/lib/tftpboot directory using```
sudo tar -xvzf netboot.tar.gz -C /var/lib/tftpboot/
```Then changed ownership permissions with```
sudo chown -R nobody:nogroup /var/lib/tftpboot
```The PXE configuration is already done for you in the netboot package.

I entered a text file named tftp into /etc/xinet.d as directed. File contents were```
service tftp
  {
        disable                 = no
        socket_type             = dgram
        wait                    = yes
        user                    = root
        server                  = /usr/sbin/in.tftpd
        server_args             = -v -s /var/lib/tftpboot
        only_from   = 172.31.0.240/28
        interface   = 172.31.0.252
  }
```I doubt this step was essential, because I entered the text as shown. However, my subnet was 192.168.2.0, so the last two lines did not match my subnet. I planned to change them to my subnet numbers, but I forgot, and it worked anyway. Two of the three How-Tos do not have you put in these addresses. One has you put in the other aguments (disable to server_args) Two of the How-Tos have you edit the file /etc/default/tftpd-hpa to change RUN_DAEMON from "no" to "yes". I did this.```
#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"
```I think this last step probably overrides the changes made in /etc/xinet.d/tftp, but I didn't do the experiments to see.

After this was set-up, I attached the PowerVault 725N to the network router. I made sure the services xinet, tftp-hpa and dhcp3-server were running (System --> Administration --> Services), then powered on the PowerVault. I got into the BIOS using F2 (found the service manual on-line) and set it to do a Re-Install Boot. In a minute the Ubuntu logo appeared, with menu choices for what kind of system to install. I picked Server, and it installed in the same fashion as the Alternate Install CD does, with a text-based interface. It got all the packages over the internet. It took about an hour. The only problem I had was that I could not get the partitioner to designate a swap partition, but I set aside unallocated space to do this later. After installation, I rebooted, went to the BIOS screen, picked Normal Boot, and got the grub menu. The system booted fine.

---

