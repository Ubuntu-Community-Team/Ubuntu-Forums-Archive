---
title: "installing drivers"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by imacbo on 2007-03-27
OK I need a step by step the newest newbie to Ubuntu. I have an Edimax EW-7608Pg with the disk. And the drivers are on the disk.

---

### Post by dstew on 2007-03-27
Look on the disk for the linux driver(s). Post here what you see in that directory.

---

### Post by imacbo on 2007-03-27
in the debian folder the files are load, read me, rt61.ko, RT61STA.DAT, RT61STAV1000_k2.6.8-2-386_Debian.tar , RT2561, RT2561S, RT2661, and UNLOAD

---

### Post by imacbo on 2007-03-27
this is the read me but i tried to follow it and everytime i would get an error message



For 2.4 series kernel:
a. $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.
    
b. Use 'chmod' command to change access right of following script files :
   'load', 'unload', 'Configure'
 
c. run 'cp ../2.4x/Makefile .'
d. $make config         # config build linux os version

e. $make all            # compile driver source code

f. $cp RT2561.bin /etc/Wireless/RT61STA/	# copy firmware
   $cp RT2561S.bin /etc/Wireless/RT61STA/
   $cp RT2661.bin /etc/Wireless/RT61STA/

g. $load                # load/insmod module(rt61.o)

Note: Script functionality:
load            load module to kernel
unload          unload module from kernel
Configure       retrieve linux version 


For 2.6 series kernel:
a.  run 'cd STA/Module'
        'cp ../2.6x/Makefile .'

b. $make all

c. $cp RT2561.bin /etc/Wireless/RT61STA/	# copy firmware
   $cp RT2561S.bin /etc/Wireless/RT61STA/
   $cp RT2661.bin /etc/Wireless/RT61STA/
   
d.  run '/sbin/insmod rt61.ko'  (as root)
        '/sbin/ifconfig ra0 inet YOUR_IP up' 


For big endian platform:
a.  replace Makefile with Makefile.RTL865x

---

### Post by dstew on 2007-03-27
Copy the debian folder from the CD to your desktop. It looks like you should do the steps a. and b. for the 2.4 kernel, then a. to d. for the 2.6 series kernels.

What errors are you getting?

---

### Post by imacbo on 2007-03-27
do i have to change the directory to desktop. when i try i get an error that the path does not exist

---

### Post by imacbo on 2007-03-27
also i am not too good with the terminal so how sure it look exactly when i type it? When I type the first command i replace the x.x.x.x. with the 6.8.-2-386 right? man I am so lost on this I need some help bad.

---

### Post by imacbo on 2007-03-27
bump

---

### Post by imacbo on 2007-03-28
please i need help with this

---

### Post by david_kt on 2007-03-28
Instead of tar, you can use right click and choose extract here.

Could you see any debian package in debian folder? May after extracting a compressed file? If not, ASSUMING you have kernel 2.4, this is what you should do:

1. Copy RT61STAV1000_k2.6.8-2-386_Debian.tar to your desktop. 
2. Right click that file, and choose extract here.
3. Open a terminal.

Below steps are in terminal:
4.  Go to extracted folder, I guess it is 
[INDENT]cd /Desktop/RT61STAV1000_k2.6.8-2-386_Debian/Module[/INDENT]
Please make sure to go to the correct directory, as I only could guess the extrated folder name.
5. chmod +x load
6. chmod +x unload
7. chmod +x Configure
8. make config
9. make all
10.sudo cp RT2561.bin /etc/Wireless/RT61STA/
11. sudo cp RT2561S.bin /etc/Wireless/RT61STA/
12. sudo cp RT2661.bin /etc/Wireless/RT61STA/
13.sudo load

Key in your password if requested.

DK

---

### Post by imacbo on 2007-03-28
ok everything was going great untill I got to the chmod +x Configure. Then it told me that there was no such file. So i tried to skip it and that would not work. So i created a file called configuer and the the chmod +x configure worked. the next problem was the make config it would not go past that. once again i tried to skip it and me make all would not work. so this is where I am stuck once again trying to intall the same drivers for 3 days now. can some one please help me before i pull what little hair i have left out.:confused: :confused: :confused:

---

### Post by david_kt on 2007-03-29
No, you should not create that file. In this case, may be it is small "c" used in the actual file, as compared to big"C" in the readme file. So, please change step 7 to:

[INDENT]7. chmod +x **c**onfigure[/INDENT]

The different is configure with small c. Before I follow your readme file that said it is Configure with big C.

Please try again and let me know if still problem.
DK

---

### Post by starcannon on 2007-10-01
****UPDATE****
Installed Gutsy on the machine I bought this card for, everything works, no effort on my part, plug and play.
******************

I just bought this card, the box says its compatible with linux.
Thats only partially true, the drivers that come with it indicate that they are only useful for WEP.
I'm a bit annoyed I NEED WPA. 
Who's using wep anymore? I haven't been able to connect to wifi networks on wep in over a year where I live..
Wish they would just say "Linux WEP Only" on the box.
grrrr.... there went $50

---

