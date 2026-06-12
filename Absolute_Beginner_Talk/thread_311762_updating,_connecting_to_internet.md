---
title: "updating, connecting to internet"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by kirsten on 2006-12-03
hi, so i am completely new to linux/ubuntu and just installed 6.06 LTS.  i am dual-booting windows, and the internet connection is working fine there; i am directly plugged into a wireless router, and i know the password to get into the wireless connection, but windows is not prompting for a password.  when i first installed, i was prompted to update ubuntu, and that there are 202 updates. from there, everything fails, and i am unable to find a working webpage.  it tells me that eth0 is active, but from there i have no clue whatsoever. please help?

---

### Post by taurus on 2006-12-03
What's the output of this command from a terminal, Applications -> Accessories -> Terminal?

```
ifconfig
```

---

### Post by kirsten on 2006-12-03
ok, here it is:

kirsten@Igor-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:1F:6A:0D
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe1f:6a0d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:48 dropped:0 overruns:0 frame:0
          TX packets:22 errors:1 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3812 (3.7 KiB)  TX bytes:2512 (2.4 KiB)
          Interrupt:193 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3038 (2.9 KiB)  TX bytes:3038 (2.9 KiB)

---

### Post by taurus on 2006-12-03
What happens when you run this from a terminal?

```
ping -w 3 www.yahoo.com
```
Otherwise, it could be your router...

---

### Post by kirsten on 2006-12-03
it says ping: unknown host [www.yahoo.com](www.yahoo.com)

---

### Post by taurus on 2006-12-03
What does your /etc/resolv.conf look like then?

```
cat /etc/resolv.conf
```

---

### Post by kirsten on 2006-12-03
nameserver 192.168.1.1

---

### Post by taurus on 2006-12-03
Hmm...  You also need a line that say

```
search <your gateway IP>
nameserver 192.168.1.1
```
Replace the <your gateway IP> with the actual IP address of your gateway/router!

---

### Post by kirsten on 2006-12-03
hmm, where would i find that information at? should i go back into windows and try an ipconfig command?

---

### Post by taurus on 2006-12-03
If you can get into the router (from a web browser), you can get that.  If not, get it from Windows if that's easy for you.

On the other hand, can you surf the web with the LiveCD because you can copy it, /etc/resolv.conf, from the LiveCD to your harddrive...

---

### Post by kirsten on 2006-12-03
ok, so i went through ipconfig and got this:

Ethernet adapter Local Area Connection:

Connection-specfic DNS Suffix. :
IP Address.................... : 192.168.1.2
Subnet Mask................... : 255.255.255.0
Default Gateway............... : 192.168.1.1

from there, i managed to reset the router, and received the same information...

so my next question is this, do i use the default gateway in the command line as suggested above? or should i be using the DNS that is obviously blank?

---

### Post by taurus on 2006-12-03
Do you still have the LiveCD handy?  Can you boot your machine from it and see if you can surf the web with it?  Then, you just copy the /etc/resolv.conf from the LiveCD over to your harddrive...

---

### Post by kirsten on 2006-12-03
ok, i can try that, but being my complete lack of experience with this, how would i copy it from the cd? do i search for the file, etc?

---

### Post by taurus on 2006-12-03
Boot into LiveCD.  Then open a terminal, Applications -> Accessories -> Terminal, and paste the output of these commands here.  Once I know for sure which partition your Ubuntu is on, I will walk you through the whole thing if you want...

```
sudo fdisk -l
cat /etc/resolv.conf
```

---

### Post by kirsten on 2006-12-03
ok, this is what i get:

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065*512 = 8225280 bytes

Device Boot      Start     End     Blocks     ID     System
/dev/hda1        1         1402    11261533+   7     HPFS/NTFS
/dev/hda2        1403      3314    15338140    b     W9 5 FAT32
/dev/hda3        3315      4863    12442342+   5     Extended
/dev/hda5        3315      3378    514048+     82    Linux
/dev/hda6        3379      3509    1052226     83    Linux
/dev/hda7        3510      4863    10875973+   83    Linux

and then:

nameserver 192.168.1.1

---

### Post by taurus on 2006-12-03
Can you surf the web with the LiveCD?

```
ping -w 3 www.yahoo.com
```

---

### Post by kirsten on 2006-12-03
it ran some code, and the browser does work

---

### Post by taurus on 2006-12-03
So the network works fine with the LiveCD!!!  /etc/resolv.conf looks exactly the same on the LiveCD as on your harddrive,

```
nameserver 192.168.1.1
```
Boot into Ubuntu again and see if the network is working now!!!

---

### Post by kirsten on 2006-12-03
nope, no go:( i'll be leaving for a bit, but i should be back in a few hours...i have absolutely no idea why it won't connect, but thanks very much for the help!

---

### Post by kirsten on 2006-12-04
hi, 

so as a refresher: dapper tells me that i have 202 updates, but will not open a webpage through either the browser or terminal.  it will, however, do both of these from the installation disk.  so, what i am wondering if something did not get copied during the initial installation? i should be getting back to my computer by 6 pm est, if anyone has any ideas? thanks!

---

