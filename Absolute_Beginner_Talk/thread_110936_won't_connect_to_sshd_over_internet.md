---
title: "won't connect to sshd over internet"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by darckhart on 2006-01-01
hi 

i did a search on the forums about this topic, but the threads didn't quite cover the problem i'm having, or i just can't interpret it correctly. any help is appreciated.

the machine with sshd:
ubuntu 5.10 with sshd using port 2297, internal ip 192.168.1.149, external dynamic ip is whatever sbc assigns

my problem is that i have installed sshd, and i can connect to it from my windows machine over the LAN using the internal address, but when my friend tries to connect from the internet using the external dynamic ip, it never works. i have my router (Linksys WRT54G) forwarding port 2297 to 192.168.1.149. i do not believe i have any firewalls blocking any traffic.

what i tried so far:
1. maybe it doesn't like port 2297, changed it back to 22. set router to forward 22. nothing.
2. put myself into the dmz. nothing.

so i guess my questions are
1. is the router not really forwarding the traffic?
2. does my isp block ssh traffic? despite the port number change?


thanks very much for your replies.

---

### Post by encompass on 2006-01-01
have you ever used shieldsup test to see if your port 22 is open? or perhaps even blocked.  That may tell you if your ISP is blocking that port.  You could also check the firewall on the windows computer.. I haven't the fogiest of how windows firewall works... but turning it off my help debug the issue.
Lastly... I would make sure your are entering the proper IP of your dynamic address give you from the ISP.  [www.whatismyip.com](www.whatismyip.com) to see you address and use that entry.
That is my best bet.  Just trying to help.:rolleyes:

---

### Post by darckhart on 2006-01-02
thanks for the suggestions, but i'm pretty sure those are taken care of since any login attempt from the LAN will work. i think what i will try next is to directly connect to my dsl modem. this will definitely tell me if the router is bein screwy. now all i have to do is figure out how to setup pppoe on ubuntu...

---

### Post by Suger on 2006-01-02
could your friend try a ssh -vvv next time, so we know when it goes wrong ?

---

### Post by darckhart on 2006-01-02
sure thing. i'll ask him next time i see him online.

btw where exactly are the sshd logs kept? i've just been looking at the system's auth logs for now...

---

### Post by Suger on 2006-01-03
should be in the syslog, by default

---

### Post by darckhart on 2006-01-03
yea, that's what i thought too, but when i did a grep ssh on the log, it came up empty. in fact, when i did a grep ssh on the whole /var/log directory, the only log with any ssh entry was auth.log

anyway, i flashed the firmware on my linksys router with HyperWRT. it adds some interesting features. i also enabled incoming connections log on the router, so hopefully i'll be able to find out what's going on from that. i'll play with it after i get home from work later today.

---

### Post by darckhart on 2006-01-07
ok so what i found out is that when i am connected directly to the dsl modem, my friend gets an error message that i can understand (Permission denied (publickey).) therefore, i conclude that the problem i had is directly related to my router not forwarding the port correctly. now, how to solve that....

---

