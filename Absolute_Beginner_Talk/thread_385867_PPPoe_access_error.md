---
title: "PPPoe access error"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Shaunak on 2007-03-16
Whenever i try using the "sudo pppoeconf" command i get the following:

[FONT="Fixedsys"]Error Message: Sorry, I scanned 1 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem[/FONT]

Imm using Ubuntu 6.1
I was able to connect fine earlier but now i get the above error. [i think my isp changed my router]

I believe it has something to do with the wireless router compatibility but its configuration/choice/firmware is not in my hand as it is provided by my ISP.

My connection works fine in windows.



[FONT="Century Gothic"]PS: I am very new to linux and will need a detailed walkthrough :)[/FONT]

---

### Post by Kobalt on 2007-03-16
If it's a router you have now you don't need to use the pppoeconf command. What do you get when you type 198.162.0.0 in firefox ? Can you please post us the output of the following command line : ```
ifconfig
```

---

### Post by Shaunak on 2007-03-16
My ISP uses the router to provide the connection, I still have to provide the username and password. Much like a office lan network. 

198.162.0.0 in firefox dosnt help.

Ill type in ifconfig and post back soon.

---

### Post by Kobalt on 2007-03-16
My mistake, sorry, I meant 192.168.0.0
I always mess those up..

---

### Post by Shaunak on 2007-03-17
Some screenshots:
[[IMG]http://img490.imageshack.us/img490/5706/screenshotax0.th.png[/IMG]](http://img490.imageshack.us/my.php?image=screenshotax0.png)
firefox 192.168.0.0

[[IMG]http://img490.imageshack.us/img490/2042/screenshot1sd9.th.png[/IMG]](http://img490.imageshack.us/my.php?image=screenshot1sd9.png)
access error

my ifconfig log: [http://rapidshare.com/files/21426945/if_config_log.html](http://rapidshare.com/files/21426945/if_config_log.html)

---

### Post by kvonb on 2007-03-17
The first thing I would do is hassle your ISP.  If they changed something, they need to fix it.

I'm quite sure there is no "Microsoft Windows required" clause in your internet contract!

See if you can get some technical info from them, it might help in diagnosing the problem.

Actually, see if there IS already a ppp process running on your system by typing this in a terminal:

```
ps uax | grep ppp
```

This is what I get:

```
root      3295  0.0  0.1   2764   884 ?        Ss   Mar13   0:02 /usr/sbin/pppd call dsl-provider
user01    26211  0.0  0.1   2800   764 pts/0    S+   15:50   0:00 grep ppp
```

To stop it, I believe you need to issue the command:

```
sudo poff

```

Then you should be able to run pppoeconf again, see if that works.

To re-connect after possibly editing the file /etc/ppp/peers/dsl-provider, simply type:

```
sudo pon dsl-provider
```

Regards, Kev :)

PS.  If you do NOT select "connect automatically" or "connect at startup" whatever it is called in pppoeconf, then you can install an app called "gpppon" from synaptic, it's a PPPoE dialup GUI tool for your desktop, so you just click on connect/disconnect.

---

### Post by mahiyar on 2007-03-17
Do you have dual boot? Does the same work under windows? Are all your cables and board secure can you see the green light on the card?

---

### Post by Shaunak on 2007-03-17
I have dual boot, everythings fine under windows.




@kvonb: i have had several chats with my ISP :)  They keep assuring me that they themselves use REd Hat 10 on some of their computers and everything's dandy on that. 

The sudo poff didnt help.

---

