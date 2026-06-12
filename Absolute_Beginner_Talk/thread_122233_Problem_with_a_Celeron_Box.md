---
title: "Problem with a Celeron Box"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by boyfrienddan on 2006-01-27
Hi!

I was hoping somebody could give me some tips about what I can do to solve this problem with my Celeron machine. I was trying it out to become a test Internet server for my elementary school computer lab. It's an old Celeron 366Mhz. I've tried first to make it into a main ubuntu-server, which almost worked, except that it seemed to have problems with the network cards (I installed two, one was a realtek and the other the original netgear that came with the box). I succeeded in replacing the realtek one when I revamped the machine and loaded windows XP and found out that it wasn't working. I then proceeded to get another replacement card to make sure I still had to. 

Now I suspected that the first time I tried the ubuntuserver mode, that it was only a network card issue, which gave me a DHCP error (which didn't connect to my everpresent lan-based internet), and so I tried loading ubuntu again, this time in desktop mode (I am a newbie, by the way), hoping to see both cards working this time.

Apparently, it recognizes both cards, but it doesn't give me the Internet connection, even though I changed its IP settings. I'm writing this thread from the Windows end of the same machine, and it works perfectly fine. What do you think is wrong?

As of the moment I'm trying to still test this machine and not want it to be an XP dual-boot, since I want to test it as a server. Another problem I noticed is that gnome loads really really really slow, as with its handling of applications, although hopefully I'll be able to revamp this again to only a server setup. I have 128MB RAM. 

Any guesses? Thanks.

---

### Post by bscbrit on 2006-01-27
Well, lets look at the current network configuration.  Please tell me the output of the following command:

ifconfig

Secondly, how is the network configured.  Ethernet connection to a modem/router, or a hub, or another machine (I'm not sure what you mean by 'lan-based internet')?

---

### Post by boyfrienddan on 2006-01-28
I did ifconfig already when I turned to failsafe, and it gave me both the results for the eth0 and eth1. One thing I noticed though was a 100% loss in sent (I kinda forgot what particular sent that was). 

I am using a broadband router (linksys wrt54g) and is serving 25 windows XP machines through my local network. It is also my current DHCP server and gateway. All computers here are set up with static IPs.

Thanks.

---

### Post by bscbrit on 2006-01-28
I'm definitely confused now. 

If all of your computers have static IP addresses, what is your DHCP server serving to?

I know that ifconfig will give you the data relating to eth0 and eth1 but can you give the results to me please?  I'm trying to help pinpoint where your network is failing and its hard to do using my crystal ball alone....:-D 

Can you ping each of your 25 XP computers from the server?  Can you ping the server from your XP computers?

Is your gateway NIC able to access the internet?

---

### Post by boyfrienddan on 2006-01-29
I just deleted ubuntu from my celeron machine in hopes to get a fresher start. Sorry.

Right now, the 25 computers have static IPs so that my classroom management software (NetOp) can work better. I have also experienced difficulty with IP address acquisitions so I set them all with their IPs. Usually, the DHCP server would serve mostly my wireless clients.

Anyways, when I did have my ubuntu root running with the machine, I tried pinging my gateway, and it didn't reply. I could easily ping the router, and of course go to the internet with the rest of my machines. That was already when I had it set to dual boot with an XP installation, whereas XP is able to load both ethernet cards without fuss, and have internet too.

my network cards: netgear and dlink.

Thanks for your help. Sorry if I get really confusing with my descriptions. I have zero Linux knowledge for one . . .

---

### Post by bscbrit on 2006-01-30
OK, are you going to install ubuntu again or are you going to try something different?

---

### Post by boyfrienddan on 2006-01-30
I was trying to install ubuntu again, and was checking the DHCP response when its starts accessing the network. It said that it can't automatically setup the DHCP and is telling me that it may be that the network is slow or that there is no DHCP server. That would not be possible because:

- on this same machine WinXP easily gets to the network and Internet with the same network cards I've been trying out

- all my WinXP boxes can easily get to the network

I have noticed however that whenever it scans for my network devices, it comes out only with realtek and another brand, instead of netgear and dlink, which are the cards that I actually have (the realtek is another standby which I used first, but have discarded as I was thinking it was not working).

I've been reading through the forums and have found out that celerons are OK (especially since I have at least 128MB RAM on the machine, which is double the system requirements), even with the desktop setup. I don't know if it is a motherboard or a device conflict with mine.

If this pushes through, I still want to make this machine a server, and I might just replace gnome with xfce, since I also read that gnome hogs a lot of processing time and memory.

So, do you think it actually is a network brand problem?

---

### Post by bscbrit on 2006-01-31
No, not necessarily - but we go back to my question of 3 days ago.  I _do_ think it is a NIC configuration problem but, without the output from ifconfig there is not much that I can do to assist. :p If you show me the output, perhaps we can begin to track where the fault lies.

---

### Post by boyfrienddan on 2006-02-20
I have since tried other machines, and i was doomed to failure. I tried to revive an Intel board, which I had in abundance, but now only a few are working. apparently the board had this thing with the memory modules, and so i had to abandon that. I found myself an old amd k6-2 box instead and tried to soup it up. I used the same NICs however, and I'm in the same problem again. I got this from one of the threads and it is almost the exact same results I'm getting now:

[http://ubuntuforums.org/archive/index.php/t-81385.html](http://ubuntuforums.org/archive/index.php/t-81385.html)

eth0 Link encap: Ethernet HWaddr 00:11:D8:1E:85:08
inet addr: 10.112.0.19 Bcast:10.112.15.255 Mask 255.255.240.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
RX packets:8922 errors:0 dropped:0 overruns:0 frame:0
TX packets: 75 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000

lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric: 1
Rx packets:23 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors: 0 dropped0 overruns: 0 carrier:0
collisions:0 txqueuelen:0
Rx bytes:1319 (1.2KiB) TX bytes:1319 (1.2 KiB)

Just replace eth0 with eth1, and its the exact same thing. I've been trying to check for NIC drivers, but of course, without access to the internet for my amd k6 box, I'm as dead as a dodo.

Thanks again

---

