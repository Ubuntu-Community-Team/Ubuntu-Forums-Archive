---
title: "Internet connection problem"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by csaga on 2007-05-18
I have a cable Internet, and frequently loose connection. When I try to reconnect with [COLOR="Red"]sudo pon dsl-provider[/COLOR] I got az error message: The file dsl-provider file not exist.
Some times the Internet connection is working fine.
Thanks for answer!
Csaba

---

### Post by deadgobby on 2007-05-18
If you use cable internet, it should not be DSL, most likely DHCP. If you have a Router and/or a cable modem that is not issued by your cable company. You need to call them and have them reset the line. Some times you need to unplug the cable modem and wait for a minute and plug it back in. Reboot Ubie and it should reset to the proper. What is your ISP?

---

### Post by csaga on 2007-05-18
Ok but I dont have a modem, I have cable link connection to the Internet.
Thanks for answer!

---

### Post by Wim Sturkenboom on 2007-05-18
If your connected directly, ask your provider for the settings. If you have some kind of box in between, you have a modem and you need to configure it first.

In that case, you have to create a the file dsl-provider. I seem to remember that the utility is called pppoe-config. To check it, run *man -k ppp* in a terminal. Once you've found it, run the command in a terminal (sudo probably required). It will ask some questions and next save the settings. In my case, it was indeed the file *dsl-provider*.
Once configuration is done, you can use *pon dsl-provider* to connect; on my system, sudo is not required for this command.
The command *plog* can be used to check if the connection attempt was successful. Please note that often the result of the connection attempt 'disappears' after a while (depending on some config).
The command *poff* can be used to disconnect.

---

### Post by csaga on 2007-05-18
I'm setting up connection, succesfully with pppoeconf. The ISP provider give me onlly an Account and Password. Some time gone fine the Internet connections, but some times loose coonections. When I restart Ubuntu, everything is OK. How can I resolve the problem, without restarting the system?
Thanks for answer!

---

### Post by Wim Sturkenboom on 2007-05-18
When you loose the connection, try [http://64.233.167.99](http://64.233.167.99) in the addressbar of the browser. If it takes you to google, your name resolving does not work. If you get an error, something else is wrong.

---

