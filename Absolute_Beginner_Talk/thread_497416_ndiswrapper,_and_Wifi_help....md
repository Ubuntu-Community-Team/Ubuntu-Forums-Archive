---
title: "ndiswrapper, and Wifi help...???"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by User X on 2007-07-10
Hey Guys,

I am still working on my wireless connection and I need a bit of help.  I have done as described on the first page, about half way down, in this post "http://ubuntuforums.org/showthread.php?t=494168&highlight=ndiswrapper" by Kevdog where he gives information on installing ndiswrapper, however, I get an error when trying to install the program and it tells me at the end that ndiswrapper is not installed.  Can someon verify that the terminal comands given are correct for this application?  I don't know what they mean so I can't tell - I am a newb.  Also can somone point me in the correct direction for installation instructions?  I downloaded ndiswrapper off the net and brought it to my PC via a flash drive if that changes anything.  Thanks in advance for the help.

---

### Post by ronocdh on 2007-07-10
Try the [installation instructions]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/") on the ndiswrapper page. They may be of more use for you. Follow them meticulously!

---

### Post by User X on 2007-07-11
Hey thanks!  I'll try this...

---

### Post by User X on 2007-07-11
after executing:

"make distclean"
and
"make"
I get this:

make -C driver
make[1]: Entering directory `/home/aaron/ndiswrapper-1.46/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/aaron/
ndiswrapper-1.46/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/aaron/ndiswrapper-1.46/driver/built-in.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/crt.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/hal.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/iw_ndis.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/loader.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/ndis.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/ntoskernel.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/ntoskernel_io.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/pe_linker.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/pnp.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/proc.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/rtl.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/wrapmem.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/wrapndis.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/wrapper.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/usb.o
  CC [M]  /home/aaron/ndiswrapper-1.46/driver/divdi3.o
  LD [M]  /home/aaron/ndiswrapper-1.46/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/aaron/ndiswrapper-1.46/driver/ndiswrapper.mod.o
  LD [M]  /home/aaron/ndiswrapper-1.46/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/aaron/ndiswrapper-1.46/driver'
make -C utils
make[1]: Entering directory `/home/aaron/ndiswrapper-1.46/utils'
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

... and a whole lot more - all errors and warnings???  Does anyone have any idea whats wrong...?  This is pretty frustrating...

---

### Post by jrandolph on 2007-07-11
I had some major problems trying to install ndiswrapper 

I finally forgot all that and now i use 

wlassistant

maybe try this?? -- worked for me!!:)

sudo apt-get install wlassistant

then run

sudo wlassistant

---

### Post by jw5801 on 2007-07-11
Before you can compile the program from source you first need the programs that do this! The files it says are missing are all C header libraries, and to get them simply type this in terminal:
```
sudo apt-get install build-essential
```
If you try "make" again after getting the above package then everything should be fine.

On another note it's also a good idea to update your kernel headers before you compile:
```
sudo apt-get install linux-headers-`uname -r`
```
note that the symbols on either side of the uname -r are back tics (located to the left of the 1 on most keyboards). These back tics tell the terminal to execute the command contained within them and put the output into that position of the original command. uname -r is a command that outputs the kernel version you have installed.

Hope that helps!

---

### Post by User X on 2007-07-12
"sudo apt-get install build-essential"

This command won't run as I do not have an internet connection without the wireless working.  I downloaded the ndiswrapper off the internet - why would there be pieces missing???  (I got if from my other computer)

---

### Post by jw5801 on 2007-07-12
Ah, ok. That makes things a touch more interesting. It's not that there's pieces missing, what you have downloaded is the "source code" for ndiswrapper, which then needs to be "compiled" for your system. When writing C code, one refers often to standard extra functions (ie. printing to screen is the function "printf()"). Now rather than every programmer writing out all these functions every time they want to use them, they are included as header files (stdio.h, string.h etc etc), and the compiler then finds any place the source code references one of these header files and replaces it with the proper function, and after all that, translates it into something the processor can understand.

