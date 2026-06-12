---
title: "internet problem"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-09-15
hi , 
i am using ubuntu 7.04 fiesty , my internet was  working fine in pppd mode and now it stopped working . i have dsl connection. can somebody tell me what is the problem?


i think maybe it could help


aman@Ultimate:~$ pppoeconf
About to execute /usr/sbin/pppoeconf.
This command needs root privileges to be executed.
enter root passwd:
Password:
su: Authentication failure
Sorry.
Incorrect password or command failed. Try again? (y/n)n
daman@Ultimate:~$ sudo pppoeconf
Password:
Plugin rp-pppoe.so loaded.
daman@Ultimate:~$ poff
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$ poff dsl provider
/usr/bin/poff: I could not find a pppd process for provider 'dsl'. None stopped.
daman@Ultimate:~$ pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
daman@Ultimate:~$ pon dsl provider
The file /etc/ppp/peers/dsl does not exist. Please create it or use
a command line argument to use another file in the /etc/ppp/peers/ directory.
daman@Ultimate:~$ pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
daman@Ultimate:~$ plog
Sep 16 02:42:17 Ultimate pppd[6201]: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
Sep 16 02:42:38 Ultimate pppd[6213]: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
daman@Ultimate:~$ poff
/usr/bin/poff: /bin/kill failed.  None stopped.
daman@Ultimate:~$

---

### Post by damansandhu on 2007-09-15
somebody help plz

---

### Post by damansandhu on 2007-09-15
help me out guys

---

### Post by mikewhatever on 2007-09-15
Any idea why it stopped working? Think, there must be something. Why do you type all those commands? Did you have to do it to connect before?

---

### Post by damansandhu on 2007-09-16
when i setup internet connection by typing "pppoeconf" its says that internet connection has been triggered , but no website opens and nothing works.

---

### Post by damansandhu on 2007-09-18
i dont know , it says internet connection has been triggered but i cant access internet , plz help me out , now i have to use stupid windows for the sake of internet.

---

### Post by damansandhu on 2007-09-18
i have checked the dsl router connection , its properly connected and i even can browse my router by typing "192.168.1.1" in firefox . when i type "sudo pon dsl-provider" in terminal , it says that some file is loaded , means that internet is connected , but i cant acess internet , it was working fine few days ago , i dont know what happened now .

---

### Post by revelation.now on 2007-09-18
okay, firstly, we'll see if your internet connection is up. 

Try pinging google.com

we'll expect that to fail, but if it comes back with something its probably a firefox config issue or your DNS is not resolving which are, in my opinion, the most likely.

secondly, ping 72.14.207.99 
(its what google is resolving to for me right now. it should respond)
if you get something here, then it was an issue mentioned above

that aside, you say you can get to your router via your browser. You'll have to tell us more about your set up. I'll assume its connected via ethernet, but it sounds like your trying to dial a connection via bridge mode or something of the sort. This should be possible, but your router might already be dialling the connection for you, so maybe check its log to see if its just getting CHAP authentication issues, in which case its an issue with your ISP. Fill us in with a bit more info and we can be more help

---

### Post by damansandhu on 2007-09-18
ok , when i try to open google , firefox says that it is unable to find server.

and when i try to ping google by typing "ping 72.14.207.99" in terminal , it says operation not permitted.
I connected Internet before doing this By TYping "pon dsl-provider"

---

### Post by damansandhu on 2007-09-18
reply plz

---

### Post by damansandhu on 2007-09-18
i have set my router in bridge mode , i am using dialer in xp to connect to internet

---

### Post by damansandhu on 2007-09-18
i need help plz

---

### Post by damansandhu on 2007-09-18
i think there is some problem in the dialer , but i have inserted username and password correctly.

---

### Post by damansandhu on 2007-09-18
hi , why are you not posting poeple.

---

### Post by damansandhu on 2007-09-19
Post Plz

---

### Post by damansandhu on 2007-09-19
lol still no reply

---

### Post by damansandhu on 2007-09-19
i am waiting for replies

---

### Post by damansandhu on 2007-09-19
reply plz

---

### Post by damansandhu on 2007-09-20
reply

---

### Post by damansandhu on 2007-10-02
help plz

---

### Post by LetThereBeRawk on 2007-10-02
If you're behind a router, then I think that you shouldn't have to use a PPP dialer. Your router should handle connecting to the DSL connection and as long as your network card is functioning, it should connect to the network automatically with the built-in network auto config.

If it's a DSL modem connected USB to the computer, I don't know the best way to get that going.

---

