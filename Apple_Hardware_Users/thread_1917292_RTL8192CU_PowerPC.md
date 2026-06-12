---
title: "RTL8192CU PowerPC"
date: 2012-01-29
forum: Apple Hardware Users
---

### Post by mw1coe on 2012-01-29
Hi.

Been reading the forums and hopefully someone can help me here.

I have an Emac running Lubuntu and 1 Non working Realtek RTL8192CU USB Wireless Card.

I have tried all the suggestions but I guess that this PowerPC is a totally different Issue.

Has anyone managed to get one of these working or is the PowerPC simply not able to run this Card ?

Many thanks

Rob..

---

### Post by Khayyam on 2012-01-30
mw1coe ..

I'm not sure what instructions you have attempted to follow but it shouldn't be an issue with PPC (an 'endian' issue), Realtek's are generally well supported on all platfroms. I assume its [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190"), have you tryed the solution posted [here]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")?

HTH

---

### Post by mw1coe on 2012-01-30
When I run :

sudo bash install.sh

Aftern some lines of data load I get :

Please select card type(1/2):

1) RTL8192cu
2) RTL8192du

I select RTL8192cu 

You have selected RTL8192cu
rtw_version.h has existed!
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=ppc CROSS_COMPILE= -C /lib/modules/2.6.38-13-powerpc/build M=/home/emac/wireless/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-13-powerpc'
Makefile:556: /usr/src/linux-headers-2.6.38-13-powerpc/arch/ppc/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.38-13-powerpc/arch/ppc/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-13-powerpc'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

The Wireless card is Not Recognized and as a result I cannot get any further..
This is where I have gotten on every attempt to get this wireless working.

Could you or someone help where I am going wrong ?

Thanks

Rob..

---

### Post by Khayyam on 2012-01-31
Rob ...

The rtl8188C_8192C_8192D_usb source is expecting that you have the kernel sources and/or linux-headers, and that the kernel you are currently booting was built by you (or at least that you have the headers, Makefiles, etc, consequent to your kernel). It needs certain information from */arch/ppc/Makefile in order to ascertain how the kernel was configured, and which libraries/headers it should link to. As it doesn't find these it can't compile the module. The 'linux-headers' package should provide you with these files, I assume this package isn't installed.

To install type the following at a command prompt
```
sudo apt-get install linux-headers-$(uname -r)
```You should then be able to compile and install the RTL8192cu driver using the method outlined in the post linked to above.

HTH

---

### Post by mw1coe on 2012-01-31
OK I bit the Bullet and Upgraded to 11.10

Still not able to compile..

uname -r

3.0.0-15-powerpc

OK I checked and linux Headers in installed..

when I try to install the card i get the same errors..

Now I do not have a Arch/PPC folder on this PC

I do have a Arch/Powerpc folder though..

Is that the Problem ?

Rob..

---

### Post by Khayyam on 2012-02-01
Rob ..

I had assumed, perhaps wrongly, that the 'install.sh' was getting its buildhost environment information (2.6.38-13-powerpc) from 'uname', and setting the path it looks for the Makefile accordingly. Not having the 'install.sh' script to hand I can't look at it to see why it might fail. Your not really helping in this regard, as your reporting leaves me mostly guessing.

Do you really "get the same error[s]" .. I mean **exactly** the same error? So, on '3.0.0-15-powerpc' it states:
```
Makefile:556: /usr/src/linux-headers-2.6.38-13-powerpc/arch/ppc/Makefile: No such file or directory
```Or does it in fact read:
```
Makefile:556: /usr/src/linux-headers-3.0.0-15-powerpc/arch/ppc/Makefile: No such file or directory
```If the former then the 'install.sh' has the path hardcoded, and will need to be edited to reflect your particular setup. If the latter then it's looking in the right place but the directory structure doesn't reflect what it expects.

So, if you want me to help, you need to give me more information than you are currently.

As for "Arch/PPC" .. Linux is a **case sensitive** OS, you do not have "Arch/Powerpc" but "arch/powerpc". Had I not known this, I might have suggested you do something like "ln -s /path/Arch/Powerpc /path/Arch/PPC" which simply wouldn't have worked as these filenames are **not** uppercase.

