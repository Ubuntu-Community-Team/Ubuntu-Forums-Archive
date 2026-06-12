---
title: "Lost in Wireless"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by StrangeObsession on 2007-05-14
Hello all,
 As i have found through these forums, wireless internet connection seems to leave people frustrated and confused and so i dont feel too bad not being able to get mine set up. But i am starting to run out of options. NDISwrapper didnt work for me, after i installed it my wireless card wasnt even detected. And as far as the bcm43xx method i have yet to meet anyone with a decent connection. my iwconfig is as shown:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"l"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr : off   Fragment thr : off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I think i read somewhere that commenting out the "lo" connection might help but cant remember which file i should comment it from. i am using a linksys router with its default name "linksys". And i am using it without any passwords, yes i know its unsafe, but im in the middle of nowhere so not too worried about someone leeching from my wireless. currently i havent installed any packages i am running from a clean install of ubuntu fiesty fawn 7.04. If anyone has any advice please post, thank you.

---

### Post by skwishybug on 2007-05-14
I don't have advice, but I can provide feedback on my experience, I've never had any problems with connection on my wireless (Broadcom 4318) and get a very good signal. I'm limited at my router as it is an older B only router.

It does take a bit to set up, but there are a couple of very good how-tos that get me up and running quite quickly.

iwconfig: 
eth1      IEEE 802.11b  ESSID:"thebug"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:B5:04:0F   
          Bit Rate=11 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by lamalex on 2007-05-14
I am someone who has a good connection with bcm43xx. It works just as good as in windows. as for commenting out, you'd want to comment out a line in /etc/network/interfaces

---

### Post by StrangeObsession on 2007-05-14
ok thank you ill have to try that after i get home from work, and i was noticing that my essid says "l". anyway to change that? i remember going through the network manager and setting up the manual connection and setting it to "linksys". is there another method through the terminal?

---

### Post by StrangeObsession on 2007-05-14
and actually what is the commenting command.... im used to "//", is it still this?

---

### Post by StrangeObsession on 2007-05-14
Bump up

---

### Post by StrangeObsession on 2007-05-14
and for somereason when i try to connect through the irc client it says that the password is wrong.... either i am blind or i got a bad client but... i cant seem to find where i would insert the password.

---

### Post by Karl S. on 2007-05-15
> actually what is the commenting command.... im used to "//", is it still this?

It's the # sign. Go into the text file (e.g., /etc/network/interfaces) and just put a # before any of the lines you want to comment out. 

By the way, I don't recall getting wireless to work by commenting out lo, though. If I remember correctly, I had it working in Edgy by commenting out every line BUT the lo lines. However, right now I'm trapped in trying to get wireless working in a new Feisty install with a BCM4318.

---

