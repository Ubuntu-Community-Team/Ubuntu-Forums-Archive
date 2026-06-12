---
title: "Install Trendnet Wireless USB - TEW-424UB 3.0R"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by saviles on 2007-03-13
I've just installed Ubuntu for like the 3rd time this week on my laptop. I thought i'd try to install this USB wireless device that i have to finally give it internet access. I've searched this forum (and google) about how to install this TEW-424UB device. There are a few options that require using the ndiswrapper. Unfortunately most of the instructions i find have to do with the SIS chip and earlier versions. 

When i do a "lsusb" i see the following:

Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 

I've been primarily looking at this post:
[http://ubuntuforums.org/showthread.php?p=2077497](http://ubuntuforums.org/showthread.php?p=2077497)

So my questions are the following:
- is there another way to install this since the chip is by Realtek instead of an SIS one?
- should i go and use the ndiswrapper method anyway?
- is there a location that can give me step-by-step instructions on how to install it?

I would appreciate any help.

Thanks.

---

### Post by rootkit on 2007-03-14
You are lucky, your adapter is a RTL8187B and is fully supported
drivers are here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by saviles on 2007-03-15
Great! I'll have to check it out when i get home later. I'll post what my experience was.

How did you know exactly what adapter this device used?

---

### Post by saviles on 2007-03-15
So far I haven't been successful in installing the module. :(

After following the step in the readme file, the last few lines i see are the following:

```

.. more similar warnings above
WARNING: "ieee80211_wx_set_rate" [/home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.ko] undefined!
  CC      /home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.mod.o
  LD [M]  /home/saviles/Software/rtl8187B_linux_24.6.1021.0212.2007/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
saviles@ubuntu:~/Software/rtl8187B_linux_24.6.1021.0212.2007$ 

```

Now I continue with the following commands (as noted in the Readme)

```

saviles@ubuntu:~/Software/rtl8187B_linux_24.6.1021.0212.2007$ sudo ./wlan0up
insmod: error inserting 'r8187.ko': -1 Unknown symbol in module
wlan0: ERROR while getting interface flags: No such device
saviles@ubuntu:~/Software/rtl8187B_linux_24.6.1021.0212.2007$ sudo ./wlan0down 
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8187 does not exist in /proc/modules
saviles@ubuntu:~/Software/rtl8187B_linux_24.6.1021.0212.2007$ sudo ./wlan0up
insmod: error inserting 'r8187.ko': -1 Unknown symbol in module
wlan0: ERROR while getting interface flags: No such device
saviles@ubuntu:~/Software/rtl8187B_linux_24.6.1021.0212.2007$ lsmod
Module                  Size  Used by
ieee80211_rtl          70020  0 
ieee80211_crypt_ccmp_rtl     8832  0 
ieee80211_crypt_tkip_rtl    11520  0 
ieee80211_crypt_wep_rtl     6272  0 
ieee80211_crypt_rtl     7044  4 ieee80211_rtl,ieee80211_crypt_ccmp_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl
nls_utf8                3200  1 

```

Doing an 'ifconfig' i do not see the wlan0 adapter show up. its obviously listed in lsmod. I've noticed that after a system reboot the modules are no longer listed when i do 'lsmod'.

Can someone point out if i'm doing something wrong?

I've attached my installation process from start to finish. I'm also using the following driver: 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432)

Thanks again.

Sijis

---

### Post by noodles12 on 2007-03-15
i tried installing that driver and i get similar issues.

---

### Post by noodles12 on 2007-03-20
Did you ever get this issue resolved? i think I am going to return the usb thing. I can't get it to work.

---

### Post by saviles on 2007-03-20
Nope. I've never gotten this resolved. I've also sent the company an email but I haven't heard back from them yet either. :(

I haven't tried using the NDISwrapper and that's pretty much the last option I can think of.

---

### Post by saviles on 2007-03-22
I got a response from Realtek and they said i should try the following driver: rtl8187_linux_26.1024.0209.2007.tar.gz (see attachment)

