---
title: "Slow download speeds"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Elhindenburg on 2007-11-05
I just installed Ubuntu 7.10 amd64 and am using a ralink2500 wireless network adapter (pci). The wireless worked right out of the box and worked on LiveCD before the install however the maximum speed I am getting is about 70KBps. I am only located about 10 meters from my router (full speed in windows) and a wired connection works fine and at full speed (I cant use a wired connection however because then the cable would run through the kitchen).

I have a 1500/256k adsl connection and have been testing the speed by download from my ISP's file server (and others). The wireless is using a 64bit WEP encryption.

I have no idea what the problem is so any help would be appreciated, It just seems that the speed is capped at around 70KBps and it is very annoying.

```
wlan0     IEEE 802.11g  ESSID:"********"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: **:**:**:**:**:**   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

** out the SSID and MAC address, these values are correct but I am unsure on the others.

---

### Post by hyper_ch on 2007-11-05
How about using the eth0 to verify the download speed? If it is faster on eth0 then you know it's not the wifi... just to be sure.

And: WEP is not an encryption...

---

### Post by Elhindenburg on 2007-11-05
When using eth0 I get around 165KBps for the same files.

Encryption/Protection all the same to me, I doubt anyone is going to be stealing my connection on my farm :P

---

### Post by hyper_ch on 2007-11-05
Why then encrypt at all ;)

Hmmm, well.... what if yuo move closer to your router? Will the download speed be improved?

---

### Post by ushills on 2007-11-05
Use the serial monkey drivers, although the card is suppported I had similar issues with a RT61 based card - slow downloads (512kb/s)

I used the serial monkey drivers and my net speed went up to 5+Gb/s.  So although the drivers worked in Fiesty they are unreliable in Gutsy.

Have a look on the forums for advise as I only have the info for the RT61 card.

---

### Post by Elhindenburg on 2007-11-05
Even with the router and antenna right next to each other there was no improvement :(

---

### Post by Elhindenburg on 2007-11-05
> Use the serial monkey drivers, although the card is suppported I had similar issues with a RT61 based card - slow downloads (512kb/s)

I used the serial monkey drivers and my net speed went up to 5+Gb/s. So although the drivers worked in Fiesty they are unreliable in Gutsy.

Have a look on the forums for advise as I only have the info for the RT61 card.
Ok ill give it a shot and see what happens.

---

### Post by ushills on 2007-11-05
There is a guide here 

[http://ubuntuforums.org/showthread.php?t=584657](http://ubuntuforums.org/showthread.php?t=584657)

---

### Post by Elhindenburg on 2007-11-05
Followed those instructions and it now runs perfectly, I cant thank-you enough hyper_ch/ushills, very much appreciated :)

---

