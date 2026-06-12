---
title: "How to start openvpn in background"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by mellibra on 2006-05-31
I start openvpn in terminal, when I close the terminal, it's also terminated. I try to run with & in background,but it does not work.

---

### Post by Perfect Storm on 2006-05-31
Tried making a launcher with it, instead of starting it up in the terminal?

---

### Post by linuchsan on 2006-05-31
--daemon

---

### Post by mellibra on 2006-05-31
I met a problem: my vpn configuration file and .crt file are in ~/VPN/ and I login as non-root user. Every time I start vpn I need to cd to /VPN and input "sudo openvpn xxx.ovpn", it works. But in other directory, I input "sudo openvpn ~/VPN/xxx.ovpn" it fails and log says cannot load .crt file. How to fix this problem?

---

### Post by Perfect Storm on 2006-05-31
Make script for would properly do the trick.

Make a new file that end on .sh
and write something like this:

```
#!/bin/bash

cd /where/the/VPN/is
sudo openvpn xxx.ovpn

```

chmod +x it. Now create a launcher that point to the script instead.

---

### Post by mellibra on 2006-06-01
Great! It works, Thanks

---