So far I've tried the instructions in the readme and i still isn't working. However, i did notice that the last line after i run ./makedrv i get the following warning/error:

./makedrv: 14: mipsel-linux-gcc: not found

So far i haven't been able to find what package "mipsel-linux-gcc" is part of. When i looked at the  makedev file, the last line it executes is just:

mipsel-linux-gcc -v

Typically the 'v' flag is just checking the version of the package. I could be wrong in this case.

Can someone try using the driver they provided me and tell me if you get similar results?

---

### Post by noodles12 on 2007-03-24
I tried it right before i returned it and got similar results. I looked up that mispel thing and it seems like something for a virtual linux OS and has nothing to do with us. (At least that's what I ended up getting out of my research.) 

G'luck man.

---

### Post by whitesox on 2007-04-11
Hate to rain on anybody's parade, but the Rev 3.0 isn't Realtek 8185, but Realtek 8187B.... a much more obscure version 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#1432")
but yet they still claim to have linux support.
I Will fix this.

---

### Post by cubdukat on 2007-05-26
I recently downloaded both the drivers posted here and the ones on Realtek's site, and attempted to install them both following the readme instructions. 

Needless to say, it did not work. I have the build-essential package installed, so I should have everything the script needs to build the drivers.

Any help would be greatly appreciated, and I have attached a copy of the shell output. Maybe someone could figure out what's going on. 

Oh, by the way, I'm doing this on Ubuntu Studio.

---

### Post by sbrunner91709 on 2007-06-12
Any Luck??  I have been trying for the Past 2 weeks to get this installed,  I finally came accross this thread.

---

### Post by cubdukat on 2007-06-12
Sadly, no. I've given up on it. I'll just wait until RaLink comes up with a better driver, since this is probably happening in every single other distro as well. I remember having trouble with RaLink drivers with my older Belkin F5D7000 card, but they eventually straightened it out. The only reason I'm not using that card instead is that I have no available PCI slots since I upgraded my motherboard.

I'll have to do my updating of Ubuntu Studio the hard way--through dialup.

---

### Post by mr.v. on 2007-07-16
So I just got the same wireless adapter so that I could play World of Warcraft at work (fortunately my boss doesn't use Ubuntu so I think I'm safe here)....


Anyway, I'm using Ubuntu 7.04. The Trendnet TEW-424UB 3.0 uses the Realtek 8187B chip. Drivers are available for linux for the 8187B on realtek's website, however, there's a catch. 7.04 uses the 2.6.20 series kernel. There were some significant changes to the kernel architecture since those drivers were written and compiling against it breaks many older modules. Still there's hope if Realtek doesn't want to do the legwork. I've gotten some ways.

Many of the compilation errors you see are for a preprocessor macro **INIT_WORK** which was changed from having 3 parameters to 2 in the kernel source headers. Therefore, it breaks any code calling it. That said, I changed the INIT_WORK lines in the driver by removing the Data field and those errors disappeared. 

A bunch more were the result of #including <linux/config.h> but config.h was removed as of 2.6.19 series kernels. So if you just remove those references or touch linux/config.h in the include tree you can avoid that error.

However, there's still more that I'm stuck on too. I get a compile error still complaining about the use of a page* pointer. I can't figure this one out. It's defined in <asm/page.h>. However, including that file specifically doesn't result in successful compilation. It still complains that page.h is used without defining.

Since it was only in the cryto library function of the driver, I thought maybe I could get it working without crypto at first and that would be a start. So I compiled it commenting out the page* pointers. And Voila! it compiled and linked.

However, if I run the scripts it complains:
> ~/src/rtl8187B_linux_24.6.1021.0212.2007$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Unknown symbol in module
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Unknown symbol in module
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Unknown symbol in module
insmod: error inserting 'r8187.ko': -1 Unknown symbol in module
wlan0: ERROR while getting interface flags: No such device

I'm not sure where to go with this. I'm only a mediocre programmer at best and just learning to hack on linux let alone kernels or drivers or more.

Any other expert's help would be appreciated.

---

### Post by pritamps on 2007-10-11
Hey,

I got the card working!

Use ndiswrapper along with the drivers that come on the CD. They aren't stored directly using the files. So first install the Trendnet software on Windows (or using wine on linux), and get into the installation directory. The drivers are there. Use those and everything works!

-Pritam

---

### Post by kboykowboy on 2007-11-02
ok now i'm in this problem too... running into a lot of problems here 
;-).. challange it is...

