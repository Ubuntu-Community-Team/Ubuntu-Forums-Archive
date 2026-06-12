---
title: "Wi-fi, WAP, WEP, (un)secured networks"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-05-04
Hello folks,

I've been using an unsecured network for the last two months now, I guess it belongs to one of my neighbors. Anyway, I was wondering...

1. Are there any chances that this neighbor can see what I'm doing with my computer when I'm suing his/her network?

2. How can I secure the channels when I'm using an unsecured network that is not mine?

3. Do I need to configure Ubuntu with firewalls, etc for use with wi-fi?

Thank you!

---

### Post by Acglaphotis on 2007-05-04
1- Yeah.

2- You cannot.

3-No, the firewall is built into the kernel (gotta love linux), but you may need to install some drivers for your  wifi card. If you provide more info about the wireless card we can help you figure out the driver and installation.

Hope i helped.

-Acgla

---

### Post by the8thstar on 2007-05-05
> 1- Yeah.

Yikes! What can they actually see? Can they see if they are actively looking, or do they see what I'm doing because it's also happening on their computer screen simultaneously?

> 2- You cannot.

Wow, that's not good news. Unsecured network = insecure user :(  No cloaking device, aka fake IP address for instance? By the way, is it illegal to use someone else's bandwith if the network is unsecured?

> 3-No, the firewall is built into the kernel (gotta love linux), but you may need to install some drivers for your wifi card. If you provide more info about the wireless card we can help you figure out the driver and installation.

Hmm... I'll try and find the info for you ASAP.

---

### Post by Acglaphotis on 2007-05-05
They can see the packages you send and receive if they really wanted to (they can see your emails, the pages you see and even your passwords!), but the chances are really slim, so, about your second question i dont know, i dont live in the us so im not familiar with us law. Ah, and about your wifi card, i think you will probably find it in the device manger (**System > Preferences > Hardware Information**)

-Acgla

---

### Post by chili555 on 2007-05-05
With the most basic software, they can see the web addresses you visit, Google, Yahoo, Ebay, pr0n4u.com, etc. More sophisticated software can log keystrokes. Is that your Visa number I saw go by? However a user that hasn't bothered to secure his network may not be sophisticated enough to go to these measures, unless it's a trap!

I'm not sure the legalities of unsecured networks has been fully determined in court. I would rather argue that it's illegal. I would ask the jury if they felt that leaving the keys in your car gives the8thstar the right to use it for any purpose and if they left the front door to the house unlocked long enough to walk to the mailbox, if the8thstar now is given the right to use the house for any purpose. I think, although there are some differences to wireless, the jury would agree it's not legal to use my stuff, just because it's unlocked.

Be careful.

---

### Post by the8thstar on 2007-05-05
> However a user that hasn't bothered to secure his network may not be sophisticated enough to go to these measures, unless it's a trap!

Well, that's what I am hoping on, but you're right, you never know!

Do you guys have any idea about the type of hardware I should buy to set up my own wi-fi network with my other computer that's connected to the DSL line (wired connection) and running Windows XP? This way, I would have my own secured and legal network to use. ;)

---

### Post by viciouslime on 2007-05-05
You want a wireless ADSL router. There are hundreds of them on the market these days. They're pretty cheap too, you can get a decent one for about £30, no doubt less in the states.

---

### Post by jimrz on 2007-05-05
> **the8thstar said:**
> Well, that's what I am hoping on, but you're right, you never know!

Do you guys have any idea about the type of hardware I should buy to set up my own wi-fi network with my other computer that's connected to the DSL line (wired connection) and running Windows XP? This way, I would have my own secured and legal network to use. ;)

have really good experiences with netgear wireless routers and you can get one pretty cheap. i would then connect your dsl and your other computer directly to the router via it's wlan + ethernet ports and use it's ap to connect your wifi box. the router will provide dhcp, nat, ip assignment by mac address, etc making for a fairly simple setup.

---

### Post by viciouslime on 2007-05-05
> **jimrz said:**
> have really good experiences with netgear wireless routers and you can get one pretty cheap. i would then connect your dsl and your other computer directly to the router via it's wlan + ethernet ports and use it's ap to connect your wifi box. the router will provide dhcp, nat, ip assignment by mac address, etc making for a fairly simple setup.

I can also vouch for netgear as well as linksys.

---

### Post by Frak on 2007-05-05
Just so you know, its illegal to use someone else's WiFi network without their consent, unless the network is listed as "Public" or something of the sorts, such as what Apple Airports list their default, unsecured, network as.

---

### Post by the8thstar on 2007-05-05
Thanks guys for the technical feedback. How do I protect the wi-fi network from intruders under Windows XP and Ubuntu?

About the legal aspect of things, the reason I connected to the network is because Windows XP (originally this is the OS I was using at the time) labeled it as "Public" by default. I guess any unsecured network is considered "Public" in XP. With Ubuntu, I have no idea.

---

### Post by Frak on 2007-05-05
The ESSID's never change no matter what OS your using unless the owner changes the ESSID, so if it is listed as "Public" and its unsecured, it is perfectly legal to use.

EDIT
And you can setup a WEP or WPA Protocol over the network to block intruders.

---

### Post by the8thstar on 2007-05-05
> The ESSID's never change no matter what OS your using unless the owner changes the ESSID, so if it is listed as "Public" and its unsecured, it is perfectly legal to use

Good!!! At least this issue is out of the way now. I still don't feel confident about the possibility of having someone sneek on me so I think I'll go ahead and buy the wi-fi kit.

> And you can setup a WEP or WPA Protocol over the network to block intruders.

Yet another thing to research with Ubuntu ;) Oh well, I'm sure I'll learn something usedful!

---

### Post by octoberdan on 2007-05-05
> **the8thstar said:**
> Hello folks,

I've been using an unsecured network for the last two months now, I guess it belongs to one of my neighbors. Anyway, I was wondering...

1. Are there any chances that this neighbor can see what I'm doing with my computer when I'm suing his/her network?

2. How can I secure the channels when I'm using an unsecured network that is not mine?

3. Do I need to configure Ubuntu with firewalls, etc for use with wi-fi?

Thank you!

1. Definitely.
2. You can tunnel communication through ssh, but understand that it is illegal to use a network without the owner's explicit permission.

---

### Post by octoberdan on 2007-05-05
> **the8thstar said:**
> 
About the legal aspect of things, the reason I connected to the network is because Windows XP (originally this is the OS I was using at the time) labeled it as "Public" by default. I guess any unsecured network is considered "Public" in XP. With Ubuntu, I have no idea.

Check out the commands
```
iwconfig
```
and 
```
sudo iwlist <interface> scan
```

If you are serious about wireless security, I'd suggest buying a book on the subject.

---

