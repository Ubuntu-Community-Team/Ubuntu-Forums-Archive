---
title: "oops... screwed up /etc/hosts"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by HeavyEddie on 2006-09-07
OK, I did the following command as part of the vhost installation and apparently stopped at an inopprotune moment.

```
mv /etc/hosts /etc/hosts.0
```

Now, whenever I try to use sudo I get the following error.
```
sudo: unable to lookup ed-laptop via gethostbyname()
```

So, I assume I can reverse the paths on the mv command above and be in pretty good shape... the problem is I can't do it since sudo or gksudo no longer work.

Any suggestions?

---

### Post by shinythings on 2006-09-07
If you have a live CD (the normal install CD is a live CD) you could boot with that and change the path back.

---

### Post by bodhi.zazen on 2006-09-07
boot live CD.

Mount HD

sudo mv HD_mount_point/etc/hosts.0 HD_mount_point/etc/hosts

---

### Post by Fedz on 2006-09-07
The reason why it happens I think is the 127.0.0.1 in the hosts file at the beginning.

If you try to reboot in 'safe mode' it's something to do with ipv4 and ipv6 which relates to the host file in /etc/hosts

It happened to me when I just tried to check for updates so I tried to put the hosts file back using sudo cp hosts /etc/hosts and got the result you did.

So it reality (and much to my horror and misunderstanding) changing the /etc/hosts file is quite dangerous and or fickle :rolleyes:

I genuinely offer my sincere apologies for my part of posting the query earlier to try this myself ...

Kind regards

---

### Post by HeavyEddie on 2006-09-07
OK, I got the hosts file back and look at the contents just fine.  It didn't work, so I booted back to the live cd and did a chmod 777 on it... thinking it may be a permissions issue.  No luck.

Hmmmm... what next?

In a weird twisted way, it is nice to be challenged again.  Learn by doing I always say :)

---

### Post by bodhi.zazen on 2006-09-07
Boot to live CD, mount HD,
```
 sudo cp /etc/hosts HD_mount_point/etc/hosts
```

---

### Post by HeavyEddie on 2006-09-07
I've tried that... reboot to the live cd to try it again.  Still nothing.

hmmmmmmmm

---

### Post by bodhi.zazen on 2006-09-07
Perhaps the problem is not with /etc/hosts then.

Post /etc/hosts ? :-k

Perhaps vhost is not correctly configured. :-k

---

### Post by HeavyEddie on 2006-09-07
OK, I've been playing with this a bit and broke another system.  :)  On this new system I did the complete install and the sequence vhost has you take is this...

```

mv /etc/hosts /etc/hosts.0
ln /etc/vhosts /etc/hosts
vhost addhost test.com test -f
vhost lshost
mozilla http://test.com #open "http://test.com" in a web browser
mv /etc/hosts.0 /etc/hosts

```

This process fails at the 3rd line.  However, I think it is the ln that is screwing me up a bit.  How do you remove a link?

The difference is I still have a root window open on this computer and can probably fix the problem if we can figure it out.

---

### Post by HeavyEddie on 2006-09-07
OK, I got it fixed on this system anyway.  I'm not exactly sure why it works... but it did.

[list]
[*]I copied a version of the hosts file
[*]deleted both hosts & vhosts.  I read up on ln a bit and I don't see a way to break the link, so I just deleted both.
[*]I changed the hostname back to localhost
[/list]

It works.  Seems I have a little more reading to do :)

---

