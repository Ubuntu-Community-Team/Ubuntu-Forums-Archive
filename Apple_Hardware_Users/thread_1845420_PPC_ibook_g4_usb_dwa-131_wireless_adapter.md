---
title: "PPC ibook g4 usb dwa-131 wireless adapter"
date: 2011-09-17
forum: Apple Hardware Users
---

### Post by skythra on 2011-09-17
Hi,

A while ago i was given a PPC based ibook g4 and asked to run skype on it. I booted it and mac OS whatever was dead, every time it'd either fail to boot, or crash shortly after. After fiddling I got it into the OS enough times to notice that every time it tried using the wireless it'd instantly die. The airport could well be dead.

I installed ubuntu 10.04 on it and was impressed that ubuntu was working so well. I then installed a proprietary driver for the airport and instantly the laptop became unstable. OK well that's problem solving over, the airport is probably useless.

I left it many months but then came back to it after moving house and deciding to leave it aside after unpacking and threw on ubuntu 10.10. Everything but wireless working, and I am pretty happy. Physical wired LAN allowed updates and so on. I threw on 11.04 as an update, but then suspend didn't work. Because of the enormously long boot time of this old ibook, that wasn't acceptable and due to the lack of support and lack of reason to move from 10.10 to 11.04, I decided to reinstall again. 

So sitting happily at 10.10 everything (including suspend working) I decided to use a spare wireless USB the dwa-131 which is a wireless N based on some boardcom chipset. There's many threads about the specific issues that people have with installing it as it doesn't run out of the box (it apparently did for one revision maybe but then there was some regression). 

Anyhow so i've followed the following steps from another thread:

[http://ubuntuforums.org/showpost.php?p=9690593&postcount=8](http://ubuntuforums.org/showpost.php?p=9690593&postcount=8)
```
1. download the driver (bmjbmj's link didn't work, but you can get it at the bottom of this page: http://www.realtek.com.tw/downloads/...true#RTL8192SU
2. cd ~/Downloads/
3. unzip [the name of the driver you downloaded, versions vary]
4. cd ~/Downloads/[the name of the driver you downloaded, versions vary]/driver/
5. now open nautilus and navigate to the above directory, copy the name of the tar.gz archive in the driver folder
6. tar -xvzf [the tar.gz archive name that you copied]
7. cd ~/Downloads/[the name of the driver you downloaded, versions vary]/driver/[the name of the archive you just decompressed, without "tar.gz" at the end of the name]/
8. remember, if the files and folders get confusing, look in nautilus to find the names you need.
9. Build the driver using these four commands in order, each may take a couple minutes, be patient:
a. sudo su
b. make clean
c. make 
d. make isntall
10. thanks again to bmjbmj for his instructions, im merely elaborating on them, for other noobs like myself.
```

Okay so no worries, I get up to step 9 instantly because I'd happily already found other solutions to get to step 8. I make myself super user and make clean. But then I type "make" and i get the following output:
```
root@skythra-mac:/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401# make
make ARCH=ppc CROSS_COMPILE= -C /lib/modules/2.6.35-30-powerpc/build M=/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-powerpc'
Makefile:547: /usr/src/linux-headers-2.6.35-30-powerpc/arch/ppc/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.35-30-powerpc/arch/ppc/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-powerpc'
make: *** [modules] Error 2
root@skythra-mac:/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401# 
```
Which leaves me stumped. I installed the kernel headers from another google around in order to find how make works. But googling "make" isn't very good. Such an ambiguous word leads to many different results. 

I thought I'd need to install something named kernel-devel for my specific version but I don't know how to use that. I tried to get yum to work, so I ran apt-get install yum, and yum installed. But I don't think it has the right repositories or whatever they're called because yum won't update anything, nor install anything. 

Anyway can someone please give me hints from here :)

Thanks.

---

### Post by skythra on 2011-09-17
As an update I went through to the folders where the folder should be that it can't find...

make says ```
Makefile:547: /usr/src/linux-headers-2.6.35-30-powerpc/arch/ppc/Makefile: No such file or directory
```
I then went and got to:
/usr/src/linux-headers-2.6.35-30-powerpc/arch/ 
Then it stops. There's no folder called "ppc". 

There is howerever, a folder called "powerpc". I'm not very versed in linux, but is it possible that there's been a typo and one of these should be called the other? I mean they probably need to line up right?

So I don't want to ruin my install just yet, but I might try renaming powerpc to being ppc and see what happens...

Okay so I did that but then I don't understand the output nor can I go much further...

