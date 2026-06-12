---
title: "TightVNC/Hamachi/Remote Desktop question"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by rbc on 2008-02-26
I'll apologize ahead of time for posting this, but I've read and read and read, and read, and my head is spinning at this point. My Ubuntu laptop is at home. My Windows XP computer is at work. I want to access the Ubuntu computer from work. I installed TightVNC on the XP computer, and was able to download and install Hamachi on the Ubuntu computer. By the way, there is no I would have been able to do that if I didn't spend my entire work day reading these forums instead of actually doing work. I ran ifconfig and got the IP address. here are the questions:
Have I done all the prep work?
How do I connect now?
Do I have to change Remote Desktop? If so, to what?
As always, thanks in advance.

---

### Post by chris.a.barker on 2008-02-26
Without know how you have setup your network I can only help you to configure the machines correctly. With that stated do this:

On the Ubuntu machine go to System->Preferences->Remote Desktop, check the box that says "Allow Other Users To View Your Desktop" and make sure that "Allow Other User To Control Your Desktop" is also checked.

That is all the preparation you need to do on the Ubuntu machine. Now you should be able to fire up TightVNC and connect to your home computer. I must caution you that this is a huge security risk. One possible way to mitigate the risk a bit is by setting a password on the screen you check the above boxes on. Additionally, you will need to have some consideration for routers or firewalls within your network. You would theoretically have to perform some sort of port forwarding or open the ports on a firewall to make this all happen. Another point to consider is that your employer may block non standard ports. For example ports that are not used in day to day communication such as port 80, 443, 21 and so on. These are just a few considerations so you know what you are getting yourself into.

Cheers!

---

