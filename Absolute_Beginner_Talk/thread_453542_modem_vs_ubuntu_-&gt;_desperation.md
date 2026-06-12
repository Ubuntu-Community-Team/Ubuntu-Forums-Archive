---
title: "modem vs ubuntu -&gt; desperation"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by shilkie on 2007-05-24
I've a dell inspiron 9400 notebook on which I've installed ubuntu 6.10 (kenerl verson: 2.6.17-10-generic) with an internal modem: conexant HDA D110 MDC V.92
characterized by a hsf chipset related to which I've downloaded the driver:
[http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.60.00.09full/hsfmodem_7.60.00.09full_k2.6.17_10_generic_ubuntu_i386.deb.zip](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.60.00.09full/hsfmodem_7.60.00.09full_k2.6.17_10_generic_ubuntu_i386.deb.zip)

I'm attaching to this post the output of scanModem...

after that I've entered:
unzip hsfmodem_7.60.00.09full_k2.6.17_10_generic_ubuntu_i386.deb.zip
sudo dpkg -i hsfmodem_7.60.00.09full_k2.6.17_10_generic_ubuntu_i386.deb
sudo hsfconfig

and the installation begun requiring my e-mail address, the nation from which i come from, and the license key (that I don't have but this is another question... :/ )
but activating the connection from system->administration->network, after having configured all the connection properties (/dev/modem/ port) it hasn't connected to the internet.

then I've checked that drivers were been installed correctly:
sudo lsmod

and within the output there were something related to 'hsf' so I've deducted that they were been installed properly.

then I've tried:
ls /dev | grep tty

and within the output there was: ttySHSF0
so I've tried to setting the port as /dev/ttySHSF0
but the connection problem was not solved.

Is there any very good person who would like to help me????plz....I've finished any candidate solution idea :(

---

### Post by Bachstelze on 2007-05-24
Which program are you using to make the connection ?

---

### Post by towsonu2003 on 2007-05-25
there seems to be an open source driver for your modem but I'm not sure if it works. See [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant) 

According to the link above, you did everything correctly. Now, I would try to dial out using wvdial, using this guide:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9)

You can find the main dialup howto in my signature. hope this helps. if wvdial cannot dial, see the options the above link (for wvdial) talks about and after trying them post us the output that wvdial spits ( ;) ) at you.

PS. if you cannot connect in your first try with wvdial, try a few more times. I sometimes have to try for 30 minutes to connect (although mine is another modem chipset)

PSS. you're doing the correct thing according to your modemdata.txt

---

