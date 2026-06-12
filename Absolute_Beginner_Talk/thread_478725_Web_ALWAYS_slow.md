---
title: "Web ALWAYS slow"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-19
well, by 'slow' i mean slower than windows.
in windows the pages load alsmot instant.

i have to wait 10 seconds on linux.
i see no differenct between Firefox and Swiftfox.
i tried Swiftweasel and Opera....

all still slow!
does anyone know whhy?

---

### Post by Rocket2DMn on 2007-06-19
Perhaps it's a DNS issue, like it's taking forever to query the DNS server.  Some people say disabling ipv6 fixes some problems.

---

### Post by skymera on 2007-06-19
i disabled IPV6...i think.
i can post some stuff like iwconfig and modules if it helps

---

### Post by skymera on 2007-06-19
no one else can help? :(

---

### Post by Myglaren on 2007-06-19
Not really help but..
I installed a new router - D-Link DSL-G624T and my Edgy and Dapper machines both were practically useless.  Firefox only worked on two sites, very very slowly, same with Epiphany and Galeon.  Konqueror was better but still very slow compared to the XP and Vista machines.

Then a power cut scrambled the Edgy machine almost completely.

A couple of days later the Fiesty discs arrived, did a clean install and now this (Fiesty) machine is far and away faster than all the others put together.

It is my probably completely mistake view that Ubuntu needed to discover the router from a clean install - I had no need to intervene at any stage and it runs perfectly.

I know that this is a typical Windows solution to any given problem but maybe a clean install wouldn't be such a bad thing, after all it takes no time at all compared to the opposition.

---

### Post by aks44 on 2007-06-19
I had the very same problem the very moment I enabled iptables.

UDP DNS queries wouldn't be allowed back in, so I had to wait for the timeout before a TCP query would be done.

To check that, use in the terminal :

sudo iptables -L | grep DROP


If you get results from the above command, it's more than likely that your problem is the same as mine.
If this is the case, I can post my iptables scripts here, but don't expect too much support from me (especially on the "init.rd" thing), I'm too much of a noob on those matters... I'm still wondering how I managed to make this work :(

EDIT: gonna sleep now, so don't expect a reply from me before about 18-20 hours from now on... but I'll check the thread when I come back from work ;)

---

### Post by skymera on 2007-06-19
i entered the above command
```
 scott@scott-desktop:~$ sudo iptables -L | grep DROP
scott@scott-desktop:~$ 

```

thats all that happened

has that disabled ip tables?

---

### Post by aks44 on 2007-06-19
that means that your iptables (firewall) has the original configuration, ie. ACCEPT all, so your problem isn't the same as mine.

sorry I can't be of no more help on this matter I fear, I don't know enough about linux to be of any help on problems I didn't already faced...

---

### Post by ramjet_1953 on 2007-06-20
Check this link out:

[http://www.opendns.com/](http://www.opendns.com/)

It speeded things up for me.

If you are using an ADSL router, you just need to put the Open DNS ip addresses into it.

There is no need to do any configuration to your Linux install.

Also, make sure that you have disabled ipv6.

Here's how:

  **How-To: Disable IPV6 to speed up Internet. **

There's an easy way: instead of changing aliases file, create fie named [COLOR="Blue"]bad_list[/COLOR] in [COLOR="Red"]/etc/modprobe.d[/COLOR] containing this line:
Code:
[COLOR="Red"]alias net-pf-10 off[/COLOR]
Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.
 
Regards,
Roger :cool:

---

### Post by skymera on 2007-06-20
i want to use opendns but whenever i put their server ip's into network settings and restart,
they are gone :(

---

### Post by skymera on 2007-06-20
any on know why?

---

