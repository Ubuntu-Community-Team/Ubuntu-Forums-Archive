---
title: "Install is ok - but no wifi internet connection!"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by DizMan on 2008-02-03
Hi there!

First of all - let me warn you. I'm a total rookie when it comes to Ubuntu. Mit Ubuntu experience is about 15 minutes!

Then I want to say "WOW" to the Ubuntu folks. Ubuntu installed in about 15 minutes on an old IBM T23 thinkpad. It imported links, docs and the like from the Win XP prof. installation and set up a dual boot. Impressive and neat!!! Gone are the days where Linux could only be installed by experts! The only thing which didn't work "out of the box" was partitioning of the HD. It took a loooooooong time and didn't work. Luckily I had a bootable cd with Partition Magic and the problem was solved.

[COLOR="Red"]But... I'm babbling away here. Sorry! My problem is that I can't get my wireless to work. And without networking Ubuntu won't survive on my laptop. So please help![/COLOR]

I've got a Zyxel G-260 which is an 802.11g Wireless USB 2.0 Adapter. I want to connect to my router (and the internet). The router is a Zyxel P-2602HW-D1A Dsl and SIP router. I'm using WPA-PSK. There's no problem connecting in win XP - but it seems that Ubuntu does not find the USB wifi adapter at all.

When I look in: Administration -> Network it only says "Wired connection" and "Modem connection". There are no "wireless connection".

I tried to read in "Ubuntu Help Center" which suggested to use NDISWrapper. As it said I tried to install the NDISWrapper using Synaptic Package Manager. It said then to open NDISWrapper by using the menu System -> Administration -> Windows Wireless Drivers. But the entry "Windows Wireless Drivers" does not appear in the menu. What to do..? I am (until now) a windows person, so the only thing i could think of was rebooting. Of course it didn't solve the problem! So please give me a hand here...

...And a bonus question. Is it possible to be able to print on my printer (Canon PIXMA MP500). The printer is connected via USB to my main pc which runs win XP prof. Sharing is enabled on the main pc.

Thanks in advance!

Greetings from Diz...

---

### Post by (((X))) on 2008-02-03
> **DizMan said:**
> Hi there!

First of all - let me warn you. I'm a total rookie when it comes to Ubuntu. Mit Ubuntu experience is about 15 minutes!

Then I want to say "WOW" to the Ubuntu folks. Ubuntu installed in about 15 minutes on an old IBM T23 thinkpad. It imported links, docs and the like from the Win XP prof. installation and set up a dual boot. Impressive and neat!!! Gone are the days where Linux could only be installed by experts! The only thing which didn't work "out of the box" was partitioning of the HD. It took a loooooooong time and didn't work. Luckily I had a bootable cd with Partition Magic and the problem was solved.

[COLOR="Red"]But... I'm babbling away here. Sorry! My problem is that I can't get my wireless to work. And without networking Ubuntu won't survive on my laptop. So please help![/COLOR]

I've got a Zyxel G-260 which is an 802.11g Wireless USB 2.0 Adapter. I want to connect to my router (and the internet). The router is a Zyxel P-2602HW-D1A Dsl and SIP router. I'm using WPA-PSK. There's no problem connecting in win XP - but it seems that Ubuntu does not find the USB wifi adapter at all.

When I look in: Administration -> Network it only says "Wired connection" and "Modem connection". There are no "wireless connection".

I tried to read in "Ubuntu Help Center" which suggested to use NDISWrapper. As it said I tried to install the NDISWrapper using Synaptic Package Manager. It said then to open NDISWrapper by using the menu System -> Administration -> Windows Wireless Drivers. But the entry "Windows Wireless Drivers" does not appear in the menu. What to do..? I am (until now) a windows person, so the only thing i could think of was rebooting. Of course it didn't solve the problem! So please give me a hand here...

...And a bonus question. Is it possible to be able to print on my printer (Canon PIXMA MP500). The printer is connected via USB to my main pc which runs win XP prof. Sharing is enabled on the main pc.

Thanks in advance!

Greetings from Diz...

I couldn´t install ndiswrapper from synaptic too, so I compiled that program.
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
Get stable version.
then follow this tutorial: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
Ignore the lines beginning with wget.
Instead, download wifi drivers for windows and ndiswrapper, as I mentioned above.
good luck.

---

### Post by zachthejones on 2008-02-03
also, make sure you do a search for your specific USB wireless router on the forums, that might yeild some more specific instructions for you! Best of luck!

---

### Post by DizMan on 2008-02-05
> **(((X))) said:**
> I couldn´t install ndiswrapper from synaptic too, so I compiled that program.
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
Get stable version.
then follow this tutorial: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
Ignore the lines beginning with wget.
Instead, download wifi drivers for windows and ndiswrapper, as I mentioned above.
good luck.


Hi thanks!

...Close but no cigar! I tried to the best of my abily to follow your advise and did everything as described in the tutorial. I also found my USB wifi adaptor on the list of supported devices and copied the win driver to a directory on the linux laptop. 

The downloaded Ndiswrapper is in: /home/lars/Install/ndiswrapper-1.52
My win driver is in: /home/lars/Install/zyxel-g260-driver