output when I ran make on the driver looks like
```
root@skythra-mac:/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401# make
make ARCH=ppc CROSS_COMPILE= -C /lib/modules/2.6.35-30-powerpc/build M=/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-powerpc'
  CC [M]  /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.o
In file included from /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:30,
                 from /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_byteorder.h:31,
                 from /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/osdep_service.h:316,
                 from /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:23:
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:24: error: redefinition of typedef ‘__u16’
include/asm-generic/int-ll64.h:23: note: previous declaration of ‘__u16’ was here
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:28: error: redefinition of typedef ‘__u32’
include/asm-generic/int-ll64.h:26: note: previous declaration of ‘__u32’ was here
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:32: error: redefinition of typedef ‘__u8’
include/asm-generic/int-ll64.h:20: note: previous declaration of ‘__u8’ was here
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:36: error: redefinition of typedef ‘__u64’
include/asm-generic/int-ll64.h:30: note: previous declaration of ‘__u64’ was here
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:103: warning: "__swab16" redefined
include/linux/swab.h:99: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:104: warning: "__swab32" redefined
include/linux/swab.h:108: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:105: warning: "__swab64" redefined
include/linux/swab.h:117: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:107: error: conflicting types for ‘__fswab16’
include/linux/swab.h:46: note: previous definition of ‘__fswab16’ was here
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/swab.h:111: error: conflicting types for ‘__fswab32’
include/linux/swab.h:55: note: previous definition of ‘__fswab32’ was here
In file included from /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/rtl871x_byteorder.h:31,
                 from /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/osdep_service.h:316,
                 from /home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.c:23:
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:32: warning: "__constant_htonl" redefined
include/linux/byteorder/big_endian.h:14: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:33: warning: "__constant_ntohl" redefined
include/linux/byteorder/big_endian.h:15: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:34: warning: "__constant_htons" redefined
include/linux/byteorder/big_endian.h:16: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:35: warning: "__constant_ntohs" redefined
include/linux/byteorder/big_endian.h:17: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:36: warning: "__constant_cpu_to_le64" redefined
include/linux/byteorder/big_endian.h:18: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:37: warning: "__constant_le64_to_cpu" redefined
include/linux/byteorder/big_endian.h:19: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:38: warning: "__constant_cpu_to_le32" redefined
include/linux/byteorder/big_endian.h:20: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:39: warning: "__constant_le32_to_cpu" redefined
include/linux/byteorder/big_endian.h:21: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:40: warning: "__constant_cpu_to_le16" redefined
include/linux/byteorder/big_endian.h:22: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:41: warning: "__constant_le16_to_cpu" redefined
include/linux/byteorder/big_endian.h:23: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:42: warning: "__constant_cpu_to_be64" redefined
include/linux/byteorder/big_endian.h:24: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:43: warning: "__constant_be64_to_cpu" redefined
include/linux/byteorder/big_endian.h:25: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:44: warning: "__constant_cpu_to_be32" redefined
include/linux/byteorder/big_endian.h:26: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:45: warning: "__constant_be32_to_cpu" redefined
include/linux/byteorder/big_endian.h:27: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:46: warning: "__constant_cpu_to_be16" redefined
include/linux/byteorder/big_endian.h:28: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:47: warning: "__constant_be16_to_cpu" redefined
include/linux/byteorder/big_endian.h:29: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:48: warning: "__cpu_to_le64" redefined
include/linux/byteorder/big_endian.h:30: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:49: warning: "__le64_to_cpu" redefined
include/linux/byteorder/big_endian.h:31: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:50: warning: "__cpu_to_le32" redefined
include/linux/byteorder/big_endian.h:32: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:51: warning: "__le32_to_cpu" redefined
include/linux/byteorder/big_endian.h:33: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:52: warning: "__cpu_to_le16" redefined
include/linux/byteorder/big_endian.h:34: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:53: warning: "__le16_to_cpu" redefined
include/linux/byteorder/big_endian.h:35: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:54: warning: "__cpu_to_be64" redefined
include/linux/byteorder/big_endian.h:36: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:55: warning: "__be64_to_cpu" redefined
include/linux/byteorder/big_endian.h:37: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:56: warning: "__cpu_to_be32" redefined
include/linux/byteorder/big_endian.h:38: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:57: warning: "__be32_to_cpu" redefined
include/linux/byteorder/big_endian.h:39: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:58: warning: "__cpu_to_be16" redefined
include/linux/byteorder/big_endian.h:40: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:59: warning: "__be16_to_cpu" redefined
include/linux/byteorder/big_endian.h:41: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:72: warning: "__cpu_to_le64s" redefined
include/linux/byteorder/big_endian.h:91: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:73: warning: "__le64_to_cpus" redefined
include/linux/byteorder/big_endian.h:92: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:74: warning: "__cpu_to_le32s" redefined
include/linux/byteorder/big_endian.h:93: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:75: warning: "__le32_to_cpus" redefined
include/linux/byteorder/big_endian.h:94: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:76: warning: "__cpu_to_le16s" redefined
include/linux/byteorder/big_endian.h:95: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:77: warning: "__le16_to_cpus" redefined
include/linux/byteorder/big_endian.h:96: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:78: warning: "__cpu_to_be64s" redefined
include/linux/byteorder/big_endian.h:97: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:79: warning: "__be64_to_cpus" redefined
include/linux/byteorder/big_endian.h:98: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:80: warning: "__cpu_to_be32s" redefined
include/linux/byteorder/big_endian.h:99: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:81: warning: "__be32_to_cpus" redefined
include/linux/byteorder/big_endian.h:100: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:82: warning: "__cpu_to_be16s" redefined
include/linux/byteorder/big_endian.h:101: note: this is the location of the previous definition
/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/include/byteorder/little_endian.h:83: warning: "__be16_to_cpus" redefined
include/linux/byteorder/big_endian.h:102: note: this is the location of the previous definition
make[2]: *** [/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/skythra/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401] Error 2
```

So there were errors and warnings neither of which I understood.

After doing that i tried "make install" but that didn't work either.

I'm not sure how to go any further now.

---

### Post by rsavage on 2011-09-17
Can't give you any help with the compiling I'm afraid, but have you checked out whether the natty kernel has the driver already built in?  I know you don't want to use standard ubuntu 11.04, but xubuntu 11.04 is excellent.  If you want a really fast boot time then there is lubuntu  They are both pretty easy to install on an ibook using the minimal cd.

---

### Post by skythra on 2011-09-19
Yeah I've already looked, it didn't work.

Just to further the problem, nothing will compile. 

This actually is bad, because there's more than just a driver or two that I want to compile, some things are only distributed by source. 

If I can't compile then there's a large reason to give up on the old book.

---

### Post by rsavage on 2011-09-19
I think you are being a bit negative!  If you don't want your ibook then I'll have it!!

Easy way to compile within the package system is explained here [http://ubuntuforums.org/showthread.php?t=1816161](http://ubuntuforums.org/showthread.php?t=1816161) .

---

