---
title: "Issue with unwanted multiple users"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by desmo on 2008-02-25
Hi,

 When running "top" in the terminal I see "2 users" or "3 users" and running "users" in terminal indicates all 2 or three are my loggin. I got firestarter firewall installed after this all occured, and I can see IPs are beeing blocked frequently.  
Anyone know a solution to this, am I hi jacked or what is going on? 

Regards
Desmo

---

### Post by PeterJS on 2008-02-25
How many terminals do you have open? The desktop session itself counts as 1 user logged in, and each additional terminal get's it's own login. In essence you can't run top in a graphical environment and ever see less than two users. You can run the command w to see who the users logged in are, and where they are logged in from.

---

### Post by spiderbatdad on 2008-02-25
every virtual terminal is a separate user in the same session. You could have each terminal running separate programs...that's one of the great things about linux. So, there's your desktop login, then each terminal you open creates another user in the same login account.

---

### Post by desmo on 2008-02-25
cheers, thanks

w gives me this output

USER     TTY      FROM              LOGIN@   IDLE        JCPU      PCPU                 WHAT
kim      :0             -                     19:57       ?xdm?   3:31m    0.17s                 x-session-manag
kim      pts/2    :0.0                  20:25        0.00s     0.11s      0.00s                w

So the upper is just me running X, and the lower is the active terminal running w, correct?

Any recomendations of firewalls etc that are good to have ? (Right now I got firestarter)


Best regards

---

### Post by PeterJS on 2008-02-25
Firewalls as bit of a misnomer in linux, there is only one firewall, called iptables that's built in to the kernel itself. There are lots of graphical tools to configure and monitor iptables, but it will function all on it's own without user intervention. Also firewalls aren't needed unless you've installed server software above and beyond the base install. One point of pride in Ubuntu security is that it ships with no ports listening by default, ie nothing for a firewall to protect. So unless you've installed server software a firewall isn't going to change much beyond the protection you all ready have, think gaurd dog protecting an empty hen house. Firestarter's probably the best you're going to do for gnome apps, if you're running KDE you might look in to gaurddog.

---

### Post by desmo on 2008-02-25
Excellent
Thank you for the informative answers, that makes me a lot more confident in my previous usage of Ubuntu! It was all just a lack of knowledge from my side.

---

### Post by desmo on 2008-02-25
Another question about this. Will Gaim or Skype or other apps be possible holes in due to deamons listening to ports?

Regards
Kim

---

### Post by PeterJS on 2008-02-25
You're making me think, I don't know about skype, but for Gaim/Pidgin I believe that they only communicate with the protocol servers for the protocols you're using. For file transfers and direct connections I know they have to open ports to listen for the connections, I would assume that they're smart and only accept connections from the expected IP, but I haven't specifically looked. This still leaves them vulnerable to maliciousness from expected connection, and kernel level attacks on the net stack itself, no amount of firewalling is going to save you from attackers you invite in, and for attacking the netstack, you'd need a ***very*** smart firewall that hooked into every running application so it knew only to allow address they were expecting, which is completely infeasible, doubly so given that the apps themselves might not know the information.

Yes they do allow inbound connections, but if you opened the firewall to allow these features it'd be the same as not having a firewall. If you wanted to reduce functionality you could use a firewall for that extra bit of protection, but (for gaim/pidgin at least) the window of opportunity is very small, and probably safe, it'd take real co-ordination and planning to watch a machine for direct connection requests and reply faster than the expected end point.

---

