---
title: "nm-applet freezes system"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Joe Moren on 2007-11-29
I am very happy with Ubuntu 7.10 with a few exceptions. The main problem is trying to disable wireless using the nm-applet. During 'Boot' wireless gets connected to a local city wide WiFi network. If I right click the Network Manager Applet Icon (4 signal strength bars) & tick 'Enable wireless' [toggle off],if the icon changes to 2 little monitors, everything is fine & the USB adapter is dis-connected! Most times the signal strength bars stay & although the connection is dropped, I can no longer connect or open any thing such as 'System Monitor', 'Terminal', can't Ctrl-Alt, Backspace or shut down. Have to kill power and re-Boot.
 Had 'System Monitor' & 'Terminal' up today when it froze & fortunately was able to take a screenshot of 'top' (attached). The CPU usage % went very high and the sensor for the CPU displayed a rising temperature!.
 I also have LinuxMint which is based on Gutsy & I'm having  the same nm-applet problem, even though it is a fresh install with very little customizing.
My desktop is an E-Machine T3990, 2.80 GHz, 1 Gig Ram & 80 Gig Hard Drive.
The wireless is a 'My Essentials" (Belkin) ME-1001 USB Adapter which worked out of the box with both Gutsy & Mint.  All help & suggestions are welcome! Joe

---

### Post by bjarneh on 2007-11-29
hello,

i've had more or less the same problem, not a complete hangup, but NetworkManager really gets stuck once in a while and i have to kill it and restart it.

if it get so bad that you can't do anything then there is not much to do :-)
you could probably create a script which runs every 30 sec. or so which just checks out how bad NetworkManager is eating away at your resources


PID=`pgrep NetworkManager` - should give you it's PID(s) and then
SLEEP=`cat /proc/$PID/status | grep SleepAGV | cut -b 11-12` - sleep average

this should be quite low when it uses 99% cpu
then

if [ "$SLEEP" -lt "30" ];then
pkill NetworkManager && NetworkManager # restart it
fi

---

### Post by Bigbird999 on 2007-11-29
replacing network manager with  wicd solved all these problems for me.  I did it my first day with Ubuntu (by the synaptic package manger, I think).  Just search and there is a how-to.  If I remember correctly, it automatically uninstalls nm and down loads everything you need.

BB

---

### Post by Joe Moren on 2007-11-30
Thanks for the responses. Right on Bigbird', I deleted both WifiRadar & NetworkManager, then used dialup to get wicd via synaptic on Mint. Works great & I can turn wireless on & off with no problems. Thanks to 'bjarneh' for your script suggestion, I'll keep that in case I decide I can't live with out the 'nm-applet'. Now both Gutsy & Mint work great! When I can get a Federal Income Tax program for Linux to prepare '07 taxes off-line, I will be Microsoft 'FREE'.  :) Joe

---

