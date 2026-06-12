---
title: "How to secure your system?! Monitor Network Traffic? HELP!!!"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by arthur5005 on 2007-11-05
Ok new to ubuntu, but not a blind idiot here. Once upon a time in 1998 my friend did install slackware on my system, had my way with it, got frustrated and switched back to windows. But now I'm back in Ubuntu and loving it. I've been running it for over a year now (first Fiesty, now Gutsy of course). Know my system pretty well and I LOVE it, never switching back.. oh but things are worrying me.

Well recently, as in a couple days ago, on my screenlets network traffic monitor, I noticed that my network traffic on the upload was a bit wack, infact way to high, although at the time I attributed it to some torrents I had running, but it was still 3 fold higher than all my uploads combined. On my network this is my only machine running in DMZ (linux.. secure.. right?) and today I started my system up, looked right into my widget layer for the weather, and noticed my upload was off the chart, but NOTHING was running.

Ok.. now I'm no networking expert, but I'm not not naive either, something's generating this traffic. So I've poked around on the net, hesitant to even be on the net, watching my upload for the session on my system monitor FLY like spikes everywhere. Closed down everything that I could my weather widget, browser, anything that I could that would do any form of networking and watched my total upload for the session hit 400 mbs in fifteen minutes. So I found some network monitoring tools, and I think i settled on Wireshark. And of course, my computers trying to make connections to IP addresses all over the internet and ip addresses to me. So I took my self off DMZ to see what kind of difference that might make. An immediate slow down in how much I was uploading, still a couple of massive spikes, but now it's leveled off to almost nothing. *phew* Almost the last time I put my self on DMZ.. ok what next well

So I'm taking a look at these scary looking packets here, and they all look a little something like this:
1104 76.155630 124.243.157.62 192.168.2.4 UDP Source port: 26277 Destination port: 6881
1105 76.155684 192.168.2.4 124.243.157.62 ICMP Destination unreachable (Port unreachable)
with a WHOLE bunch of different ip address, now but wait a second.. I 'KNOW' i don't have any bittorrent clients open, why does this look like bit torrent traffic always to port 6881. Hrmm Uber suspicious and in the time it's taken me to read some more info about linux security on some other forum, even though my upload isn't going as crazy as it used to, there's still huge occasional spikes, which has driven up my upload another 100mb in about 20 minutes here.

Now I just used both rkhunter and chkrootkit, only rk hunter gave me a warning about hidden files in these directories:

[19:18:10] Checking for hidden files and directories [ Warning ]
[19:18:10] Warning: Hidden directory found: /etc/.java
[19:18:10] Warning: Hidden directory found: /dev/.static
[19:18:10] Warning: Hidden directory found: /dev/.udev
[19:18:11] Warning: Hidden directory found: /dev/.initramfs

otherwise netstat gave me the following:
arthur@Wintermute:~$ netstat -vat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State
tcp 0 0 *:nfs *:* LISTEN
tcp 0 0 *:netbios-ssn *:* LISTEN
tcp 0 0 *:sunrpc *:* LISTEN
tcp 0 0 localhost:ipp *:* LISTEN
tcp 0 0 localhost:smtp *:* LISTEN
tcp 0 0 *:47739 *:* LISTEN
tcp 0 0 *:52124 *:* LISTEN
tcp 0 0 *:microsoft-ds *:* LISTEN
tcp 0 0 *:54845 *:* LISTEN
tcp 0 0 Wintermute.local:41932 192.168.2.1:www TIME_WAIT
tcp 0 0 Wintermute.local:41931 192.168.2.1:www TIME_WAIT
tcp 0 0 Wintermute.local:41934 192.168.2.1:www TIME_WAIT
tcp 0 0 Wintermute.local:41938 192.168.2.1:www TIME_WAIT
tcp 0 0 Wintermute.local:41933 192.168.2.1:www TIME_WAIT
tcp 0 0 Wintermute.local:41937 192.168.2.1:www TIME_WAIT
tcp 0 0 Wintermute.local:41935 192.168.2.1:www TIME_WAIT
tcp 0 0 Wintermute.local:41936 192.168.2.1:www TIME_WAIT
tcp6 0 0 *:5900 *:* LISTEN

problem is I have no idea whats kosher and what's not.. isn't 5900 vino? I'm almost 100% sure I have remote desktop connections turned off. (checks) yes it's turned off.

can anyone help point me in the right direction for what I need to be doing? Just did a quick test, put my self back on DMZ to see how fast my upload'll fly.. Yup!.. Ug...

on packets it seems I get a couple of these once in a while:
1701 129.428921 192.168.2.1 224.0.0.1 IGMP V2 Membership Query

a couple of series of these
1501 64.470299 192.168.2.4 72.39.213.124 TCP 3602 > 29221 [RST] Seq=0 Len=0
1502 64.480190 72.39.213.124 192.168.2.4 TCP [TCP ACKed lost segment] [TCP Previous segment lost] 29221 > 3602 [ACK] Seq=2920 Ack=1 Win=65135 Len=0
1503 64.480198 192.168.2.4 72.39.213.124 TCP 3602 > 29221 [RST] Seq=1 Len=0
(in that order from some random ip addresses)
some friendly http stuff
but the majority of these packets when I go to DMZ look like this:
1697 127.412680 77.176.225.219 192.168.2.4 UDP Source port: 63039 Destination port: 6881
1698 127.412740 192.168.2.4 77.176.225.219 ICMP Destination unreachable (Port unreachable)

and I just want a reliable to figure out where all my upload traffic is coming from!! what I might be able to do in face of a cracker on my machine
help plz?

Best
Arthur
__________________

---

### Post by knightzor on 2007-11-06
first thing i would do is not put my machine in the DMZ, if you have to i would be using some kind of firewall on there IPTables etc (not sure if you are, you didn't mention). If you need some things accessible from the internet, you should port forward the specific ports on your router/firewall to the pc.

could you post your running processes? 
from terminal:
ps aux

---

