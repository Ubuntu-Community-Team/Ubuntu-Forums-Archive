---
title: "change a setting no internet"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2006-07-22
Hello.
At my house I have yahoo dsl and it works fine but at the office it doesnt work (ubuntu/kubuntu Live cd)

In windows I Do the one or manu following things (not in that order,im just typing as I remember).

1st..turn off the router, then after a min. turn it on.

2nc.. ctrl panel, network connections..properties (rightclick)
and then click Repair 

3rd. The same thing but I disable the connection..then reenable it.

4.- Try with many settings, ctrl panel, network connection, bring iup the properties. On the device there is a configure button, in there I go to the advanced tab , And i go straight to "LINK Speed & Duplex"..and change it until I get the browser to work properly.

Thats easy right? ..Now..How do i do the last step in Ubuntu,(kubuntu)?

so far I found about the ethtool.. and tried this
sudo ethtool -s eth0 speed 10 duplex half
and when i just do ethtool eth0 shows that the speed is still 100mbs full duplex...

Can anyone help??

---

### Post by gigaferz on 2006-07-24
Well thanks for looking..

And I found a way aroun this..

I changed the speed  on the livecd  and It works..

I changed it to 10mbps half duplex...

I used mii-tool...

Has anyone ever noticed that when somebody wants to know how
to mount the windows partition they get like 50 replys right away???...

And if somebody comes with something else they barely look at that??

---

### Post by mips on 2006-07-24
Well you figured it out on your own so give yourself a pat on the back.

Sorry I only replied to you now but as you can see you did it on your own which is great.

---

### Post by gigaferz on 2006-07-24
THank you.

I think Its a good tip for all the guys that can not make the internet work..before getting all technical..

---

