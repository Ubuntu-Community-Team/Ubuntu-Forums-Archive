---
title: "SSH stopped working (I think)"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by NDPeter on 2008-02-08
I've been trying to setup a new build to serve mainly the purpose of a central spot to backup files to.

What I've done so far was install the LAMP deal so I could put up some pages if I wanted to mess with that.  That was successful.

Then I needed a way to get files to and from this machine over the internet.  after much reading, it seemed scp or sftp to be a good bet and so I installed the openssh-server package from synaptic.  Got in there...followed some instructions and changed the port and limited which users I wanted to have access.  All was well.  I moved about 100MB of stuff last night and all went smoothly.  Showed up this morning with new folders created and files all dumped right where I expected.

Sometime between then and now I've lost the ability to connect to my computer.  I did install ampache, but not sure what that would have to do with it.  

when I use 

```
ssh localhost 
```

i get a connection refused error

```
ssh: connect to host localhost port 22: Connection timed out
```

Also when I've tried connecting using FileZilla or WinSCP from some other spots I now get Authentication Failed errors where I was able to connect and transfer files before.

I've googled and basically come up with fixes regarding firewalls (I didn't have firestarter installed when this started, but have it now, but turned off for the moment), and routers (not using one).  I've stopped, and restarted ssh.  

I'd be grateful for any help.  I am fairly green when it comes to this, so if you somehow get the impression I have some sort of clue, you'd be mistaken.  

Thanks in advance for any insight.

---

### Post by Dr Small on 2008-02-08
If you changed ports, then that is the problem.
Try this:
```
ssh localhost -p *port*
```

Specify the port that you changed it to, there.

Dr Small

---

### Post by PeterJS on 2008-02-08
You might try checking if sshd is running:
```

ps aux | grep sshd

```

---

### Post by NDPeter on 2008-02-08
> **Dr Small said:**
> If you changed ports, then that is the problem.
Try this:
```
ssh localhost -p *port*
```

Specify the port that you changed it to, there.

Dr Small

I thought you were onto something.  I got further than before.  It asked about the key, then asked for my password.  at that point i got a 

"Permission denied, please try again"

Thanks for the idea.  I've come across some other threads you've worked on in my searches already.

---

### Post by NDPeter on 2008-02-08
> **PeterJS said:**
> You might try checking if sshd is running:
```

ps aux | grep sshd

```

Thanks.  Gave this a shot.  And if I understand correctly, it is running.

```
ndpeter@lead:~$ ps aux | grep sshd
root      6524  0.0  0.0   5280   992 ?        Ss   18:05   0:00 /usr/sbin/sshd
ndpeter   6711  0.0  0.0   2976   756 pts/0    R+   18:38   0:00 grep sshd
```

That first line means it is running, right?

---

### Post by bodhi.zazen on 2008-02-08
just currious , why are we ssh localhost ?

Sounds as if you have a problem with log in, hard to know if it is your user, key, or password.

Try:

ssh user@localhost -p xx

And it you are trying to ssh into a remote server, use the hostname or ip address.

---

### Post by NDPeter on 2008-02-08
> **bodhi.zazen said:**
> just currious , why are we ssh localhost ?

Sounds as if you have a problem with log in, hard to know if it is your user, key, or password.

Try:

ssh user@localhost -p xx

And it you are trying to ssh into a remote server, use the hostname or ip address.

I was using ssh localhost as it was giving me the same errors as with the hostname.  I think it was Dr Small who suggested a similar thing in another thread and I had the same problems with that (using user@localhost).

Thanks for the tip though.  I'm learning most (ALL) of this on the fly.  Check my post below...I have fixed it for the moment.  But I have a question why that worked.

---

### Post by NDPeter on 2008-02-08
I was playing around a little more and got into editing the sshd-conf file a little more.

I had added yesterday at the end of the file

AllowUser *user1,user2*

As noted in my original post it worked just fine last night and this morning.  Just now I deleted the second user.  It was entered with just the comma separating them and no spaces as I read somewhere else.  After deleting that bit, I was able to login, both from a terminal here and using filezilla on my laptop.

Any idea why this worked?  I wonder now as I think I'll want to add other users later on and that seems to add another layer of protection.

Thanks to all of you for checking and and offering your ideas. esp Dr Small.  When I used 'man ssh' I couldn't make heads or tails of the stuff.  Now that I saw the port listed the way you wrote, it pops right out when I look at it.

---

### Post by Dr Small on 2008-02-08
Well, I have never restricted it for certain users, but my guess would be, that it either needs to be:
```
AllowUser user1 user2
```

Or:
```
AllowUser user1, user2
```

And I would play around with those different settings.

Dr Small

---

### Post by bodhi.zazen on 2008-02-08
The syntax is

> AllowUsers user1 user2

(at least that works on my end)

Hi Dr Small :twisted:

---

### Post by Dr Small on 2008-02-08
> **bodhi.zazen said:**
> The syntax is



(at least that works on my end)

Hi Dr Small :twisted:
Hi, how ya doin' ? :D
You should know that SSH is my favorite topic :)
I don't know why, but ever since I discovered it, it never ceases to facinate me!!

Dr Small

---

