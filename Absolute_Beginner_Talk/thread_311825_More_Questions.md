---
title: "More Questions"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2006-12-03
Ok Ive installed Ubuntu and thankfully XP seems to be working fine.
Firstly at the Boot options why are there so many ptions relating to Ubuntu?
Secondly, I have a D-Link DSL G624T router but Im not wireless. I tried the net but cant get passed the homepage.Do I have more to do to establish a connection?

---

### Post by nixclusive on 2006-12-03
The first option allows you to start Ubuntu normally.

The second option allows you to start Ubuntu in 'recovery mode'. Its like safe mode in windows; just that its command line and you can resume to normal boot without restarting.

The third option allows you to test your RAM for any discrepency and possible solutions to fix it.

Do you have an ADSL connection? Like what do you do in Windows to start your connection?

---

### Post by Mac70 on 2006-12-03
Yes I have ADSL. I read somewhere that a wired connection would connect automatically but if I try a search I get the wee timer but it just keeps going.

---

### Post by nixclusive on 2006-12-03
Are you able to connect in Windows? 

Do you actually enter some kind of user/pass combination to authorize the connection?

---

### Post by TerryHowe on 2006-12-03
If you can't get past the home page, it sounds like you don't have Internet connectivity at all.  Did you configure for DHCP?  I assume your router would support DHCP, that would be easiest.

If not, you'll have to select a private IP 10.0.0.20 for example and configure your router as your "gateway".  I assume you know the IP for your router in this case.  You'll also have to configure your a DNS server in this case which I think you put in the /etc/route file if I recall correctly.

---

### Post by Mac70 on 2006-12-03
I didnt think this thru properly.To get to my router I put in an IP address.Ill investigate further.

---

### Post by Mac70 on 2006-12-03
OK. Went back into Ubuntu and got into the router.I ran the connection wizard using thee same settings for BT and status says connected but still nothing.
Please dont tell me I need different settings from my Windows connection!

---