HOW did you doo it?! i installet ndiswrapper... cd into the dir where i 
put the net8187b.sys file did the sudo ndiswrapper-i net8187b.inf

it said it installet it

then did 
sudo ndiswrapper -i RTL8187B.sys
[sudo] password for jacob:
installing rtl8187b.sys ...
couldn't find SourceDisksFiles section - continuing anyway...
couldn't get manufacturer section - installation may be incomplete
jacob@xubuntu:~/netdriver$ 

so... still no go

---

### Post by cubdukat on 2007-11-02
If you did "sudo ndiswrapper -i" twice, that would cause that. You only have to do that once. After that you'd type "sudo modprobe ndiswrapper," then if it works, "sudo ndiswrapper -m".

---

### Post by kboykowboy on 2007-11-02
jacob@xubuntu:~$ sudo modprobe ndiswrapper 
[sudo] password for jacob:
jacob@xubuntu:~$ sudo ndiswrapper -m
module configuration already contains alias directive

jacob@xubuntu:~$ 

i fear i'm just shooting in the dark here... i really dont know what i'm doing, just typing commands and hoping it will work at some point in time.... 

there is no real walk through of this is there?!

it still dont work.. my old pcmcia card does though - thats how i'm posting... could it be conflicting!?

When looking in my /etc/network/interfaces i see this

> # The primary network interface
auto eth0
iface eth0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-key xxxxxxxxxxxxxxxxxxx
        wireless-essid xxx


this morning i'm doing a reinstall of the entire xubuntu..... see if i messed something up 

J

---

### Post by kboykowboy on 2007-11-03
IT WORKS

Installet the drivers on my pc. copied the files .inf and .sys to the ubuntu (after reinstalling xubuntu without my other pcmcia network card blogged in)



jacob@ubuntu:~$ sudo ndiswrapper -i net8187b.inf
[sudo] password for jacob:
installing net8187b ...
jacob@ubuntu:~$ sudo ndiswrapper -l
net8187b : driver installed
        device (0BDA:8189) present
jacob@ubuntu:~$ sudo modprobe ndiswrapper
jacob@ubuntu:~$ 

did the settings in network settings and restarted...

now writing from it!! 

thanks to all in the threat for helping!

and looking forward to test WPA with this card at my girlfriends house!

---

### Post by coolbrook on 2007-11-30
I'm struggling with this adapter too.  I can see that it's being detected when I tupe lsusb and ndiswrapper -l shows

*net8187b               driver installed, hardware present*

but it's not listed in ifconfig or iwconfig.

---

### Post by coolbrook on 2007-12-07
bump

---

### Post by coolbrook on 2007-12-10
I'm getting warmer.  I can now see wireless networks in my area, but I can't connect to my own which uses WEP.  Anytime I enter the key, then I'm prompted to do the same thing about 20 seconds later.  I appreciate any help on this one.

---

### Post by rgordon1982 on 2007-12-11
This card is also giving me some issues. I'm able to successfully install the card and get it connect to the router/internet while encryption is turned off on the router. However, attempting to enable WPA on the router causes the Network Manager to constantly ask me for the network password. It may even show that I'm successfully connect for a second or two but then always disconnects me and repeats the cycle. Has anyone be able to successfully get this card working with WPA?

I am using the Window drivers for this model with the latest version of NDISWrapper (1.5)

---

### Post by snyperx on 2007-12-11
Well add me to the list.  I bought a Gateway ML6721 and can not get the Realtek 8187B wireless adapter working.  Actually I am not even sure what to do.  I have read a few other threads, but none of them supply any kind of step-by-step process, which is what I need.  Seems to be hit or miss.  Some people are able to fix it others are not.

---

