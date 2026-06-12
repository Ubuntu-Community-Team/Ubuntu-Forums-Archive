---
title: "Wifi connected through terminal, mail client.. but can't load web pages?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-05
Hi everybody,

I hope that the forum moderators don't get steamed about my having the same problem posted a couple of different ways, but I am sort-of stuck here, and don't know which forum would be the most appropriate for this problem.

So, since I *am* a n00b, I'll try here and see if anyone can get me straightened out.

Here is the the thread in the repository support forum that I posted to try to resolve this:

[http://ubuntuforums.org/showthread.php?t=229768](http://ubuntuforums.org/showthread.php?t=229768)

I have followed all the troubleshooting advice, but don't know where to go from here.

One more thing, I am able to connect to my mail server through Evolution Mail, and it sends and receives fine.

I'll admit, I'm stumped and after sitting in a coffee shop that has an open wifi network for two days on-and-off, it's starting to wear on me a little.

TIA for *any* and all help.

Kent

---

### Post by Carbonfish on 2006-08-05
Bump

---

### Post by AirRaven on 2006-08-05
Have you got a DNS address set up in System->Administration->Networking->DNS?

If you don't have one, use the [OpenDNS](http://opendns.com/)- enter "208.67.222.222" and "208.67.220.220". 

Did it work previously, or is this a completely new thing that's been the same since you installed Ubuntu?

---

### Post by Carbonfish on 2006-08-05
Hi AirRaven, Thanks for taking the time to respond.

This is a new problem that has been the same since I installed Dapper. I just installed Ubuntu for the first time on the IBM ThinkPad that is detailed in my signature. Pretty much everything worked out of the box, but  I can't get the internal modem to work even though it is recognized in the device manager (I understand that this is a known issue with the PPP thing), but I am not really worried about that. I would just like the PCMCIA wifi card to be able to connect to whatever open network happens to be around. The card is recognized by the OS (as far I can tell from the device manager, I am still not very hip to the terminal... But I'm trying! :D ) and it looks like I am connected in the terminal. If you look at the steps that I took in the other thread that I linked in the opening post in this thread, you can see what I have tried.

I also did an iwconfig and here is the output:

eth1 IEEE 802.11b ESSID:"springcreek" Nickname:"Prism I"
Mode:Managed Frequency:2.462 GHz Acess Point: 00:11:50:OA:IE:8D
Bit Rate:11 Mb/s
Retry limit:16 RTS thrff Fragment thr=0 B
Power Management: off
Link Quality=30/92 Signal level=137/153 Noise level=107/153
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

Thats about it. Right this minute I am not where there is a wireless network, so I will have to get somewhere with an open net to try your suggestions (that is one of the things that is making this process difficult and frustrating for me, and possibly for you guys too.)

Anyway, I will enter the DNS addresses you recommended and go from there.

Thanks, and I'll post back here when I get to a networked spot.

Kent

---

### Post by Carbonfish on 2006-08-05
Bump.

For the next hour or so I will be where there is a wireless network available if anyone has any suggestions for me.

Thanks,

Kent

---

### Post by AirRaven on 2006-08-05
> **Carbonfish said:**
> Bump.

For the next hour or so I will be where there is a wireless network available if anyone has any suggestions for me.

Thanks,

KentDid the DNS servers I reccomended help at all?

---

### Post by Carbonfish on 2006-08-05
Hi,

No. I entered them in the DNS servers box under the DNS tab in network settings, and when the wifi card connected it listed a server of 192.168.X.X

What next?  :D 

KC

---

### Post by AirRaven on 2006-08-05
Try pinging Yahoo.com or any other address again?

```
ping yahoo.com
```

If that works and your net's still not working, I have no idea how to help. 

Many apologies. I hope you find a way to sort out your problem somehow. There's only so much coffee a man can drink, remember. :(

EDIT: Have you checked to see whether you can set up your internet on the Ubuntu Live/Install CD? I have frequent internet problems- disabling ipv6 helps for me, but I seriously doubt it would for you. If you want to try it, then just edit /etc/hosts and change it so the lines commented out in here are commented out in yours:
```
127.0.0.1 localhost stelhan-desktop
127.0.1.1 stelhan-desktop

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```

Then change the line *alias net-pf-10 ipv6* in /etc/modprobe.d/aliases to *alias net-pf-10 off*.

Like I said- I seriously doubt this will help you- I think it's a totally different problem. It's just the only thing I can suggest. You'll have to reboot after doing this to see if it works. If it fails, there's no real need to change it back- ipv6 isn't essential.

---

### Post by Carbonfish on 2006-08-05
Hi again AirRaven,

I pinged yahoo, and got:

PING yahoo.com (216.109.112.135) 56(84) bytes of data
64 bytes from yahoo.com (216.109.11.135): icmp_seq=1 ttl=54 time=109 ms

and that repeats for the 9 times that I let it ping before I hit  "ctrl C" to stop it.

I don't know why this thing won't connect through the GUI. :sad: 

Also, if I try to update through the terminal it just times out. Why can I ping, but can't seem to do anything else?

Anybody?

Oh yeah, wacky n00b question: After I do the command line thing, particularly if I sudo and am asked for my password, do I have to do anything special to log out before I quit the Terminal, or do I just "exit" the same way I would on my Mac?

Thanks for your help AirRaven.

KC

---

### Post by AirRaven on 2006-08-05
> **Carbonfish said:**
> Oh yeah, wacky n00b question: After I do the command line thing, particularly if I sudo and am asked for my password, do I have to do anything special to log out before I quit the Terminal, or do I just "exit" the same way I would on my Mac?

The [FONT="Courier New"]sudo[/FONT] command works identically to the Mac OS X version- just wait for a few minutes and it "wears out". 

As a general rule of thumb, it's not advisable to use "sudo" for graphical applications- just a small himt. Use the [FONT="Courier New"]gksu[/FONT] command instead- otherwise it may seriously mess up your system. ([FONT="Courier New"]gksudo[/FONT] is also usable)

---

