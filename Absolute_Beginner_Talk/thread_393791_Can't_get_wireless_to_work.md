---
title: "Can't get wireless to work"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by madcello on 2007-03-26
I'm very new to linux and i'm using Ubuntu 6.10.

I have an Atheros 5212 but in Network Tools it gives me "unknown interface". In the same Network Tools wifi0 is giving signal but if i make "iwlist scan" is ath0 that shows the ethernet.
I've read in other threads about restricted drivers but i already have them installed.

I have another network card (a wired one) that i have disabled in Networking.

I'm trying to connect using Wicd. I can see the connection but after i press "connect" it tries to get an ip and says again "not connected".

Can you help me?
I'm a real noob in linux.

Thank you very much!

---

### Post by mahy on 2007-03-26
What does the command 'iwconfig' show you?

---

### Post by madcello on 2007-03-26
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"JPFARQ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:4A50-4641-5251-4144-4D49-4E   Security mode:restricted
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by mahy on 2007-03-26
I'd do this: disable wifi0 and then use wifi-radar to connect to the Net (via ath0). If it doesn't help, let me know.

---

### Post by madcello on 2007-03-26
How do i disable wifi0 ?

---

### Post by chili555 on 2007-03-26
Are you sure your WEP key is correct?```
Encryption key:4A50-4641-5251-4144-4D49-4E Security mode:restricted
```128-bit WEP is exactly 26 characters, but you have 22. Perhaps you have obscured the real code, a very good idea, or perhaps you made an error.

---

### Post by madcello on 2007-03-26
double post.

---

### Post by madcello on 2007-03-26
What i've did was just a copy/paste the values.

It's not a WEP, it's WPA-PSK.

How do i disable wifi0 ?

---

### Post by chili555 on 2007-03-26
> It's not a WEP, it's WPA-PSK.I questioned it because the format shown in iwconfig is exactly the way WEP would appear, except there are too few characters. Second, in my Network Tools, there is no option to set up WPA. Did you install and configure wpa_supplicant?

---

### Post by madcello on 2007-03-26
I didn't toutch wpa_supplicant

---

### Post by madcello on 2007-03-26
I now have internet but not from wireless. I got tired of almost a week trying to connect that i talk to my office admin and ask him to connect by wire. I configure a static ip and i could connect this way.

I have to tell that this is frustrating!:(

---

### Post by eljalill on 2007-03-26
Sorry about your frustration... but hey, you just posted today :)
If you want your computer to connect to a network, that is wpa encrypted, you need the wpa_supplicant. You have to install it, either through synaptic, or per apt-get install .

You might also want to install a Network manager like  WiCD or- NetworkManager, both are in the repositories.

Please say, what (if anything) you need more help with of this

---

### Post by Hoaxe on 2007-03-26
I have the exact same problem when i am at work

everything is exactly the same as the OP's situation.

also to note.

when i look at my connection properties for ath0 it says it is an ethernet type when it is at the same time the only connection receiving a signal.

wifi0 is the connection that is receiving a connection but it is not reckognised as a wifi because it is not getting a signal. it simply doesn't show a signal bar at all.


help anyone?

is madwifi my solution?

---

### Post by madcello on 2007-03-26
Thank you, eljalill
but i check for wpa supplicant and is installed and i've installed Wicd. Wicd was the one that showed me the wireless connection but it could not connect to it.

---

### Post by eljalill on 2007-03-26
I had the same problem once, when I didn't know that my brother had installed a Mac filter...

But I guess your administrator should know about this kind of stuff and tell you... but maybe sth to check?

---

### Post by camz on 2007-03-26
Well, you device must be working or there would be no link quality or name etc. in network, change the wireless settings to DHCP, and make sure the correct network name is there. set the password type to hexadecimal, but dont insert a password.

in the terminal, type:

iwconfig wifi0 enc xxxx-xxxx-xx open

(replace the xxxx with your WEP key

now type:

dhclient wifi0

If that doesn't connect, I am sorry but it's the best I have. :P

---

### Post by camz on 2007-03-26
oh and replace wifi0 with whatever yours is, mine was rausb0, some are wlan0, eth0 etc..

---

### Post by Hoaxe on 2007-04-01
ok, i found this a while ago but i forgot to post it here [so sorry!! :( ] 

the solution you need is on this page: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

as far as i can tell, this is the only way we should connect to wireless and it should come right out of the install. we shouldn't need to find out what is the connection name, ubunutu should just tell us like it will when you do all those steps. 

enjoy

---

### Post by raceduck on 2007-04-25
I tried the debianadmin guide; the wireless network option does not appear. I can stay connected to wired or go to manual configuration. Manual configuration doesn't allow a wireless option. What have I missed? All the recommended packages are installed, I guess. Yes, I am very noob to this...

---

