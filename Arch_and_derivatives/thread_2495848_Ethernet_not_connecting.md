---
title: "Ethernet not connecting"
date: 2024-03-04
forum: Arch and derivatives
---

### Post by mitul11 on 2024-03-04
I'm trying to install arch linux on my machine. My PC is connected with the ethernet but when I'm trying to do ping google.com or whenever I'm trying to access the internet, it just doesn't work. Almost as if the ethernet is just connected to the machine but it is not using any internet. This has been the case with popOS, Ubuntu and other distros too.

---

### Post by howefield on 2024-03-04
Thread moved to the "*Arch and derivatives*" forum.

---

### Post by aljames2 on 2024-03-04
Hi and welcome to the forum

Since this is happening regardless of your OS, it sounds like possibly a physical hardware/wire problem, or potentially your computer is not receiving an IP, it could be other things as well. A few things you could try:

- Do you have another ethernet cable you can try?
- Check if your computer is getting an IP from your router.  **ip a**
- If no IP, check if your router's DHCP  server is turned on.  One of the first things I do after installing an OS  that has a wired connection is assign a static IP address.  Either way,  you should have an IP for your computer right now.
- Can you ping the gateway?
- Is the router allowing outbound traffic?
- Do you have a firewall on this computer that is disallowing outbound traffic? This is more relevant if you have been tweaking firewall settings.
- It could be a bad ethernet port on your computer. Do you have another computer/laptop you could plug in and see if it works from there on your network?
- Was it working before and now it's not, or has it never worked?

---

### Post by oldnub on 2024-03-05
If you've never set up your ethernet connection with Linux before, do this via the konsole:

nmcli con edit type pppoe con-name "any name you want and include these quotes" PRESS ENTER

set pppoe.username yourofficialdialuploginusernamewithoutquotes PRESS ENTER

Save

Confirm yes to save

QUIT

Then your internet connection will try to connect maybe 5 or 6 times (if not manually press connect) and each time a window will ask you for your (dialup) password.

Enter your dialup password for each of these windows until the system connects.

:P

 It always works for me. I usually follow this YouTube video: /watch?v=9efzfmXDEFI

---

