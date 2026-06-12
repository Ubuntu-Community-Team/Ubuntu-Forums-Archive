---
title: "[SOLVED] Unable to resolve network name"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-04-22
For some reason all my (Windows) computers can't resolve my Ubuntu's box network name and I have to do everything through IP.  Is this normal?  Can I fix this?

---

### Post by kevinlyfellow on 2007-04-22
What exactly are you trying to do with it?  Do you just want to share files over the network or are you looking to use ssh?

Basically out of the box, ubuntu is nice and secure, since most people don't have a need to interact with windows computers.  If you want to do something extra, you need to install special software to do so.

---

### Post by heimo on 2007-04-22
> **AncientPC said:**
> For some reason all my (Windows) computers can't resolve my Ubuntu's box network name and I have to do everything through IP.  Is this normal?  Can I fix this?

Yes. You can setup DNS records(* for your computers or you can make your Ubuntu box talk the same language with Windows (they use different way of name resolving). I'd start here:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

*) Or you could maintain hosts files.

---

### Post by AncientPC on 2007-04-22
> **kevinlyfellow said:**
> What exactly are you trying to do with it?  Do you just want to share files over the network or are you looking to use ssh?

Basically out of the box, ubuntu is nice and secure, since most people don't have a need to interact with windows computers.  If you want to do something extra, you need to install special software to do so.

Not for file transfer, but for ssh, vnc, etc.

> **heimo said:**
> Yes. You can setup DNS records(* for your computers or you can make your Ubuntu box talk the same language with Windows (they use different way of name resolving). I'd start here:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

*) Or you could maintain hosts files.

I'd prefer to stay away from the host file route and I know Windows boxes use NETBios to resolve names, I was just wondering how to get them to recognize the Ubuntu box.

---

### Post by heimo on 2007-04-22
> **AncientPC said:**
> I know Windows boxes use NETBios to resolve names, I was just wondering how to get them to recognize the Ubuntu box.

You have the answer right there. Personally, I'd just add hosts to DNS, but the other approach is to make your Ubuntu box talk netbios.

---

### Post by AncientPC on 2007-05-30
Takes 30 seconds to fix:
[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

---