So far so good. As far as I can tell everything went ok until this command: "sudo make". Then about 5 pages of text came down the screen - and at least 2 or 3 of them was filled with errors and warnings. Here I show the first 25 lines or so. Any idea as to solve my problem? You know a laptop without internet is like a mug of coffee without the coffee!!! :KS

Thank you for your help...

>>> txt from terminal

lars@lars-laptop:~/Install/ndiswrapper-1.52$ sudo make
make -C driver
make[1]: Entering directory `/home/lars/Install/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/lars/Install/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/lars/Install/ndiswrapper-1.52/driver/built-in.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/crt.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/hal.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/iw_ndis.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/loader.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/ndis.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/ntoskernel.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/ntoskernel_io.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/pe_linker.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/pnp.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/proc.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/rtl.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/wrapmem.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/wrapndis.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/wrapper.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/usb.o
  CC [M]  /home/lars/Install/ndiswrapper-1.52/driver/divdi3.o
  LD [M]  /home/lars/Install/ndiswrapper-1.52/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/lars/Install/ndiswrapper-1.52/driver/ndiswrapper.mod.o
  LD [M]  /home/lars/Install/ndiswrapper-1.52/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/lars/Install/ndiswrapper-1.52/driver'
make -C utils
make[1]: Entering directory `/home/lars/Install/ndiswrapper-1.52/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
... and so on
... and so on
... and so on

<<< txt from terminal

---

### Post by (((X))) on 2008-02-05
And you  installed  build-essential?
I googled for that and that is what people recomending,

---

### Post by DizMan on 2008-02-05
...Sorry, but i don't understand your question. I know i'm a complete newbie in UbuntuLand, so most of the time I just type in the code given to me without understanding what i'm doing...

Could you enlighten me a bit more? :confused:

I downloaded the lastes stable version (1,52) of ndiswrapper and then I tried to follow the guide point for point. I also copied the windows driver file (INF) for my zyxel usb adaptor. But without success. Normally - in windows - the zyxel lights up in a blue colour, when it is inserted into the usb-port. But in Ubuntu is doesn't light at all - and there is no "wireless network" item in the networks menu.

Any idea how to proceed..? - thanks again and sorry that my questions are a bit stupid...

---

### Post by (((X))) on 2008-02-05
:)
search for package: build-essential via synaptics

---

### Post by (((X))) on 2008-02-05
> **DizMan said:**
> and there is no "wireless network" item in the networks menu.


$ nm-applet&

this might bring the icon back on the panel.

---

### Post by DizMan on 2008-02-05
ok... Trying that at once. At the moment i'm having internet access on the laptop via Ubuntu - i found an old 25 m ethernetcable and hooked it up to my adsl-router. So now the kitchenfloor is occupied with my cables. But I only think it stays there until my wife sees it!

---

### Post by (((X))) on 2008-02-05
ok, here is what you can do to get rid of those cables by tomorrow.:P
first install build-essential via synaptic, when follow exactly everything written in howto, 
ignore lines with build-essental... whatever..and wget...whatever...
If it still not working, try older version of ndiswrapper, don´t know if that will help.
Anyway Good luck

---

### Post by DizMan on 2008-02-09
> **(((X))) said:**
> ok, here is what you can do to get rid of those cables by tomorrow.:P
first install build-essential via synaptic, when follow exactly everything written in howto, 
ignore lines with build-essental... whatever..and wget...whatever...
If it still not working, try older version of ndiswrapper, don´t know if that will help.
Anyway Good luck

Hi again (((X)))

Thanks very much for your help. I'm sorry to admit it but by now Ubuntu is driving me crazy!!!

I've had some succes with connecting - but my gosh this thing is teasing me...

After following your "howto" there suddenly was an "wireless network" item in the network menu. Cool! I typed in all the info, my essid and my wpa-psk key. My adaptor started flashing in a blue colour but no connection. :confused:

Then I entered my router and set the connection to "no encryption" and "broadcast SSID". Not to my liking - but as an experiment!

Ta dah!:) Now the Ubuntu laptop found my network. I set up encryption again, and now I can connect to my network including encryption: But only when my router is broadcastning the SSid and "roaming mode" is enabled in the wireless connection entry in the Network Settings. I simply cannot get it to work, when i don't broadcast my SSID. It also means that I have to enter the wpa-key any time I connect to the net. I would very much like to be able to have an entry in the "wireless connection" menu, where I store my wpa-key my gateway address and my ip-address - oh, that reminds me: I also had to let the router do DHCP to make it work. Annoying. I like to know te ip address of every pc...

I don't like a visible network - any idea how to make it work right? Now I'm on the internet (with the limitations mentioned). My next "demand" is, that it is so easy to get on the net, that my wife can use the laptop - in fact she owns it :lolflag:

If I have to go to my other pc - reconfigure the router and enter a wpa-key on the laptop then I'll never get my wife (or my self) to use Ubuntu in the long run...

Thanks again.!.


...so an idea to the Ubundu dev. team: Ubuntu looks cool and does a great job importing user settings from the win installation and so forth. I think it is the smoothest linux dist. i have tried to install the latest years. But I think wifi networking is essential if ordninary users are going to use it. Nowadays you buy a laptop in the supermarket and expect to be on the net 15 minutes after the laptop is out of the box. Just my 2 cents...  :-)

---

