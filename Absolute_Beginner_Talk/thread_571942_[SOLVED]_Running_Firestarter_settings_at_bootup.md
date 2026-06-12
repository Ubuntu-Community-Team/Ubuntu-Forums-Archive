---
title: "[SOLVED] Running Firestarter settings at bootup"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-09
I realize that Firestarter is a graphical settings editor for the built-in firewall. I ran it and set it up the way I wanted it to run.

However, the settings don't seem to "take." If I go to [*_[COLOR="RoyalBlue"]Steve Gibson's Shield's Up[/COLOR]_*]("https://www.grc.com/x/ne.dll?bh0bkyd2") site after booting and before running Firestarter, I get different results than if I boot, run Firestarter, and then go to Shields Up. Therefore, it seems that the settings are not being saved. 

Specifically, the differences are that before running Firestarter, some of the ports are not in stealth mode and the Ping test is failed. When I run Firestarter and go back to that site, all is well. So what's going on and how do I fix it?

This is something very elementary that I'm ignorant of, I'm sure.

---

### Post by Dr Small on 2007-10-09
Having Firestarter run at bootup can not have any effect on it.
Firestarter only configures iptables as the GUI, so it is not actually changing settings at starting firestarter.

Dr Small

---

### Post by expatCM on 2007-10-09
Not quite sure what is your problem but if your settings are not being saved perhaps you want to start firestarter from the cli using gksudo.

I think you will find that ping is set off by default.

When you have a system up and running some ports will need to be open if you are to use the Internet.  You can see what ports are open and what is using them with the following command
sudo netstat -tcp -p

---

### Post by JBAlaska on 2007-10-09
Go to edit, preferences, policy and check "apply policy changes immediately" 

Then go to firewall and check the first and third entry (I'm guessing your not on dialup)

You can also go to advanced firewall settings and check "drop silently"

---

### Post by Alan Stancliff on 2007-10-10
> **Dr Small said:**
> Having Firestarter run at bootup can not have any effect on it.
Firestarter only configures iptables as the GUI, so it is not actually changing settings at starting firestarter.

Dr SmallActually, Dr. Small, running Firestarter does seems to have an effect on the functioning of the firewall in my experiments, as I document below. I realize Firestarter is a graphical editor of iptables,the real firewall capacity built into Linux. Nevertheless, starting Firestarter _does_ change iptables when it starts up.  

I have tested this several times. When I boot up and go to the Shields-Up site, this is the message I get: 
[INDENT][I]Solicited TCP Packets: RECEIVED (FAILED) — As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.

Unsolicited Packets: PASSED — No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)

Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.[/I][/INDENT]

Moreover, those ports which are closed are not in stealth mode, although all open ones are.

Then when I start Firestarter, 2 seconds later this is the message I get:
[INDENT]*Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.*[/INDENT]
So despite what the theories say, the empirical evidence shows that running Firestarter _*does*_ change the way iptables works.

> **expatCM said:**
> Not quite sure what is your problem but if your settings are not being saved perhaps you want to start firestarter from the cli using gksudo.

I think you will find that ping is set off by default.

When you have a system up and running some ports will need to be open if you are to use the Internet.  You can see what ports are open and what is using them with the following command
sudo netstat -tcp -pActually, expat, on my system, ping is not set to off by default. It apparently is set to on. That's one of my problems, as I mentioned in my earlier post. 

I don't know what you mean by starting Firestarter "*from the cli using gksudo*." I am very much a beginner with Linux and Ubuntu, although I have been playing with computers since 1984. Where would you suggest I look to learn more about cli and gksudo?

Concerning your comments on open ports, yes, some ports need to be open to communicate with the outside. But _all_ should be in stealth mode, whether they are on or off. Having a port in stealth mode means something different than having it off. The Shields-Up site referenced above has a lot of material on this.

> **JBAlaska said:**
> Go to edit, preferences, policy and check "apply policy changes immediately" 

Then go to firewall and check the first and third entry (I'm guessing your not on dialup)

You can also go to advanced firewall settings and check "drop silently"
Hi JBALaska, 

I did as you suggested, and this did not cure the problem.
[IMG]http://www.castlecops.com/zx/alanstancliff/divide.gif[/IMG]

I hate to sound like I'm carping, and I appreciate the three of you taking time out to help me. But so far, none of these suggestions have solved my problem. I hope I can get this resolved.

---

### Post by Alan Stancliff on 2007-10-12
**_*[COLOR="RoyalBlue"][SIZE="6"][CENTER]UPDATE[/CENTER][/SIZE][/COLOR]*_**


Okay, good people, I'm going to mark this thread SOLVED. Below I'll tell you how to fix this problem, which is real. I solved this problem as explained below, and it was easy, and it is safe.
===========================

[SIZE="4"]P[/SIZE]erhaps you found this thread because you were wondering how to have Firestarter start each time you boot. Or maybe you do realize that Firestarter is mainly a graphical settings editor for the firewall built into Ubuntu/Linux (iptables). At any rate, you've noticed you're not protected at boot until you run Firestarter.

Maybe you went to the excellent [**_[COLOR="RoyalBlue"]Shields Up[/COLOR]_**]("https://www.grc.com/x/ne.dll?bh0bkyd2") web site and found you were not completely protected until you ran Firestarter.

[SIZE="4"]If[/SIZE] this is your situation, read on, because I found the answer.

Reboot without running Firestarter, start up a terminal, and type in (or cut and paste in) the following:
```
sudo iptables -nL
```
If you get this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
you need to enable Firestarter's configuration settings so they automatically start up at boot time.

[IMG]http://www.castlecops.com/zx/alanstancliff/divide2.gif[/IMG]
[SIZE="6"]***_[COLOR="RoyalBlue"]The solution[/COLOR]_***[/SIZE]
As it happens, forum member **_nvteighen_** wrote a very detailed step-by-step explanation of what you must do. To read it, [**_[COLOR="RoyalBlue"]click here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=3308220&postcount=1") for the forum message. If you want to read the whole thread, [**_[COLOR="RoyalBlue"]click here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=3308220&postcount=1").

---

### Post by cam381 on 2007-11-16
All Firestarter does is let you manage settings for iptables in a graphical GUI. You only need to run Firestarter when configuring settings such as allowing or blocking ip addresses or websites.

---

### Post by Alan Stancliff on 2007-11-16
> **cam381 said:**
> All Firestarter does is let you manage settings for iptables in a graphical GUI. You only need to run Firestarter when configuring settings such as allowing or blocking ip addresses or websites.
Yup, we all know that Firestarter is a GUI front end for managing iptables. Please see the previous posts in this thread for problems **getting the settings to stick** from session to session. Also, please see *_**[COLOR="RoyalBlue"][this thread]("http://ubuntuforums.org/showpost.php?p=3308220&postcount=1")[/COLOR]**_* to see how this problem was solved.

This problem was marked closed because the above references provided the fix for the problem.

---

### Post by brett611 on 2008-01-01
Alan,
Thanks for your persistence w/r/t "Firestarter is just a GUI"....I have been beating my head against the same issue & arguments but am not technical enough to respond with a smack down.  Thanks for the link - problem appears to be solved for me as well.
Regards,

---

