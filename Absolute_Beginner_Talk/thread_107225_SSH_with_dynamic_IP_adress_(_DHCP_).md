---
title: "SSH with dynamic IP adress ( DHCP )"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Biased turkey on 2005-12-22
I would like to communicate between my computer at work and my homesystem.
I understand that I can do it via SSH, but the problem is that BOTH at home and at work the IP adresses are assigned dynamically so I wouldn't know which IP adress to give after the SSH command.
Is there any way to solve that or does SSH requires at least 1 system with a static IP adress ?
tia

---

### Post by Swab on 2005-12-22
There are loads of websites offering URLs for dynamic ip addresses...  for example [http://www.no-ip.com/]("http://www.no-ip.com/")  Basically you run some software that lets them know when your ip changes..

---

### Post by dragonfyre13 on 2005-12-22
Try no-ip.com. It has a free service that you can sign up for, and you can select port forwarding to the ssh port.

Make sure that you renew your dynDNS once in a while.

---

### Post by dragonfyre13 on 2005-12-22
Dang, he got to it before me. ^_^

---

### Post by az on 2005-12-22
I have used Dyndns.com for this.

You can install ddclient (from the universe repository) and it can use your dyndns account.

Dyndns offers some paid services, but dynamicdns (what you need) is free.  And it works very well.

You set up your account and pick your doman name.  Example, you can create a username, password and tell it to use andrew.dynds.org

Then you install ddclient at home and tell it your account info.  From work, you can do

ssh [email]me@andrew.dyndns.org[/email]

andrew.dyndns.org will be resolved to your current ip address.  ddclient can check every few inutes to see if the ip address your isp gives you has changed and inform dyndns.

---

### Post by Biased turkey on 2005-12-22
Thanks a bunch to all of you who took some of their time to reply ( and to reply very fast  )
I just checked both noip and dyndns websites.

Special thanks to Azz for detailing the whole procedure.
Now, I'll be able to play Stratego ( pytego ) with my wife while I'm at work :)

---

