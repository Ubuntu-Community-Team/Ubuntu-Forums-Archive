---
title: "How to move Conky?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ubu_n00b69 on 2007-03-10
have successfully Installed Conky on a AMD 3200+ w/an Asus AV31 Mobo, 768MB of DDR400 Ram with a Radeon RV200 Graphics Card on 6.06LTS

Following the How To, Conky is installed on the Bottom Left of my Desktop.
How would I edit .conkyrc to move it to the Upper Right corner of the Desktop?

Thank you for all of your time.

---

### Post by taurus on 2007-03-10
Applications -> Accessories -> Terminal
```
gedit  ~/conkyrc
```
Scroll down until you get to the section where you want it to start.

---

### Post by ubu_n00b69 on 2007-03-10
Thank you for your quick response.

I have been looking at the Code in .conkyrc, and, unfortunately for me, do not know which variables to change to move it.

Here is the code I am using, pasted from the Conky screenshots here in the forums.

This code has a broken ethernet module, it is always at zero.

Again, Thank you for your time.


background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color black
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}
ppp0 $alignr ${addr ppp0}

Inbound $alignr ${downspeed ppp0} kb/s
${downspeedgraph ppp0}
Outbound $alignr ${upspeed ppp0} kb/s
${upspeedgraph ppp0}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

---

### Post by ubu_n00b69 on 2007-03-10
A quick ammendment...

This Conky is on the Upper Right Corner.
It just has a broken ethernet.

Is the line:
alignment top_right
how it sets it's position?


Thanks again...

---

### Post by taurus on 2007-03-10
Yes, it is top right.

```
**alignment top_right**
```

---

### Post by ubu_n00b69 on 2007-03-10
Taurus,

I would like to thank you for not only the help on this thread, but on numerous other posts I have been reading to learn the nuts and bolts of this Linux Distro.

You spend much time helping others, and I wanted to let you know that us n00bs really appreciate it, even if not everyone says "Thank You".

I will play with the file and when I get what I want, I will post it so that others may use it and tweak it.

It's in the RH Corner, with Black text now, but still a broken ethernet.

Thanks again...
Mike

---

### Post by taurus on 2007-03-10
You're welcome and if you want to fix the eth0/ppp0 thing, will see what we can do, if that's what you want.

```
/sbin/ifconfig
```

---

### Post by ubu_n00b69 on 2007-03-10
Output:

racerx@Racer-X-AMD-Box:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:6E:03:F2
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe6e:3f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4443394 (4.2 MiB)  TX bytes:270844 (264.4 KiB)
          Interrupt:193 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:256 (256.0 b)  TX bytes:256 (256.0 b)

---

### Post by taurus on 2007-03-10
Do you want conky to display the IP address of your machine and download and upload speeds, something like this?

[http://conky.sourceforge.net/conky.png](http://conky.sourceforge.net/conky.png)

Here's the code for it.

```

${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 70}Up:${color #22ccff} ${upspeed eth0} k/s
${color black}${downspeedgraph eth0 32,150 ff0000 0000ff} $alignr${color black}${upspeedgraph eth0 32,150 0000ff ff0000}

```
Just insert those lines into your ~/.conkyrc, right after "**Hostname $alignr $nodename**".

---

### Post by ubu_n00b69 on 2007-03-10
Thanks again...
The Code worked just fine. eth0 works now.

---

### Post by taurus on 2007-03-10
Glad to hear conky is working fine for you now.

---

