---
title: "ndiswrapper and interface query"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by BigWinston on 2005-07-23
Hi All,

I have just installed ubuntu for the first time and like what I see. I can't get my wirless card working though.

My card is a Linksys WMP11 Wireless-B adapter. I have followed some of the previous posts on this forum successfully (installing gcc, ndiswrapper, etc).

When I do the 'ndiswrapper -l' command I see 'wmp11nfds   driver present!' displayed and I have run 'ndiswrapper -m' and rebooted my machine.

The problem is I dont see anywhere wlan0 and if I run 'iwconfig' I get the following :

lo  no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

Can anyone offer any advice?

Thanks.

---

### Post by scoon on 2005-07-23
Hey there, 

Unload the linksys driver and reload it.  See if that clears things up for you.

regards, 

scoon

---

### Post by BigWinston on 2005-07-23
Yup. Done that. Restarted.

Still not available.

Should it come up automatically or do I have to "create" it?

---

### Post by scoon on 2005-07-23
Hey there, 

You need to make certain the ndiswrapper is getting loaded.  You can check if it is by lsmod.  If it is not, then you need to modprobe -v ndiswrapper. After loading you can do a sudo /etc/init.d/networking restart and then you should see it in iwconfig.

regards, 

scoon

---

### Post by BigWinston on 2005-07-23
Ok,

I have just executed 'modprobe -v ndiswrapper' and I get the following error message.

insmod /lib/modules/2.6.10-5-386/misc/ndiswrapper.ko
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/misc/ndiswrapper.ko): Operation not permitted.

Any Ideas?

P.S - Thanks for your help scoon - much appreciated!

---

### Post by scoon on 2005-07-23
Hey there, 

Yes.  You need superuser status to insert modules.

try: sudo modprobe -v ndiswrapper

regards, 

scoon

---

### Post by BigWinston on 2005-07-24
I type that in and I still get the same error. I checked my users and groups settings and there is no root (?!).

Do I need to try and log in as root now, or try and add priviliges to my user account?

---

### Post by scoon on 2005-07-24
Hey there, 

First, does uname -r return 2.6.10-5-386 ? 

What if you stat /lib/modules/2.6.10-5-386/misc/ndiswrapper.ko ?

What do you get?

regards, 
scoon

---

### Post by BigWinston on 2005-07-24
Hi!

Ok, I managed to sort out full priviliges for my user.

So now when I enter 'sudo modprobe -v nidswrapper' I get the following response:

'insmod /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko'

Then I perform 'lsmod' and can see 'ndiswrapper   109044(size)  0(used by)'.

Now I look at iwconfig and still see no devices listed for wlan0.

hhhhmmmm........  :???:

---

### Post by BigWinston on 2005-07-24
Ok.

I was looking around on some other sites and saw that 'ndiswrapper -l' should have said

hardware present, driver present

Mine didn't specify the hardware was present so I used the inf file from the driver CD (rather than a download) and it all works as far as seeing 'wlan0' in iwconfig. Terrific!

BUT,  now I can not join a network (either encrypted or no encryption).

I perform 'iwlist wlan0 scanning' and get a couple of networks listed, so the card appears to be working fine.

I have used the System > Administration > Network Settings Tool. Specified the configuration to be DHCP there, entered the ESSID (the key where appropriate). Click OK and I think it's trying to activate and resolve its information but it cant.

So I typed 'ifdown wlan0' and then 'ifup wlan0' and see the following...

sit0: unknown hardware address type 776
Listening on LPF/wlan0/<MAC ADDRESS>
Sending on LPF/wlan0/<MAC ADDRESS>
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8   (etc).
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Any ideas? Does this look OK or is something screwed in my config.

As I say, I can see the networks - I just cant get on to them!!  ](*,)

---

### Post by scoon on 2005-07-24
Hey there, 

Try this:  /etc/init.d/networking restart


regards, 
scoon

---

