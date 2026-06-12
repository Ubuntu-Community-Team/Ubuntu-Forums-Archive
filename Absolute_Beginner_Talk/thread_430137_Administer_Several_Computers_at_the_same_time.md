---
title: "Administer Several Computers at the same time?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-05-01
I am hoping to get my wife into Ubuntu, but i was wondering if there is a way to do all of the administrative tasks on her computer remotely on mine... basically so that she can do her thing while I update her computer and whatnot. I know that Linux is a multi-user OS, so I am fairly certain that I can do this... would anyone be willing to help me learn how?

---

### Post by louieb on 2007-05-01
Don't know about several at the same time. But for your wifes PC, install openssh-server and make yourself an account with admin group membership.
Then in the terminal its >ssh 192.168.#.## to logon to the remote machine. 
I've got my router assigning the same IP to each of my wired machines based on mac address. Have tried to set up static IP yet on a  wireless connection yet.  but I hope someone comes along with an explication of that.

---

### Post by brennydoogles on 2007-05-01
> **louieb said:**
> Don't know about several at the same time. But for your wifes PC, install openssh-server and make yourself an account with admin group membership.
Then in the terminal its >ssh 192.168.#.## to logon to the remote machine. 
I've got my router assigning the same IP to each of my wired machines based on mac address. Have tried to set up static IP yet on a  wireless connection yet.  but I hope someone comes along with an explication of that.

Just Curious... could I do the same with my Mother-In-Law's computer across town?? As long as I know the ip it should be no problem right?

---

### Post by freebeer on 2007-05-01
I think so.  If she's also behind a router, you'd need to make sure the ports are forwarded.

I can log into my home machine from work using Putty on the Windows machines at work.  I'm pretty sure you can do it using a graphical UI, too, but I haven't gotten that far down the road yet.  :D

---

### Post by Cypher on 2007-05-01
Locally or remotely, SSH is your way into a machine to administer it. Doing it locally is a cinch as you just need know the IP and not worry about anything blocking your access. Working across the Internet, you would want to know the IP of the remote router and also re-configure SSH on your M-I-L's machine to listen on a different port than the standard 22 (something hidden and one that only you know) and then with her router you'd port forward any request on that secret port to her computer.

---

