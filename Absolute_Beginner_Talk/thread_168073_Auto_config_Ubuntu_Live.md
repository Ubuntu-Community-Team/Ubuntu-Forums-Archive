---
title: "Auto config Ubuntu Live"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Stuperfied on 2006-04-29
Ok, continuing from here "http://www.ubuntuforums.org/showthread.php?t=167694" so far I have this:
```
#!/bin/sh
sudo mkdir /media/hda1
sudo mount /dev/hda1 -t vfat -o iocharset=utf8,umask=000 /media/hda1
sudo mkdir /media/hda5
sudo mount /dev/hda5 -t vfat -o iocharset=utf8,umask=000 /media/hda5
sudo unzip /media/hda5/temp/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb.zip -d /home/ubuntu/
sudo dpkg -i /home/ubuntu/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb y Australia vera.hurt@gmail.com FREE

```
I have set it up here as a fat file system but I will have to get someone to show me how to make that NTFS instead. Also, I have just tacked the parrameters onto the end of the dpkg command that I want to pass to the driver installation to give you an idea of what I want to happen.

This script hopefully will also configure the LAN, Internet connection and printer but so far, I get stuck here. Can anyone help me with the rest of it or at least point me in the right direction please? Your help is most appreciated.

---

### Post by cilynx on 2006-04-29
To mount an NTFS partition instead of FAT32, make sure hda1 and hda5 are NTFS partitions and change 'vfat' to 'ntfs' in your mount lines.

As for the module params, install the module package as you have and then do a 
"modprobe hsfmodem y Australia [email]vera.hurt@gmail.com[/email] FREE" or something close to it.

---

### Post by yager on 2006-04-29
[QUOTE=Stuperfied]sudo mkdir /media/hda1
sudo mount /dev/hda1 -t vfat -o iocharset=utf8,umask=000 /media/hda1
sudo mkdir /media/hda5
sudo mount /dev/hda5 -t vfat -o iocharset=utf8,umask=000 /media/hda5
[/QUOTE]

