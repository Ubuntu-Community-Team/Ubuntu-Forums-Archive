---
title: "Help! My ubuntu computer keeps crashing"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-06
I recently was reading a simple website about how to make my ubuntu computer a server. I followed its simple instructions by changing my /etc/hosts to:

127.0.0.1       localhost
127.0.1.1       computer name

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Now my computer keeps crashing. The normal log on program will not run and has to run an alternate one each time. I keep trying to change it back to the original values but even in root access the file access is denied when I never I try to open it even though I never said to deny access. Also, in order to even access root I had to type su then my password. The root itself would not load. I have to go through a konsole. I know it was just that one file but I do not know why it would crash my entire computer. 


I would greatly appreciate if you could tell me how I could access /etc/hosts and how to fix my computer. 

):P

---

### Post by ^rooker on 2007-02-06
3 things:

a) What are the permissions of your /etc/hosts?
what does "ls -la /etc/hosts" say?

It could be that the file is simply write-protected, meaning you have to CONFIRM edits additionally (in vim it's ":wq!" instead of just ":wq").



b) sudo has problems if the hostname can't be resolved correctly, so it might be that you can't sudo right now... And by default there is NO real "root" user on Ubuntu.
Here are some problems I've experienced myself with [wrong hostnames on Ubuntu]("http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=400").



c) What exactly do you mean with "crashing"?

---

