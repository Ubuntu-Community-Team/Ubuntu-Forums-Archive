---
title: "wireless laptop setup"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-04-02
Hi I have purchased a wireless pcmcia card which should arrive soon and was reading up on how to use it. i am going to use it when i am out and about with my laptop and get into public accessable internet connections or whatever the term is. One of those howto pages said to get a program called 'wireless assistant' by using the 'add/remove' feature in edgy but......this is the error i got:

Cannot install 'wlassistant'

This application conflicts with other installed software. To install 'wlassistant' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

.....how do i do this?

---

### Post by rearden on 2007-04-02
I've never heard of this "wlassistant," but I use my laptop out and about and I've found the Gnome-Network-Manager to work perfectly well, which is installed by default with a regular Ubuntu installation.

---

### Post by Lardadart on 2007-04-02
> **rearden said:**
> I've never heard of this "wlassistant," but I use my laptop out and about and I've found the Gnome-Network-Manager to work perfectly well, which is installed by default with a regular Ubuntu installation.

That might be because you are using feisty fawn. My brother had the same problem, couldn't get his wireless to work in edgy so after asking what to do in this fantastic forum, I installed feisty fawn for him. I don't know much about this kind of stuff but that certainly helped him.

---

### Post by rapattack1 on 2007-04-02
MMMmmmmm thanks but i think i will wait and see what others say that may have used 'wirelesss assistant' because i need something in edgy. i can't go to feisty incase something stuffs up and i don't have a machine that  i can access. i did some fiesty upgrades on another machine that originally had edgy and i can't boot now. then there is the machine that i had edgy on that the mouse is frozen. unfortunately i have been using another machine with crappy old windoze as this laptop is just too old and using dialup is a pain. plus i am just not good with the kb on laptops.

---

### Post by rapattack1 on 2007-04-05
Well it seems I have wireless assistant set up even though it's program icon is not showing correctly it does search for suitable connections but there are questions that it asks for me to be able to connect to which one I choose. There were 3 to select from and in the questions it wants an ESSID and WEP(I think that is what it is?). What are those things?

---

### Post by Gina on 2007-04-05
ESSID is the same as SSID as set in your router wireless LAN settings (the network name) - WEP is encryption for wireless to prevent unauthorised access.  This allows only you and those with the same key to access your LAN.

---

### Post by rapattack1 on 2007-04-05
Can you tell me how to solve these things then? Sorry I am brand new to this stuff. I am trying to access the net via these connections. I am not accessing my desktop or a network known to me. I don't know how to term it. There are more details in the posts above.

---

### Post by rapattack1 on 2007-04-05
I forgot to mention that the card arrived today and I have spent hours trying to get this happening. I have downloaded so many things via synaptic.

---

### Post by rapattack1 on 2007-04-05
The screen shots show what is happening below!

---

### Post by rapattack1 on 2007-04-07
OK so I was out and about today as things seem to be working but form the error I got i need to be logged in as root. Anyone know how to do that and use the program "Wireless assistant"? It seemed like I saw several open connections but the connection would fail.

---

### Post by rapattack1 on 2007-04-07
Well I did this after some more research on this forum:

carolyni@carolyni-laptop:~$ sudo wlassistant
Password:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Creating link /root/.kde/socket-carolyni-laptop.
Created link from "/root/.kde/socket-carolyni-laptop" to "/tmp/ksocket-root"
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
Creating link /root/.kde/tmp-carolyni-laptop.
Created link from "/root/.kde/tmp-carolyni-laptop" to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Creating link /root/.kde/cache-carolyni-laptop.
Created link from "/root/.kde/cache-carolyni-laptop" to "/var/tmp/kdecache-root"
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

wifi0     no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): ath0
Permissions checked.
ifconfig_status: /sbin/ifconfig ath0
scan: /sbin/iwlist ath0 scan
No networks found!


I also set wlassistant on startup but wasn't getting anywhere with that. I know there are not networks to connect to while I am inside my apartment so will have to wait till tomorrow to get outside to see what happens.

---

### Post by rapattack1 on 2007-04-16
I know that I am still talking to myself but the latest is that I have transferred my hd to another laptop because I thought at least gnome-ppp was working but unfortunately when I go to connect the system freezes. Anyway getting back to the wifi card. I sorted out that I need to logged on as root to used wlassistant. Orr change the permissions. Anyway I will try and find out by myself and hope I get somewhere. Thought I would describe the latest hoping that someone knows what to do.

---

### Post by rapattack1 on 2007-04-19
Good news the wifi thing is working now. I did the same command "sudo wlassistant" and the GUI came up so I just had to chose which connection. I was at a pub/bar and there was free wifi access. Synaptic also updated wlassistant and things work better than ever. I also reinstalled gnome-ppp but after coming home and connecting to dialup it still freezes the system when I connect.

---

