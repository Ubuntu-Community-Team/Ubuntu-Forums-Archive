---
title: "Ubuntu Firewall?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by buzlink on 2006-09-19
I understand that there is a firewall installed by default in Ubuntu?
How do I use it and check it's stats?
I'm familiar with Windows Firewalls such as Zonealarm.  How do I use something similar in Ubuntu?
Something that makes sure misc. programs are not accessing the net and such would be great as well.

Thanks

---

### Post by jd65pl on 2006-09-19
Check out firestarter in the repositories it is a gui front end to the pre-installed firefall iptables.

Thanks

J

---

### Post by Jussi Kukkonen on 2006-09-19
No firewall by default (several in synaptic though). You won't find something like zonealarm for linux, I believe. I've not heard of anything that handles outgoing connections -- I'm sure someone will correct me though.

I'm not sure I've really understood the point though: now that ZA is widely used, all the home-phoning-malware-applications just use IE (which of course is approved for internet connections) to phone home... and ZA stays quiet.

The same has happened in the unix side years before, because of better networking tools: many trojans/backdoors just use e.g. the system ssh-executable to open connections. A linux ZoneAlarm couldn't stop that... the only way to prevent it is to not run the original trojan/backdoor in the first place.

---

### Post by bodhi.zazen on 2006-09-19
Ubuntu (Linux) has a built in firewall (IP tables) that is quite robust.

If you want to limit out going connections, install firestarter and set the outbound rules to restrictive. You will then need to allow certain connections or your browser will not work.

As has been pointed out, firewalls on any OS have limits, but they do help.

---

### Post by sarum on 2006-09-19
Hi: I've installed Firestarter and am confused. Type Firestarter into the search box at the top of this page.Loads of help; one guy said make 'outbound' - 'restrictive' and you'll be OK: but as bodhi.zazen points out, you need to do something else.Then there are others dealing in formidable detail.I'll stay with Firestarter(we're nearly all different so no 1:size fits all), but for the home computer/beginer - has anyone any comments on 'ipkungfu'. I can find no threads here. Cheers Sarum

---

### Post by bodhi.zazen on 2006-09-19
> **sarum said:**
> Hi: I've installed Firestarter and am confused. Type Firestarter into the search box at the top of this page.Loads of help; one guy said make 'outbound' - 'restrictive' and you'll be OK: but as bodhi.zazen points out, you need to do something else.Then there are others dealing in formidable detail.I'll stay with Firestarter(we're nearly all different so no 1:size fits all), but for the home computer/beginer - has anyone any comments on 'ipkungfu'. I can find no threads here. Cheers Sarum

Start with this:

[Firestarter documentation](http://www.fs-security.com/docs.php)

---

### Post by buzlink on 2006-09-19
So how do I go about installing Firestarter?

Thanks

---

### Post by NetworkGuy on 2006-09-19
From a terminal, type ```
sudo apt-get install firestarter
```

---

### Post by 3rr0r on 2006-09-19
get it from synaptic... not sure if you need to add the multiverse and/or universe though.

---

### Post by buzlink on 2006-09-19
> **NetworkGuy said:**
> From a terminal, type ```
sudo apt-get install firestarter
```

```
E: Couldn't find package firestarter

```

---

### Post by NetworkGuy on 2006-09-19
As 3rror stated, you will need to enable to universe to getthe package.  

The easiest way I know how to do it is to use synaptics from administration --> synaptic package manager  (Taking a guess on the path right now)   

Click on options / preferences  (I think) and enable all checkboxes for Dapper 6.06 LTS.  Click OK until you are back out to the main synaptic window, click reload, then scroll down until you find firestarter, mark the box for installation then click apply.

---

### Post by buzlink on 2006-09-19
> **3rr0r said:**
> get it from synaptic... not sure if you need to add the multiverse and/or universe though.
Got it through synaptic.  Was trying to use the command line to give it some use but oh well.
THanks

---

### Post by mssever on 2006-09-19
While there's nothing wrong with using Firestarter, you shouldn't worry too much about a filewall in Ubuntu. By default, all ports are closed, making it virtually imposible to crawl in from the outside. And as far as malware on your local machine goes, you're pretty safe--especially if you stick to software from respected repositories. In the open source world, any software that phones home will be detected quickly and taken out and shot.

Now, if you choose to install a server, you need to think more about security.

---

### Post by sarum on 2006-09-20
On the previous page I mentioned the trouble I was having with Firestarter due to an overload of advice. bodhi.zazen suggested trying[COLOR="Red"] Firestarter Documentation[/COLOR]. This is just the thing I needed and I'm kicking myself for not finding it myself. Thanks bodhi.zazen and good luck Buzlink............Sarum

---

### Post by buzlink on 2006-09-21
How do I enable Firestarter to load at startup?
Thanks

---

### Post by jd65pl on 2006-09-22
You do not need firestarter to to load at startup, the program is merly for the configuration of a firewall which is already running (iptables). There is no benefit from getting firestarter to start its GUI at startup.

---

