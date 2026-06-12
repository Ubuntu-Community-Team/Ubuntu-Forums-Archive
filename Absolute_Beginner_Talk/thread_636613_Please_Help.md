---
title: "Please Help"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Robbey on 2007-12-10
I am an ABSOLUTE  Noobie when It comes to Ubuntu. Today I just dual booted xp and Ubuntu, I really want to connect to the net via Ubuntu and have no idea how. I am not automatically running with a Ethernet cable. I have a wireless network card (name given below) that picks up our router. When I provide all the information needed to correspond with the router it obviously doesn't work since I haven't installed the drivers yet, lol. So yea were do I go from there, I have the CD for the driver but it only runs on Xp...and please don't answer with 'run the terminal' etc etc because I would have no idea D:

Card Name- RaLink Wireless LAN Card

---

### Post by Aseld on 2007-12-10
Have you checked that it doesn't just work?

---

### Post by Robbey on 2007-12-10
> **Aseld said:**
> Have you checked that it doesn't just work?

Yep, wont open.

---

### Post by exactopposite on 2007-12-10
have you attempted to connect to the internet with it or are u just assuming it doesn't work since u haven't installed any drivers?

---

### Post by Robbey on 2007-12-10
> **exactopposite said:**
> have you attempted to connect to the internet with it or are u just assuming it doesn't work since u haven't installed any drivers?

I have attempted, all it did was search. Everything was properly in order.

---

### Post by Robbey on 2007-12-10
Bump

---

### Post by hyper_ch on 2007-12-10
Post the output of the following commands:

```

lspci | grep Ra

```

```

ifconfig

```

```

iwconfig

```

```

sudo iwlist scan

```

```

cat /etc/network/interfaces

```

```

cat /etc/resolv.conf

```

```

sudo route

```

And next time use not a generich "Need help" thread title.

---

### Post by Robbey on 2007-12-10
> **hyper_ch said:**
> Post the output of the following commands:

```

lspci | grep Ra

```

```

ifconfig

```

```

iwconfig

```

```

sudo iwlist scan

```

```

cat /etc/network/interfaces

```

```

cat /etc/resolv.conf

```

```

sudo route

```

And next time use not a generich "Need help" thread title.

Do I do this on Xp?

---

### Post by vikramsharma on 2007-12-10
> **Robbey said:**
> Do I do this on Xp?

You have to do this on Linux not on Xp.  You would have to do this in the program called Terminal.  Go to Applications Menu, there look for Accessories look for application (program) called Terminal.  You have to use the Terminal to run the command listed and please paste the outcome in this thread.  Hope what I wrote was helpful in some way.

---

