---
title: "problems with ssh"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-12-14
I looked around on the forum but found nothing of real relevance.

I have ssh installed on my desktop and laptop, both run ubuntu 6.06 exclusively, I am trying ssh from my laptop into my desktop from within my LAN.

I installed ssh onto my laptop as well as putty, at my desktop I edited the /etc/sshd_config file to listen on port 443 restarted the daemon and all of that.

From the command line at my laptop I:  sudo ssh charles@192.168.1.101 -p443 and it just hangs there, no complaining or nothing.

Both systems run firestarter but I specified an exception and was able to successfully log into the desktop through a windows box using putty in the past...

I dont really know where to start diagnosing the problem so any ideas would be greatly appreciated.

---

### Post by FryerFox on 2006-12-14
As a start, use nmap to see which ports are open on your server:
> nmap 192.168.1.101

---

### Post by charles.g.moore on 2006-12-15
it just says that they are all filtered

---

### Post by chrisfay on 2006-12-15
Have you tried stopping your firewall completely and testing? Its best to start with the least restrictions and work your way up....

```
sudo iptables -F
```

---

### Post by steve.horsley on 2006-12-15
On your desktop, make sure that sshd is running with this command:
**sudo netstat -plant**
and you should see a line like this:
```
tcp6       0      0 :::443                   :::*                    LISTEN     4411/sshd
```
Although it says tcp6, sshd is listening on both tcp6 and tcp4 in reality.

On your laptop, you don't need to use sudo to launch the ssh client. And you might need a space between -p and 443, and you may need the port number before the host:
**ssh -p 443 charles@192.168.1.101**

---

### Post by rich.bradshaw on 2006-12-15
You don't want to sudo ssh, only sudo things that are modifying system files. Normally sudo is something that you wouldn't want anyone to do, and other commands are things you feel happy with anyone doing if you see what I mean.

i.e. opening Firefox isn't sudo, because I don't mind who comes into my house and does that, but rm -r * is sudo, for obvious reasons.

---

