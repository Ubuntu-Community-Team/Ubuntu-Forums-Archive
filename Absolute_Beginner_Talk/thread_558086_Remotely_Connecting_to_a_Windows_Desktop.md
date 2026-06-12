---
title: "Remotely Connecting to a Windows Desktop"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-09-23
I created a thread previously about the same thing but I wasn't clear enoguh. On windows, there is a program called remote desktop connection. when you open it, all you have to do is type in a url and, voila, you are connected. Is there anything as simple in Ubuntu?

---

### Post by Pumalite on 2007-09-23
Ubuntu>Ubuntu=openssh-server
Ubuntu>Windows=samba

---

### Post by wheredidrealitygo on 2007-09-23
ignore that last post, it's not what you're referring to.

what you want is the terminal server client, which is located at:

applications, internet, terminal server client.

it will allow for you to remote desktop out.

---

### Post by bodhi.zazen on 2007-09-23
> **wheredidrealitygo said:**
> ignore that last post, it's not what you're referring to.

what you want is the terminal server client, which is located at:

applications, internet, terminal server client.

it will allow for you to remote desktop out.

+1 

this is what you want (terminal server client). It is a snap to user an acts as you expect.

ssh connects you a command line . samba is for sharing devices (printers, shared drives, etc).

---

### Post by Pumalite on 2007-09-23
Sorry guys. I learn everyday.

---

### Post by intense.ego on 2007-09-23
I tried using TSC, but no matter what i do, it says that an error occured. could you guide me as to what needs to put in the form? like, under username, is it the username of the computer i am using right now or my username on the other network?

---

### Post by wheredidrealitygo on 2007-09-23
It's the username and password of the computer you're trying to connect to.

Which kind of windows computer are you connecting to?

XP or after?

or 2000 and before?

XP and after use the protocol RDPv5, 2000 and before use RDP.

Also remember, the computer you're connecting to must be a windows XP PRO (home won't work), or Vista Business/Ultimate. The less expensive versions don't offer this functionality.

Make sure to right click "my computer", and go to the "properties" on the computer you're connecting TO, and make sure that the REMOTE tab has everything checked to allow incoming connections.

Repost if you need more help, hopefully we don't have to get into port-forwarding and firewalls..

---

### Post by wirelessmonkey on 2007-09-23
You can also download rdesktop 
then from the CLI just type:  rdesktop <ipaddress.of.computer.you.want.to.connect.to>

---

### Post by ranger1873 on 2007-09-23
> **wirelessmonkey said:**
> You can also download rdesktop 
then from the CLI just type:  rdesktop <ipaddress.of.computer.you.want.to.connect.to>

Correct. That's what he is looking for.

---

