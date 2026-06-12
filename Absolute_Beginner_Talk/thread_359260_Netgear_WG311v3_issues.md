---
title: "Netgear WG311v3 issues"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Debello on 2007-02-11
I have searched the forums, used Macdo's instructions (which were very very helpful untill this point) and googled my brains out, but can not find a resolution to my issue.

Using 6.10 with a Dell GX260 Intel CPU

**My issue:**

   I can install ndiswrapper using synaptic package manager
   using the drivers from [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip) (have tried other links for the drivers found on the forums and other places, and have even tried from the cd even though not advised to do so)

    I install the drivers using the following command from the directory where I have the inf/sys files at:

```
ndiswrapper -i WG311v3.INF
```

I then do a ndiswrapper -l and shows:

```
wg311v3  driver installed, hardware present
```

I then to do the following and return no errors:

```
sudo modprobe ndiswrapper
```

From everything I seen/read I then should be able to do a "dmesg" and see in the log that ndiswrapper loaded the driver.

When I do a "dmesg" I get the following and thats it

```
ndiswrapper version 1.37 loaded (preempt=no, smp=yes)
usbcore: registered new driver ndiswrapper
```

I then do a ifconfig and only get the config for "lo" (eth0 disabled at the moment)

If I go into system-->administration-->networking the card isn't listed, only my wired NIC and no configured modem connection.

Any help is greatly appreciated

---

### Post by simonbowen on 2007-02-12
Hi There

I am a complete linux newbie. I have had the same problem with the openSUSE distro on my desktop. I am running a WG311T and I tried using the ndiswrapper, everything seemed to "work" ok. Still no wireless device listed. Although with Ubuntu the network card worked out of the box. I eventually came to some sort of conclusion it was a Atheros card which complicated things. 

I came to no resolution to this problem so I installed Ubuntu and used that instead, but I am pretty sure it was something to do with the fact it was an Atheros card. I'd be interested to find out if there is a solution to this since I'd like to use openSUSE as my server.

---

### Post by ubuntu_demon on 2007-02-22
I would suggest to not use ndiswrapper. First undo the steps you have done trying to make it work with ndiswrapper. Then install the restricted modules for your kernel.

$uname -r

Then choose which one to install based on that result :
$ sudo aptitude install linux-generic
$ sudo aptitude install linux-386
$ sudo aptitude install linux-686

This packes makes sure that you will always have the relevant restricted modules even after a kernel upgrade.

Login to your router and set your router to unsecured.

Now do a reboot and configure your network using system->administration->networking.

If all is well now you will have wireless internet :).

Otherwise you might need to modprobe some modules but we'll see about that later if necessary :)

Assuming you have wireless internet :

Now you will need to configure some security settings. One which is very easy is mac-filtering. You can do this in your router and you don't have to do anything on your pc (wireless) settings.

You can additionally use WEP if you decide to use WEP you need to configure this on your router and in system->administration->networking.

Instead of WEP you can use WPA(2). Which is harder to setup. If you decide to do this then here's a guide :
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

I'm very interested in your experiences. I hope you get WPA2 personal running with CCMP/AES. I'm searching for a wireless card myself see :
[http://www.ubuntuforums.org/showthread.php?t=363633](http://www.ubuntuforums.org/showthread.php?t=363633)

the netgear WG311T is one of the candidates

---

