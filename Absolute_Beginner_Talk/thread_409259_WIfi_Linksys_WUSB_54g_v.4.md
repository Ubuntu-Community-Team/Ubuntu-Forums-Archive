---
title: "WIfi Linksys WUSB 54g v.4"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-14
Oh most helpful and knowledgeable:

I have just bought a LInksys WUSB 54g v. 4 wireless net adapter.  It is plugged in and under the SYstem-Administration-Network, it is listed (which is further than I got with my last usb adapter).

But I am still not able to connect to the internet.  What steps do I need to take?

I tried to configure the wireless connection:

1)  I don't know *exactly* what to type in ESSID or how to find out.
2)  I have it set to DHCP.
3)  When this didn't work, I found the Windows driver and installed it into ndiswrapper.  It says the network hardware is present.  But still - no go.

After reading what other people did with this adapter, I feel like I am making this more complicated than necessary or I am just missing something.  Please help.

Peace,
Lance

Oh yeah, when I typed iwconfig, this is what I got:

```


lo        no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"Huffman Family Network"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:19:5B:57:5C:EF   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-41 dBm  Noise level:-204 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

### Post by awiggin on 2007-04-14
BTW -

After reading my own post, I typed in "Huffman Family Network" to ESSID.

Still no go.

I have faith you can all help me - it is the principle of ubuntu.

-Lance

---

### Post by awiggin on 2007-04-14
I am pleading for your help.

If I don't get the wireless working this weekend before my wife gets home (out until tomorrow night), she may pull the plug on this whole experiment of mine.

She is really tired of CAT5 wires running across her bedroom.  So am I.

I feel like I am close.

-Lance

---

### Post by wieman01 on 2007-04-14
Alright then. I have a WUSB54G V4 as well, so perhaps we can get together here. First of all, please type in this command and post the results here:
> iwlist scan
And also turn off wireless encryption, enable DHCP (as you have mentioned), and tell us what your network's name is ("Huffman Family Network")?

This should be an easy one as long as you don't make use of encryption at this stage.

_**EDIT:**_
Forget about "ndiswrapper" and the Windows driver for the time being... it's too complicated for now.

---

### Post by awiggin on 2007-04-14
OK - after typing iwlist scan, I got this:

```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


```

Also. when I typed iwconfig I got this:

```


lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```

I believe the rausb0 went away because I followed these instructions:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

(those instructions involved ndiswrapper, so if we can avoid ndiswrapper, that would be great.  So far, that has never worked for me.)

Thank you for your help.

-Lance

---

### Post by awiggin on 2007-04-14
I don't know how to get my rausb0 back after following these instructions:


First you'll see that in the admin -> network there is a rausb0 wireless. However that does not work with the native drivers provided (think they used rt2570)

Step 1

So you need to blacklist it first in a file situated in etc/modprobe.d/

Code:

$sudo gedit /etc/modprobe.d/blacklist

add the following line in the blacklist file

blacklist rt2570

---

### Post by wieman01 on 2007-04-14
> **awiggin said:**
> OK - after typing iwlist scan, I got this:

```


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


```

Also. when I typed iwconfig I got this:

```


lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```

I believe the rausb0 went away because I followed these instructions:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

(those instructions involved ndiswrapper, so if we can avoid ndiswrapper, that would be great.  So far, that has never worked for me.)

Thank you for your help.

-Lance
Alright, let's continue in the other thread... will be easier for all parties involved.

---

