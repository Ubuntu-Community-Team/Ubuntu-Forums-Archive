---
title: "Ipod-Convenience troubles - SSH:  IPDADRESS:  name or service not known"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Dontgetit on 2008-03-02
Hello!  I have searched the forums (and Google) and hope I'm posting in the right place.  I'm having lots of trouble with ssh and the ipod-convenience script all of a sudden.

I have it running on two computers with Gutsy.  It was working on my laptop last night and then all of a sudden, when I pop a terminal and write "iphone-mount" I get the following error.

ssh: IPDADDRESS: Name or service not known

I have uninstalled and reinstalled ipod-convenience many times.  I know the issue isn't with my iphone because i'm able to mount it on my other computer.

PLEASE HELP!  I'm really at a loss and am desperate for guidance.

Thanks so much!

---

### Post by adouba on 2008-03-02
I am getting the same problem too.

---

### Post by ntetreau on 2008-03-04
I can confirm this is a bug in the latest ipod-convenience ([bug 198139]("https://bugs.launchpad.net/ipod-convenience/+bug/198139"))

I found a workaround i think.  In iphone-mount :

```

sudo gedit /usr/bin/iphone-mount

```

Change line 66 from:

```

    if ssh root@192.168.6.136 test -d /var/mobile; then

```

to

```

    if ssh root@$IPADDRESS test -d /var/mobile; then

```

I still get the "ssh: : Name or service not known" message but it mounts fine for me

By the way, you guys might want to take the habit of posting your ipod touch or iphone problems in the following [thread]("http://ubuntuforums.org/showthread.php?p=4450518#post4450518") as most users are subscribed to it and can help faster!

---

### Post by nick77 on 2008-03-09
I just stumbled upon the same issue, however, as you can see below, during the time I've been searching the web for this problem, the first try to connect to the wrong IP address timed out, afterwards, the correct one appeared, login went fine....

```
nick@nick-desktop:~$ iphone-mount
ssh: : Name or service not known
ssh: connect to host 192.168.6.136 port 22: Connection timed out
root@10.10.10.183's password: 
read: Connection reset by peer
You don't have a Firewire GUID, so we will create one

```

definetly a bug, so;-)

nick

---

### Post by ntetreau on 2008-03-10
The bug is fixed in the latest ipod-convenience 0.8

---