Take a look [here](http://packages.ubuntu.com/feisty/devel/build-essential), there should be some .deb files you can download and take to your linux box on a usb key or something. Don't forget that you'll need all the related packages as well, as the original is dependent on them. Also, to install a .deb package, cd to the directory it's in and put ```
sudo dpkg -i package-name.deb
```
Good luck! Report back if there are any more problems (and if there aren't just so we know :p)!

---

### Post by User X on 2007-07-12
Ironically enough, I entered:

sudo apt-get install build-essential

in Termanal and this time instead of telingl me it could not connect, I got a prompt to insert the Ubuntu CD and it seemed to work.  Thank you for all your help in trying to figure this out and also for providing explanations in addition to the terminal commands - I have a hard time just typing stuff and hoping that it will work without knowing what I'm actually doing.

I think I may have it pretty well figured out but I still have a question:  What does the "sudo" part of a command do?  I find that if I don't have permission to do something I just forward the command with "sudo" and it works...?  Also, what is the default password to log in as "root"?  This is the superuser account, correct?

---

### Post by odbasta on 2007-07-12
Here's a link to some Sudo info..

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I'm also a freakin noob at this, but as far as I can tell, prefacing a command with "sudo" is almost like issuing that command as root.  In which case, I don't really see the need to ever log in as root, unless for some obscure hardware issues or something.

Hope this helps.

---

### Post by User X on 2007-07-12
hmm... I thought I had it but I just rebooted to computer and now the settings are not taking... I think I have messed it up.  How do I remove Ndiswrapper and all of its contents to start over???

---

### Post by User X on 2007-07-12
It says I have an old version of "package" - where do I get a new version???

---

### Post by User X on 2007-07-12
Ok, when I restart the computer the wireless goes away... I don't have to reload the driver every time do I???

---

### Post by jw5801 on 2007-07-12
You shouldn't have to manually reload it every time. All you have to do is add ndiswrapper to the list of kernel modules that are run at start up. To do this, input the following into terminal: ```
sudo echo ndiswrapper >> /etc/modules
```
"echo" will print again whatever you type after it, and the >> tells the terminal to print the output of "echo" into the file after it. You may get a permissions error here in which case try the following:
```
sudo -s
echo ndiswrapper >> /etc/modules
exit
```
Where "sudo -s" makes any command executed after it be done as root, and "exit" leaves this state.

After that, ndiswrapper should be running when you start up.

Can you post this "package" error if you're still getting it? Not sure what would 'cause that... when you are connected to the net, try: ```
sudo apt-get update
sudo apt-get upgrade
```
and see if that changes anything.

and on an earlier note, there is no "default root password" in fact you can't log in with full root privelages. This is one of linux's main strengths against viruses (and also the main vulnerability of XP) because it means a virus can't just edit everything throughout the system and break it, because it would need root privelages to do that, and it can't get them.

So you have got the wireless working? It's just getting it to start up when you boot up your computer? Also check out this [thread.](http://ubuntuforums.org/showthread.php?t=297092) It's specifically about one wireless card, but all the ndiswrapper commands and stuff are the same, the only difference is what driver you need to use.

---

### Post by User X on 2007-07-13
This is from the instalation page at ndiswrappers web sit:

"To load the module type modprobe ndiswrapper. If you get no error, the driver should now be loaded. You can verify this by checking the system log produced by dmesg. If the driver is loaded successfully, you should see a message in the system log ndiswrapper version version loaded Make sure the version version here matches the version of ndiswrapper package that you downloaded and installed. If you get a different version, you have an old version of **package**, which you should uninstall, and then go back to step 1."

I am installing version 1.47, but I get a version of 1.32 from the dmesg command???  So I guess I have an old version of "package"?  Or should that read: "the package"?  Thank you for all your help you are very knoledgeable about linux/ubuntu; may I ask how you know so much?  Again I am very greatfull.  I will try to get ndiswrapper running at startup now.

I have gotten as far as being able to view my wireless network, but I'm still having problems connecting.  I have not had much time to figure out what causes this.  I get the essid and can see the router using the network tool in the top right corner of the desktop, and it has the option to connect to wireless networks now.  But when I enter my WEP key I do not get a connection.  It tries and tries but no connection...?

The post you recomended I read was helpful.  There are many commands listed there that I didn't do - that said I think I am Ok with the way I went about getting where I got (if that sentance makes any sence).  He used the unzip command to open an *.exe file though; is this typicaly of how you unwrap a *.exe file in linux?

---

### Post by jw5801 on 2007-07-13
Hmm... So you put:
```
modprobe ndiswrapper
```
and then the output of ```
dmesg | grep ndiswrapper
```
gives you "ndiswrapper version 1.32 loaded"? I think that would mean that there's an old version of ndiswrapper installed as well as the current one. Could that be the case? If so try:
```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
```
then (making sure you're in the directory you extracted ndiswrapper.tar.gz into) run ```
sudo make uninstall
``` repeatedly until you get the same output a few times in a row, then run:
```
sudo make
sudo make install
sudo modprobe ndiswrapper
dmesg | grep ndiswrapper
```
and see if you get the right version.

For background info the "|" is called a pipe and it sends the output of the command before it to the input of the comand after it. When used with "grep *keyword*" it will search through the ouput and only print lines containing *keyword*, which is very useful for this sort of thing!

Also, is your driver listed in the output of ```
ndiswrapper -l
``` and if so, is there an alternate driver listed as well? If there is make sure you add it to the blacklist file:
```
sudo -s
echo blacklist *AlternateDriver* >> /etc/modprobe.d/blacklist
exit
```
(where *AlternateDriver* is the alternate listed in ndiswrapper -l)else it will prevent the ndiswrapper driver from working.

As far as extracting a .exe "unzip" is usually the first option, there's a couple of others listed on the ndiswrapper site, but I've only ever done it once and that was to get my driver from an install file. And the reason I have some idea what I'm doing with ndiswrapper is that I went through all this to get mine working too. I've also done a bit of programming at uni (hence the big explanation about C and compilers :p) so command line stuff tends to come pretty naturally to me.

Glad to be of help!

---

### Post by User X on 2007-07-13
Thank you for the Pipe information, thats handy.  I will try the uninstall/reinstall advice tonight.  As far as the driver goes, it does recognize the card, and there are no alternate devices listed.  It adds wireless connectivity to the networking tool in the upper right hand corner icon on my desktop, and when used it even sees my network.  It won't connect yet though.  Also any changes I make during a session seem to be wiped out when I reboot the machine.

On a side note you will be happy to know I fixed my screen resolution without even having to bug you with the problem!  I can now advance it to the resolution I would like, where as before it wouldn't go past 1280x768.:)

---

### Post by anewguy on 2007-07-13
As a very new person to Linux and Ubuntu, do you mind if I ask why you are compiling ndiswrapper? :)  When first tried Ubuntu I also followed that download/compile page and had nothing but problems.   I ended up just reintalling Ubuntu and then  I just installed ndiswrapper.from the LiveCD and also installed network-manager-gnome (since I use the gnome desktop manager).  The only problem I had in the entire process with my notebook was locating the correct Windows .sys and .inf files for my wireless - ndiswrapper itself just worked.

Since I am VERY new at this I am curious in what situations do you need to compile ndiswrapper instead of just installing the binary?

---

### Post by jw5801 on 2007-07-13
> **anewguy said:**
> As a very new person to Linux and Ubuntu, do you mind if I ask why you are compiling ndiswrapper? When first tried Ubuntu I also followed that download/compile page and had nothing but problems. I ended up just reintalling Ubuntu and then I just installed ndiswrapper.from the LiveCD and also installed network-manager-gnome (since I use the gnome desktop manager). The only problem I had in the entire process with my notebook was locating the correct Windows .sys and .inf files for my wireless - ndiswrapper itself just worked.

Since I am VERY new at this I am curious in what situations do you need to compile ndiswrapper instead of just installing the binary?
The version of the ndiswrapper module that comes default with Ubuntu is a very old version. Some drivers are much more likely to work using the more recent version of it (there is a list on the ndiswrapper homepage).
Also, you shouldn't really need to install "network-manager-gnome" as it is the default network manager in gnome, and is part of any Ubuntu install :p

> **User X said:**
> Thank you for the Pipe information, thats handy.  I will try the uninstall/reinstall advice tonight.  As far as the driver goes, it does recognize the card, and there are no alternate devices listed.  It adds wireless connectivity to the networking tool in the upper right hand corner icon on my desktop, and when used it even sees my network.  It won't connect yet though.  Also any changes I make during a session seem to be wiped out when I reboot the machine.

On a side note you will be happy to know I fixed my screen resolution without even having to bug you with the problem!  I can now advance it to the resolution I would like, where as before it wouldn't go past 1280x768.:)
Good work on the screen resolution!
It appears as though linux is recognizing your wireless card, we just need to get you connected to your network. After looking around a bit, I'm lead to believe that there is an old ndiswrapper kernel module that comes as default with an Ubuntu install, so there's a good chance the two might be interfering. That might also explain why your changes are reverting after a reboot. So try uninstalling it all and starting again.

---

### Post by anewguy on 2007-07-13
> **jw5801 said:**
> The version of the ndiswrapper module that comes default with Ubuntu is a very old version. Some drivers are much more likely to work using the more recent version of it (there is a list on the ndiswrapper homepage).
Also, you shouldn't really need to install "network-manager-gnome" as it is the default network manager in gnome, and is part of any Ubuntu install :p
....

Thanks for the info.  BTW - my ndiswrapper and tools were updated by the default update manager.  It's strange about network-manager-gnome, since when I heard of it I went to synaptics and it wasn't green boxed - I actually had to install it.  Perhaps I did something else stupid somewhere!:)

---

### Post by jw5801 on 2007-07-14
Hmm... I dunno. When I look in the synaptic package manager, the version of ndiswrapper shown there is 1.38, whereas 1.47 is the most recent. I dunno about the gnome network manager, maybe because I had a usb wireless adaptor in plugged in that linux recognised out of the box the installer was smart and installed it for me... lol, No idea! What version of ndiswrapper has synaptics updated to for you? 'cause if it's the most recent then that would be very useful! Type "ndiswrapper -v" and let me know what it says under module details & version.

---

### Post by User X on 2007-07-14
Well, good news and bad...  First, I uninstalled ndiswrapper, then installed it again - this time the version is correct (yahoo!).  I loaded my drivers and viola!  My wireless network shows up in the list of networks - so I tried to connect and it even let me connect!!!  (I knew something had to go wrong though!)  I rebooted the computer to see if the changes stuck and kerpow!  They did!!!  On start up it asked to the key to gain access to my network -  However I can connect to the network but I can't get online...?  Firefox just gives me mesages that it can't connect to anything...???

---

### Post by jw5801 on 2007-07-14
Hmm... well we certainly got ndiswrapper working which is good! Can you access anything else that's shared on your network? In Firefox under Edit > Preferences, take a look at the "how Firefox connects to the internet" part and see what it has (I attached a screenshot of where it is to this post). Mine is just set to "direct connection to the internet" but I guess it would depend on how your network was set up. Did you have to configure any proxy settings on any other computers on the network?

---

### Post by anewguy on 2007-07-14
> **jw5801 said:**
> Hmm... I dunno. When I look in the synaptic package manager, the version of ndiswrapper shown there is 1.38, whereas 1.47 is the most recent. I dunno about the gnome network manager, maybe because I had a usb wireless adaptor in plugged in that linux recognised out of the box the installer was smart and installed it for me... lol, No idea! What version of ndiswrapper has synaptics updated to for you? 'cause if it's the most recent then that would be very useful! Type "ndiswrapper -v" and let me know what it says under module details & version.

Apparently mine must have been older and updated to 1.38, as that is what the version shows.

Thanks again for the info, and also thanks for being so helpful to everyone on this forum!:)

---

### Post by User X on 2007-07-15
I don't have anything else to access over my network - unless I can try to ping my laptop or something...?  Oddly enough though I can't access the routers firmware from firefox using the routers IP address...?  I will check that screen in firefox and report back.  I can't stay online long though - my dog ate through my AC Power supply chord on the laptop and now I only have %41 battery life till later this week!

---

### Post by User X on 2007-07-15
Ok, I checked that setting page about how firefox connects to the internet on both my laptop and my desktop (the ubuntu machine).  On the laptop it's set to "connect directly to the internet" and on the desktop it is also set to "connect directly to the internet".  Any other ideas???  When I do an iwconfig I see my network and it ways it has a %25 signal.  Does this mean it is connected or just is recieving a signal?

---

### Post by jw5801 on 2007-07-15
Haha, tough break on the power cable! Did you try pinging the router (or your desktop) from your laptop? Open up a terminal and put in ```
ifconfig
``` and we'll check if you've been given a proper IP address (eth1 or wlan1 or something like that will be your wireless interface). Would your router have restricted access (ie. only allow access to known hardware addresses)? My iwconfig looks like this while I'm connected to my wireless network, so hopefully yours looks similar:
> eth1      IEEE 802.11g  ESSID:"Motorola7169"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:A5:91:B8:34   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:40  Invalid misc:79   Missed beacon:0
When you say you get a connection, does the network manager applet say something along the lines of "Wireless network connection to 'Essid' (blah%)" when you hover over it?

Sorry if that rambles a bit I'm just firing out ideas as they come into my head :p
First port of call would be to look at "ifconfig," then try pinging your router. If neither of those are working (ie. no IP address and no response from ping), then have a look at the settings on your router. It sounds as though linux is reconizing your wireless card, so the problem is most likely on the network end.

---

### Post by User X on 2007-07-16
I will go try this now.  Should I leave the setting in linux to manual configurationg or roaming mode?  I can't write to long a post cause I only have %23 power left... I get just about the same thing when I do an iwconfig.  I get my essid, and only a %26 connection strength.  Ok I will go try it now and get back to this thread later this morning from work...  Thanks for the help!

---

### Post by jw5801 on 2007-07-16
Leave it in roaming if you can. If it can read the network and connect without you needing to input the essid then that would seem like a good sign. Good luck!

---

### Post by User X on 2007-07-16
Ok, I can't ping the router, and I can't ping my other computer.  I did ifconfig and everything seemed normal, I got an IP address of 192.168.1.102.  It does say it is connected to my essid when I hover my mouse over it.  What settings am I looking for in my router...?  I would think I should be able to connect to it's firmware through my Ubuntu computer but I can't.  I will access it from my laptop - hope it doesn't take more than 35 minutes...  Any more ideas??  Could I maybe have the wrong driver in ndiswrapper - would this change anything?

---

### Post by jw5801 on 2007-07-16
Hmm... Well since linux is recognising your wireless card and appears to be functioning correctly I would think you had the right driver. What did you use and what card do you have? It may be that there's a default driver in Ubuntu that would interfere unless you blacklist it.

As for the router, on mine under the "Wireless" tab there's a section labeled "MAC Access Control" and another labeled "MAC Access Control List." Check for something similar and make sure either the hardware address of the wireless card is on the list (it'll be a string of hexadecimal numbers like "00:11:7E:A3:FD") or that the overall setting is set to "allow any station access" or something similar to that.

---

### Post by User X on 2007-07-16
The card is not really a card, it's a chip on the motherboard.  It is the marvel 88W8388 chip.  It's an Asus A8V-E deluxe motherboard.  

     Authentication Type: Auto 
      Basic Rate: 1-2 Mbps
      Transmission Rate: 2       
     CTS Protection Mode: Disable     
      Frame Burst: Disable   
      Beacon Interval:   100     
      DTIM Interval:  1     
      Fragmentation Threshold: 2346
      RTS Threshold:   2347 
      AP Isolation: Off 
      Secure Easy Setup:Enable
  These are my routers advanced settings and all the mac filtering is disabled.  gota go no battery...

---

### Post by jw5801 on 2007-07-16
Ok, well the only other thing I can think of to try, is turning off all the encryption and security settings and seeing if there's any difference then. If that doesn't work then I'm out of ideas so you might want to start a thread in the "Networking & Wireless" forum. List your chip, the driver you used, and if you can post the output to ifconfig and iwconfig. Sorry I can't be of more help!

---

### Post by User X on 2007-07-17
Oh, don't be sorry!  You have been a great deal of help!  Thanks so much, I will try the networking forum and see if someone over there knows what I am doing wrong.  Thanks again!

---

