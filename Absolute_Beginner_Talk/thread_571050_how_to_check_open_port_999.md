---
title: "how to check open port 999"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by powerfulx100 on 2007-10-08
how do i check if a port is open or closed in ubuntu? for example port 999? please reply fast , thaaank youuu

---

### Post by shad0w_walker on 2007-10-08
You can see a list of ports that are listening by running this command:

```
netstat -l
```

that will print a of all listening ports on a system.

---

### Post by powerfulx100 on 2007-10-08
ya but how do i know if  a specific port is blocked or open while not listening/active?

---

### Post by Vadi on 2007-10-08
You can also just do 'telnet localhost ###', where ### is the port number. If it's closed, you'll get something like this:

vadi@vadi-laptop:~$ telnet localhost 12345
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

And if you don't, then something is open!

---

### Post by Vadi on 2007-10-08
Just check here ([click]("https://www.grc.com/x/ne.dll?bh0bkyd2")).

All ports are closed on Ubuntu by default, I believe.

---

### Post by chewearn on 2007-10-08
If it is an internet side port, you can probe the port using ShieldsUp! at grc.com

---

### Post by powerfulx100 on 2007-10-08
thank you Vadi, very useful. i found port ex. 999 closed. now how do i open it now?

---

### Post by expatCM on 2007-10-08
to open the port perhaps the easiest approach is to use Firestarter which is in the repositories.

---

### Post by Vadi on 2007-10-08
Of course, you want to be aware of the risks involved with an open port. They're closed for a reason!

---

### Post by powerfulx100 on 2007-10-08
i hate to use fire starter as it might block other stuff out. any command to unblock port 999 :mad:?

---

### Post by powerfulx100 on 2007-10-08
ok downloaded firestarter but all the options in the policy tab of firestarter is grayed out. what to do man?

---

### Post by expatCM on 2007-10-08
Firestarter is about as harmless as it gets.   To open a port click on the Policy tab and then Add Rule.  It should be straight forward.

If you want to look at the "real" approach then all you need do is to edit your iptables.    This is generally not much fun.  Here is a tutorial
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

---

### Post by expatCM on 2007-10-08
If the Add Rule is grayed out then perhaps you are not logged in with the necessary permission.

Try starting firestarter from the cli

gksudo firestarter

and that should do it ....

---

### Post by powerfulx100 on 2007-10-08
ok that link has too much reading, i just need a quick solution :mad:

---

### Post by powerfulx100 on 2007-10-08
expatCM thank you for your attempt to help: i did gksudo firestarter still same **** :)

---

### Post by powerfulx100 on 2007-10-08
help please?

---

### Post by Dr Small on 2007-10-08
> **powerfulx100 said:**
> ok downloaded firestarter but all the options in the policy tab of firestarter is grayed out. what to do man?
You have to click inside one of the white fields below, such as "Allow Connections from host" or "Allow Service" and then click the "Add Rule" button.

Dr Small

---

### Post by JBAlaska on 2007-10-08
You have to **right click** in one of the fields as Dr Small said

---

### Post by Vadi on 2007-10-08
You don't really seem to know what you are doing, if it's not a secret, why do you need that port completely open to the world?

---

