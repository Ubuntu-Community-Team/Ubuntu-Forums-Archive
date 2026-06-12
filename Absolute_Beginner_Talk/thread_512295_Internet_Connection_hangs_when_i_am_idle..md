---
title: "Internet Connection hangs when i am idle."
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by rahimveron on 2007-07-29
Hello guys, i have installed ubuntu 7.04 dual-boot with XP.
My problem is when i connect to the net and surfing the connection is fine. But when i am idle ,say reading a n article for a minute, the connection just hangs and drops and i have to re-connect again. However there is no problem of line dropping or hanging when i am on XP.
This is getting quite frustrating as i have to re-boot to XP all the time.
Remember agin when i am continously surfing its ok ,its only when i am idle the line gets hanged.
Plz help......I dont want to go back to XP.

---

### Post by rahimveron on 2007-08-01
Come on guys help me!!!

---

### Post by Austin_KW on 2007-08-01
Not sure what you mean by connection dropping (wired/wireless), (connection to the internet, connection to your router?);

Check the command "ifconfig -a" before and after the connection drops.

Also check your dns config before and after the connection drops with "cat /etc/resolv.conf"

---

### Post by rahimveron on 2007-08-02
Thank you Austin for the reply
I connect through ethernet. If i am idle for 2-3 minuted the net connection freezes/dropp and i have to power-off my ADSL modem and do pon again.

---

### Post by Austin_KW on 2007-08-02
I dont use pppconfig (i use a dsl router and configure ppp on the router). But check the advanced options for Idle timeout. There should be an option to set this to none.

---

### Post by rahimveron on 2007-08-02
Where are the advance options?

---

