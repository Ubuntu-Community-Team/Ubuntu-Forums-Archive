---
title: "[SOLVED] fserve port forwarding problem"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by _sluimers_ on 2008-03-02
Okay, this should show my port forwarding problem:

[[IMG]http://img128.imageshack.us/img128/9563/screenshot2ev6.th.png[/IMG]](http://img128.imageshack.us/my.php?image=screenshot2ev6.png)
[[IMG]http://img225.imageshack.us/img225/7020/screenshot1ot9.th.png[/IMG]](http://img225.imageshack.us/my.php?image=screenshot1ot9.png)
[[IMG]http://img216.imageshack.us/img216/4208/screenshotsn8.th.png[/IMG]](http://img216.imageshack.us/my.php?image=screenshotsn8.png)


My goal is to get an Fserve called Obsidian2 working.
As you can see I am running dansguardian.
I have no clue of what to do.
Something with iptables..?

---

### Post by glennric on 2008-03-02
You could try installing firestarter.  It is a GUI frontend for iptables.  You will have to figure out what ports to open, and then set up the firewall with firestarter.  Firestarter has a list of standard ports built in so you might be able to figure out what port you need to open from there.

Edit:  From your screenshots it seems you know which port to open.  Set that up with firestarter.  It is much easier to use than iptables from the command line.

---

### Post by _sluimers_ on 2008-03-02
I don't know how to use firestarter in combination with dansguardian.
I don't know which ports to open, they're the result of googling 'port fserve' and finding the first port number that came up.

---

### Post by _sluimers_ on 2008-03-05
Since I always read other people's threads hoping the question has been solved, I'll update what I've got so far:

After a few days of tedious trial and error I've come to the conclusion that I have either 3 or 2 firewalls, One NAT firewall, one normal firewall on the modem/router and firehol.

Turning the firewall off on the modem/router doesn't stop it from having to port forward.

DCC Chat is on port 59
DCC send however is on a random port unless configured otherwise.
DCC send needs one port per file send. So you expect 

To make fserve in xchat half-work with all these firewalls running I had to do the following:

in xchat go to Settings->Preferences->Network->File transfers
Then mark get my address from IRC server
I decided to add 400 (way more than necessary) ports by 
..altering First DCC send port from 0 to 53000
..altering Last DCC send port from 0 to 53400

Then I restarted xchat.

I NAT forwarded port 59 and 53000 to 53400 on my router.

I've done the following in the terminal:
```

rogier@rogier-laptop:~$ sudo iptables -I INPUT -p tcp --dport 59 -j ACCEPT
rogier@rogier-laptop:~$ sudo iptables -I INPUT -p udp --dport 59 -j ACCEPT
rogier@rogier-laptop:~$ sudo iptables -I INPUT -p tcp --dport 53000:53400 -j ACCEPT
rogier@rogier-laptop:~$ sudo iptables -I INPUT -p udp --dport 53000:53400 -j ACCEPT

```

I added this to /etc/firehol/firehol.conf:
```

# dcc chat
iptables -I INPUT -p tcp --dport 59 -j ACCEPT
iptables -I INPUT -p udp --dport 59 -j ACCEPT

# DCC send
iptables -I INPUT -p tcp --dport 53000:53400 -j ACCEPT
iptables -I INPUT -p udp --dport 530000:53400 -j ACCEPT

```

Right now, the router's firewall is still off, so I don't know what effect it will have,
but right now I can fserve small textfiles... for some reason I have not succeeded in sending
avi's. I don't know yet about mp3's and such.

I have no clue why...

Could it have anything to do with having these files stored on extrenal harddisk?

---

