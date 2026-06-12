---
title: "SSH tunneling to enable Jabber"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Repabil on 2008-01-29
Hello,

I'm trying to ssh tunnel through my server at home to enable jabber from school.

**Situation**
[LIST]
[*]I can't connect to jabber directly from school
[*]I've got a server at home which I can ssh into from school (eg ```
ssh server-ip
``` works)
[/LIST]

So I executed:
```
sudo ssh -L 5223:localhost:5223 server-ip
```
and set gossip to connect to localhost on port 5223. *But* it fails to connect. What's wrong?

---

### Post by Het Irv on 2008-01-29
Let me make sure I know how this works.  You connect to your server though SSH, then on the server you connect to jabber.  All of the information from jabber is going through SSH correct?

Is the connection between your computer and the server touching port 5223 at all?  If so it might be blocked on a router somewhere.

If I am wrong please tell me.

---

### Post by smurphy_it on 2008-01-29
Are you running a proxy server at home ?  From what I can gather, the line you used **sudo ssh -L 5223:localhost:5223 server-ip** is in case you are running a proxy server.  If you aren't running a proxy server, the command should be **ssh -D 5223 server-ip** and I don't believe you need the *sudo* prepended to your command lline.


If jabber is using port 5223, you might need to force it on your home's end to use another port, like say 443.....

Not an expert by any means here.

---

### Post by Repabil on 2008-01-29
I'm not using a proxy. Can't get it to work with suggested way of using -D either.

---

### Post by Repabil on 2008-01-29
I also tried the following [technique]("http://new.linuxfocus.org/English/December2006/article394.html") without success:```
ssh -L 1234:localhost:4242 -R 4242:jabber.org:5222 isiarlon.hopto.org
```

---

### Post by Het Irv on 2008-01-29
Do you have any way of telling where in the process you are getting stopped?  It seems to be that jabber is not working somewhere on the stream.  I am not familliar with jabber, do you need a program for it to work?

---

### Post by Repabil on 2008-01-29
> **Het Irv said:**
> Do you have any way of telling where in the process you are getting stopped?  It seems to be that jabber is not working somewhere on the stream.Dunno. That's what I'd like to do to troubleshoot.> **Het Irv said:**
> I am not familliar with jabber, do you need a program for it to work?I'm using the jabber client [Gossip]("http://packages.ubuntu.com/gutsy/gnome/gossip").

---

### Post by Het Irv on 2008-01-29
Where is the client located? I assume that you have the client on your Computer and the server is just doing a version of port forwarding.  Does your school have a proxy server?  Many time they take the form of a web filter such as Websence or St.Bernard.  

But then again this doesn't matter because SSH itself works just not the jabber going though it.
Your school may have a packet filtering system in place.  That is the only thing I can think of.  Many IM clients allow viruses through because of the way they work.  Therefore some places go to great lengths to block them.

That doesn't mean I am right.  As you can see I don't know that much about SSH.

---

### Post by bodhi.zazen on 2008-01-29
Just a friendly reminder, cracking OPN (Other People's Networks ie school / office / any network where you are not the sys admin) is NOT SUPPORTED here.

So, before you do this kind of thing, OBTAIN PERMISSION from your sys admin. Failure to do so can result in harsh consequences.

---

### Post by zekica on 2008-01-29
> **Repabil said:**
> So I executed:
```
sudo ssh -L 5223:localhost:5223 server-ip
```
and set gossip to connect to localhost on port 5223. *But* it fails to connect. What's wrong?
I think you have to type:
```
sudo ssh -L 5223:jabber_server_hostname:5223 server-ip
``` to setup forwarding to **jabber_server_hostname** instead of trying to connect to localhost:5223 (localhost of your home server).

You can also try:
```
sudo ssh -f -L 5223:jabber_server_hostname:5223 server-ip -N
```

---

