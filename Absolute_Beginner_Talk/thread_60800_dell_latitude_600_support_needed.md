---
title: "dell latitude 600 support needed"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by thejonesfactor on 2005-08-29
hello there,
i have installed ubuntu on my dell laptop, but am having the following niggles;
1. when i try to play any audio file it says i must run gst-register, does anyone know anything about this app?
2. i am connected on my network but cannot access the internet, have tried all manner of configurations, but no joy
3. eject on my cd drive not functioning, using paperclip route, anyone have any ideas why this is so?
thanking you all in advance
cheers

---

### Post by KingBahamut on 2005-08-29
1. [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

2. Give us your configuration, we will hash it out for you. 

3. Is there a CDROM in there, or is it empty. Can you not eject it when the system starts up?

---

### Post by thejonesfactor on 2005-08-30
hi there, thanks for the quick response

1. i should have thought of the codecs, thanks. i left my ubuntu installation CD at home so will run that stuff this evening

2. once again thanks for the offer to help, exactly what info do you need from me? networks are my absolute weakest area when it comes to computers 
in connection properties i have:

Connection Properties: eth0

Internet Protocol (IPv4)
Address: 192.168.0.2
Broadcast: 192.168.0.255
Subnet Mask: 255.255.255.0

NetWork Device
Type: Ethernet
Address: 00:10:60:5F:C8:2D

3. it does eject at startup when things are still in the Dell stage of boot up, but after that nothing, whether there is a CD in or not

many thanks
thejonesfactor

---

### Post by thejonesfactor on 2005-08-31
hi all

1. thanks for the help KingBahamut, the codecs installed great, 

2. i am still however having difficulty getting my laptop to access the Net through my network, i can see the other machines on the network fine, but no Internet

3. CD eject still unco-operative

4. i have a PCMCIA modem for a 3G connection with local service provider MTN here in South Africa, but unfortunately it does not come with Linux support, the software for Windows OS is called Mobilink and the card is Novatel Wireless, is anybody out there familiar with 3G & MTN in a South Africa context?

once again thanking you all in advance,

cheers
thejonesfactor

---

### Post by davmac on 2005-08-31
Could you describe your network and internet connection in a bit more detail (what connects to what, etc) and can you provide the output of the commands ifconfig and iwconfig?

Regards,

Dave Mac

---

### Post by davmac on 2005-08-31
...and for the CD problem, what happens if you open up a terminal window and;

cd /
sudo eject /media/cdrom

Regards,

Dave Mac

---

### Post by thejonesfactor on 2005-08-31
Hi Dave

I ran that commmand line in Terminal, but no luck. This possibly due to fact that the forum put your response on 2 lines and I might be putting in the wrong spaces

I ran cd /sudo eject /media/cdrom & cd/sudo eject/media/cdrom

did I do it right?

cheers
thejonesfactor

---

### Post by xmastree on 2005-08-31
the command is normally```
eject /media/cdrom
``` 
but to run it as root, you need to use sudo. So you would type```
sudo eject /media/cdrom
```I don't think you need to cd/ first.

---

### Post by thejonesfactor on 2005-08-31
hi Dave

I am not too good at networks, but will endeavour to explain our steup. It is a MS Windows network running through a Linux server to Sentech MyWireless Internet connection, I ran those commands you suggested and below are the results;

craig@CraigLaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:60:5F:C8:2D
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:60ff:fe5f:c82d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000          
          RX bytes:150 (150.0 b)  TX bytes:378 (378.0 b)
          Interrupt:11 Base address:0x4800
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4434730 (4.2 MiB)  TX bytes:4434730 (4.2 MiB)

craig@CraigLaptop:~$ iwconfig
lo        no wireless extensions.
sit0      no wireless extensions.
eth0      no wireless extensions.

Looking forward to hearing from you, cheers thejonesfactor

---

### Post by thejonesfactor on 2005-08-31
many thanx xmastree, ran it as root, problem solved, ejecting manually and through software

---

### Post by KingBahamut on 2005-08-31
Jones, what is the contents of your resolv.conf in /etc? 

I bet your getting a DNS issue. 

When you open up firefox and input this address what happens.........

[http://216.239.57.99](http://216.239.57.99)

---

### Post by thejonesfactor on 2005-09-01
hi there KingBrahamut

resolv.conf contains folder update-libc.d which contains fetchmail:

#!/bin/sh

while [ "$1" ]; do
	if [ "$1" = "--nscd" ]; then
		exit 0
	fi
	shift
done

if [ -x /etc/init.d/fetchmail ]; then
	/etc/init.d/fetchmail try-restart
fi

and postfix:

#!/bin/sh -e

# make sure we're still here...
[ -x /usr/sbin/postconf ] || exit 0

cp /etc/resolv.conf $(/usr/sbin/postconf -h queue_directory)/etc/resolv.conf
/etc/init.d/postfix reload >/dev/null 2>&1

exit 0

firefox and that IP addy you suggested comes back with a Google Server Error

cheers
thejonesfactor

---

### Post by thejonesfactor on 2005-09-01
hi there

i am also trying to get my 3G connection going ithrough MTN here in South Africa, i have followed instr from another thread about Vodacom 3G but have got stuck

i have followed these instructions up to the point of needing to instal gnome-ppp, but it does not appear to be on my Ubuntu CD, where can I download this from, or what is my next step

here are the commands and results so far:

craig@CraigLaptop:~$ tail /var/log/syslog
Sep 1 10:36:52 localhost cardmgr[6327]: executing: 'modprobe serial_cs'
Sep 1 10:36:52 localhost udev[8686]: removing device node '/dev/ttyS2'
Sep 1 10:36:52 localhost cardmgr[6327]: executing: './serial start ttyS2'
Sep 1 10:36:52 localhost kernel: ttyS2 at I/O 0x3e8 (irq = 3) is a 16550A
Sep 1 10:36:52 localhost udev[8695]: creating device node '/dev/ttyS2'
Sep 1 10:50:40 localhost -- MARK --
Sep 1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 l ost synchronization, throwing 4 bytes away.
Sep 1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 l ost sync at byte 1
Sep 1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 l ost sync at byte 1
Sep 1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
craig@CraigLaptop:~$ sudo cardctl info
Password:
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="Novatel Wireless"
PRODID_2="Merlin UMTS Modem"
PRODID_3="U630"
PRODID_4=""
MANFID=00a4,0276
FUNCID=2
craig@CraigLaptop:~$ sudo apt-get install gnome-ppp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnome-ppp
craig@CraigLaptop:~$


thanking you in advance

thejonesfactor

---

### Post by shmuley on 2005-09-04
hi, i also have a Dell latitude C600 and I was having some weird issues with the network and internet browsing side of things.  I was able to get an DHCP IP address and could browse my LAN but, web pages could only be browsed if I put in the correct IP address i.e 66.102.9.147 for google.com.   I followed the instuctions found at [http://ubuntuguide.org/](http://ubuntuguide.org/)
to speed up firefox and it now works like a dream \\:D/ .   I dont know but I think that it was the IPv6 bit that made the difference.  I am also fyi using a 3com wireless pcmcia card.
g luck Shmuley

---

