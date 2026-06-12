---
title: "Playing with ifconfig"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-08-19
Hello, 
I have been recently playing/reading manuals for command "ifconfig".
It has come to my attention that I can bring eth0 down, but after that I can't bring it up again.
Here's what I do.
1. ```
sudo ifconfig eth0 down
```
The interface goes down
2. I try to bring him up with a command ```
sudo ifconfig eth0 up
```
Nothing happens. I wait. Nothing happens still.
3.  I go to System -. Administration -> Networking and I see that eth0 is enabled. But I just brought him down with #1 and internet doesn't work!
4. I disable it, enable it again and it works.

So, my question is, it it that I am doing something wrong, or is it that the GUI (System > Administration > Networking) doesn't see that eth0 is down? Is this a bug or a [PEBKAC]("http://en.wikipedia.org/wiki/Pebkac")?

Thanks, 
Klaidas

---

### Post by tkiesel on 2006-08-19
Try using ifup and ifdown and see what results you get.

ifup - brings an interface up
ifdown - brings an interface down

sudo ifdown eth0
sudo ifup eth0

etc.

---

### Post by steve.horsley on 2006-08-19
Right. I think ifup is a higher level command than ifconfig, and that ifup will not only ifconfig up, but will also use ifconfig to give it an ip address or use dhclient to use dhcp to get an ip address if needed, as controlled by /etc/network/interfaces.

---

