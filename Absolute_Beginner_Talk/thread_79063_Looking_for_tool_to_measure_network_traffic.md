---
title: "Looking for tool to measure network traffic"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by Momo88 on 2005-10-19
Hi,

I'm new to Linux and just recently installed Ubuntu 5.04. One thing that I'm really missing is a tool similar to DU Meter in the Windows world that allows me to measure my network traffic (up and download). The tool should be running in the background and log daily and monthly bandwith usage.

I read about ipac-ng which I already installed, but I was not able to configure it correctly. There seems to be a similar tool to DU Meter for KDE called KTrafficAnalyzer. However, I have no idea on how I could install this under Gnome.

Who can recommend me a tool with similar functionality as DU Meter? And pls, don't forget that I'm new to Linux. So detailed instructions on how to install or set up the recommended tool would be highly appreciated.

Thanks a lot!
Momo88

---

### Post by KingBahamut on 2005-10-19
sudo apt-get install etherape 

This is probably the best one to use graphically. To get all the network traffic youll need to dump your eth0 into promiscuous mode via 

sudo ifconfig eth0 promisc 

but once you do that, EtherApe will show up a Star Spread of all the network traffic on your network. 

Dont want graphical, 

try 

sudo apt-get install iptraf

Alternately you can install slurm, that will show you an in and out of traffic built up with a small graphic representation.

---

### Post by Momo88 on 2005-10-19
Hi KingBahamut,

thanks a lot for the quick reply. I tried both of the tools that you suggested. I like slurm since it's rather simple and gives me the information I want. 

Just one more question. Is there a way to configure slurm, so it will keep adding all the traffic it measures for a whole month? I have a monthly limit at my isp which I'd like to monitor.

Thanks
Momo88

---

### Post by Momo88 on 2005-10-22
Hi,

trying to configure slurm in a way that would allow me long-term logging of my internet usage I came across a note by the developer that said that slurm wasn't designed and never will be to summarize and store data over a week or month.

So I'm back again where I started looking for a small application that would allow me to find out how much up and download traffic I used today and the whole month (something like DU Meter in the Windows world).

If anybody could point me into the right direction - perhaps with instructions on how to set up the specific tool.

Thanks a lot in advance!

Momo88

---

### Post by Original Brownster on 2005-11-03
[QUOTE=Momo88]Hi,

So I'm back again where I started looking for a small application that would allow me to find out how much up and download traffic I used today and the whole month (something like DU Meter in the Windows world).

Momo88[/QUOTE]

Hi Momo88,
I was just searching for something myself as I have a cap with my ISP since I moved house.
Then I remembered - gkrellm automatically gathers your usage and you can look at the weekly / monthly stats at any time.

Should be just what you want.

---

### Post by duckboy on 2005-11-03
Thanks for the information on EtherApe, what a cool utility! I am new to Linux and I have just installed Ubuntu 5.10 on my computer and I am loving it!

---

### Post by RSX311 on 2005-11-11
edit: nevermind.

---

### Post by Hwoarang on 2006-11-26
You can add FTB-net-gauge Monitor which you can find in Gdesklets

---

### Post by ron999 on 2006-11-26
I'm missing DU Meter too :(

---

### Post by ihristov on 2007-07-20
> **Momo88 said:**
> Is there a way to configure slurm, so it will keep adding all the traffic it measures for a whole month? I have a monthly limit at my isp which I'd like to monitor.

Correct me if I am wrong, but I believe that iptables has this feature built-in.
All you have to do to set it up a rule for incoming and another for outgoing traffic.
It will meter all the traffic passing trough these chains for the duration your machine is up.

I know this from using IPCop.
In my IPCop machine I can see

```
$ iptables -nvL INPUT
Chain INPUT (policy DROP 14165 packets, 2057K bytes)
 pkts bytes target     prot opt in     out     source               destination
3033K  663M CUSTOMINPUT  all  --  *      *       0.0.0.0/0            0.0.0.0/0

$ iptables -nvL OUTPUT
Chain OUTPUT (policy ACCEPT 2381K packets, 613M bytes)
 pkts bytes target     prot opt in     out     source               destination
2381K  613M CUSTOMOUTPUT  all  --  *      *       0.0.0.0/0            0.0.0.0/0

```

You can then reset the counters of the CUSTOMINPUT chain every 1st of the month.

In IPCop there is a special add-on that will record traffic consumption per day. See a [screenshot]("http://allan.kissack.co.uk/index.php?option=com_content&task=view&id=39&Itemid=26")

---

### Post by darioandrade on 2007-10-15
Check vnstats. 

apt-get install vnstats

after that run:

vnstats -i eth0 -u

and then insert the line below in crontab (crontab -e)
*/5 * * * * /usr/sbin/vnstats -i eth0 -u

(instructions are approximate, you should consult manual for precise information)

it should print number of bytes consumed in each month, week, day or year.

Cheers,
Dario

---

### Post by wormser on 2007-10-15
You should also take a look at ntop.

---