I'm partially guessing, but it may be the script is looking for 'ppc' when the Makefile is under 'powerpc'. You can temporarily create a 'symbolic link' from powerpc to ppc and resolve this.
```
sudo ln -s /usr/src/linux-headers-3.0.0-15-powerpc/arch/powerpc /usr/src/linux-headers-3.0.0-15-powerpc/arch/ppc
```Once the driver has compiled (assuming it now does) you can remove the link:
```
sudo rm -f /usr/src/linux-headers-3.0.0-15-powerpc/arch/ppc
```Now, should there still be some problem please report the error exactly as its displayed. You might also attatch the 'install.sh' script so I can get some idea of what its doing. The more information you provide me the better I can see what the issue is ..

HTH ..

---

### Post by mw1coe on 2012-02-01
Khayyam

I'm sorry if I have appeared Vague as that was never my Intention and obviously in doing so didn't exactly make problem solving any easier and for that I apologize.

I decided to see if a Later Build might solve the Issue as I know that later versions of Ubuntu claim to have support out of the box.

I therefore upgraded to 12.04.

Reading your Post I modified the test to reflect the newer Kernel of 3.2.0-12

After typing Sudo Bash Install.sh the whole screen filled with data and began running the install.


During the install I got a ton of the following :

/usr/src/linux-headers-3.2.0-12-powerpc/arch/ppc/makefile:mad:xxx: warning : overriding commands for target `x `

/usr/src/linux-headers-3.2.0-12-powerpc/arch/ppc/makefile:mad:xxx: warning : ignoring old commands for target ` x `

`xxxx` numbers from 100 to 1520
'x' numerous entries including kernelversion and export-report and /

I am also seeing "permission Denied" flash up just after the messages pop up then replaced by the next line.

Can you help explain whats going on as it's been doing this for over 10 minutes..

I have included a Copy of install.sh as requested.

Thanks Rob..

---

### Post by Khayyam on 2012-02-02
Rob ...

These errors (or rather 'warnings') seem fairly harmless, its just means gcc (the compiler) has been passed the '-W' (warn) switch.

Getting 'permission denied' on the other hand, sounds more serious, but its hard for me to figure out whats causing it without more information. Reading the script I think the issue relates to the fact that the script will attempt to run 'su -c', and as your [root account is not enabled]("https://help.ubuntu.com/community/RootSudo") you will get a 'permission denied'. You might try 'sudo -i' and then 'bash ./install.sh' to get arround this problem (root can run 'su -c').

I'm not sure how Ubuntu sets up its groups and/or sudoers, but I'm guessing (seeing as the root account is disabled by defualt) users will need to be is some kind of 'admin' or 'wheel' group to use 'su'. So, should the above fail, we can add your user to whatever group it needs to be in.

HTH ..

---

### Post by mw1coe on 2012-02-02
Well I still got no Wireless but I do have a result in that trying :

lsusb

Now reports Realtek Semiconductor Corp  RTL8188CUS 802.11n WLAN so now it's recognized just  need to get it to access networks..

---

### Post by Khayyam on 2012-02-03
Rob ...

OK, so the driver is now compiled and installed .. and loads when the device is inserted. From the above linked tutorial we know that the driver works for that particular (11.10) user, so its probably just a matter of how you are configuring the connection, or perhaps some missing component/package required for authentication with your wireless router.

You should look and see what the logfile (/var/log/messages) shows when inserting the card, and when you attempt to associate with the router. You should also check you are configuring the authentication method correctly (eg: if your wireless router requires WPA, then make sure you have that authentication method selected in your wireless setup).

Boot without the card connected and in a terminal 'tail -f' ('follow') the log file ..

```
sudo tail -f /var/log/messages
```When you connect the card the logfile should show the module being registered, and various 'messages' from the kernel. You should then attempt to associate with your wireless router, further messages should be logged to the file (probabaly from wpa_supplicant). These messages should provide some idea of why the connections are failing.

There may be other possible reasons for your not getting "connected",  perhaps your wireless router is not providing dhcp, but I'll assume this is a client problem and that you understand how the router is setup and what you need to provide to the router to authenticate.

HTH ...

---