### Post by Kansasguy on 2007-12-11
Hi, brand new to Linux, I have three computers in a home network, one wired PC with XP, a laptop with XP, and a third PC (600mgh, 256k memory) which did have XP, but now has Ubuntu 7.10.  This third PC was working with the 424UB, and now I want to use it with Ubuntu.  Do I have to download ndiswrapper from the net to my PC (wired) and then put it on a flash drive and take it to the other one, or is it on the Ubuntu disc/program.  I did find the drivers on the trendnet disc with the .inf file if that helps.
HELP.    Thanks

---

### Post by dawonn on 2007-12-18
PROBLEM:
I had the same issue as above, I got the drivers from the trendtech website for the TEW-424ub 3.0R and use ndiswrapper. I tried to connect to any WEP 'protected' network and the gnome network manager would just prompt me again and again for a key until i was blue in the face with rage. 

SOLUTION:
I used the command line to establish a connection then request an IP via DHCP. and poof! in business!:KS

```

iwlist wlan0
sudo iwconfig wlan0 essid <AP NAME> ap <AP MAC ADDRESS> key <KEY IN HEX>
sudo dhclient wlan0

```


I've made a [ubuntu wiki page]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_3.0R_(ndiswrapper)") for the info pertaining to the 3.0R, I hope it helps someone in the future

---

### Post by coolbrook on 2007-12-18
I caved, bought a Netgear USB adapter and it's working, but I'll suscribe to this thread since I kept the 424UB and I'll try dawonn's solution when I build another machine.

---

### Post by Kansasguy on 2007-12-21
Coolbrook,  I just got to this stage:

Installed drivers:
net8187b : driver installed
        device (0BDA:8189) present

and am trying to follow your wiki page (THANKS!!)

Can you give me something close to what would go into the spaces in:

sudo iwconfig wlan0 essid <AP NAME> ap <AP MAC ADDRESS> key <KEY IN HEX>
sudo dhclient wlan0

that is, for AP Name, and AP Mac address and Key IN HEX, if you can, I will know more what to look for in my router stats.    (for example: is AP name the same as SSID?)   Thanks,    ht

---

### Post by dawonn on 2007-12-21
You have no idea how happy I am to hear that the wiki was helpfull, Thanks!

Example for you~ :)
```

sudo iwconfig wlan0 essid <AP NAME> ap <AP MAC ADDRESS> key <KEY IN HEX>
sudo iwconfig wlan0 essid homenet ap 00:12:2B:FF:12:32  key 6c757a65726173647579797979

```

The essid and ap MAC address can be copied and pasted right from the info that is returned from:
```

 iwlist wlan0

```

Obviously the key is a key, so you'll need to enter that from what is in your Access point.

Good luck! I'm around.

[edit] added example to wiki too.

---

### Post by whorush on 2008-01-06
dawoon, great wiki!  thanks!

i did the install part, and it seems to install all well and good, but it doesnt come up under my list of network connections/devices and when i run "iiwlist wlan0", and it says "iwlist: unknown command 'wlan0' (check iwlist --help)'

went to the guys on the irc channel, they told me to run this, which indicated to them that something didnt work:

brad@amd64:~/Desktop$ cat /var/log/syslog |grep loadndisdriver
Jan 5 21:53:07 amd64 loadndisdriver: loadndisdriver: load_driver(337): coudln't find valid drivers files for driver net8187b
Jan 5 21:53:07 amd64 loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8187b
Jan 5 21:53:07 amd64 loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8187b

i think the problem could be the files  i installed it from.  i'm using 64bit 7.10 ubuntu and i installed it on a 32bit XP  laptop, and then went into the drivers folder, and there was only an inf and sys file.  but youre saying i need all three, including the cat file.  whats the deal?

thanks!
bradley

---

### Post by dawonn on 2008-01-06
Ah yes, amd64.... You are really a challenge seeker aren't you. ^_^ I'm not sure that this works at all on the AMD64 platform... But, I don't have my amd64 hardware on the same side of the earth as me right now, so I can't test it myself. 

