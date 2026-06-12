---
title: "Network problem"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by rmx on 2008-01-07
Hello,

I installed ubuntu last week and my wireless network connection was ok.

Now when I boot ubuntu the connection is ok but when I open firefox or synaptics or anything that needs internet, the connection goes down and keep asking me the password.


I insert the password exactly as I always done, but after a while it asks me again and again.


The wireless netwok is configured with WEP 64 bits HEX open.

I know it is no router problem because I configured the same way in windows and it works.

Anyone have a clue?

greetings

Rui

---

### Post by lisati on 2008-01-07
You might want to check out the "keyring manager" which can help manage your network passwords.

---

### Post by jeffus_il on 2008-01-07
Are you using NetworkManager?

---

### Post by rmx on 2008-01-07
[B]lisati: 
[/B]It seems not related with manager of passwords since even, I type it again and again network don´t work no more.

Strangely when I reboot, everything seems ok.

Keyring manager ask me the unlock keyring pass.
I type it and Net appears ok.

but as soon I need internet it goes down, and keeps me asking the password.

[B]jeffus_il:
[/B]NetworkManager? Do you mean the applet with blue bars on notification area? In that case I am.

---

### Post by jeffus_il on 2008-01-07
Yes it has little things that spin around, go into its configuration and cancel the roaming mode, then define the connection manually, could be that it causes a problem, I have found it has problems with certain drivers.

---

### Post by rmx on 2008-01-07
I've tried to do so, and it didn't worked either.

The strangest thing is that before reinstalling ubuntu last week I've always used roaming mode with no problems.

And after reinstalling it worked ok, but now I can't connect.

---

### Post by jeffus_il on 2008-01-07
Can you post the output of iwconfig in a terminal?

---

### Post by rmx on 2008-01-07
sure jeffus-il.

just a second to reboot on ubuntu and reboot on windows again

---

### Post by rmx on 2008-01-07
ok 
here it is. the encrypton key I masked with * but it was with the correct key:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"SpidersFromMars"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:11:D8:56:4D:DC   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:****-****-**   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by rmx on 2008-01-07
without emoticons


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"SpidersFromMars"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:11:D8:56:4D:DC   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:****-****-**   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by jeffus_il on 2008-01-08
OK, It sees the access point, it has its address, but it doesn't associate with it, this could be an encryption/key problem, maybe someone else will pick up something here, HELLO!!!

---

### Post by manmohanpv on 2008-01-08
If nothing worked, pls try installing Wicd

sudo apt-get install wicd and configure your /etc/network/interfaces files

-manmohan

---

### Post by rmx on 2008-01-08
**manmohanpv**

I can't install other software because I can't access the net on ubuntu.

And I would love to understand why this is happening since I'm a computer student.

I feel like it could be an encryption/key problem too. but I haven't change the key and it use to work fine.

rmx

---

### Post by jeffus_il on 2008-01-08
Use the terminal and the commands iwconfig and ifconfig mainly iwconfig for the wireless device.
try iwconfig --help or "info iwconfig" and see if something there helps you, you can't do any damage there, just lose your connection, which is lost anyway ...
and the changes are temporary so a reboot wipes them out.

Permanent changes are in /etc/network/interfaces.

Take a look at that file and see the content.

---

### Post by jeffus_il on 2008-01-08
my interfaces file looks like this:
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-key s:*****
wireless-essid linksys
auto wlan0

---

### Post by rmx on 2008-01-08
jeffus_il:

Now I'm even more confuse: I booted to ubuntu and net is working. 
I didn't do anything.

I'm going to post the pre iwconfig :

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"SpidersFromMars"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:11:D8:56:4D:DC   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:****-****-**   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

#########################
and now iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"SpidersFromMars"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:D8:56:4D:DC   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:****-****-**   Security mode:open
          Power Management:off
          Link Quality=82/100  Signal level=-48 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

#########################

well I can see a change from 
eth1      **unassociated ** ESSID:"SpidersFromMars" ->  eth1     ** IEEE 802.11g  **ESSID:"SpidersFromMars" 

So my question now is if my eth1 sudendly becames unassociated is there any command or script to associate to IEEE 802.11g again?

thank you

RMX

---

### Post by jeffus_il on 2008-01-08
There are a number of ways, you could restart networking by doing:
sudo /etc/init.d/networking restart

,but it would be good to get to the root of the problem.

Also check that your path from your antenna to your access point is as clear as possible, apparently the higher the ap the better, you may have something interfering with the radio transmission, which weakens the signal and you loose the connection, microwaves are often the culprit, maybe you have other electrical equipment in the area, maybe a transformer?

---

### Post by rmx on 2008-01-08
jeffus_il:

Even considering Ubuntu manages the same HD (wireless card) in a different way than XP (I mean: ubuntu power polices can be more radical and put the WC in a "weak signal" mode), I find very strange that the problem was related with signal.

Because exactly in the same conditions I booted with XP and it was OK.

And under the same environment conditions, today I booted and rebooted Ubuntu with no problem.

(!)

Anyway, thank you jeffus_il ;)

---

### Post by jeffus_il on 2008-01-08
True, I thought that since you setup was OK, maybe the environment was variable, you are right.

---

### Post by manmohanpv on 2008-01-09
I had similar problem, but i was able to connect to unsecured network and downloading wicd resolved my issue.

Are you sure that you are not able to connect access points which does not require a password?

-manmohan

---

### Post by cmittle on 2008-01-12
> **jeffus_il said:**
> my interfaces file looks like this:
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-key s:*****
wireless-essid linksys
**auto wlan0**

Thank you for posting the above.  For some reason my file did not have the bold part at the end.  I added that, restarted networking and now my wireless works.

Cory

---

