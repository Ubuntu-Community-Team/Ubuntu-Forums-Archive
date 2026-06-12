---
title: "Ubuntu 12.04 and Atheros AR9485 wireless"
date: 2012-05-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Andrey Vasyliev on 2012-05-19
Hi,

I have ASUS Zenbook UX31e with Atheros AR9485 wireless adapter inside. I have a problems with wi-fi connection quality and stability. Signal level is too low (on Win7 was twice better) and Internet connection often disappears.

At the same time another laptop with Win7 works with wi-fi perfectly: good signal level and stable internet connection.

Can anyone help with this?

Thanx!

---

### Post by aimpau on 2012-05-19
Hi there,

Same problem here.

Check this for a probable solution and let's compare notes.

[http://www.emmolution.org/?p=253]("http://www.emmolution.org/?p=253")

---

### Post by Andrey Vasyliev on 2012-05-19
Thank you for help.

Done. But signal level is still low (2-3 ticks) and internet connection sometimes disappears (at the same time wi-fi connected, but signal is 1 tick). On Win7 using this laptop I get 4-5 ticks...

BTW router is really close to Zenbook...

Any ideas?

---

### Post by Andrey Vasyliev on 2012-05-19
Sometimes it's 5 ticks..... Strange behavior
BTW, if it's matter - power management for adapter is off.

---

### Post by aimpau on 2012-05-19
connection on my part is sporadic as well. give this a try:

[http://linuxblog.avserver.info/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/]("http://linuxblog.avserver.info/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/")


I think it may have something to do with this:

[http://askubuntu.com/questions/130379/ubuntu-12-04-wifi-problem-atheros-communications-inc-ar9285-wireless-network-ad]("http://askubuntu.com/questions/130379/ubuntu-12-04-wifi-problem-atheros-communications-inc-ar9285-wireless-network-ad")

---

### Post by metadeus on 2012-05-19
I have the same problem -- my wifi on asus zenbook has too weak signal. Windows 7 is ok.

I found no solution. The problem is still here on Fedora and openSUSE.

---

### Post by aimpau on 2012-05-19
May it's because of being "hard blocked".


For those having problems right now, can you open a terminal and type:

```
rfkill list
```

and paste your details here.

---

### Post by aimpau on 2012-05-19
STRANGE:

Four hours ago, I had my eM250 plugged in and I can't get a decent connection.

NOW, running only on battery, connection is flawless. Anyone else experiencing this?

The only diff is that when you type

```
iwconfig
```

the Power Management for plugged in is OFF and when on battery is ON.

Anyone got a clue on this one?

---

### Post by Andrey Vasyliev on 2012-05-19
Right now I had a problem again. I run:

```

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


```

So, no hard blocks.

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BlackHata"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:A0:F2:A2   
          Bit Rate=72.2 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Power management is OFF as usual, because I have disabled it following recommendations.

I haven't any idea whats wrong....

---

### Post by vikingmonkey81 on 2012-05-20
Same here + a new issue...
Does anybody else only see the connected AP, and no others?
I know there are several available in the area, based on same laptop (Asus Zenbook UX31E) with Win7 & another laptop with Ubuntu

---

### Post by metadeus on 2012-05-20
```
~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"**** off and make your own"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 50:67:F0:17:A0:D0   
          Bit Rate=18 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=21/70  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0

```
And I don't see other than mine APs too.

---

### Post by Andrey Vasyliev on 2012-05-20
I catched additional info about this bug. When my wi-fi hanged again I runned iwconfig


```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

..

---

### Post by aimpau on 2012-05-20
Thanks for the update guys.

So far, mine has been working fine for almost 20hours now, plugged in or not. Last thing I did before it worked is that I performed a linux kernel update. Can you guys update yours (use ethernet for the meantime)?

---

### Post by metadeus on 2012-05-21
You're lucky!
I've updated kernel just now, but no difference.

```
~$ uname -a
Linux metaisys 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux
```

Did you do anything else?

---

### Post by dimitarkolev on 2012-05-23
I have the very same problem with my ZenBook

---

### Post by marcio_mi on 2012-05-23
I also have the same problem on my zenbook. It is really unpredictable: sometimes it connects without problems for the entire day (with a very low signal strength even though I sit 3m away from the AP), then it starts disconnecting every minute. Every disconnect i have to disable wireless and re-enable it in order to connect again to the access point. As others mentioned, I can only see my own AP and not others'.

I don't have the laptop with me right now, but will try some hacks suggested.

---

### Post by dimitarkolev on 2012-05-23
I tried this:
[http://linuxblog.avserver.info/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://linuxblog.avserver.info/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/)
and there is no difference at all, my kernel is 3.2.0-24-generic i tried installing 3.3.7 which was no better.

The only thing that kind of helped me: **Possible workaround**: set the BSSID for your single access-point network ([see here]("http://ubuntuforums.org/showpost.php?p=11647255&postcount=643"))

Its still very poor signal 30/70 and slow connection but at least does not drop.

---

### Post by vikingmonkey81 on 2012-05-23
Trying this now, lets see how it goes:
[http://pleph.appspot.com/init/posts/view/2657865](http://pleph.appspot.com/init/posts/view/2657865)

---

### Post by tuvor on 2012-06-24
I also have poor signal strength on my UX31.
 I have tried what was in the blog to no avail, can not think of something else than
 that drivers would be completely useless in linux. is there any other driver I can try?

---

### Post by apokkalyps on 2012-09-21
Bump.  Has anyone verified a solution for this?  Many of us are having the problem so please tell us if so.

I'm having this same problem since I got my Acer S3 Ultrabook with the AR9485.  I will connect to my router and although the wifi icon (usually) stays constant, I stop being able to make requests and I have to click the icon, disconnect and reconnect to the network, at which point it works perfectly well until 2-120 minutes later when it happens again.  

This is intolerable since I bought this laptop to ssh into all my other machines, and I cant hold a constant connection for more than 15 minutes.

I keep a ping running in a terminal to my router all the time, most of the time my latency is 1-3ms, when this problem happens it starts bouncing around and works its way to 1,000-20,000ms, and then I know I have to disconnect and reconnect and it IMMEDIATLY goes back to 1-3ms.

I have a dual boot, 12.04/win7, and win7 also seems to have this problem, so it's not just ubuntu.  

I know not everyone has the s3, but since the acer s3 has the ar9485, it might be relevant to note that there are several google hits for Acer S3 users reporting this identical problem but in windows.  And the advice might be helpful for everyone else with the AR9485 in other machines.
[http://forums.whirlpool.net.au/forum-replies.cfm?t=1929061](http://forums.whirlpool.net.au/forum-replies.cfm?t=1929061)
Some people here say they have fixed it by turning off power saving in windows.  Can anyone tell me how to do something similar in ubuntu?

Another suggestion they have is to update from the driver version 9.2.0.439 (which I infer is the windows default) to 9.2.0.474.  
[http://www.ultrabooksforum.com/viewtopic.php?f=10&t=33](http://www.ultrabooksforum.com/viewtopic.php?f=10&t=33)
Here a user says Acer told him to update to the latest driver as well, and he tried it and it resolved the issue.

Here is a link to the 9.2.0.474 AR9485 driver from the acer page:
[http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/Wireless%20LAN_Atheros_9.2.0.474_W7x64_A.zip?acerid=634647103122158329&Step1=Notebook&Step2=Aspire&Step3=Aspire%20S3-951&OS=721&LC=en&BC=Acer&SC=PA_6](http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/Wireless%20LAN_Atheros_9.2.0.474_W7x64_A.zip?acerid=634647103122158329&Step1=Notebook&Step2=Aspire&Step3=Aspire%20S3-951&OS=721&LC=en&BC=Acer&SC=PA_6)


[http://www.atheros.cz/atheros-wireless-download.php?chipset=60&system=5](http://www.atheros.cz/atheros-wireless-download.php?chipset=60&system=5)
This crazy czech website supposedly has much more recent drivers 10.0.0.75 released just 2 weeks ago, but they are only the .inf files (which I think is all you really need so whats with the 45mb install package that usually comes wrapped around windows drivers?).

Can anyone help me try to use either of these newer driver options?

---

### Post by apokkalyps on 2012-09-21
Ok so there is this page dedicated to Acer S3 in linux.  
[http://www.linlap.com/wiki/acer+aspire+s3](http://www.linlap.com/wiki/acer+aspire+s3)
I have used it for a few things and I dont know why I just thought to reference it for this.  But it says specifically
>  One person has reported problems with the wireless chip, after some time wireless connections just disconnected. So, if you experience such problems you can fix it by compiling the Compat wireless drivers for the 3.0 kernel. Heres how :

First download the “build-essential”, “automake”, package in the Ubuntu Software center.

Download the file following this link:
[http://www.orbit-lab.org/kernel/compat-wireless-3.0-stable/v3.0/compat-wireless-3.0-2.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3.0-stable/v3.0/compat-wireless-3.0-2.tar.bz2)
Uncompress it using archive manager or another solution.

Compile and run it. 

Which sounds really promising, but when I run sudo make, I get
[http://pastebin.com/LsQZKa55](http://pastebin.com/LsQZKa55)

a linux mint thread where someone got the same error trying to install compat-wireless said it was "entering the wrong headers. Try to install the latest linux-headers 3.4"  I'm trying that next (so far my tangent stack is 4 deep)

---

### Post by gumis88 on 2012-10-13
Unfortunately nothing that is mentioned in this thread helped me. I have asus zenbook with AR9485 and under ubuntu (12.10) and fedora 17 singal and connection quality is low. At the same time if I boot into Windows I have no problems at all.
Is there anybody that solved low signal problem under linux for zenbook with AR9485?

---

### Post by avenger337 on 2012-10-30
I can also confirm wireless issues with this setup.  I thought it would be helpful here to document all of the fixes I've tried, as well as my machine info.  I'm very interested in finding a solution to this problem, so I'm happy to provide any additional debug information that I can.

I am running Ubuntu 12.04 x64 on an ASUS Zenbook UX31E.  Here is the relevant information about my machine:

```
> uname -a
Linux XXXX 3.5.0-17-generic #28~precise1-Ubuntu SMP Tue Oct 9 22:04:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

``````

12:02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

```(As you can see I upgraded to the 3.5 kernel based on [this Community Wiki page]("https://help.ubuntu.com/community/AsusZenbook#Wireless") to try to solve the problem)

```
> ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19626 (19.6 KB)  TX bytes:19626 (19.6 KB)

wlan0     Link encap:Ethernet  HWaddr e0:b9:a5:d3:00:49  
          inet addr:192.17.252.116  Bcast:192.17.255.255  Mask:255.255.248.0
          inet6 addr: fe80::e2b9:a5ff:fed3:49/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:562366 (562.3 KB)  TX bytes:98495 (98.4 KB)

``````

> iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```(Note that power management is off; also note that it claims I'm not currently associated with an access point, even though I am -- I believe this to be [an unrelated bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1035590"))

Now for things I've tried to fix the problem:


[LIST=1]
[*]Kernel update to 3.5
[*]Disable hardware crypto:
```
 /etc/modprobe.d > cat ath9k.conf
options ath9k nohwcrypt=1

```
[*]Disable ANI (I'm not really sure exactly what this does, I tried it on a whim based on [this thread]("https://wiki.archlinux.org/index.php/ASUS_Zenbook_UX31E#Wireless"))
```
 /sys/kernel/debug/ieee80211/phy0/ath9k # cat disable_ani
1

```
[*]When I am at home or somewhere with a fixed router, I set the BSSID of the access point in the Network Manager.  Note that **this does solve the problem in my case!**  However, it is not good enough, because when I am at work or other places, I cannot set this BSSID, and thus still get terrible performance.
[/LIST]
I can't think of any other specific changes I've made at this point, but I've been working on this for over a month now, so I may have done something else that I've since forgotten about.


With regards to the problem, my wireless card appears to simply drop out periodically.  The length of time ranges from a few seconds to a few minutes, but it seems to be doing this on a fairly consistent basis.  This manifests itself in the syslog in a number of different ways.  The most common message I see is the following:


```

Oct 30 13:17:35 midget337 wpa_supplicant[1171]: CTRL-EVENT-DISCONNECTED bssid=0e:06:1a:d3:00:49 reason=4
Oct 30 13:17:35 midget337 NetworkManager[1130]: <info> (wlan0): supplicant interface state: completed -> disconnected
Oct 30 13:17:35 midget337 NetworkManager[1130]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 30 13:17:35 midget337 wpa_supplicant[1171]: Trying to authenticate with 0e:06:1a:c4:64:da (SSID='IllinoisNet' freq=2437 MHz)
Oct 30 13:17:35 midget337 kernel: [  302.305824] wlan0: authenticate with 0e:06:1a:c4:64:da
Oct 30 13:17:35 midget337 kernel: [  302.310674] wlan0: direct probe to 0e:06:1a:c4:64:da (try 1/3)
Oct 30 13:17:35 midget337 NetworkManager[1130]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 30 13:17:36 midget337 kernel: [  302.513105] wlan0: direct probe to 0e:06:1a:c4:64:da (try 2/3)
Oct 30 13:17:36 midget337 kernel: [  302.716883] wlan0: direct probe to 0e:06:1a:c4:64:da (try 3/3)
Oct 30 13:17:36 midget337 kernel: [  302.920618] wlan0: authentication with 0e:06:1a:c4:64:da timed out
Oct 30 13:17:42 midget337 kernel: [  308.548716] wlan0: authenticate with 0e:01:1a:d3:00:49
Oct 30 13:17:42 midget337 wpa_supplicant[1171]: Trying to authenticate with 0e:01:1a:d3:00:49 (SSID='IllinoisNet' freq=2412 MHz)
Oct 30 13:17:42 midget337 kernel: [  308.555199] wlan0: send auth to 0e:01:1a:d3:00:49 (try 1/3)
Oct 30 13:17:42 midget337 wpa_supplicant[1171]: Trying to associate with 0e:01:1a:d3:00:49 (SSID='IllinoisNet' freq=2412 MHz)
Oct 30 13:17:42 midget337 kernel: [  308.563381] wlan0: authenticated
Oct 30 13:17:42 midget337 NetworkManager[1130]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 30 13:17:42 midget337 kernel: [  308.569844] wlan0: associate with 0e:01:1a:d3:00:49 (try 1/3)
Oct 30 13:17:42 midget337 wpa_supplicant[1171]: Associated with 0e:01:1a:d3:00:49


```
Note that wpa_supplicant has gone from a connected state to disconnected, and the reason given is '4' -- looking in the code for wpa_supplicant, this corresponds to WLAN_REASON_DISASSOC_DUE_TO_INACTIVITY.  I'm not really sure what this means, but I found a forum thread that suggested it was some sort of power management issue.


In other cases, I also see messages like the following in my syslog:


```

Oct 30 08:54:01 midget337 wpa_supplicant[1233]: CTRL-EVENT-CONNECTED - Connection to 06:0b:1a:d3:00:49 completed (reauth) [id=0 id_str=]
Oct 30 08:54:01 midget337 NetworkManager[1189]: <info> (wlan0): supplicant interface state: associating -> completed
Oct 30 08:54:43 midget337 pptp[25457]: nm-pptp-service-25438 log[logecho:pptp_ctrl.c:677]: Echo Request received.
Oct 30 08:54:43 midget337 pptp[25457]: nm-pptp-service-25438 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Oct 30 08:55:15 midget337 wpa_supplicant[1233]: Trying to authenticate with 00:0c:e6:6f:47:72 (SSID='UIUCnet' freq=2462 MHz)
Oct 30 08:55:15 midget337 kernel: [76182.617695] wlan0: authenticate with 00:0c:e6:6f:47:72
Oct 30 08:55:15 midget337 NetworkManager[1189]: <info> (wlan0): supplicant interface state: completed -> authenticating
Oct 30 08:55:15 midget337 kernel: [76182.622261] wlan0: No basic rates, using min rate instead.
Oct 30 08:55:15 midget337 kernel: [76182.622357] wlan0: direct probe to 00:0c:e6:6f:47:72 (try 1/3)
Oct 30 08:55:15 midget337 kernel: [76182.825056] wlan0: direct probe to 00:0c:e6:6f:47:72 (try 2/3)
Oct 30 08:55:15 midget337 kernel: [76183.028781] wlan0: direct probe to 00:0c:e6:6f:47:72 (try 3/3)
Oct 30 08:55:16 midget337 kernel: [76183.232315] wlan0: authentication with 00:0c:e6:6f:47:72 timed out
Oct 30 08:55:21 midget337 wpa_supplicant[1233]: Trying to authenticate with 06:0b:1a:d3:00:49 (SSID='UIUCnet' freq=2462 MHz)
Oct 30 08:55:21 midget337 kernel: [76188.866615] wlan0: authenticate with 06:0b:1a:d3:00:49
Oct 30 08:55:21 midget337 kernel: [76188.881750] wlan0: send auth to 06:0b:1a:d3:00:49 (try 1/3)
Oct 30 08:55:21 midget337 wpa_supplicant[1233]: Trying to associate with 06:0b:1a:d3:00:49 (SSID='UIUCnet' freq=2462 MHz)
Oct 30 08:55:21 midget337 kernel: [76188.883548] wlan0: authenticated
Oct 30 08:55:21 midget337 NetworkManager[1189]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 30 08:55:21 midget337 wpa_supplicant[1233]: Associated with 06:0b:1a:d3:00:49

```
While the messages in the log are different (maybe because the AP is unsecured in this case?), the behaviour is nearly identical -- every 30-600 seconds, the wireless card tries to "reauth".

Are there any suggestions as to what might be going on here?  I've seen some suggestions that the 3.6 kernel has better wireless support.  Should I try upgrading to this?  Is there any other information on my machine I can provide?  I haven't seen a formal bug report for this issue anywhere, is it worth filing one?

Thanks for your help!

---

### Post by avenger337 on 2012-11-01
Hi, all,

I've found some further information that may be useful.  First, [here is another post from a guy]("http://comments.gmane.org/gmane.linux.kernel.wireless.general/94770") that looks like he's having exactly the same problem.  He had one further suggestion to try, that is to disable ipv6.  I did this, and it did not help.

Next, there are a whole host of different bug reports that are of varying degrees of similarity to the issue talked about here.  [This bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154") is the closest one I've been able to find.

Finally, and perhaps most usefully, I [found a thread]("http://nilvec.com/disable-scanning-in-networkmanager-when-connected/") suggesting that the scanning behaviour of NetworkManager is causing wireless to hang.  Apparently, NetworkManager scans for new channels exactly every 2 minutes, which can cause the wireless to hang.  I went back and looked at my syslog again, and I'm getting disconnection events exactly every 2 minutes, which makes me suspect that this might be the problem.

According to that thread, there's no way to disable this behaviour except by modifying the NetworkManager source (though the thread is two years old at this point).  Anyways, I'm going to attempt to update my networkmanager code via the procedure described and see if that helps my connectivity issues.  I'll report back once I'm done.

---

### Post by wag1 on 2012-11-06
Hello to the community! 

Am using ubuntu on my ux21 for almost a year now and actually hadn't faced this problem until the system upgraded to 12.10. After the upgrade my wifi connection got disconnected every couple of minutes with: 

"All devices are disconnected, going to restore regulatory settings". 

The problems exists in current 3.5 kernel, but if I boot up with the 3.2.0-32-generic kernel I no more get this message and wireless connection gets stable again!

Hope this info will help somehow. And please, do share it with the devs, if possible, as I'm not sure where exactly to post that, so this could be fixed in the latest kernel versions. Tx

_UPD: 3.2.0-32 does not help either. I was mistaken._ Problem disappeared only for a couple of hours after booting into 3.2 kernel - now I still get All devices are disconnected message every couple of minutes. That makes me really mad.. =(

---

### Post by avenger337 on 2012-11-06
I can confirm that modifying the code (as described in my previous post) does not solve the problem.  I still disconnect and reconnect frequently.  I think I may see about upgrading to the 3.6 kernel; I've read a few places that the wireless support in this kernel is a lot better, but I'm not optimistic...

---

### Post by gfmichaud on 2012-11-19
The bug is declared
- here, for Canonical : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971809)
- here, in the kernel : [https://bugzilla.kernel.org/show_bug.cgi?id=49201](https://bugzilla.kernel.org/show_bug.cgi?id=49201)

Feel free to help or provide information. :)

---

### Post by Potential Business User on 2013-01-26
I have an Asus U36JC laptop with an Atheros AR9285 card (which I understand is similar to the AR9485 card), and the problem (in may case, network activity stopping after a few minutes, requiring reboot or disconnecting and reconnecting) started for me when I tossed my 'g' router and got an 'n' router.

The problem went away when I changed the router settings to use only 'b' and 'g' but not 'n'.

Admittedly not an ideal solution, but easier than recompiling.

---

### Post by Craigbob on 2013-03-24
I have no idea why, and not sure if it'll help but think its worth mentioning. i have a packard bell dot s, with a "AR9485" anyways it will not connect on wifi, will just keep re-trying... until i unplug my power lead...  then it will connect first time for reasons i don't understand, and then if i plug my power back in... it'll just carry on staying connected

---

### Post by Stickee on 2013-06-30
Hmm.. weird, this worked for me as well.  I had ping up, pinging 8.8.8.8 with no response.  The second I unplugged power, I start getting responses.

---

### Post by gfmichaud on 2013-07-10
The bug has been solved and the patches will be included in the next kernel (3.11 ?).


It is possible to backport the fix to your current kernel :
1) get the lateste archive  here : [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/)
2) uncompress the archive and go in the uncompressed folder
3) run "make defconfig-ath9k", then "make" and then "sudo make install"
4) reboot and enjoy the patched version of the driver ;)

---

### Post by torresrandy on 2013-08-08
hello gfmichaud. i have been searching around the web for a solution to this problem and you seem to have the right idea!

the only problem is, that i don't quite understand what you're saying to do.  I am running on Linux Mint and my kernel is Linux randy-UX31E 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Could you explain step 3 for a beginner?

---

### Post by rrc326 on 2013-08-18
This worked perfectly!  Thanks for posting.

> **gfmichaud said:**
> The bug has been solved and the patches will be included in the next kernel (3.11 ?).


It is possible to backport the fix to your current kernel :
1) get the lateste archive  here : [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/)
2) uncompress the archive and go in the uncompressed folder
3) run "make defconfig-ath9k", then "make" and then "sudo make install"
4) reboot and enjoy the patched version of the driver ;)

---

### Post by rise99 on 2013-08-20
I too wanted to chime in and have been suffering with the Atheros wireless problem. My wireless worked fine in Windows but Linux it showed between 30% and 55% even when standing next to the router.  Anyway, I stuck in a usb realtek wireless-n adapter;to test out that there was a problem with the Atherios card, and it worked perfectly fine 

So I did what the above poster said and it worked perfectly.  I am now showing at 80% connection rate. a huge improvement. 

Just as @gfmichaud and @rrc326 say, do the following.  it works great. 


The bug has been solved and the patches will be included in the next kernel (3.11 ?).

It is possible to backport the fix to your current kernel :
1) get the lateste archive here : [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/)
2) uncompress the archive and go in the uncompressed folder where mine was /home/"yourusername"/downloads/backports-20130618/
3) go into a terminal in that last folder and type "make defconfig-ath9k", wait to finish, then type "make", wait to finish, and then type "sudo make install"
4) you will be prompted to enter your password, do so, wait to finish
5) reboot and enjoy the patched version of the driver ;)

I tried to explain as much of it as possible so, hope this helps....

---

### Post by pulseur on 2013-08-26
It worked perfectly for me too under Linux Mint 15 Olivia with Asus N550J
THX a lot man :)



> **gfmichaud said:**
> The bug has been solved and the patches will be included in the next kernel (3.11 ?).


It is possible to backport the fix to your current kernel :
1) get the lateste archive  here : [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/)
2) uncompress the archive and go in the uncompressed folder
3) run "make defconfig-ath9k", then "make" and then "sudo make install"
4) reboot and enjoy the patched version of the driver ;)

---

### Post by Kiril_Donov on 2014-05-04
Hi All,

I'm very new in Ubuntu and I'm in love with it. 
I've got an Asus N550JK. I installed 14.04, but my wireless is not working. I can see the networks, but can't connect. In Windows 8.1 it works fine. My wifi adapter is Intel. I tried to follow the steps that were recommended above, but after I go in the uncompressed folder and start the terminal by Cltr+Alt+T, I type "make defconfig-wifi" and this is what I get:
make: *** No rule to make target 'defcongih-wifi'. Stop.
I suppose, the file couldn't be found. I also tried with "ath9k" just to test and got the same message. Both files are present in the defconfigs folder.
Thanks a lot for any help!

P.S. I've got Ubuntu only at the moment, no Windows.

---

### Post by xdonbaldwin on 2014-06-15
> **rise99 said:**
> I too wanted to chime in and have been suffering with the Atheros wireless problem. My wireless worked fine in Windows but Linux it showed between 30% and 55% even when standing next to the router.  Anyway, I stuck in a usb realtek wireless-n adapter;to test out that there was a problem with the Atherios card, and it worked perfectly fine 

So I did what the above poster said and it worked perfectly.  I am now showing at 80% connection rate. a huge improvement. 

Just as @gfmichaud and @rrc326 say, do the following.  it works great. 


The bug has been solved and the patches will be included in the next kernel (3.11 ?).

It is possible to backport the fix to your current kernel :
1) get the lateste archive here : [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/)
2) uncompress the archive and go in the uncompressed folder where mine was /home/"yourusername"/downloads/backports-20130618/
3) go into a terminal in that last folder and type "make defconfig-ath9k", wait to finish, then type "make", wait to finish, and then type "sudo make install"
4) you will be prompted to enter your password, do so, wait to finish
5) reboot and enjoy the patched version of the driver ;)

I tried to explain as much of it as possible so, hope this helps....


Hey rise99 I am fairly new to Ubuntu and I'm having trouble following your directions. I'm a noob and not ashamed to say it. I actually have two questions - 1. Is there a specific archive from the list I should get or does it matter which one - 2. How exactly do I go into the terminal in that last folder? Like I said I'm very new to Ubuntu and I am kinda having a rough time following some of the instructions on here (mainly because I'm kinda dense at times and I get confused as to what exactly I am being told to do lol). If you could clarify that would be greatly appreciated. Thank you for your time.

---

### Post by mörgæs on 2014-06-15
The only important thing in the post above is 'solved in kernel 3.11'. 

Just do a clean install of 14.04 using wired internet access and you will get there.

---

### Post by xdonbaldwin on 2014-06-15
Do I need to do a backup of my files before doing a clean install of 14.04?

---

### Post by mörgæs on 2014-06-15
Please read the top link in my signature.

---

### Post by xdonbaldwin on 2014-06-15
Thank you for all the good advice and I will definitely give it a try as soon as I manage to figure out whether or not certain files (that are currently missing) are still on my laptop.  I will definitely keep you all informed on how everything goes and I will be spending a lot of time on the forums trying to learn everything I can about Ubuntu.  Thank you again for spending the time to help me.

---

### Post by mörgæs on 2014-06-15
You're welcome. 

Please let me know if anything in the guide is unclear.

---