It does indeed seem that ndiswrapper driver has failed to load. I think you really need to find where that mystery file went off to. Check the status of the driver with: 

```

ndiswrapper -l

```

other than the missing file, other things to consider might include, but certainly not limited to: Extracting the drivers on a 32 bit windows machine produces only 32 bit drivers; extracting the drivers on a win64 machine would give you 64 bit drivers. this means you need to get a copy of win64 to extract the drivers, or find a direct download of them somewhere.

Good luck!

---

### Post by whorush on 2008-01-06
ok, i installed it on two XP machines.  i go to "C:\Program Files\TRENDnet\TEW-424UB\Driver" and there is only net8187b.inf and rtl8187B.sys.

when i use only those two, and install it says "installing net8187b ..." and then returns without errors.  looks like it works.

then i run "ndiswrapper -l" and it returns "net8187b : driver installed", again looks like it worked.

now, using ndisgtk, the gui says,

"net8187b
Hardware present: Yes"

again looks good.

i did it again very carefully and this time "cat /var/log/syslog |grep loadndisdriver" returns nothing.

but i still dont see wireless in the list of networks and "iwlist wlan0" still doesnt work.

thanks!
bradley

---

### Post by dawonn on 2008-01-06
You're right, that does look VERY promising! Sorry, I misunderstood earlier.

It is possible that the interface was named something else, try typing 'iwconfig' to see if it picks up any wireless cards, if it finds one, it will display a bunch of fun information for you.

---

### Post by whorush on 2008-01-07
iwconfig says

lo   no wireless extensions
eth0   no wireless extensions


iwlist is a program, iwlist --help gives me a bunch of options, but when i put in "iwlist wlan0" it says

iwlist: unknown command 'wlan0' (check 'iwlist -help')

---

### Post by whorush on 2008-01-07
a while ago, i went through and deleted some packages that i didnt think i'd use.  maybe i deleted one needed for wireless networking?  not sure.  but i dont know how to find out?

once again, thanks for all your help so far!

---

### Post by dawonn on 2008-01-08
based on the output of iwconfig, your computer can't find any wireless cards even though ndiswrapper appears to have found the card and driver. If you are not dependent upon using the AMD64 architecture, then I would install the x86 version and try that. 

I use AMD64 on one of my computers and see no real improvement on day to day activities, so If I were in your spot right now, I'd throw a x86 install disc in the drive and try it again. Otherwise, keep looking around IRC and the forums for someone more experienced than myself and report back here if you you find a solution. Update the wiki accordingly.

Good luck!:KS

---

### Post by Nickotym on 2008-01-09
I am at the exact same stage that whorush is.  Let me know if you get anywhere.

Thanks

---

### Post by Nickotym on 2008-01-09
I got it working I think, will have to double check tonight.  I opened ndisgtk in a console using:
> sudo ndisgtk

then I removed all the drivers listed that were invalid and then reloaded the net8187b.inf  that i downloaded from the[ realtek link ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") (the winxp/2000 driver).

That got me to the same point as whorush.  After logging out,restarting the Xserver and logging back in it seems to be working.  iwlist wlan0 scan shows the avail essids.  the card shows up under iwconfig.

---

### Post by Nickotym on 2008-01-10
Update:

I forgot, I had to add some information to /etc/network/interfaces.  I will post later tonight the lines I had to add, am not on that computer right now.  

When I got home, the card was recognized and could find my essid, but I couldn't get to internet through it.  I think I may need to remove the requirement for a key to access the wireless router for the card.  I will try to post later on what I do and if it works.

Also instead of just restarting xserver, I had to restart the computer to get the changes to take effect.

---

### Post by Nickotym on 2008-01-10
Here is what i added to /etc/network/interfaces

code:
> auto wlan0
iface wlan0 inet dhcp
wireless-essid  MYESSID
wireless-key  XXXXXXXXXX


I am still having trouble getting dhcp to work.

---

### Post by Nickotym on 2008-01-11
I disabled DHCP in network settings and then assigned an IP to my box.  After a restart the card works and I am using it now.

---

