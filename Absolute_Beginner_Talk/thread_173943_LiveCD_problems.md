---
title: "LiveCD problems"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by Mr_Cynical on 2006-05-11
I was thinking of setting up an Ubuntu dual boot, so last night I tried the LiveCD. Everything worked fine except for two features of my (Sony VAIO K415b) laptop:

[LIST]
[*]The (built in) wireless card. Windows says it's a 'Lan-Express AS 802.11g miniPCI Adapter' which *I think* is made by Atheros. Ubuntu didn't detect it at all (it did detect my ethernet card, no problems there)
[*]The battery. I'm aware that 'battery life remaining' counters can be inaccurate in Linux generally, but Ubuntu didn't even detect my battery's existence - I even pulled the power cable out from the back of the laptop, and the laptop stayed on, and the 'battery in use' light came on (I think the light is probably done by the BIOS, but it shows that the battery system itself is working fine). The Ubuntu system tray icon still claimed that my laptop was 'on mains power'.
[/LIST]

**EDIT:** I've discovered that Ubuntu was actually detecting my wireless card, but just didn't know what it was (detecting it as 'lo'). Also, my wireless network uses WPA, will the linux WPA drivers work with my wireless card?

---

### Post by macdo on 2006-05-11
'lo' is the local loopback, normally.

Try typing ```
ifconfig -a
``` into a terminal. That shows you all network interfaces, not just the ones that are running.

---

### Post by nobbynolsn on 2006-05-11
I have just run the livecd on an older Portege - I believe it is probably a wireless b card - built in. My system originally came up with no wireless connection and io but i just had to enable it.

I went to **System: Administration: Networking** - then clicked enable before typing in my home network parameters. It was simple for me so I guess it's not the same problem. The ethernet port was not configured either ( perhaps cause it wasn't plugged in?)

I am still using the LiveCD now - as I type.

I'm obviously not an experienced user so the above solution may be too simple.

---

### Post by Mr_Cynical on 2006-05-11
[QUOTE=macdo]'lo' is the local loopback, normally.

Try typing ```
ifconfig -a
``` into a terminal. That shows you all network interfaces, not just the ones that are running.[/QUOTE]
The problem is that the LiveCD (at least the one I have) doesn't come with Terminal included, and to get it I have to download it from the internet. And to do that I need to get my Wireless working. Grr - I suppose I could try and connect to my router via ethernet.

---

### Post by macdo on 2006-05-11
Are you sure? That's very surprising!
If there is no terminal, you can either install it from the CD or use ctrl-alt-F1, which will give you the command line (ctrl-alt-F7 to return to X).

---

