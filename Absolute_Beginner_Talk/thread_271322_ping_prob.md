---
title: "ping prob"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-04
hello

is the ping command different from windows

i type ping then ip address and it says pinging blah blah blah bytes of data
then the cuursur gos to the next line and just blinks.
i can type stuff in on the line.
i have turned the icmp filtering off in the firewall.
it should at least say packets dropped or something right??
i never had prob like this on windows so im stumped.

---

### Post by w7zac on 2006-10-04
> **uk_sphinx said:**
> hello

is the ping command different from windows

i type ping then ip address and it says pinging blah blah blah bytes of data
then the cuursur gos to the next line and just blinks.
i can type stuff in on the line.
i have turned the icmp filtering off in the firewall.
it should at least say packets dropped or something right??
i never had prob like this on windows so im stumped.
Hi. I am a newby also but first try pinging your local host 127.0.0.1
then yourself, which is listed when you bring up your network connection,
probably 192.168.0.100 or .101 etc. If you can ping yourself, then tcpip is working. I am having similar problems pinging winxp and winme pc's on my local network, If you have a winxx maching running, try their help/support to get you going. make sure samba is working and you can at least see yourself in the remote places software.

w7zac
:-D

---

### Post by uk_sphinx on 2006-10-04
>  Hi. I am a newby also but first try pinging your local host 127.0.0.1
then yourself, which is listed when you bring up your network connection, 

are you confused about 127.00.00.1???
127.00.00.1 (local host) is your own computer.
its the equvalant of typing your own ip address in.
think its pointless pinging yourself.
im not on a lan.
im trying to ping my friend to see if he is online.

---

### Post by uk_sphinx on 2006-10-04
forget this question i figured out the problem.

unless you specify the amount of packets to send -c 5 then it will continually send packets forever.

you also have to specify echo recieve -R to display return data.

i think this explains it. i like these flags you have to set in ubuntu. i never learned this on windows.

ahhhh   the power of the "man" command.

---

### Post by explodecomputer on 2007-02-23
Hey hey,

So hypothetically speaking, imagine if you were to accidentally forget to specify how many packets to receive, and you just happened to have been sending and receiving packets with no idea how to stop them for the last 15 minutes... then what would you do?

Not that I would be silly enough to do such a thing, heh heh.

Thanks in advance for any help!

---

### Post by steve.horsley on 2007-02-23
Ping in Linux is different in behaviour. 

Firstly, as already mentioned, it goes until you stop it, unless you specify a count when you start it. 

Secondly, it doesn't print anything if it doesn't receive anything. You can detect lost packets in a mostly working connection by looking for missing sequence numbers, not by looking for timeout messages. Ping also prints a set of statistics when you stop it with Ctrl-C.

> So hypothetically speaking, imagine if you were to accidentally forget to specify how many packets to receive, and you just happened to have been sending and receiving packets with no idea how to stop them for the last 15 minutes... then what would you do?

If you didn't know to stop them with Ctrl-C, you could close the console window, or "killall ping" from another window, or use xkill to kill the console window, or ps and kill to kill that specific process. Or reboot.

---

### Post by explodecomputer on 2007-02-23
Thanks =]

---