In case I get this wrong, here is the source.
[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

Change the above to this.
```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1 ntfs ro,nls=utf8,umask=0222 0 0
sudo mkdir /media/hda5
sudo mount /dev/hda5 /media/hda5 ntfs ro,nls=utf8,umask=0222 0 0
```

This is read only as NTFS is not officially supported for Read/Write.  If you want write, You can go to this link but watch the warning.

[https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28fuse%29%7C%28ntfs%29](https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28fuse%29%7C%28ntfs%29)

---

### Post by Stuperfied on 2006-04-29
Thanks yager, this is in a script so do I still need the -o? and could you explain that in a little more detail please cilynx? Do you mean.

```
#!/bin/sh
sudo mkdir /media/hda1
sudo mount /dev/hda1 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda1
sudo mkdir /media/hda5
sudo mount /dev/hda5 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda5
sudo unzip /media/hda5/temp/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb.zip -d /home/ubuntu/
sudo dpkg -i /home/ubuntu/hsfmodem_7.47.00.00full_k2.6.12_9_386_ubuntu_i386.deb
sudo modprobe hsfmodem y Australia vera.hurt@gmail.com FREE

```

Is this correct or do I put it all on the same line or something? I dont really know that much about dpkg and your mentioning modprobe just now is the first ive heard of it.

Edit: Oh, I see yager, your thinking fstab file, this is a script im putting on a floppy, I think when you use the mount command, you need to specify parrameters like -o for options and -t for type.

---

### Post by cilynx on 2006-04-29
-t is the switch for what type of filesystem you're mounting
-o tells "mount" that you're going to pass some options
ro means "read only"
nsl=utf8 means to use the utf8 character set (this is safe)
You should do a little research on umask.  It's a little more complex than I can explain in a one-liner.
Your script looks good to me, having not run it.
"modprobe" is the module loader.  "dpkg" installs the actual file that is the module.  "modprobe" loads it into the kernel.  The options for the module get passed to modprobe as it's actually doing the work.
Your line separation in the script is fine.

---

### Post by Stuperfied on 2006-04-29
Ok, cool. So we now have a script which 'should because its untested' mount her drives and install her modem driver for her. Can we now tell it to configure her LAN and Internet connection? Does anyone know how to do that?

---

### Post by yager on 2006-04-29
[QUOTE=Stuperfied]Does anyone know how to do that?[/QUOTE] You are really going to pull this off!!! 

I found this page.  It talks about the HSF driver about 1/2 way down the page.  It is not very friendly toward this driver and implies that the smart-link drivers may support some modems that this driver supports.  It also states that if you don't buy the license, you max out at 14.4k.

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Here is some additional info that may also be helpful.  Sorry I can't help with the modem.  I have not had to play with a modem for years now.  Cable is great at 3MB/s.

[http://xlife.zuavra.net/columns/20021104/#drivers](http://xlife.zuavra.net/columns/20021104/#drivers)

---

### Post by Stuperfied on 2006-04-30
Was there ever any doubt. ;) :P 
Thanks for the links, im reading them now, they have already come in usefull with helping me refine my scripts. I will make all materials available if and when I get it done.

```
#!/bin/sh
sudo mkdir /media/hda1
sudo mount /dev/hda1 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda1
sudo mkdir /media/hda5
sudo mount /dev/hda5 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda5
sudo unzip /media/hda5/temp/hsfmodem_*.deb.zip -d /home/ubuntu/
sudo dpkg --install /home/ubuntu/hsfmodem_*.deb
sudo hsfconfig -a
```

My floppy drive light wont go off and it doesnt seem to be updating the contents. Maybe I mounted it wrong, anyone know the correct format for mounting a floppy drive?

---

### Post by cilynx on 2006-04-30
What kind of LAN / Internet connection are we looking at?

As for the floppy:
```

sudo mount /dev/fd0 /floppy
sudo cp whatever /floppy
sudo umount /floppy

```
wait for the light to go out before taking out the disk.  It can take a while as floppies are slow

---

### Post by Stuperfied on 2006-04-30
2 computers, home network.
host Brezy Ubuntu Dial-Up 192.168.0.1
guest WinXP via switch (dont know IP, not needed anyways)


```
ubuntu@ubuntu:/$ sudo umount /media/floppy0
ubuntu@ubuntu:/$ sudo mount /dev/fd0 /floppy
mount: you must specify the filesystem type
ubuntu@ubuntu:/$ sudo mount /dev/fd0 -t vfat -o rw,user,auto,umask=000 /media/floppy0
ubuntu@ubuntu:/$ 
```

problem:
open floppy0 in file browser - works, light comes on then off, contents displayed.
eject disk and insert another - no light, contents unchanged.
reload - no light, contents unchanged.
wait for a while - light comes on, stays on.
reload - contents dissapear.
close and re-open file browser - drive remains on clicks once, contents unchanged.
reload - no effect, light still on.
wait - light stays on.

---

### Post by cilynx on 2006-04-30
You can't switch disks with the device mounted.  It's the disk you're mounting, not the drive.

Put in disk
Mount disk
Copy stuff to disk
Unmount disk
Wait for light to go off
Take out disk
Be happy

As for your network, you're going to need something along the lines of dnsmasq and some way to put a hole in your iptables firewall to let masq through.  You can find a simple, insecure iptables script for masq here:

[http://www.wolfteck.com/~rcw/upscript-iptables]("http://www.wolfteck.com/~rcw/upscript-iptables")

---

### Post by Stuperfied on 2006-04-30
Ok, I downloaded the file "dnsmasq-2.30.tar.gz". What are the shell commands to install it?

---

### Post by Stuperfied on 2006-04-30
I have gone ahead and tried to do it myself, I hope this is correct.
```
#!/bin/sh

sudo mkdir /media/hda1
sudo mount /dev/hda1 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda1
sudo mkdir /media/hda5
sudo mount /dev/hda5 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda5
sudo unzip /media/hda5/temp/hsfmodem_*.deb.zip -d /home/ubuntu/
sudo dpkg --install /home/ubuntu/hsfmodem_*.deb
sudo hsfconfig -a
sudo dpkg --install /media/floppy/pmount_*.deb
sudo cp /media/hda5/temp/dnsmasq-*.gz /home/ubuntu
sudo gunzip /home/ubuntu/dnsmasq-*.gz
tar -xvf dnsmasq-*.tar
make install dnsmasq-*

MODPROBE=/sbin/modprobe
IPTABLES=/sbin/iptables
DEPMOD=/sbin/depmod
EXTIF="ppp0"
INTIF="eth1"

echo -e "\n\nLoading firewall script...\n"

echo -en "   loading modules: "
echo "  - Verifying kernel module deps..."
$DEPMOD -a

echo "----------------------------------------------------------"

# Main IPTABLES module
echo -en "ip_tables, "
$MODPROBE ip_tables

# Stateful connection tracking framework
echo -en "ip_conntrack, "
$MODPROBE ip_conntrack

# FTP connection tracking
echo -en "ip_conntrack_ftp, "
$MODPROBE ip_conntrack_ftp

# IPTABLES NAT
echo -en "iptables_nat, "
$MODPROBE iptables_nat

# FTP NAT
echo -en "ip_nat_ftp, "
$MODPROBE ip_nat_ftp


echo "----------------------------------------------------------"


echo "   enabling forwarding..."
echo "1" > /proc/sys/net/ipv4/ip_forward

echo "   clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -t nat -F

echo "   FWD: Allow all connections OUT and only existing and related ones IN"
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG

echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

echo -e "firewall script complete."

```

---

### Post by Stuperfied on 2006-04-30
Latest update, still dont know how to install dnsmasq, any help would be appreciated. Also, the dpkg command is auto running the modems config file after install and hence prompting the user for input. Is there a way to stop that or to at least pass the parameters to it automatically?

```

#!/bin/sh

echo "--- Mounting Hard Disk Partitions ---"
mkdir /media/hda1
mount /dev/hda1 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda1
mkdir /media/hda5
mount /dev/hda5 -t ntfs -o ro,nls=utf8,umask=0222 /media/hda5

echo "--- Installing Modem Drivers ---"
unzip /media/hda5/temp/hsfmodem_*.deb.zip -d /home/ubuntu/
dpkg --install /home/ubuntu/hsfmodem_*.deb

echo "--- Updating Mount Modules ---"
dpkg --install /media/hda5/temp/pmount_*.deb

echo "--- Installing dnsmasq ---"
cp /media/hda5/temp/dnsmasq-*.gz /home/ubuntu
gunzip /home/ubuntu/dnsmasq-*.gz
tar -xvf dnsmasq-*.tar
# install /home/ubuntu/dnsmasq-*

# echo "--- Configuring Network ---"
# MODPROBE=/sbin/modprobe
# IPTABLES=/sbin/iptables
# DEPMOD=/sbin/depmod
# EXTIF="ppp0"
# INTIF="eth1"

# echo -e "\n\nLoading firewall script...\n"

# echo -en "   loading modules: "
# echo "  - Verifying kernel module deps..."
# $DEPMOD -a

# echo "----------------------------------------------------------"

# Main IPTABLES module
# echo -en "ip_tables, "
# $MODPROBE ip_tables

# Stateful connection tracking framework
# echo -en "ip_conntrack, "
# $MODPROBE ip_conntrack

# FTP connection tracking
# echo -en "ip_conntrack_ftp, "
# $MODPROBE ip_conntrack_ftp

# IPTABLES NAT
# echo -en "iptables_nat, "
# $MODPROBE iptables_nat

# FTP NAT
# echo -en "ip_nat_ftp, "
# $MODPROBE ip_nat_ftp


# echo "----------------------------------------------------------"


# echo "   enabling forwarding..."
# echo "1" > /proc/sys/net/ipv4/ip_forward

# echo "   clearing any existing rules and setting default policy.."
# $IPTABLES -P INPUT ACCEPT
# $IPTABLES -F INPUT 
# $IPTABLES -P OUTPUT ACCEPT
# $IPTABLES -F OUTPUT 
# $IPTABLES -P FORWARD DROP
# $IPTABLES -F FORWARD 
# $IPTABLES -t nat -F

# echo "   FWD: Allow all connections OUT and only existing and related ones IN"
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
# $IPTABLES -A FORWARD -i $EXTIF -o $INTIF -j ACCEPT
# $IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
# $IPTABLES -A FORWARD -j LOG

# echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
# $IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

# echo -e "firewall script complete."

```

---

### Post by cilynx on 2006-04-30
The easiest way to install dnsmasq on a Debian-based system (such as Ubuntu) is:
```

sudo apt-get install dnsmasq

```
As an aside, you should be able to do the same with the modem drivers as opposed to having the .deb on hand.

What are you using the pmount*.deb for?

As for the firewall script, make sure the INTIF and EXTIF are set to your internal and external network interfaces.  They may be right as-is, just be sure.  Also, pretty much everything in that firewall scripts needs to be done sudo.

On your mount lines for the ntfs partitions, I would get rid of the umask option and just let it use the default.

---

### Post by Stuperfied on 2006-04-30
Does apt-get download the packages off the net? It is an easier way of installing them and I thank you for mentioning it. However, if it does need to download them off the net first then I couldnt use it for the modem driver because I cant get online without it. As for pmount*.deb, check the following post, it should explain it.

[http://ubuntuforums.org/showpost.php?p=554900&postcount=20](http://ubuntuforums.org/showpost.php?p=554900&postcount=20)

I dont know what INTIF AND EXTIF are and I dont know what you mean by internal and external network interfaces but im confident that if it does become a problem, you will be able to guide me through it. As for the script, the whole thing is in the one executable file and I execute it with the "sudo sh /media/floppy/AutoConfig" command (AutoConfig being the name I gave to the script). In the mount lines for the ntfs partitions as you have mentioned, for some reason, the disks are not accessable to anyone other than root unless I have that in there.

Well, im off to bed now, thank you very much for you help thus far and I look forward to seeing what you all have for me in the morning.

---

### Post by cilynx on 2006-04-30
Ah yes, I should have thought of that.  Yes, "apt-get" downloads off the net.  You will have to install the modem first and get online, then you can download and install the other packages.  Depending on how big the packages are, it may make sense to do it how you were originally planning as download time could be obnoxious.

Pmount appears to be a wrapper around mount that lets normal users issue mount commands.  Alrighty.

INTIF and EXTIF are just variable names in that firewall scripts that represent the internal and external interface.  Your internal interface is the network card that connects to your LAN.  Usually, it's eth0 or eth1.  Your external interface is the one that connects to the Internet.  With a dial-up system, it's usually ppp0.

Just out of curiosity, what part of the world are you in?  You're going to bed and I just got up =)

---

### Post by Stuperfied on 2006-04-30
Ya, im in Australia, I just got out of bed, lol. So how do I install dnsmask properly from the .tar.gz?

---

### Post by cilynx on 2006-04-30
instead of installing dnsmasq from the .tar.gz, I would just pull the .deb and have that on hand instead of the .tar.gz...then you can just "dpkg -i dnsmasq-x.x.deb"

---

### Post by Stuperfied on 2006-04-30
Where can I get the .deb from?

---

### Post by Stuperfied on 2006-05-01
Ok, got the .deb now. What can we do about getting her dial up connection auto configured with her user/pass and the phone number to dial into?

Edit: Hmm, no replies. Maybe its time to start a new topic again.

---

