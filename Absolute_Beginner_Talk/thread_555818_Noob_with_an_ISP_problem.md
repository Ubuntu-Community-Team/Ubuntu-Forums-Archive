---
title: "Noob with an ISP problem"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Deedlit on 2007-09-20
Here's the problem.  I have been file sharing back and forth with my boyfriend over the internet. Yesterday I had someone remotely view my computer that wasn't him.  I have changed the settings to allow for it to ask me permission and need a password.  I am told for added security I should change my ip address.  I tried numerous times, and it has stayed static. Per Road Runner, they can't help me, it must be an Ubuntu problem, because they do not support static ip address. I have researched trying to fix this, and I'm not finding anything that has helped me change my ip address.  Could someone help me please?  Thank you in advance.

---

### Post by w4ett on 2007-09-20
I'd try turning your cable modem off for 15-20 minutes, then restarting your system....while roadrunner doesn't support static ip addresses, your dynamic ip address change is not immediate...you retain the same ip while the modem is connected to your cable node.

---

### Post by Deedlit on 2007-09-20
I unplugged the cable modem, and waited, and still I have the same ip address I had when I started. Do you have any other suggestions?

---

### Post by stalker145 on 2007-09-20
1. You can not change your WAN IP address. Only your ISP can do that.

2. I would strongly suggest, if you haven't already, that you change your passwords. If someone was on your machine, they can come back at will until you close that door.

3. It wouldn't hurt to strengthen your firewall - either at the router or on your computer.

I've had many problems with RoadRunner and their IP addressing. 

The business-class customers are given a static IP - no problem.

Consumer-class (home people) are given dynamic IP's. No one I've talked to have been able to tell me how often the IP address changes. I've had my IP change twice in one week and I've also had the same one for three straight months. I even left my MODEM off one time when I went on a week-long vacation and came back to the same IP that I had when I left.

Good luck dealing with RoadRunner - They make buffoons look good.

P.S. It's not an Ubuntu problem :P

---

### Post by Ant_Merlin on 2007-09-20
> Consumer-class (home people) are given dynamic IP's. No one I've talked to have been able to tell me how often the IP address changes. I've had my IP change twice in one week and I've also had the same one for three straight months. I even left my MODEM off one time when I went on a week-long vacation and came back to the same IP that I had when I left.

IP addresses are changed by ISP`s on an adhoc basis, this is due to the lack of available public IP addresses, basically there are more people using the internet around the world than there are IP addresses. This is why IPv6 has supposed to be coming out (will be a long time yet). Basically if everyone with internet access around the world connected right now, there would not be enough IP addresses to cope!!!. however you could always setup a proxy IP address. this basically give you a different IP and masks your real one.
there are lots of free sites that provide this service:
Try this one for more info[http://www.proxyblind.org]("http://www.proxyblind.org")

---

