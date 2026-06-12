---
title: "how can i change the timout on ssh"
date: 2008-10-14
forum: Apple Hardware Users
---

### Post by ja660k on 2008-10-14
hey guys,
i use macosx and
i need to be able to change the ssh timeout
because im working remotely and need to compile my code constantly,
sometimes when i write.. (over about 5 minutes)

the terminal freezes and ssh timesout

can someone help me change the timeout
on the local machine not the server?

---

### Post by Wicca on 2008-10-14
Hi,

I know nothing about OSX but in Linux you can put in /etc/ssh/ssh_config to set the timeout to 5 minutes:
```
ConnectTimeout 300
```
So maybe have a look at the OSX equivalent of ssh_config?

---

### Post by ja660k on 2008-10-14
does it have to have # infront of the line
cos the others do

---

### Post by Wicca on 2008-10-14
> **ja660k said:**
> does it have to have # infront of the line
cos the others do

No, remove the # to make it active. The symbol # means that what is following on the same line, needs to be treated as comment (text) instead of code.

---

### Post by cyberdork33 on 2008-10-14
Also, you should look into using 'screen'. This way even if the ssh connection is dropped, the processes will continue on the server, and you can reconnect and reactivate the screen you want.

---

