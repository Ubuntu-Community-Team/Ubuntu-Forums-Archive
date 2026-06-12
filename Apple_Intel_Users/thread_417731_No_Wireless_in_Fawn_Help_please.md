---
title: "No Wireless in Fawn Help please"
date: 2007-04-21
forum: Apple Intel Users
---

### Post by bigred3373 on 2007-04-21
Anyone figure out how to get Airport Extreme to connect to the web? Seems also my Ethernet connection isn't going to work it was then quit i had to switch back to my OS X to post this i been searching but have not found anything of use:confused:   thank you in advanced  i was trying the network in Ubuntu it kept saying i was connected but nothing loaded up  I am using 17 inch IMAC Intel core duo not the core 2 duo and not a macbook :) I posted in networking and wireless seems there isn't a soultion to it :(

---

### Post by ronocdh on 2007-04-22
> **bigred3373 said:**
> Anyone figure out how to get Airport Extreme to connect to the web? Seems also my Ethernet connection isn't going to work it was then quit i had to switch back to my OS X to post this i been searching but have not found anything of use:confused:   thank you in advanced  i was trying the network in Ubuntu it kept saying i was connected but nothing loaded up  I am using 17 inch IMAC Intel core duo not the core 2 duo and not a macbook :) I posted in networking and wireless seems there isn't a soultion to it :(
I have heard very few reports of wireless working well in Feisty, especially on Macs. Best bet for now is to plug in via ethernet.

---

### Post by Greywhind on 2007-04-22
Actually, you CAN get your wireless working. I just did it, and it's not hard. I also have a 17" iMac Intel Core Duo, with a Broadcom 4310 wireless card.

First, to check if you also have the same card, do this:
```
lspci | grep Broadcom\ Corporation
```

If you see something involving the number 4310, you can use the following to get it working:

1. Open System->Administration->Network and find the device eth1. Open the settings for eth1, and uncheck the box that says "Roaming". This will prevent NetworkManager for interfering with the following process. (NetworkManager is that networking icon in the upper-right corner of your screen.) For some reason, NetworkManager didn't work for me, and I had to turn it off when I installed the wireless driver.

2. Open synaptic package manager (from System->Administration->Synaptic Package Manager) or a terminal.

3. If using synaptic, search (ctrl+f) for "ndiswrapper" and select the packages related to ndiswrapper, then install them.

4. If using terminal, type:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils
```

5. Open a terminal and type:
```
sudo gedit /etc/modprobe.d/blacklist
```

6. Add these lines to the file so nothing interferes with ndiswrapper, then save it:
```
# remove the following to allow use of bcm43xx for wireless
blacklist bcm43xx
```

7. Download the driver for your card at the following link:
```
ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
```

8. Either use synaptic or a terminal to install cabextract:
```
sudo apt-get install cabextract
```

9. Run the command:
```
cabextract sp33008.exe
``` (do this if you're already in the directory with sp33008.exe in it, if not, use "cd <path to sp33008.exe>" to get to that directory first.)

10. While still in the same directory as sp33008.exe, run the command:
```
sudo ndiswrapper -i bcmwl5.inf
``` (that's a lowercase I as in "Into")

11. Type:
```
sudo ndiswrapper -l
``` (that's a lowercase L as in "Loopy")

12. If you see something like, "Driver installed," you've done it right.

13. Type:
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo gedit /etc/modules
```

14. Add the following line to the file:
```
ndiswrapper
```

15. Type:
```
sudo iwconfig
```

16. If you see a device called "eth1," everything is probably working correctly.

17. You can also type the following command to make sure your wireless card is seeing networks, especially yours. Also, it can help you know what your network's ESSID is for the next step:
```
sudo iwlist scan
```

18. Type:
```
sudo iwconfig eth1 essid "<YOUR NETWORK'S NAME>"
``` (where <YOUR NETWORK'S NAME> is actually the name you gave your network)
```
sudo iwconfig eth1 key restricted <YOUR WEP PASSWORD>
``` (where <YOUR WEP PASSWORD> is actually the password for your network. NOTE: This assumes you're using a WEP password. If not, don't do this step.)

19. Type:
```
sudo dhclient
```

20. If it seems to have gotten an IP address and you can open web pages, you've successfully finished configuring your wireless network. Congratulations.

Good luck. I hope this works for you. If not, please post here again - it's possible I mistyped something.

---

### Post by ronocdh on 2007-04-22
That is one killer post. I assume anyone can substitute a different driver based on their chipset, perhaps by consulting the ndiswrapper page on SourceForge?

---

### Post by ronocdh on 2007-04-22
> **ronocdh said:**
> That is one killer post. I assume anyone can substitute a different driver based on their chipset, perhaps by consulting the ndiswrapper page on SourceForge?
Well, the driver I found online was the net5416, which ironically (to me, anyway) is the same one Apple provides for XP. I tried using both versions, but I'm stuck. ```
ragnarok@DragonBoat:~$ ndiswrapper -l
inf : invalid driver!
net5416 : driver installed
ragnarok@DragonBoat:~$ 

```
Help?

---

### Post by Greywhind on 2007-04-22
I'm afraid I don't know exactly what your problem is, since I haven't tried other cards than my BCM4310.

Did you check sudo iwconfig and sudo iwlist scan to see if it was actually working despite saying the driver was invalid? I doubt it, but I suppose it's possible.

Maybe you could look up exactly what wireless card you have and then search the web for other tutorials about getting it working.

In fact, the driver should be the same one as the Windows one, since ndiswrapper really just makes Windows wireless drivers work in Linux.

Hope you manage to fix it.

---

### Post by Tyrdium on 2007-04-22
The C2D Macbook Pros use the Atheros AR5418. I've been having a similar problem to ronocdh with the Lenovo and D-Link drivers.

I grabbed the Atheros driver installers (not sure which to use) from the Boot Camp drivers CD image and uploaded them to [here](http://tinyload.com/1694). I'll probably try them out tomorrow.

---

### Post by miguev on 2007-04-22
Hey!
Unless you want to use WPA encription you don't need to use ndiswrapper anymore, you can use [madwifi 0.9.10.30]("http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n") (experimental, but works fine for me).
I'm very happy to tell you this because [it was just when I loaded the Atheros XP drivers with ndiswrapper when my keyboard and mouse became unusable]("http://ubuntuforums.org/showthread.php?p=2345424#post2345424").
Now my MacBook Core 2 Duo is working fine in both network interfaces, the NetworkManager applet (nm-applet) is making everything so easy... I have more details and some screenshots in [my blog]("http://www.miguev.net/2007/04/15/ubuntu-704-feisty-beta-en-macbook-core-2-duo/") (in Spanish)

---

### Post by ronocdh on 2007-04-22
> **Tyrdium said:**
> The C2D Macbook Pros use the Atheros AR5418. I've been having a similar problem to ronocdh with the Lenovo and D-Link drivers.

I grabbed the Atheros driver installers (not sure which to use) from the Boot Camp drivers CD image and uploaded them to [here](http://tinyload.com/1694). I'll probably try them out tomorrow.
I have tried those already, to no avail. Please try, though, and post your results; I'm worried that I "misinstalled" them, because I originally used the command series given [here]("https://help.ubuntu.com/community/MacBook"). That worked for me in Edgy, but it's a no-go in Feisty.

I am unable to remove the net5416 driver now! Says **incorrect ioctl**, and it stays. Argh. 

And miguev, WEP is a must for me, but thank you! ;)

---

### Post by saxin on 2007-04-22
I have not installed Ubuntu Feisty Fawn on my Macbook Core Duo, but I used the LiveCD. My wireless worked out of the box with WEP when I used the LiveCD.

---

### Post by Greywhind on 2007-04-22
Actually, ronocdh, if all you need is WEP encryption, not WPA, then you should use Madwifi, or so I've heard, for an Atheros wireless card (Note: WEP is different from WPA).

---

### Post by Alfdog on 2007-04-22
THANK YOU SO MUCH! Greywhind

I'm using that #$%^$ (broadcom) 4310 card in my Dell m1210, so I can use OSx86.  Your post did the trick, I think my main problem was finding the right windows drivers, since there are so many to choose from.

thanks again
alf

---

### Post by bigred3373 on 2007-04-22
seems i got my work cut out for me will let you all know if the first time works i am not good at all the coding so i will get back soon thanks all of you are the best here:):KS :KS

---

### Post by ronocdh on 2007-04-22
> **bigred3373 said:**
> seems i got my work cut out for me will let you all know if the first time works i am not good at all the coding so i will get back soon thanks all of you are the best here:):KS :KS
This guy makes me grin like crazy.

---

### Post by Tyrdium on 2007-04-22
Posting from wireless on Ubuntu. The madwifi SVN release works great. :D

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Actually, you CAN get your wireless working. I just did it, and it's not hard. I also have a 17" iMac Intel Core Duo, with a Broadcom 4310 wireless card.

First, to check if you also have the same card, do this:
```
lspci | grep Broadcom\ Corporation
```

If you see something involving the number 4310, you can use the following to get it working:

1. Open System->Administration->Network and find the device eth1. Open the settings for eth1, and uncheck the box that says "Roaming". This will prevent NetworkManager for interfering with the following process. (NetworkManager is that networking icon in the upper-right corner of your screen.) For some reason, NetworkManager didn't work for me, and I had to turn it off when I installed the wireless driver.

2. Open synaptic package manager (from System->Administration->Synaptic Package Manager) or a terminal.

3. If using synaptic, search (ctrl+f) for "ndiswrapper" and select the packages related to ndiswrapper, then install them.

4. If using terminal, type:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils
```

5. Open a terminal and type:
```
sudo gedit /etc/modprobe.d/blacklist
```

6. Add these lines to the file so nothing interferes with ndiswrapper, then save it:
```
# remove the following to allow use of bcm43xx for wireless
blacklist bcm43xx
```

7. Download the driver for your card at the following link:
```
ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
```

8. Either use synaptic or a terminal to install cabextract:
```
sudo apt-get install cabextract
```

9. Run the command:
```
cabextract sp33008.exe
``` (do this if you're already in the directory with sp33008.exe in it, if not, use "cd <path to sp33008.exe>" to get to that directory first.)

10. While still in the same directory as sp33008.exe, run the command:
```
sudo ndiswrapper -i bcmwl5.inf
``` (that's a lowercase I as in "Into")

11. Type:
```
sudo ndiswrapper -l
``` (that's a lowercase L as in "Loopy")

12. If you see something like, "Driver installed," you've done it right.

13. Type:
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo gedit /etc/modules
```

14. Add the following line to the file:
```
ndiswrapper
```

15. Type:
```
sudo iwconfig
```

16. If you see a device called "eth1," everything is probably working correctly.

17. You can also type the following command to make sure your wireless card is seeing networks, especially yours. Also, it can help you know what your network's ESSID is for the next step:
```
sudo iwlist scan
```

18. Type:
```
sudo iwconfig eth1 essid "<YOUR NETWORK'S NAME>"
``` (where <YOUR NETWORK'S NAME> is actually the name you gave your network)
```
sudo iwconfig eth1 key restricted <YOUR WEP PASSWORD>
``` (where <YOUR WEP PASSWORD> is actually the password for your network. NOTE: This assumes you're using a WEP password. If not, don't do this step.)

19. Type:
```
sudo dhclient
```

20. If it seems to have gotten an IP address and you can open web pages, you've successfully finished configuring your wireless network. Congratulations.

Good luck. I hope this works for you. If not, please post here again - it's possible I mistyped something.
AT NUMBER 9 I RUN THE COMMAND AND I GET ERROR NO SUCH FILE OR DIRECTORY I DOWNLOADED THE FILE SP33008.EXE ITS ON MY DESKTOP THIS IS WHERE I FAILED WHAT WENT WRONG IS IT NO DOWNLOADED TO A PROPER LOCATION???  also i messed around with network manager and got the wireless bars to show up at 0% then lost that as well kind of weird now i cant get nothing. i manually did something and got those bars up hmmmmmm  thank god for this old ppc clamshell which i want to install ubuntu but i get the black screen of death when it loads up cant see nothing i need the correct vert and refresh rates any ideas then ill have dapper.........??

---

### Post by bigred3373 on 2007-04-22
> **ronocdh said:**
> This guy makes me grin like crazy. lol WELL I GOT STUCK AND NEED A BAIL OUT.

---

### Post by ronocdh on 2007-04-22
> **bigred3373 said:**
> AT NUMBER 9 I RUN THE COMMAND AND I GET ERROR NO SUCH FILE OR DIRECTORY I DOWNLOADED THE FILE SP33008.EXE ITS ON MY DESKTOP THIS IS WHERE I FAILED WHAT WENT WRONG IS IT NO DOWNLOADED TO A PROPER LOCATION???
This is happening because you have not specified the directory where the file is. To do this, type (in the terminal):
```
cd /home/bigred3373/Desktop/FolderWithDrivers
```
Now, I just guessed at the path. Replace "bigred3373" with your username in Ubuntu, and the "FolderWithDrivers" with the, well, with the folder with drivers! =) This is assuming it's placed on your desktop. The **cd** command you just used is for "change directory."

Hope this helps!

---

### Post by bigred3373 on 2007-04-22
> **ronocdh said:**
> This is happening because you have not specified the directory where the file is. To do this, type (in the terminal):
```
cd /home/bigred3373/Desktop/FolderWithDrivers
```
Now, I just guessed at the path. Replace "bigred3373" with your username in Ubuntu, and the "FolderWithDrivers" with the, well, with the folder with drivers! =) This is assuming it's placed on your desktop. The **cd** command you just used is for "change directory."

Hope this helps!
 i suppose i have to start all over from scratch right? i will try this thanks gotta start over i am sure of it :) do i type that in before i start #9  where would i add it???   its saved on my desktop not in a folder you lost me with the folderwithdrives thing do i need to type that in as well?


should i get the book the offical ubuntu or is there another one out there already for the newest fawn? will it help me in this array of commands?  :)

---

### Post by ronocdh on 2007-04-22
> **bigred3373 said:**
> i suppose i have to start all over from scratch right? i will try this thanks gotta start over i am sure of it :) do i type that in before i start #9  where would i add it???   its saved on my desktop not in a folder you lost me with the folderwithdrives thing do i need to type that in as well?


should i get the book the offical ubuntu or is there another one out there already for the newest fawn? will it help me in this array of commands?  :)
Well, the cabextract utility is basically going to take the .exe of the drivers and rip it open, effectively barfing its contents all over the directory it was in. If you have it on the desktop, that means your desktop will immediately become cluttered with the contents of the driver package. So I would advise that you drop the .exe into its own folder on the desktop, and use the **cd** command to point to that directory. By using that command, you effectively tell any commands (that are locally oriented) to operate within that context.

---

### Post by Tyrdium on 2007-04-22
> **ronocdh said:**
> Well, the cabextract utility is basically going to take the .exe of the drivers and rip it open, effectively barfing its contents all over the directory it was in.Best description ever.

---

### Post by ronocdh on 2007-04-22
> **Tyrdium said:**
> Best description ever.
Thank you. But that laughter wasn't free: please post a brief how-to on these dern madwifi drivers, because the madwifi page is completely unintelligible to me! Needs more "barf" phrasings IMO.

---

### Post by bigred3373 on 2007-04-22
> **ronocdh said:**
> Well, the cabextract utility is basically going to take the .exe of the drivers and rip it open, effectively barfing its contents all over the directory it was in. If you have it on the desktop, that means your desktop will immediately become cluttered with the contents of the driver package. So I would advise that you drop the .exe into its own folder on the desktop, and use the **cd** command to point to that directory. By using that command, you effectively tell any commands (that are locally oriented) to operate within that context.


Okay i got that but does it matter which step i use it in? i put the setup in a folder and gave the same name as the applications.  I also tinkered around again with the net worker it seems well if nothing is enabled like the Ethernet or ports you click on the icon that looks like 2 montiors and it gives you wireless options and turns the icon into bars for wireless  you have the option to setup new wireless device though its not working wont give signal but thought i should ladle this out for everyone.

---

### Post by ronocdh on 2007-04-22
> **bigred3373 said:**
> Okay i got that but does it matter which step i use it in? i put the setup in a folder and gave the same name as the applications.  I also tinkered around again with the net worker it seems well if nothing is enabled like the Ethernet or ports you click on the icon that looks like 2 montiors and it gives you wireless options and turns the icon into bars for wireless  you have the option to setup new wireless device though its not working wont give signal but thought i should ladle this out for everyone.
Yes, do this as a preface to step 9. Greywhind was kind enough to advise the reader to do this; you can see his reminder just below the code listed in step 9.

---

### Post by Tyrdium on 2007-04-22
> **ronocdh said:**
> Thank you. But that laughter wasn't free: please post a brief how-to on these dern madwifi drivers, because the madwifi page is completely unintelligible to me! Needs more "barf" phrasings IMO.Heh, no problem.

sudo aptitude install build-essential
sudo aptitude install subversion
svn co [http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10](http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10)
cd madwifi-hal-0.9.30.10
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo wlanconfig ath0 list scan (scan for APs)
sudo iwconfig ath0 essid "foo" (connect to open AP "foo")
sudo dhclient ath0 (get IP address from DHCP)
[Etc.](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo), according to guide.

---

### Post by bigred3373 on 2007-04-22
> **ronocdh said:**
> Yes, do this as a preface to step 9. Greywhind was kind enough to advise the reader to do this; you can see his reminder just below the code listed in step 9.

well i am still getting the error message no such file or directory and i post it like this
*cd /home/shellie-desktop/desktop/hush* is the name of the folder did i do this right i am seriously doubting this. The folder is named hush its on the desktop  with the setup sp33008.exe it refuses to pick up this file frustrated as heck should i restart from number 1 i used the synaptic update manager to download the files needed packages i mean grrrrrrrrrrrr.......

After i downloaded the file from step 7 i didn't know where to save it to so it downloaded to my desktop and you said to put in a folder so it dont puke up my desktop LOL. So if there was a place to save it i wasnt aware of it thanks again you guys

---

### Post by ronocdh on 2007-04-22
> **bigred3373 said:**
> well i am still getting the error message no such file or directory and i post it like this
*cd /home/shellie-desktop/desktop/hush* is the name of the folder did i do this right i am seriously doubting this. The folder is named hush its on the desktop  with the setup sp33008.exe it refuses to pick up this file fustrated as heck should i restart from number 1 i used the snaptic update manager to download the files needed packages i mean grrrrrrrrrrrr.......
I believe Desktop must be capitalized. Details, details!

---

### Post by ronocdh on 2007-04-22
> **Tyrdium said:**
> Heh, no problem.

sudo aptitude install build-essentials
sudo aptitude install subversion
svn co [http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10](http://svn.madwifi.org/branches/madwifi-hal-0.9.30.10)
cd madwifi-hal-0.9.30.10
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo wlanconfig ath0 list scan (scan for APs)
sudo iwconfig ath0 essid "foo" (connect to open AP "foo")
sudo dhclient ath0 (get IP address from DHCP)
[Etc.](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo), according to guide.
Thank you very much, Tyrdium. I get this error on the first step:
```
ragnarok@DragonBoat:~$ sudo aptitude install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essentials"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
ragnarok@DragonBoat:~$ 

```
I have all sources checked, such as Universe, Multiverse, etc. I tried continuing beyond this point because I'm like that, and at **make** I get this mess:
```
ragnarok@DragonBoat:~/madwifi-hal-0.9.30.10$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/ragnarok/madwifi-hal-0.9.30.10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ragnarok/madwifi-hal-0.9.30.10/ath/if_ath.o
  CC [M]  /home/ragnarok/madwifi-hal-0.9.30.10/ath/if_ath_pci.o
  LD [M]  /home/ragnarok/madwifi-hal-0.9.30.10/ath/ath_pci.o
  CC [M]  /home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/ah_os.o
  HOSTCC  /home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c: At top level:
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c: In function 'main':
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal/uudecode] Error 1
make[2]: *** [/home/ragnarok/madwifi-hal-0.9.30.10/ath_hal] Error 2
make[1]: *** [_module_/home/ragnarok/madwifi-hal-0.9.30.10] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
ragnarok@DragonBoat:~/madwifi-hal-0.9.30.10$ 

```
If it's any help, next step I get:
```
ragnarok@DragonBoat:~/madwifi-hal-0.9.30.10$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.20-15-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/ragnarok/madwifi-hal-0.9.30.10/ath'
test -d //lib/modules/2.6.20-15-generic/net || mkdir -p //lib/modules/2.6.20-15-generic/net
cp ath_pci.ko //lib/modules/2.6.20-15-generic/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ragnarok/madwifi-hal-0.9.30.10/ath'
make: *** [install-modules] Error 1
ragnarok@DragonBoat:~/madwifi-hal-0.9.30.10$ 

```
=(

---

### Post by bigred3373 on 2007-04-22
> **ronocdh said:**
> I believe Desktop must be capitalized. Details, details!

I did I did Desktop was capital i swear it it didnt work it keeps saying no file arggggggggggg!!! omg i don't know what i did it finally says all done no errors!! holy cow do i go on with other steps of course  i went to number 10 and typed in as shown here is the promt   ***shellie@shellie-desktop: /Desktop/hush$ sudo ndiswrapper -i bcmw15.inf   got this error installing bcmw15..... couldn't open bcmw15.inf  No such file or directory at usr/sbin/ndiswrapper-1.9 line 174 *** it says while in same directory run that command i did and the result above was what i got??????? oops big mistake bcmw 15 is not 15 its l5 duh doh then it said invalid driver then said driver installed  arrrrrgggggg i am going bonkers next lol number 13 am i supposed to type all that in at once?

---

### Post by Greywhind on 2007-04-22
Ok, bigred3373 - I think you're close now.

Start right between step 8 and 9 in my guide.

Type:
```
cd /home/shellie-desktop/Desktop/hush/
```

Type:
```
ls
```

Do you see the file "sp33008.exe" in the listing? If so, go on to the next step, which is step 9. If that works, do:
```
ls
```

If you see "bcmwl5.inf" in the listing, go on to step 10. If not, please post the log of what commands you typed and what responses you got to them here.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Ok, bigred3373 - I think you're close now.

Start right between step 8 and 9 in my guide.

Type:
```
cd /home/shellie-desktop/Desktop/hush/
```

Type:
```
ls
```

Do you see the file "sp33008.exe" in the listing? If so, go on to the next step, which is step 9. If that works, do:
```
ls
```

If you see "bcmwl5.inf" in the listing, go on to step 10. If not, please post the log of what commands you typed and what responses you got to them here.

thank you   sorry for all this i am on step 13 know what is the code to put in you have 3 there? i got past the other steps right lol

---

### Post by Greywhind on 2007-04-22
You have to do all three. Do them in the order I typed them in my guide.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> You have to do all three. Do them in the order I typed them in my guide.

um in order do i hit enter after them all? do enter the word ndiswrapper on the pop up menu i got  named modules (/etc) -gedit and where if so

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2  below this one? what about the next codes sudo i config is that in the pop up i got or do i go bck to termnial almost done dont leave me lol

---

### Post by Greywhind on 2007-04-22
Hit enter in between each one.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Hit enter in between each one.

do enter the word ndiswrapper on the pop up menu i got named modules (/etc) -gedit and where if so

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2 below this one? what about the next codes sudo i config is that in the pop up i got or do i go bck to termnial almost done dont leave me lol

---

### Post by Greywhind on 2007-04-22
Just add "ndiswrapper" below the last line in that file. (don't put the quotes in)

Then go back to terminal for the next part, after saving the file and closing it.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Just add "ndiswrapper" below the last line in that file. (don't put the quotes in)

Then go back to terminal for the next part, after saving the file and closing it.

sudo iwlist scan gives me error interface dosen't support scanning???? should i move about to 18 or stop there?

---

### Post by Greywhind on 2007-04-22
When you type iwconfig, does eth1 show up?

Also, if you type sudo iwlist scan, is the error the only thing it gives you?

Finally, if you type ndiswrapper -l (that's a lowercase L as in "Larry"), what does it say?

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> When you type iwconfig, does eth1 show up?[B] eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/B]

Also, if you type sudo iwlist scan, is the error the only thing it gives you?
s[B]hellie@shellie-desktop:~/Desktop/hush$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.
[/B]

Finally, if you type ndiswrapper -l (that's a lowercase L as in "Larry"), what does it say?s[B]udo ndiswrapper -l
bcmw15 : invalid driver!
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

[/B]
s[B]hellie@shellie-desktop:~/Desktop/hush$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device
[/B]
 I CUT COPIED PASTE I AM ONLINE WITH THIS COMPUTER THROUGH THE ETHERNET IS THAT POSING A PROBLEM? OR DID I GOOF ALONG THE WAY SOMWHERE ??BELOW IS ALL I DID I HOPE THAT WAS SOME HELP TO LONG OMG SORRY


shellie@shellie-desktop:~$ sudo apt-get install cabextract
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shellie@shellie-desktop:~$ cd /home/shellie-Desktop/desktop/hush
bash: cd: /home/shellie-Desktop/desktop/hush: No such file or directory
shellie@shellie-desktop:~$ cd /home/shellie-Desktop/desktop/hush cabextract sp33008.exe
bash: cd: /home/shellie-Desktop/desktop/hush: No such file or directory
shellie@shellie-desktop:~$ '/home/shellie/Desktop/hush'
bash: /home/shellie/Desktop/hush: is a directory
shellie@shellie-desktop:~$ cd /home/shellie/Desktop/hush
shellie@shellie-desktop:~/Desktop/hush$ cabextract sp33008
sp33008: No such file or directory

All done, errors in processing 1 file(s)
shellie@shellie-desktop:~/Desktop/hush$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -i bcmw15.inf
installing bcmw15 ...
couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -i bcmw15. inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -l
bcmw15 : invalid driver!
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -1 bcmw15 .1nf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid'
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -l
bcmw15 : invalid driver!
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -l
bcmw15 : invalid driver!
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -l
bcmw15 : invalid driver!
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -m
Password:
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
shellie@shellie-desktop:~/Desktop/hush$ sudo modprobe ndiswrapper
shellie@shellie-desktop:~/Desktop/hush$ sudo gedit /etc/modules
sudo iwconfig
     
shellie@shellie-desktop:~/Desktop/hush$ sudo gedit /etc/modules
sudo iwconfig
shellie@shellie-desktop:~/Desktop/hush$ sudo modprobe ndiswrapper
shellie@shellie-desktop:~/Desktop/hush$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

shellie@shellie-desktop:~/Desktop/hush$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

shellie@shellie-desktop:~/Desktop/hush$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

shellie@shellie-desktop:~/Desktop/hush$

---

### Post by Tyrdium on 2007-04-22
> **ronocdh said:**
> Thank you very much, Tyrdium. I get this error on the first step:
```
ragnarok@DragonBoat:~$ sudo aptitude install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essentials"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
ragnarok@DragonBoat:~$ 

```Oho. Sorry about that. It's supposed to be "build-essential", not "build-essentials".

(Previous post now corrected.)

---

### Post by Greywhind on 2007-04-22
It looks like you're very close, at least.

Try this:
```

sudo rmmod bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan

```

If that doesn't work, try restarting and then doing the following:
```

sudo modprobe ndiswrapper
sudo iwlist scan

```

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> It looks like you're very close, at least.

Try this:
```

sudo rmmod bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan

```

If that doesn't work, try restarting and then doing the following:
```

sudo modprobe ndiswrapper
sudo iwlist scan

```

Same errors dones not support   you want me to restart the computer and d a fresh terminal? then input the codes you gave me

---

### Post by Greywhind on 2007-04-22
You could try restarting.

Another possible thing to try is to re-enable NetworkManager (roaming mode) for eth1 in System->Administration->Network. Then left-click on the NetworkManager icon (in the upper-right corner of your top bar) and tell me what the menu shows.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> You could try restarting.

Another possible thing to try is to re-enable NetworkManager (roaming mode) for eth1 in System->Administration->Network. Then left-click on the NetworkManager icon (in the upper-right corner of your top bar) and tell me what the menu shows.

Wired network connection    which i am using

wireless networks

connect to other wireless network
create New Wireless Network
Manual configuration


Restarted and tryed the codes agian same error agian
shellie@shellie-desktop:~$ sudo modprobe ndiswrapper
Password:
shellie@shellie-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

shellie@shellie-desktop:~$

---

### Post by Greywhind on 2007-04-22
Try this:
```

sudo ndiswrapper -r bcmw15 (that's a one, as in the number)
sudo ndiswrapper -l (lowercase L)

```

If it no longer shows the invalid driver, then that's good. Do the following:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

```

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Try this:
```

sudo ndiswrapper -r bcmw15 (that's a one, as in the number)
sudo ndiswrapper -l (lowercase L)

```

If it no longer shows the invalid driver, then that's good. Do the following:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

```

shellie@shellie-desktop:~$ sudo ndiswrapper -r bcmw15
shellie@shellie-desktop:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
shellie@shellie-desktop:~$ sudo rmmod ndiswrapper
shellie@shellie-desktop:~$ sudo modprobe ndiswrapper
shellie@shellie-desktop:~$ it ended here nothing else no popup or nothing

---

### Post by Greywhind on 2007-04-22
Now try sudo iwlist scan again.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Now try sudo iwlist scan again.

shellie@shellie-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device   I AM GETTING GRRRRRRR SAME PROBLEM THANK GOD I AM NOT YOUR WIFE YOU WOULD HAVE CHOKED ME BY NOW LOL LOL

shellie@shellie-desktop:~$

---

### Post by Greywhind on 2007-04-22
How strange. Everything looks like it should be working. Does NetworkManager list any wireless networks when you click on it?

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> How strange. Everything looks like it should be working. Does NetworkManager list any wireless networks when you click on it? NO just that i am connected to wired ethernet and what i posted before wirless networks connect to other wirless :( you have been so patient with me and this thank you so much for that really wish you was in florida lol you could of did this already my roaming is enabled under wirless connection no modem installed of course and agian wired connection dhcp i have gone in and disabled roaming renablked manualy try to put in my my network its dsl line from local phone company off a modem i am going to disconnect and try agian with manual config

---

### Post by Greywhind on 2007-04-22
Ok. Try turning the roaming mode off, then using steps 18-20 in my guide on page 1.

It probably won't work, but try it anyway.

Make sure you connect the wireless router to the internet first, so it can give you an IP address.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Ok. Try turning the roaming mode off, then using steps 18-20 in my guide on page 1.

It probably won't work, but try it anyway.

Make sure you connect the wireless router to the internet first, so it can give you an IP address.

nothing worked i will keep trying and redo all these steps thanks agian my brian is going to roll out of my head so i am going sign off for now fiddle a bit more and retry all the steps 1-20 agian i think it may work maybe ill keep you updated by email and here okay thanks agian      shellie

---

### Post by Greywhind on 2007-04-22
I'm sorry it didn't work easily for you - the only explanation I can think of at the moment is that you have a Broadcom 4311, which I suppose might not work with the same driver (although I saw a source that said it does).

Maybe you can find another driver that will work.

Otherwise, I don't really know what to do.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> I'm sorry it didn't work easily for you - the only explanation I can think of at the moment is that you have a Broadcom 4311, which I suppose might not work with the same driver (although I saw a source that said it does).

Maybe you can find another driver that will work.

Otherwise, I don't really know what to do.

me either thank you but you have the same broadcom right? hmmmm well i got wirless bars up where the network was but still it aint finding a siginal

---

### Post by Greywhind on 2007-04-22
You have wireless bars? That's good news at least.

I have a Broadcom 4310. The difference between the two cards could be the problem.

Unfortunately, I don't know what driver you would need if the driver is the problem.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> You have wireless bars? That's good news at least.

I have a Broadcom 4310. The difference between the two cards could be the problem.

Unfortunately, I don't know what driver you would need if the driver is the problem.

HEY I DOUBLE CHECKED AND WE HAVE SAME CARD SO SHOULD I REDO ALL THE STEPS OR NOT

shellie@shellie-desktop:~$ lspci | grep Broadcom\ Corporation
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
shellie@shellie-desktop:~$

---

### Post by Greywhind on 2007-04-22
Oh - I guess we do have the same. Sorry.

I guess you should redo the steps... not sure what could have gone wrong.

---

### Post by bigred3373 on 2007-04-22
> **Greywhind said:**
> Oh - I guess we do have the same. Sorry.

I guess you should redo the steps... not sure what could have gone wrong.
okay i will later tomorrow thanks i don't know what i did either:confused: :KS

---

### Post by bigred3373 on 2007-04-23
**I don't know what it is it will not go through until something easier comes about lol i'll stick with Ethernet if this been my laptop i would be all over this more so. Thank you and if anyone else has found this helpful i hopes they will post what they have done. I will continue to tinker if not no biggie Thanks again until the next one arrives :)**

:guitar: ROCK ON MATES:guitar: wait a second i found something here whats this?????

 UPDATE I DONT KNOW WHAT EXACTLY CHANGED BUT I FOLLOWED THESE DIRECTIONS AND MY WIRELESS STARTED WORKING
sudo apt-get update 
sudo apt-get install build-essential

Alternatively if you do not have wired Internet access, (as you are using wireless), install these by downloading the packages manually and [WWW] installing them by hand.

You will also need to make a symbolic link from kernel sources directory to the modules directory, I do not really know why this is needed, but in the ndiswrapper documentation, (ndiswrapper being the package that we will using later), it says it is needed to suppress an error when compiling.

Run the commands

sudo apt-get install linux-headers-`uname -r` 
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

Step 2 - Removing existing drivers.

Ubuntu 6.10 (Edgy Eft) comes complete with a suite of drivers that are used to control Wireless Networking, however they dont really work for this card, so we are going to have to disable them.

Run the command.

gksudo gedit /etc/modprobe.d/blacklist 

This will open up your text editor. Scroll down to the bottom and add these lines to the end of the file.

blacklist islsm 
blacklist islusb
blacklist islsm_usb
blacklist islsm_device
blacklist prism2_usb
blacklist islsm_pci
blacklist net2280

(Note: Not all of these drivers are 100% necessary in order to get the system to function, if you experience problems at a later date try removing the drivers; prism2_usb, islsm_pci & net2280)

This would probably be a good time to restart your system as these wont changes take effect until this has taken place.
Step 3 - Downloading and Compiling

In order to get the card working we will need to use the Windows Wireless Driver Emulator, ndiswrapper. I like to install all my programs through the /usr/src directory as it enables me to keep my Home folder clear of any unneeded code. So this is where we will install through.

I am currently going to install version 1.16 of ndiswrapper, as this is the version I know is functioning correctly, you can try to use newer versions, but to me it seems like harder work, as 1.16 installs fine.

Run the commands.

cd /usr/src 
sudo wget [http://kent.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.16.tar.gz](http://kent.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.16.tar.gz)
sudo tar -zxvf ndiswrapper-1.16.tar.gz
cd ndiswrapper-1.16

Ok, you should now have the package on your system, we are now going to compile it.

Run the commands.

sudo make uninstall 
sudo make
sudo make install

---

### Post by Greywhind on 2007-04-23
I'm glad you got it working.

---

### Post by bigred3373 on 2007-04-23
> **Greywhind said:**
> I'm glad you got it working.
 you helped quit and Roc to thank you both:guitar:

---

### Post by bigred3373 on 2007-04-24
**Guess what no my wireless totally disappeared its not acknowledging i have a wireless Device:confused:  How do i get it back without reinstalling Feisty agian:confused: ** I guess it never got saved and it disappeared from the codes :( HELP PANIC MODE

---

### Post by Greywhind on 2007-04-24
Try doing:
modprobe ndiswrapper

If that doesn't work, try:
ndiswrapper -l (lowercase L)
to make sure you have your drivers installed still.

If they are installed, try:
ndiswrapper -m
and then modprobe ndiswrapper

Finally, do iwconfig and dhclient as normal.

---

### Post by bigred3373 on 2007-04-25
> **Greywhind said:**
> Try doing:
modprobe ndiswrapper

If that doesn't work, try:
ndiswrapper -l (lowercase L)
to make sure you have your drivers installed still.

If they are installed, try:
ndiswrapper -m
and then modprobe ndiswrapper

Finally, do iwconfig and dhclient as normal.

i took a break then got mad and reinstalled feisty i tried running the steps again all fail am i supposed to install all the ndiswrapper files from the synaptic manager??:confused:  and then follow your steps:(  ndiswrapper common, ndiswrapper utils, and this one ndiswrapper-source?

---

### Post by Greywhind on 2007-04-25
Just go through my guide on page 1 step-by-step. Don't skip anything or do any of it out of order. Or find another guide, if you don't want to try mine again.

Edit: You don't need ndiswrapper-source.

---

### Post by bigred3373 on 2007-04-25
> **Greywhind said:**
> Just go through my guide on page 1 step-by-step. Don't skip anything or do any of it out of order. Or find another guide, if you don't want to try mine again.

Edit: You don't need ndiswrapper-source.

on number six it says add these lines # remove the following to allow use of bcm 43xx for wireless blacklist bcm43xx   do i type that in completely as it says those exact words?

---

### Post by Greywhind on 2007-04-25
Yes. And make sure you keep the line break between the first liine (which ends at "wireless") and the second line (which starts with "blacklist").

---

### Post by bigred3373 on 2007-04-25
> **Greywhind said:**
> Yes. And make sure you keep the line break between the first liine (which ends at "wireless") and the second line (which starts with "blacklist").

okay this is what i see and i typed it in does this module seem correct# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
# remove the following to allow use if bcm43xx for wireless
blacklist bcm43xx

---

### Post by bigred3373 on 2007-04-25
after  install the cabextract setup and the file sp33008.exe i get this when i try to move on to the next command

shellie@shellie-desktop:~/Desktop/hush$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -i bcmwl5.inf
sudo: ndiswrapper: command not found
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -i bcmwl5.inf
sudo: ndiswrapper: command not found
shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -l
sudo: ndiswrapper: command not found
shellie@shellie-desktop:~/Desktop/hush$ :confused:

---

### Post by Greywhind on 2007-04-25
Did you install ndiswrapper using either apt-get or synaptic? It looks like you might have missed that step.

---

### Post by bigred3373 on 2007-04-25
> **Greywhind said:**
> Did you install ndiswrapper using either apt-get or synaptic? It looks like you might have missed that step.

I did instal lthrough manager:( yup there installed when i went back into manager Should i reinstall again maybe there corrupted??????????? okay i renstalled and here what i getshellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
shellie@shellie-desktop:~/Desktop/hush$

shellie@shellie-desktop:~/Desktop/hush$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
shellie@shellie-desktop:~/Desktop/hush$  

sudo ndiswrapper -m
module configuration already contains alias directive

13
shellie@shellie-desktop:~/Desktop/hush$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory                            ERROR?????????????
shellie@shellie-desktop:~/Desktop/hush$

---

### Post by Greywhind on 2007-04-25
That's very strange. Why would it not be able to find ndiswrapper for your kernel? Did you upgrade your kernel after installing ndiswrapper?

Edit: try reading this page: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting)

Edit #2: Try this:
sudo rm -f /etc/modprobe.d/ndiswrapper
sudo ndiswrapper -m
sudo modprobe ndiswrapper

---

### Post by bigred3373 on 2007-04-26
> **Greywhind said:**
> That's very strange. Why would it not be able to find ndiswrapper for your kernel? Did you upgrade your kernel after installing ndiswrapper?

Edit: try reading this page: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting)

Edit #2: Try this:
sudo rm -f /etc/modprobe.d/ndiswrapper
sudo ndiswrapper -m
sudo modprobe ndiswrapper

shellie@shellie-desktop:~$ sudo rm -f /etc/modprobe.d/ndiswrapper
Password:
shellie@shellie-desktop:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
shellie@shellie-desktop:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory
shellie@shellie-desktop:~$ 
 **NO CLUE HAS TO WHATS GOING HERE I HAVE NDISWRAPPER 1.42 AND KNOW MY WIRELESS DISAPPEARED AGAIN FROM THE NETWORK MANAGER:confused: :confused: :( :(**

linux-headers-2.6.20-15-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  debhelper module-assistant intltool-debian po-debconf gettext html2text
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shellie@shellie-desktop:~/Desktop/hush$ 
shellie@shellie-desktop:~/Desktop/hush$ sudo apt-get install build-essential command
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package command
shellie@shellie-desktop:~/Desktop/hush$ ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
bash: kernel-version: No such file or directory
shellie@shellie-desktop:~/Desktop/hush$

**i am totally lost and the wireless device wont come back do i have to renistall ubuntu one more tim**e?

---

### Post by Greywhind on 2007-04-26
I'm sorry, but I am simply not the right person to help you - I don't know enough to fix your problems. Maybe you should try the IRC channel, #ubuntu on irc.freenode.net.

---

### Post by bigred3373 on 2007-04-26
> **Greywhind said:**
> I'm sorry, but I am simply not the right person to help you - I don't know enough to fix your problems. Maybe you should try the IRC channel, #ubuntu on irc.freenode.net. no problem thank you however its okay :)

---

### Post by vigyani on 2007-04-28
It worked like charm for me. I did fresh install of Ubuntu 7.04 (Feisty Fawn) on HP NX6310 with Broadcom bcm4310 wireless card. Thanks a lot. It is great post.

regards
Vig

---

### Post by Greywhind on 2007-04-29
Glad it worked for you. Thanks for posting.

---

### Post by haggis1606 on 2007-05-02
Oh dear I am getting the same problem.
This is confusing I cant figure out why it doesnt work :(

Sod this I am going to reinstall, prolly wont fix anything but hey.

---

### Post by voraistos on 2007-05-02
Hi. As many others i had some trouble setting up ndiswrapper, teliing me the driver was already installed, but removing it and installing mine (the one dled from dell) worked almost fine. what i dont understand is that the proprietary driver could kind of work, however unlike the ndiswrapper driver i could get a much better quality connection, and see much more networks (including the ones not broadcasting the ssid). Anyways, thank you, this is a great howto for a bad wireless card. As soon as i find an atheros one i will buy it :P

---

### Post by Count Doofus on 2007-10-21
YOU"RE LOOKING TOO HARD !!!!  TYPE THE DRIVER NAME IN THE CORRECT CASE AaBbCc.InF exactly like it is listed when you issue the dir command.


 had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename  is wrong !

Its the simple stuff that kicks my butt the worst


had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

### Post by valinux on 2007-11-15
wusb54gsc : driver installed
device (13B1:0026) present


modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory


now what?? i got the driver install and device present why is ndiswrapper doing this why??? :'( 
my head hurts but i used all my thinking googling for answers and at the last part 
ndiswrapper.ko': No such file or directory

should i download ndiswrapper.ko and put on that folder in order to fix it?:confused:

---

### Post by cyberdork33 on 2007-11-15
> **valinux said:**
> wusb54gsc : driver installed
device (13B1:0026) present


modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory


now what?? i got the driver install and device present why is ndiswrapper doing this why??? :'( 
my head hurts but i used all my thinking googling for answers and at the last part 
ndiswrapper.ko': No such file or directory

should i download ndiswrapper.ko and put on that folder in order to fix it?:confused:

Can you manually look in that folder to see if it is really not there? How did you install ndiswrapper?

---

### Post by valinux on 2007-11-18
Yes i can cd all the way to that folder..
but the file is not there..
i install the latest ndiswrapper.. .deb
and installed

I'm still looking for the answer to this problem so i can help out people that have the same wireless card

---

### Post by P1N3R on 2007-12-11
I have the same problem. The device is present and the drivers are installed. Now i can't get sudo modprobe ndiswrapper working at all. I just get FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

Help, please :)

---

### Post by xonev on 2007-12-15
I'm having the exact same problem - I had ndiswrapper 1.50 installed until today - I had compiled it myself from the source on the ndiswrapper website, but when I would install the drivers for my wireless adapter (a netgear WPN111) the kernel would crash after connecting my device and doing
```

sudo modprobe ndiswrapper
```

So, I decided to uninstall that version of ndiswrapper and get the one from apt, so I did

```
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
```

but now, once I install the drivers, it will not add the ndiswrapper module to the kernel because it cannot find ndiswrapper.ko - I remember that being removed when I uninstalled version 1.50, and apparently apt-get does not install that file?  This is weird, but I will attempt to figure it out...

---

### Post by Stu09 on 2007-12-23
> **xonev said:**
> I'm having the exact same problem - I had ndiswrapper 1.50 installed until today - I had compiled it myself from the source on the ndiswrapper website, but when I would install the drivers for my wireless adapter (a netgear WPN111) the kernel would crash after connecting my device and doing
```

sudo modprobe ndiswrapper
```

So, I decided to uninstall that version of ndiswrapper and get the one from apt, so I did

```
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
```

but now, once I install the drivers, it will not add the ndiswrapper module to the kernel because it cannot find ndiswrapper.ko - I remember that being removed when I uninstalled version 1.50, and apparently apt-get does not install that file?  This is weird, but I will attempt to figure it out...

I did the exact same thing. installed 1.51 then uninstalled it and now cannot load the module with modprobe.

Help!
PS I'm running Gutsy.

---

### Post by co1dfus1on on 2008-01-12
The file ndiswrapper.ko comes automatically with the ubuntu kernel modules package, and so is not installed by either ndiswrapper-utils-* or ndiswrapper-common. It seems that when ndiswrapper is built from source, installed and then uninstalled, it replaces and then removes this file. So to get it again you need to reinstall the [one quick search of packages.ubuntu.com later,] linux-ubuntu-modules-`uname -r` package.

EDIT:
Oops, sorry: this looks like it only works for gutsy.

---

