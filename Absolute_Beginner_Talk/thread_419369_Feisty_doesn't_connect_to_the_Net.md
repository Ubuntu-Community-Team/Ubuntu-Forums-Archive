---
title: "Feisty doesn't connect to the Net"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-04-22
Hi,
What does it mean when you can't browse the internet but you can ping URLs in the terminal?

---

### Post by lamalex on 2007-04-22
it means something is borked in firefox. what is firefox saying when you try to view pages? are you trying to view the same pages you are pinging?

---

### Post by SteelCore on 2007-04-22
Yes, same URLs.  When trying to open them in Firefox it just does nothing.  At the bottom it says "Waiting for..." whatever site I requested.

---

### Post by lamalex on 2007-04-23
hmm try a different browser? lynx is a browser for the terinal you could try. apt-get install lynx then lynx <url> and see if you can get to it.

---

### Post by SteelCore on 2007-04-23
apt-get did start the download and installation but it stopped at a point where it says "0% (Waiting for headers)".  No progress beyond that.

---

### Post by lamalex on 2007-04-23
something is wrong with your internet, reboot your machine, reset your router, or reset your modem. have you had problems before or is this recent?

---

### Post by SteelCore on 2007-04-23
> **SteelCore said:**
> apt-get did start the download and installation but it stopped at a point where it says "0% (Waiting for headers)".  No progress beyond that.

And now it failed

---

### Post by SteelCore on 2007-04-23
> **Iamalex said:**
> something is wrong with your internet, reboot your machine, reset your router, or reset your modem. have you had problems before or is this recent?

Just with Feisty and on two of my computers.   6.10 and 6.06 are running OK, even Win xp.

---

### Post by lamalex on 2007-04-23
I have no idea, try filing a bug report (through one of the others obviously).

---

### Post by SteelCore on 2007-04-23
> **Iamalex said:**
> I have no idea, try filing a bug report (through one of the others obviously).

I'll try to do that.  Thank you anyway.

---

### Post by freebird54 on 2007-04-23
Is ipv6 enabled on your machine?  Have you tried to disable it in Firefox's about:config?

---

### Post by medad on 2007-04-23
Someone else had a similar issue.  Take a look at this link.  [http://ubuntuforums.org/showthread.php?t=419396]("http://ubuntuforums.org/showthread.php?t=419396").  I hope that it helps.

---

### Post by SteelCore on 2007-04-23
> **freebird54 said:**
> Is ipv6 enabled on your machine?  Have you tried to disable it in Firefox's about:config?

I don't know how to do that. Is there a link to any instructions?

---

### Post by freebird54 on 2007-04-23
OK here's some :)

First off, enter the following into Firefox's address bar (as if going to a web site)

```
about:config
```

There is a filter feature.  Type  **DNS** into the filter.  **network.dns.disableipv6** should appear - make sure it is set to true.  If it is not, then double-click it to change it.  Then, open a Terminal and

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist ipv6
```

Save the file, exit and reboot your computer. That should speed things up!

Hope it helps.

---

### Post by SteelCore on 2007-04-23
I haven't installed Feisty yet.  I'm testing all that from the liveCd.  If I reboot all the settings will be lost.

---

### Post by freebird54 on 2007-04-23
I think that the about:config thing should be enough to browse at a decent speed, if ipv6 is the problem.  You're right, though, about the settings disappearing off a live CD boot!

Give about:config a try and see if it helps - make sure TRUE, which may or may not be default (bolded when not default)  OK?

---

