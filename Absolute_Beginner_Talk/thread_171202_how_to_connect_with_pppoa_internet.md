---
title: "how to connect with pppoa internet?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by xtreme5000 on 2006-05-06
hey guys, im completely new to linux and ubuntu, i've just installed it today. I need a little help ,. My ISP ([http://www.e4me.ae/e4me/etisalat/NewADSLConn](http://www.e4me.ae/e4me/etisalat/NewADSLConn)) uses a pppoa connection for dsl and i have a Lucent CellPipe 20A USB modem. I tried getting eciadsl, but i can't see a ubuntu version? so which version do i get? And how do i install it? This might sound a bit stupid, but  im completely new to linux and any help in getting my internet to work wud be a great help :)

---

### Post by cyangecko on 2006-05-06
Have you checked out this wiki yet?  

[https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28pppoe%29]("https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28pppoe%29")

---

### Post by xtreme5000 on 2006-05-06
That's for pppoe. Will it also work for pppoA? And my modem is a USB modem, is there any place where i can  get that ECiadsl for ubuntu, or is there a simpler way?

---

### Post by cyangecko on 2006-05-06
sorry, read it incorrectly.

---

### Post by xtreme5000 on 2006-05-06
So is there anyone who can help me or has successfully connected with a PPPoA connection? 
i found this one another site:


1. Install complete SUSE9.2 Prof (including compilers, addl. software etc. I donot know secifically what are required)
2. download rp-pppoe-3.5-327.i586.rpm file from suse site. It will be in one of the "/586" sub directories in 9.1 or 9.2 distributions.
3. copy it in /tmp directory and execute #rpm rp-pppoe-3.5-327.i586.rpm
4. download [ EciAdsl Nortek ] file from [http://eciadsl.flashtux.org/download.php?lang=en](http://eciadsl.flashtux.org/download.php?lang=en)
5. Read carefully README_GS7470.txt file in the package
6. Install the above package as per the instuction.
Note : To execute ./configure, you need to change directory to the directory where you copied the files (Eg. /tmp/eciadsl-usermode-0.10-nortek-alpha) and it should contain the file configure
7. After installation, from terminal window type "eciadsl-probe_device" and see an entry like USB-ADSL Modem / GlobeSpan Inc. (0e60:0500) . The values in the bracket are the VIP and PID values for the modem.
8. From the terminal window execute eciadsl-config-tk
9. Set values like, modem type, Select chipset GS7470. Change .bin files to GS7470Synch01.bin (It is part of the nortek package) . Copy GS7470Synch01.bin file to /etc/eciadsl folder
10. Set VID/PID values with the value you got at step 7
11. VCI..., you need to set 0.50 (It is for etisalat in UAE). Other ISPs value changes.
12. Set all the above values and unplug and replug the modem
13. from terminal window type "eciadsl-start"


but can anyone simplify it for me and tell me how to do it on Ubuntu?

Thanks in advance
X

---

### Post by Blondie on 2006-05-07
Hi,

I'm a newbie too. I haven't got a pppoa connection working but I got a pppoe connection working. Here is a simple and ubuntu specific guide how to do it, assuming nearly zero knowledge. This is the quickest way I know - I've done it several times after some clean reinstalls so I do it in my sleep now. ;) 

A) Download the following two files from the internet,
[http://eciadsl.flashtux.org/download/eciadsl-usermode_0.11-1_i386.deb](http://eciadsl.flashtux.org/download/eciadsl-usermode_0.11-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.5-4ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.5-4ubuntu1_i386.deb)
B) Somehow (CDRW, floppy, whatever) get both of the files saved in your home folder on your ubuntu install (Places / Home Folder).
C) Install them as follows. Open up a terminal (Applications / Accessories / Terminal). Type the following: "sudo dpkg -i pppoe_3.5-4ubuntu1_i386.deb". Hit enter and give password. Then type the following: "sudo dpkg -i eciadsl-usermode_0.11-1_i386.deb" Hit enter.
D) Unplug and replug your modem from the USB socket until you make sure no lights are. No lights on is *good*.
E) Open up a terminal and type "sudo eciadsl-config-tk". Give password. This launches the eciadsl configuration tool. Select your modem from the list (yours is there, I checked). Type in your username and password for your internet connection at the top. Change the VPI and VCI values to those that your ISP specifies (mine were 0 and 38 respectively). Everything else left at default works for me.
F) Click the "Remove Dabusb" button. This stops ubuntu from thinking that your modem is another device at startup. You want the eciadsl program to start it from now on. You should only have to do this once.
G) Click the "Create config!" button, then close the configuration tool.
H) Connect to the internet! Open up a terminal and type "sudo eciadsl-start". You should see it trying to connect. If it fails try closing the terminal then unplugging your modem and replugging it. Then try again.

This method actually uses the eciadsl version made for Debian but it works fine for me in Ubuntu.

The problem is that you are using pppoa and I use pppoe. Perhaps there is a file like pppoe_3.5-4ubuntu1_i386.deb but for pppoa which you could substitute in the above method. Perhaps you could get a connection with the above method since many ISPs accept both pppoa or pppoe. Hope it helped some anyway.

---

### Post by Blondie on 2006-05-07
Oh, and to state the obvious if you're using AMD64 or Powerpc chipsets you won't want to use the i386 files. You can get the specific files at,
[http://ftp.riken.jp/Linux/ubuntu/pool/universe/r/rp-pppoe/](http://ftp.riken.jp/Linux/ubuntu/pool/universe/r/rp-pppoe/)
[http://eciadsl.flashtux.org/download.php?lang=en](http://eciadsl.flashtux.org/download.php?lang=en)
(use the Debian one)

---

