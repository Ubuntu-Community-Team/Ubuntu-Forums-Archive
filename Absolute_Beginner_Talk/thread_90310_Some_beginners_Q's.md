---
title: "Some beginners Q's"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Bueno on 2005-11-14
Dear Community, 

Hello!

I am new to Linux and have a couple of questions. I currently use, yeah you guessed, MS Windows. I successfully installed Ubunto 5.10 onto a new partition.

On my original hard drive I had a logical drive where I keep my files d: When I boot from Grub into Linux, how do I get to see my d: logical drive? The partition is a FAT32 file system.

The next q is where do I start in connecting to the Web? I use a broadband modem from tiscali UK.

Cheers
Bueno:KS

---

### Post by steve.horsley on 2005-11-14
[QUOTE=Bueno]
On my original hard drive I had a logical drive where I keep my files d: When I boot from Grub into Linux, how do I get to see my d: logical drive? The partition is a FAT32 file system.[/QUOTE]
Have a look in /media. You may find that it is one of the folders in there. If not, can you post the contents of /etc/fstab?

As for the modem, I can't help you. I use a router/switch here.

Steve

---

### Post by Bueno on 2005-11-14
Steve,

Thanks for the response. In /Media there are only references to CD's and floppies. Also in /etc there in no folder or file called fstab.
:KS 
Cheers
Bueno

---

### Post by Sheco on 2005-11-14
The broadband connection is probably pppoe, you can try this:
```
sudo pppoeconf
```

if that works, there are some bugs with the way it sets everything up if you want the connection to be brought up automatically at startup, you'll probably need to edit /etc/network/interfaces fix it so it looks something like this :

```

iface dsl-provider inet ppp
provider dsl-provider
pre-up /sbin/ifconfig ethX up # line maintained by pppoeconf

```

---

### Post by Bueno on 2005-11-14
Sheco, where do I type  the Code:
sudo pppoeconf

---

### Post by Rackerz on 2005-11-14
Open up a terminal/console. Im not sure what its called in GNOME assuming your running Ubuntu.

---

### Post by Kapre on 2005-11-14
[QUOTE=Bueno]Sheco, where do I type  the Code:
sudo pppoeconf[/QUOTE]

Bueno - Click on Applications----->Accessories-------->Terminal (with a monitor icon)......a new window will pop-up------there you can type "sudo pppoeconf". Just make sure that you have all info available (username and password)

K

---

### Post by Bueno on 2005-11-16
Bueno speaking. Can anyone help. So far I still haven't solved my original questions.

---

### Post by Kyral on 2005-11-16
[quote=Bueno]Dear Community, 

Hello!

I am new to Linux and have a couple of questions. I currently use, yeah you guessed, MS Windows. I successfully installed Ubunto 5.10 onto a new partition.

On my original hard drive I had a logical drive where I keep my files d: When I boot from Grub into Linux, how do I get to see my d: logical drive? The partition is a FAT32 file system.

The next q is where do I start in connecting to the Web? I use a broadband modem from tiscali UK.

Cheers
Bueno:KS[/quote] 
First thing, the FAT32. Thing you have to realize is that the whole C: D: naming system doesn't exist in Linux AT ALL. Second thing, open a terminal and give me the output of 

```
sudo fdisk -l
``` if it wouldn't be too much trouble. That way we could get this thing kicking

---

### Post by canadianwriterman on 2005-11-16
[QUOTE=Bueno]Steve,

Thanks for the response. In /Media there are only references to CD's and floppies. Also in /etc there in no folder or file called fstab.
:KS 
Cheers
Bueno[/QUOTE]

fstab is actually a file, in /etc, not a folder. Scroll down further and you'll see it.

---

### Post by Bueno on 2005-11-16
Kyral,
The output from sudo fdisk -l showed me the partition info. I can see that the partition I want is dev/hda5.

---

### Post by Kyral on 2005-11-16
Okay now we are kicking. First off make a mountpoint. For this case its going to be /media/shared

```
sudo mkdir /media/shared
```

Now open the /etc/fstab file

```
sudo gedit /etc/fstab
```

Add this line to the bottom

```
/dev/hda5 /media/shared vfat defaults,users,rw,auto,uid=1000,gid=0000,umask=1000 0 0
```

Save it.

Now mount it with

```
mount /media/shared
```

If all went well then you should have read/write access to it

---

### Post by Bueno on 2005-11-16
Thanks Kyral!!

---

### Post by Bueno on 2005-11-17
One down one to go!

I found some good help for my tiscali modem from [http://ubuntuforums.org/showthread.php?t=44459&page=2](http://ubuntuforums.org/showthread.php?t=44459&page=2)

Originally Posted by davie
Thanks very much to everyone for that. It gave me enough info to get my adsl up and running on Ubuntu. Here's what I did, starting off with my modem unplugged from the USB:

1. System>Administration>Synaptic Packet Manager
2. Scroll down left hand menu. Click on Networking.
3. In right hand box, mark 'eagle-usb-data' and 'eagle-usb-utils' for installation.
4. Stick the Ubuntu installation CD in the drive.
5. Click Apply
6. The system should then install these two packages from the CD.
6.5 Plug in your modem.
7. Go to Applications>System Tools>Root Terminal. (Don't do what I did the first four times I tried this and go to Applications>System Tools>Terminal. You need to be in root to make it work.)
8. At the prompt type in 'eagleconfig'. This will give you a list of options for different ISPs. You'll see Tiscali at the bottom as 'UK01'
9. Type in 'UK01'
10. At the prompt, type in your ISP username
11. At the prompt, type in your ISP password
12. At the prompt about encryption, say 'no'
13. At the prompt about startup on boot, say 'no'
14. You should then get a message saying that configuration was successful.
15. Type 'startadsl'
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box. 
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 

And that should be it. Hope it helps someone. 

All the best,

Davie 

Hi, I've been following Davie's instructions above and have got to point 14 and not got the "config successful" I then typed "eaglestat" and got the following

Enter your password (given by your ISP):

Does your ISP support password encryption? [y]/nn

Do you want the connection to automaticaly be started at boot? y/[n]n
/usr/sbin/eagleconfig: line 45: strings: command not found


Loading module... [ OK ]

Loading DSP & options... [ Error ]
root@ubuntu:/home/rob# startadsl


Modem is not operational!
Check eaglestat result to know its state!

root@ubuntu:/home/rob# eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.3.2 Chipset: Eagle0
Vendor ID : 0x1110 Product ID : 0x9031 Rev: 0x200b
USB Bus : 001 USB Device : 005 Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:71:47:59
Tx Rate 0 Rx Rate 0
FEC 0 Margin 0 Atten 0 dB
VID-CPE 0 VID-CO 0 HEC 0
VPI 0 VCI 0 Delin GOOD
Cells Tx 0 Cells Rx 0
Pkts Tx 0 Pkts Rx 0
OAM 0 Bad VPI 0 Bad CRC 0
Oversiz. 0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

root@ubuntu:/home/rob#

Can anyone help?

I'm actually using v5.10 not Hoary! My provider is tiscali through a Sagem 800 modem

Cheers
Bueno

---

