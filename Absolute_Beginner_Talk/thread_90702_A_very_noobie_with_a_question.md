---
title: "A very noobie with a question"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by Rumor on 2005-11-15
Hello All:
I've recently installed Ubuntu 5.10 on my home PC with the goal of having a box with no costware on it (excpet for Neverwinter Nights for Linux). I really, really, REALLY want to be free of the yoke of Micro$oft.

However, I need to be able to vpn into my office to access our intranet based database when I am working from home. In windows it was a fiarly simple process to create the new connection, connect and then open my web browser and log in to the correct URL.

I know the same thing can be done using Ubuntu . . . but I need a real beginner's "click here, click there, type this, hold your tongue this way" type of explanation. Once I have this set up, I will be free of windows :smile: 

Thank you for your help!

---

### Post by blueplazma on 2005-11-15
What kind of VPN do you use?  Linux supports a wide variety of VPNs with the correct software - you just need to use the right program.

---

### Post by Rumor on 2005-11-15
Here at the office? We just use the plain vanilla VPN that comes with Windows 2K server. We do not use a Cisco client or anything like that.

---

### Post by Rumor on 2005-11-15
Ok, perhaps a bit more information is needed?

When I open the windows vpn icon in the system tray, the following information is on the details tab.

Device Name: WAN Miniport (PPTP)
Device Type: vpn
Server Type: PPP
Transports: TCP/IP
Authentication: MS CHAP V2
Encryption: MPPE 128
Compression: MPPC
PPP Multilink Framing: Off
Server IP Address: 10.10.10.101
Client IP Address: 10.10.10.109

Perhaps this information will be helpful? I appreciate any help anyone can give me.

---

### Post by kruz on 2005-11-15
im not to fimiliar with this
but maybe u have a remote desktop account?

rdesktop (servername)

or samba has something to do with linux/windows file connectivity

lol sry if this is no help, just throwing out some suggestions

---

### Post by Rumor on 2005-11-16
Ok, thus far I have installed pptp and pptpconfig, reading guides, how to's and suggestions from other users.

But, I am getting an error in pptpconfig. Once I enter the vpn address, domain, user ID and password, etc., I click "Add" to save the tunnel. pptpconfig gives me this error:
[COLOR="Blue"]
Failed to open /etc/pptpconfig/lock
Information entered has not been saved[/COLOR]

Does anyone have any ideas as to what I do next?

:confused:

---

### Post by AsteriskNix on 2005-11-16
Instead of beating your head against the desk. You may want to email your IT staff and let them know know your intentions.

It's not as simple as installing a client and hitting go.

There is more than likely, a VPN profile on your computer, and a cisco/nokia/openswan something on the back end in your organization.

You will need this file. example;

officeremote.pcf

which is a cisco profile that your domain/username and pw are stored both on the client and server side.

You may be surprised, my office just handed me a CD and said "cool, here is the linux vpn setup, knock yourself out".

If you aren't as lucky, you will want to grab openswan, or freeswan from the universe respository. Cisco also has a linux client.

so do a search on your windows partition for anything like *.pcf or ask what your profile is named from someone else who may have had success in your company doing this?
Good Luck!

---

### Post by Rumor on 2005-11-16
[QUOTE=AsteriskNix]Instead of beating your head against the desk. You may want to email your IT staff and let them know know your intentions.

It's not as simple as installing a client and hitting go.

There is more than likely, a VPN profile on your computer, and a cisco/nokia/openswan something on the back end in your organization.
[/QUOTE]

We do not use a Cisco client in our office. I can and have set up a windows vpn connection from my home machine running windows XP. It does not connect to my office computer. It connects to our office server and allows me to open firefox and access the internal web-based database.

pptpconfig asks for the same information that windows does to set up a vpn connection. pptpconfig won't ***save*** that information so that I can try to connect through it. I'm wondering how do I save the connection information once I put it in? I get the error message listed above.

---

### Post by endersshadow on 2005-11-16
You need to run pptpconfig as the root user:

```
sudo pptpconfig
```

I just spent TONS of time figuring this out, and I'll be posting a HOWTO shortly.

---

### Post by Rumor on 2005-11-17
[QUOTE=endersshadow]You need to run pptpconfig as the root user:

```
sudo pptpconfig
```

I just spent TONS of time figuring this out, and I'll be posting a HOWTO shortly.[/QUOTE]

Yep, that did it! Firefox won't connect to the office database/website, but I can get in and ping the server, so I'll have to ask our IT guy what to do next. In windows it is a matter of entering the correct url, perhaps it is different in ubuntu.

Thank you for getting me this far!

---

### Post by Rumor on 2005-11-19
Whee! It was a very simple fix; merely *cough* enabling traffic to flow through the vpn connection by clicking the appropriate button.

Windows no longer exists on my system!

:D

---

### Post by Bone Down on 2006-01-13
[QUOTE=Rumor]Whee! It was a very simple fix; merely *cough* enabling traffic to flow through the vpn connection by clicking the appropriate button.

Windows no longer exists on my system!

:D[/QUOTE]
what button was it????

---

### Post by Rumor on 2006-01-13
[QUOTE=Bone Down]what button was it????[/QUOTE]

The one on the Routing tab that says "All to Tunnel."

---

