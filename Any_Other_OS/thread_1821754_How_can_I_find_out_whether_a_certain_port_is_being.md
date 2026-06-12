---
title: "How can I find out whether a certain port is being blocked?"
date: 2011-08-09
forum: Any Other OS
---

### Post by hanzj on 2011-08-09
Hi,
Using a Windows XP computer, I need to conclusively find out whether a certain port is being blocked in our network. 

How can I do this?

---

### Post by mips on 2011-08-09
What type of network?

You can use one of the many online port scanning sites or use something like 'netstat'.

---

### Post by haqking on 2011-08-09
> **hanzj said:**
> Hi,
Using a Windows XP computer, I need to conclusively find out whether a certain port is being blocked in our network. 

How can I do this?

shileds up [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

or as said above netstat or nmap for scanning your network as long as it does not go against network policy and you have permission to use such tools on the network.

---

### Post by hanzj on 2011-08-09
Port 993 is the port which I need to confirm is blocked or not.

---

### Post by haqking on 2011-08-09
> **hanzj said:**
> Port 993 is the port which I need to confirm is blocked or not.

I am assuming you are having IMAP issues ?

want to give us more information ?

Are you behind a firewall on a corporate or school lan and you cant access your IMAP email ?

---

### Post by hanzj on 2011-08-09
Yes, it's for IMAP. We're on a corporate lan and I can't access email via imap/that port.

Can one of the suggested tools figure out whether this port is being blocked?

---

### Post by haqking on 2011-08-09
> **hanzj said:**
> Yes, it's for IMAP. We're on a corporate lan and I can't access email via imap/that port.

Can one of the suggested tools figure out whether this port is being blocked?

If you are on a corporate LAN then ask the administrator.

using scanning tools without permission will be or should be agasint the network policy and acceptable use policy.

If there is a reason you cant ask or dont want to ask then you shouldnt be doing it ;-)

---

### Post by hanzj on 2011-08-09
so if i can't access the port when I try several email clients, can I safely assume that the port is blocked? 
Why is it bad to use software to figure out whether a port is blocked?

---

### Post by haqking on 2011-08-09
> **hanzj said:**
> so if i can't access the port when I try several email clients, can I safely assume that the port is blocked? 
Why is it bad to use software to figure out whether a port is blocked?

you can reasonably assume it is blocked if not working however ask your administrator for a clearer picture.

it is bad becasue it is likely to be against the Acceptable use policy which you accept upon login or signed in the employee handbook without reading ;-)

again ask the administrator if unsure or uncertain on such activities, you could be seen as attempting to circumvent security and be dismissed depending on policy

---

### Post by hanzj on 2011-08-09
is using the recommend programs going to be taking up much network resources? 
In my ignorance, I imagine the software similar to sticking your hand out of a window to feel if it's raining.

---

### Post by haqking on 2011-08-09
> **hanzj said:**
> is using the recommend programs going to be taking up much network resources? 
In my ignorance, I imagine the software similar to sticking your hand out of a window to feel if it's raining.

I again refer you to your Corporate AUP and administrator or IT department.

Walking around someones house looking for open windows can be seen as suspicious activity

---

