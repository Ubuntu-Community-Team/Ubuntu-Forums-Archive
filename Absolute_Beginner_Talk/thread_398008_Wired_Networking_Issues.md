---
title: "Wired Networking Issues"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by mayank_fun2006 on 2007-03-31
Hello Every1
I just installed ubuntu 6.06 10 minutes ago (taking help from a friend in partitioning) and now it is setup. But there is the biggest problem im facing , that is no internet detection,

I am using the Realtek Rtl-8139d PCI Fast Ethernet Adapter but ubuntu is not detecting it at all. Most of my friends use the same and they are getting  a proper network.
I am totally a newbie. THe Networking window does not show anything else except a modem connection (which of course is not set up).

I have tried the command
sudo pppoeconf 

with no avail..

ThankYOu!!

---

### Post by eljalill on 2007-03-31
What is the output of lspci ? (terminal command)

---

### Post by mayank_fun2006 on 2007-03-31
Thanks for the quick reply man , but ill have to reboot my comp for that!!
Ill do it asap and get back to you

---

### Post by mayank_fun2006 on 2007-03-31
Here is the output of the command lspci : 
nick@nick-desktop:~$ lspci


0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:0a.0 Ethernet controller: Unknown device 1904:2031 (rev 01)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
nick@nick-desktop:~$

---

### Post by eljalill on 2007-03-31
At least it sees, you have an Ethernet controller :)
But when you type ifconfig it doesn't come up? Or does it?

---

### Post by mayank_fun2006 on 2007-04-01
i got this output!!!!!

nick@nick-desktop:~$ ifconfig
lo        Link encap:local loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txquenelen:0
          RX bytes:14652 (14.3 KiB) TX bytes:14652 (14.3 KiB)

nick@nick-desktop:~$




and i have one problem more!!!!!
there no sound coming!!!!!!

---

### Post by eljalill on 2007-04-01
I found this thread here, from someone who has the same problem. It doesn't sound good, but you can try what they propose, and maybe you have better luck than the OP there:
[http://www.ubuntuforums.org/showthread.php?t=312859&page=3&highlight=1904%3A2031](http://www.ubuntuforums.org/showthread.php?t=312859&page=3&highlight=1904%3A2031)
Apparently that card is a common problem.
If you have any questions, about what they did there ask!

You can find more posts in the forums and through google, when you search for the error message of your Ethernet card (1904:2031).

Sorry not to be of more help, and Sorry, I have no idea regarding the sound... You might want to start a new thread with more details about that.

---

### Post by mayank_fun2006 on 2007-04-01
thanks for the help u provided , ill try it as soon as i boot into ubuntu

---

### Post by mayank_fun2006 on 2007-04-03
Thanks for all your help :)
Got Internet working , just switched from Ethernet to USB and surprisingly it worked like a charm without needing drivers..

---

