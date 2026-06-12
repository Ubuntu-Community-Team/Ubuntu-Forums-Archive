---
title: "Mapping iwconfig commands to /etc/network/interfaces"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by linuxa on 2006-12-27
Hi there

I had some issues recently with my wirless connection after a router reset (go figure :-k ).

So after spending sometime finally getting it up again, I realized that my /etc/network/interfaces file no longer works, meaning that I'm having to manually configure all settings via the iwconfig command.

Previously, I had pretty much scraped together bits and pieces from here and there to get a working interfaces file. Now that's gone down the toilet, I'm wanting to know the **proper way** to map iwconfig commands to lines in /etc/network/interfaces.

In order to get my wireless connection going, I have to do:

```

1 sudo iwconfig wlan0 mode Managed
2 sudo iwconfig wlan0 key open <password>
3 sudo iwconfig wlan0 essid <id>
4 ifconfig wlan0 up
5 sudo ifup wlan0

```

Based upon my limited understanding of how /etc/network/interfaces file work ("man interfaces" doesn't give any specific info for wireless connections), I tried mapping lines 1 through 3 to the following lines in the interfaces file (line 4 is automatically executed by Ubuntu on boot I think, line 5 I've set up KNemo for).

```

iface wlan0 inet dhcp
essid   <id>
mode   Managed
key     <password>

```

Now the format above simply does NOT work, and upon booting the computer, the connection is always associated with my neighbours wireless network ;) 

And it's only after manually executing the 5 statements earlier that I'm able to get the connection going.

Could someone possibly tell me (or point me to the right manual) how to correctly map iwconfig commands to settings within /etc/network/interfaces please?

Thanks in advance.

---

### Post by dbott67 on 2006-12-27
```
dbott@dapper:~$ sudo gedit /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

[COLOR="Red"]auto wlan0
iface wlan0 inet dhcp
wireless-essid <your-essid>
wireless-key s:yourasciiwepkey[/COLOR]
```

The preceding **s:** is needed for ASCII WEP keys.  Remove the **s: **to use the HEX key.

-Dave

---

### Post by linuxa on 2006-12-29
thanks for the reply **dbott67**.

No go I'm afraid, that was the setting that I had before the router reset.

The only change in router config post-reset was the essid, which I had changed in /etc/network/interfaces, but it simply wouldn't take. I always get:

[I]wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]

as if it can't find the network, this is regardless whether or not I have essid broadcast on.

For the record, the essid is in lower case now (instead of upper), would that have something to do with it??

And the only way that I could get the wireless going with the 5 step manually setting the iwconfig is if I drop the wireless prefix in the interfaces file, with it, though you don't notice any change when you check on wireless status using iwconfig, you simply can't connect to the network... 

Very weird, I hate running into those Linux problems where there are no logical explanation (or in most cases, a lack of underlying understanding of the problem for me :p).

---

### Post by dbott67 on 2006-12-29
I don't have any experience with some of the wireless network manaegment tools, but my understanding is that some of them take over complete control from the interfaces file.  So, Knemo may be causing you the problem.

Try removing & purging the package and just follow the format above and try manually.

I'm afraid I'm not going to be much help on this one. :(

-Dave

---

### Post by linuxa on 2007-01-11
> **dbott67 said:**
> 
I'm afraid I'm not going to be much help on this one. :(

-Dave

That's ok Dave, I appreciate all of the valuable input that you've given me thus far. Will post more as I try to trace back to the root of the problem.

Thanks & Regards

---

