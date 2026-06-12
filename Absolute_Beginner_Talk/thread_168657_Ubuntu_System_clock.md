---
title: "Ubuntu System clock"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by yo_momma on 2006-04-30
I have a problem in which my system clock is a lot slower than my hwclock.
In doing searches accross the net I find lots in which their system clock is faster than the hwclock but nothing describes the problem I experience.

I run Ubuntu 5.10 under VMWare GSX Server on a base Win2k3 server.

My system clock looses about 3 minutes in a 5 minute span.  It is so bad in fact that I had to setup a Crontab job to sync things up

0,5,10,15,20,25,30,35,40,45,50,55 * * * * /sbin/hwclock --hctosys

Being as I am quite new to Ubuntu some of my search engine problems I run into is not knowing the correct terms to search for.

I have UTC=no

I am GMT -6 and that is where my time zone is properly set to.

What I really need it the basic instructions on how to troubleshoot this annoying issue.

Thanks in advance for any help or suggestions that I may receive.

---

### Post by jarrett.wold on 2006-05-01
You may be able to correct, by enabling time synchronization.

1.  Open a terminal 
2.  At the prompt type: time-admin
3.  Enter your password when prompted
4.  Check  "Periodically Synchronize Clock with Internet Servers"
5.  Click select a server
6.  In the box type:  pool.ntp.org
7.  Click Add
8.  Place a check next to pool.ntp.org in the list (it'll probably show up at the bottom)
9.  Click Close, then Click OK.

If the clock is off by .5 seconds it will slowly adjust it. If not, it should just bump it straight into line.

Hope that helps ;)

---

### Post by pjstadig on 2006-05-03
I have also had this problem with a VMWare GSX server on RedHat guest hosting Ubuntu. I ended up setting up an ntp sync every hour, but I wasn't satisfied with that. Here is a VMWare KB article that fully explains the issue and gives a workaround.

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1420](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1420)

---

