---
title: "Can someone help me write a small script?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by ruialexbarbosa on 2006-12-19
Hi,

at my workplace I connect to the internet wirelessly through a VPN. Everytime I want to connect to the internet I need to go to my wireless connection in network settings, deactivate the connection, then reactivate it. Only then I can connect through the VPN.

I know this is probably really simple, but I don't know how to write scripts. Can anyone write one for me?

Thanks

---

### Post by sonny on 2006-12-19
Before you make your script, why don't you try to install NetWork Manager with VPN, here's a cople of links to do it.

[HTML]http://www.ubuntuforums.org/showthread.php?t=298017[/HTML]
[HTML]http://www.ubuntuforums.org/showthread.php?t=235655[/HTML]

---

### Post by pbaehr on 2006-12-19
If that doesn't work out for you and you still want a script, I think this would do the same thing as going in and deactivating and then reactivating the connection. I'm assuming eth0 for your ethernet card. If it's something else, change it to that. You can get information about your ethernet cards by typing
```

ifconfig

``` at a command prompt.

Open a new text document. Copy and past this:
```

#!/bin/bash
ifup down eth0
ifup up eth0
exit 0

```

Save the file somewhere convenient with a name like "vpnhack.sh"

Go to the command prompt and go to the directory where you saved it. Type:
```

chmod +x vpnhack.sh

```
That makes it executable. If you named it something else, type that instead.

Now try it out by typing
```

./vpnhack.sh

```

If that does it, there's your script.

---

### Post by ruialexbarbosa on 2006-12-19
I tried it but

it says this:

ifup: failed to open statefile /var/run/network/ifstate: Permission denied

---

### Post by MrKlean on 2006-12-19
try putting sudo in front of the script run...it wil then ask for yer password..and should run then ..

---

### Post by pbaehr on 2006-12-19
> **MrKlean said:**
> try putting sudo in front of the script run...it wil then ask for yer password..and should run then ..

Oh, yeah. Sorry. Forgot about that. Should be
```

sudo ./vpnhack.sh

```

Thanks MrKlean.

---

### Post by christhemonkey on 2006-12-19
You might want to put a sleep command in there, else the third line will fail due to the ifdown not completing.

---

### Post by MrKlean on 2006-12-19
pbaerh... sometimes newbies can help to LOL!!!  I'm proud of me : ))

---

### Post by pbaehr on 2006-12-19
> **christhemonkey said:**
> You might want to put a sleep command in there, else the third line will fail due to the ifdown not completing.

I hadn't tested the script because I'm connected to my computer via SSH and the script would disconnect me.

Unless I'm mistaken, though, the "ifup up" command should wait for the previous command to finish before it executes. I'll check when I get home, though.

---

### Post by ruialexbarbosa on 2006-12-20
I'm scared to try it now... :-k :D

---

### Post by pbaehr on 2006-12-20
> **ruialexbarbosa said:**
> I'm scared to try it now... :-k :D

Don't worry. Worst case scenario it will disconnect your wireless card without restarting it and you'll have to restart it the way you usually do. There's nothing in the script that can make any real problems, and you already know how to fix the only problem that can occur.

The only other problem I can think of is that eth0 is not your wireless card, in which case you'll have to figure out what it is.

---

