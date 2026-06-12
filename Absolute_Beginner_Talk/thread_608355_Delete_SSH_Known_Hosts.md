---
title: "Delete SSH Known Hosts"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by P4rD0nM3 on 2007-11-09
Hey guys, I installed the openssh-server and I did the following...

ssh localhost

and

ssh 192.168.0.100

My question is, how do I delete the localhost entry?

Oh and one more thing? By default an ssh client is installed? Did I get it right? How do I access that ssh client? I also installed PuTTy, but I want to know where the ssh client (The one from Synaptic) is installed and how do I access it? Thanks.

Or is that ssh client that's already installed...the one in the terminal when I type 'ssh 123.123.123.123'?

---

### Post by qpieus on 2007-11-09
> **P4rD0nM3 said:**
> Or is that ssh client that's already installed...the one in the terminal when I type 'ssh 123.123.123.123'?

Yes. The ssh client is installed by default. You're using the installed ssh client when you type "ssh ...."

I'm sorry but I don't understand your question on deleting the localhost entry. If you mean how to remove it from the known_hosts file, I don't know. It's just a text file so I suppose you could edit it if you can figure out the parts you don't want. I just looked at mine and there's a bunch of stuff in there - I wouldn't know what to remove.

Why do you want to remove the localhost entry? I don't think it hurts anything to just leave it alone.

---

### Post by P4rD0nM3 on 2007-11-09
To make the list uhm...cleaner? Hehe. Where do you look for, for the known_hosts? I'm using another computer and I'm trying to change stuff remotely (Getting used to the command line).

I wanted to delete the first entry localhost...because 192.168.0.100 = localhost...but it cached both of them so I wanted to remove the localhost cache. So there's only 5 entires...192.168.0.100 up to 104. :P

---

### Post by qpieus on 2007-11-09
OK clean freak :)

The known_hosts file is at 

/home/*username*/.ssh/known_hosts

make a backup of it before you mess with it....

---

### Post by mouko on 2007-11-10
If you are asking how to change the value of localhost, I believe it is in the hosts file, so

sudo vim /etc/hosts

---

### Post by P4rD0nM3 on 2007-11-10
How do you know which one? It's encrypted... I entered localhost first so I guess it's the first one? And...if I ever mess everything up, is it safe to just delete known_hosts?

---

### Post by wariola on 2007-11-10
more or less its safe to delete known_hosts. It will build a new "known-host" database.

---

### Post by ruibernardo on 2007-11-10
Delete the line that ssh is complaining about. If it is 5, delete line 5.

---

### Post by houstonbofh on 2007-11-10
I delete mine on a regular basis.  Essentially every time something I ssh to gets a new IP address.  Sigh... "No, I didn't ask for strict checking..."

---

### Post by P4rD0nM3 on 2007-11-10
Haha, ok guys. Thanks.

---

### Post by dwhitney67 on 2007-11-10
Yep, that would blow if you "have to" delete the known_hosts file everytime you connect somewhere.  It happens to me on occasion when I am connecting to the same physical system that is running a new OS.  I believe it has something to do with the "key" files in /etc/ssh.

Anyhow, there's no harm in removing one's ~/.ssh/known_hosts.  What's a pisser is when you have to edit (or remove) the authorized_keys file.

---

