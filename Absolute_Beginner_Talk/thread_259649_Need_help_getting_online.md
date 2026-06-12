---
title: "Need help getting online"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Gord0n on 2006-09-17
My specs
AMD Athlon64 3000+
1.5gig pc3200 ram
Nvidia 7600gt
ASROCK Dual939-sata2 mobo
Onboard Ethernet
Onboard Sound

Ubuntu installed downloaded Sept15th 2006

Now as the rest posting here, Im completely new to this. But am willing to learn. But I need to get over my first hurdle.

I cannot get online with my Ubuntu installation. I have the 64bit version of Ubuntu, and have it installed. I have a million questions that I will work my way thru, but to start I need to get the net working.

I am in Canada,and use Rogers High Speed internet. Cablemodem. I connect directly to the cablemodem on this PC thru my network card. There is no network.

Firefox in Ubuntu will not connect.

PLEASE HELP MEEEEEEE.
I have searched and searched, and did find some info with some problems with the onboard ethernet in earlier versions of ubuntu, but apparently its been fixed, as I have also found info on people who use it fine.

Please help me get online with my ubuntu and my asrock dual939 sata2 onboard eth.

---

### Post by Gord0n on 2006-09-17
> **deadgobby said:**
> Have you called up your providor and talk teck with them? Any ways try rebooting the system with the cable modem on, Ubie should detect it right away. If not have you check your setting in System>Admin>Network setting or tools?
Gobby

(Ive moved thread)

Yeah, rogers does not support anthing but winxp. So no help there. I have looked in my settings, and played with them. But to no avail, and I am not really sure what they should be set at.

---

### Post by æþeling on 2006-09-17
In the terminal (menu->accesories->terminal), type:

sudo pppoeconf
(you will be prompted for your password, which you should enter)
Now, keep selecting yes, and when prompted, enter your (internet connection's) username and password. In the last window, you will also be given the commands for activating and disconnecting the connection.

---

### Post by deadgobby on 2006-09-17
Your cable modem should work. I have a cable modem and work with out any drivers. Did Ubuntu do the updates OK. Are you daul booting or using a router for 2 different PC's?

---

### Post by Gord0n on 2006-09-17
what is there is no username or password required. Its always online. No connection/disconection required.

---

### Post by Gord0n on 2006-09-17
> **deadgobby said:**
> Your cable modem should work. I have a cable modem and work with out any drivers. Did Ubuntu do the updates OK. Are you daul booting or using a router for 2 different PC's?

I am dual booting with winxp. Only one PC is involved. I dont think it updated. How can I test the connection?? All I know is when I try to go anywhere in my firefox in ubuntu, it gives me the page cannot be displayed thing.

---

### Post by gn2 on 2006-09-17
Did you have PC connected to the cable modem (with modem power on?) when you installed Ubuntu?

If not give that a try.

Also, perhaps try 32bit version, 64's a bit tricky...

---

### Post by deadgobby on 2006-09-17
What he ment is to open your terminal window. At Applications>Terminal> and type in or copy/paste

sudo pppoeconf

Then it is goign to prompt you for a password

---

### Post by Gord0n on 2006-09-17
everything was connected when I did the install. It detected the ethernet hardware fine, when installing. But it did have problems with autoconfiguring the network. started asking for my IP address and soforth.

---

### Post by Gord0n on 2006-09-17
> **deadgobby said:**
> What he ment is to open your terminal window. At Applications>Terminal> and type in or copy/paste

sudo pppoeconf

Then it is goign to prompt you for a password
Im going to try now. Will report back with results.

---

### Post by gn2 on 2006-09-17
I have had similar problems in the past and only cured it by persevering at the network configuration stage of the install process.

I had to keep re-trying until the network was properly configured before finishing the install, otherwise I could not get the thing to work at all after the install was completed.

---

### Post by Gord0n on 2006-09-17
> **deadgobby said:**
> What he ment is to open your terminal window. At Applications>Terminal> and type in or copy/paste

sudo pppoeconf

Then it is goign to prompt you for a password

It gave a "Not Connected" message
"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another runner pppoe process with controls the modem."

This confuses me as I do not use a dialup modem. Nor do I need to logon online. 

I plug my network card into my cablemodem for Shaw Highspeed.

what else can I check.

---

### Post by gn2 on 2006-09-17
You could try 32bit version?

---

### Post by Gord0n on 2006-09-17
> **gn2 said:**
> You could try 32bit version?

Yeah, Im downloading now. Will take a couple of hours tho.

---

### Post by kdub432 on 2006-09-19
there IS a problem with the ASrock dual939-sata2 mobo. However, ULi released a driver for it, which I found. Its a .c file, which I assume needs to be compiled into the kernel, but I havent the slightest idea on how to do so

---

