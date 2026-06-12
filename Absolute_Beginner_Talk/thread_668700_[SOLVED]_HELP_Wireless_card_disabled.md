---
title: "[SOLVED] HELP Wireless card disabled"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by L_e_n_n_y on 2008-01-15
[COLOR="DarkSlateBlue"]Hi, Im new in linux but I've been reading a lot about this wireless drivers issues, finally i was able to install drivers I was so excited. then I ran 'ndiswrapper -l'  it shows:
lsbcmnds: driver installed, device (14e4:4318) present; so far so good, right?
then   I ran "sudo ifup eth1"
result= ignoring unknown interface eth1=eth1

its not enable it

Am I missing a step or something?


How Can I enable my wireless interface?, Could you guys tell me in simple steps?


I'll appreciate any help[/COLOR]
Leo.

---

### Post by Papa-san on 2008-01-15
What do you get when you run:
```
sudo iwconfig
```
Likeley\\y it's going to say wlan0 or something like it...
Take a peek at the links in my signature line too...

---

### Post by L_e_n_n_y on 2008-01-15
I ran 

sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Papa-san on 2008-01-16
Sorry for the delay in responding again.
ndiswrapper -l has good output. It means your drivers are good. 

Your access point is invalid. 
```
iwlist scan
``` This will show if your ESSID is right. If you can log in to the router control panel, see if you can turn off WEP or whatever wireless security you use. Once it connects, you'll be able to turn it back on.

Also post output from```
ifconfig
```

I found a really good wireless program that I use. Look for WICD on this site or Google. Once that one is installed, it kinda takes all the guesswork out of it.

---

### Post by L_e_n_n_y on 2008-01-16
Ok man first of all I want to tell you thank you very much for you help and time you are the only one helping me so far.

OK I turned off wep security on my router and restarted my laptop then I ran these

ndiswrapper -l

lenny@lenny-laptop:~$ ndiswrapper -l
lsbcmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

second

iwlist scan

lenny@lenny-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results


Then

ifconfig             I don't see my eth1 when I ran the command

lenny@lenny-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:60:10:3B:5A  
          inet addr:192.168.1.96  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe10:3b5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3452227 (3.2 MB)  TX bytes:579314 (565.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Im sure something is missing but I don't know what it is, hopefully you can help me with all this info, Thank you man

---

### Post by Papa-san on 2008-01-16
LOL... I noticed I was the only one here trying to help you get through this... I apologize in advance, but it seems to be the blind leading the blind here!

I am referring to a thread I ran a year ago that is very similar. I managed to get through it though!

One thing I need to tell you about is that I did an update this morning, which included a kernel update. When I did the re-boot sequence, it came up with no eth1 interface. I haven't gotten it resolved yet, but one of the suggestions I got was to uninstall and then re-install ndiswrapper. Don't do anything to the drivers, just ndiswrapper.  I'm working on getting the exact code to do that and will post it here for you. We'll try that first.

I'd try ```
sudo aptitude remove ndiswrapper
``` then ```
 sudo aptitude install ndiswrapper
```
Since my wireless is down on the new kernal, I'll have to wait until I can get to a wired location to do it myself. It won't do much good if I do it with the older one I'm currently running, I think.

---

### Post by L_e_n_n_y on 2008-01-16
Well man, don't worry I'm sure that at the end we are going to get through this and we are goign to learn more about this issue.

So I've been missing around a lot in Ubuntu that now I have other kind of problem, any way I decided that I'm going to start all over again, new fresh Ubuntu installation then I'll follow everything step by step and we'll see hopefully  it'll work.  I'll let you when I'm done.

---

### Post by Papa-san on 2008-01-17
Well, let me know how it works out for you. I know that in 7.10 they made the wireless work better for most of the newer systems, but as a result, they made it worse for those of us with slightly older hardware. Fortunately, there are threads that show us how to remark out the new stuff and install ndiswrapper... Then we need to play with it a bit, but it'll function.

---

### Post by L_e_n_n_y on 2008-01-17
FINALLY...:guitar:

OK, my wireless card is working after 4 day and 7 hrs.. 

I realized that I had so many problems, but the main one was that I was ndiswrapper 1.4 instead of ndiswrapper 1.51 then I followed this forum:

[http://ubuntuforums.org/showthread.php?t=297092&highlight=network+driver](http://ubuntuforums.org/showthread.php?t=297092&highlight=network+driver) 

you need to make some changes if you don't have this laptop mode, I have an IBM but it worked just fine, I hope this can help you too if you still having problems with your wireless.

Let me know how you doing with your wireless.

---

### Post by Papa-san on 2008-01-17
AWESOME!

I'm glad you got it working. I'll eventually get around to hauling it upstairs and hooking it into my router. Until then, my old kernel works just fine...

Go ahead and mark this thread 'solved'... (In the thread tools available to you...

---

