---
title: "More problems with Wireless - It connects, then disconnects."
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-01-25
I've been having a lot of problems with wireless over the past couple weeks with Ubuntu. Since I dual boot XP I just used that for most of my stuff, but I'm starting to miss amaroK and Beryl and I'd really like to get this working. Besides, Windows is so messed up Explorer crashes from time to time. You'd think something as basic as that would work pretty well. But I digress.

What happens is that when I turn on my computer I can connect fine. I have a full set of little blue bars in the signal strength tray icon, and I can connect to the internet. Then, randomly, it'll stop working. Just minutes ago I was on Ubuntu and I started installing the updates that I'm behind on, and all the programs updated fine, but then about a minute after that it just completely lost the signal. I couldn't check my mail, use Firefox, anything. 

All the settings are correct as far as I know (SSID, WEP, etc.). If it helps, I'm running Edgy on a Dell Inspiron 2200, with a broadcom chipset (which are very hard to get working in Ubuntu and has caused me problems in the past. I'm betting the problem has to do with this). I had to try about 10 things to get wireless working, so I might have changed options as settings all over the place on the computer from following various tutorials. 

I can't think of anything I could've done that would have caused it to act like this, unless Wifi-radar did it. IIRC, that was the last thing Wifi related I installed in Ubuntu, which I have since removed (to see if it was causing the problem). 

:confused:

---

### Post by rmartz on 2007-01-26
I have heard a few others say they updated and lost connection with a Broadcom. I had the same problem, that is why I noticed, I guess. I found a post that said to # (this makes the line a remark line instead of a command line) out all the extra lines in the /etc/network/interfaces file besides the ones that contain lo or eth0.

I did this and it seemed to help.

Open Terminal.
Type sudo gedit /etc/network/interfaces

Add # infront of any line that doesn't already have one and that does not contain lo or eth0.

Save file.
Restart Wireless adapter.

Have something soft to bang if it doesn't work.

---

### Post by Amablue on 2007-01-28
Okay, I commented out all the lines that didn't have eth0 or lo in them, and it still does the same thing. It'll connect and work fine for a few minutes, then just die.

---

### Post by RomeReactor on 2007-01-28
Did you try disabling ACPI? This is from Synaptic on ACPI:

> Modern computers support the Advanced Configuration and Power Interface (ACPI)
to allow intelligent power management on your system and to query battery and
configuration status.

If not, then open Gedit or Nano or your favorite text editor:

```
sudo gedit /boot/grub/menu.lst
```

and write:

```
acpi=off
```

between "### BEGIN AUTOMAGIC KERNELS LIST" and	"## DO NOT UNCOMMENT THEM, Just edit them to your needs". Save and reboot. If it still dies, a quick fix would be to run in a terminal:

```
sudo dhclient wlan0
```

to bring your card back online (hopefuly); just substitute "wlan0" for your card if it's named differently on your system.

And (sorry for the long post) it would probably be a good idea to disable ipv6 globally:

```
sudo gedit /etc/modprobe.d/aliases
```

search for "alias net-pf-10 ipv6" and replace it with "alias net-pf-10 off".

---

### Post by rcarricato on 2007-01-29
wow you have to be the biggest life saver in the world. This guide also sped up my internet, your the greatest:guitar: [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by Amablue on 2007-02-01
Arg... still no luck. I think it's probably a combination of things that's causing this. I've had to mess around with wireless a few times before, so I've muddled with the settings more than I probably should, and I don't know what I've done to it. Without wireless though, my Ubuntu partition is pretty useless. 

Probably the easiest thing at this point for me is to just change the settings back to default and start from scratch. Is there a way to do that without reinstalling the whole OS?

---

### Post by deadgobby on 2007-02-01
Have you look in Ubies Wiki site???
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=broadcom&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=broadcom&titlesearch=Titles)

---

### Post by randytuggle on 2007-04-17
I upgraded to Feisty and this problem was resolved after installing fwcutter.

---

