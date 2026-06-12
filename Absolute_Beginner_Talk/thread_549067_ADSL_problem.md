---
title: "ADSL problem"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by carnivore on 2007-09-12
Hello!

I just installed ubuntu, being my first time using linux, i ran into problems as i had to set up my internet connection. Having a PPPoE ADSL modem, I followed the instructions in the integrated ubuntu help menu- i configured the connection through "sudo pppoeconf" command, clicked my way through yes's, only to find out that i still couldn't connect with the "sudo dsl-provider" command.
As i browsed the net for a solution, i found a suggestion to change a file with a command "sudo nano -w /etc/ppp/options", in this file there had to be a # sign put in front of one particular line. Altough I had done so, there was no change.

I have a Dell Inspiron 6400 notebook with a Broadcom 440x 10/100 network adapter,  I didn't install any drivers for the adapter, but i presume that ubuntu took care of it by default, since in the blue window of ppoeconf the three network adapters were recognised(the second one being WLAN, the third one Firewire i assume). Ubuntu automatically chose eth0 adapter for my connection, and left me no choice of switching to others, so i wonder if eth0 is definitely the Broadcom LAN card or could it be the WLAN or Firewire card?

Very gratefull for any help. Thank you.

PS: Yes I checked the old threads, but no solution to the problem offered.

---

### Post by Skrynesaver on 2007-09-12
sudo **pon** dsl-provider


Alternatively you may have a connection app on the modem/router try connecting to it from Firefox

[http://192.168.0.1](http://192.168.0.1) on my network, may vary on yours

---

### Post by carnivore on 2007-09-12
sorry my bad, i mistakenly left **pon** out as i wrote the command here, i used pon in the terminal. Here i copied my terminal window text, what happens when i try to connect(i used plog to get the status):

```
daniel@dvoglavi:~$ sudo pon dsl-provider
Password:
Plugin rp-pppoe.so loaded.
daniel@dvoglavi:~$ plog
Sep 12 13:45:47 dvoglavi pppd[6208]: Connection terminated.
Sep 12 13:46:10 dvoglavi pppd[4476]: PPP session is 3359
Sep 12 13:46:10 dvoglavi pppd[4476]: Using interface ppp0
Sep 12 13:46:10 dvoglavi pppd[4476]: Connect: ppp0 <--> eth0
Sep 12 13:46:10 dvoglavi pppd[4476]: CHAP authentication failed: Access Denied
Sep 12 13:46:10 dvoglavi pppd[4476]: CHAP authentication failed
Sep 12 13:46:10 dvoglavi pppd[4476]: Connection terminated.
```

the password i typed in is 100% correct. About the IP you are talking about, how do i get to know my IP?

---

### Post by Skrynesaver on 2007-09-12
If you do a grep of /var/log/daemon.log for DHCPACK it should return your DHCP server, assuming you are using your DSL modem to assign IP addresses try browsing to this address

---

### Post by carnivore on 2007-09-12
sorry but since i'm a complete newbie to linux OS in all aspects i don't really understand what you mean. I should write /var/log/daemon.log in terminal? Could you give me step-by-step instructions please?

---

### Post by Maestro23 on 2007-09-12
> **carnivore said:**
> sorry but since i'm a complete newbie to linux OS in all aspects i don't really understand what you mean. I should write /var/log/daemon.log in terminal? Could you give me step-by-step instructions please?

I believe he wants you to run the following in a terminal:

> cat /var/log/daemon.log | grep DHCPACK

---

### Post by carnivore on 2007-09-12
ok i tried to run that in terminal but nothing happens, the cursor just jumps to the new line.

---

### Post by RedSquirrel on 2007-09-12
Just a thought:

When you run 'sudo pppoeconf', on some ISPs, you have to enter your username as (for example):

```
username[COLOR=Blue]**@my-isp-company-name.com**[/COLOR]
```

not just *username* by itself. You might want to double-check that. ;)

---

### Post by island3 on 2007-09-13
I am having the same problem and get the same messages (authentication denied) on Feisty 7.04. I'm also brand new to Linux and it does take some getting used to for people who are not that programming literate. Just a general comment to those replying to questions. We really appreciate your intentions to help,thank you! But I think some of you forget what the basics are. It's really hard to follow responses that are not in plain English. 

:)

The sudo terminal has a place to enter your name and password, which I did. That is not the problem, I presume.

---

