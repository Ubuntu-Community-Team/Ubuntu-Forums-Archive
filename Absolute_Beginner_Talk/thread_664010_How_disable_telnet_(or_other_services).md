---
title: "How disable telnet (or other services)?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2008-01-10
There are other similar threads here, but the answers are totally simplistic and un helpful.

I want for sure to disable telnet on my Gutsy 7.10 machine, as I have gotten ssh to work and can even get to a login from my vista laptop using putty.  So I want to disable the insecure telnet completely.

All of my web research has been fruitless--but it seems like such a basic question, I must be using poor search terms.  So my specific question is:

How do I disable telnet? (specific steps please)

What other services should I disable to have a very secure machine?  And HOW if the steps are different from disabling telnet.

Thanks.

---

### Post by limac on 2008-01-10
*deleted post*

---

### Post by PeterJS on 2008-01-10
I assume that you specifically enabled telnet? You could uninstall the telnet server that you're using.

If you didn't specifically enable telent then you don't have to worry about disabling as it wasn't enabled in the first place.

---

### Post by movrshakr on 2008-01-10
What file do I put that command in?

ignore...above was a response to the deleted post from the highly educated and classy limac.

 ---movrshakr

---

### Post by yabbadabbadont on 2008-01-10
> **limac said:**
> *deleted post*

Too late buddy.  I already reported your original post.

---

### Post by movrshakr on 2008-01-10
hmmm...somehow I thought that the response would be something like...

"all the enabled services are in _____ just put a # in front of the ones you don't want to run.  And you should turn off a,b,c....

---

### Post by PeterJS on 2008-01-10
There's the gnome service admin tool. System > Administration > Services. If you really wanted to get down and dirty in the terminal you could use update-rc.d.

---

### Post by movrshakr on 2008-01-10
ummm...ok i will look at the gui, but if I wanted to use the command line, what would the full command be to disable it--more than just "update-rc.d" obviously?

IOW, specifics?

---

### Post by PeterJS on 2008-01-10
Geeze making me think here.
```

sudo update-rc.d *service_name* remove

```
or to add a service to the default boot
```

sudo update-rc.d *service_name* defaults

```
If you read the man page there are other options to give you finer control over how to add services.

The service name will be the name of one of the scripts in /etc/init.d/ now which script you're looking for I leave as an exercise to the reader.

---

### Post by movrshakr on 2008-01-10
I don't think telnet is started by a script, is it.  Aren't all of the tcp.ip services embedded in the stack somehow?

---

### Post by PeterJS on 2008-01-10
Nope. The tcp ip stack does exactly what it's told to do, nothing more, some times less if wireless is involved. Ubuntu defaults to having no network facing services on the default install. So unless you intentionally installed a telnet server, which would need an init script in /etc/init.d/ to start it at boot, you don't have a telnet server on your machine. And if you do have a telent server there are several options to disable it, from preventing it to run at boot to just plain un-installing it.

Are you confusing the telent client that is used to connect out, with a telnet server that would recieve the aforementioned connections.

---

### Post by movrshakr on 2008-01-10
I did install telnet server (and client I think) for about a week.  Then today I put ssh/putty on the ubuntu/vista machines and got it working.

Then I got to thinking I should disable the telnet server.  Thus this question here.

Also, I looked in init.d and there is no 'telnet' script there.

---

### Post by bodhi.zazen on 2008-01-10
[http://sysadmingear.blogspot.com/2007/10/how-to-disable-telnet.html](http://sysadmingear.blogspot.com/2007/10/how-to-disable-telnet.html)

---

### Post by PeterJS on 2008-01-10
All of the telent servers I found in the repository(inetutils-telnetd, krb5-telnetd, and telnetd) have telentd in the name so if you search for that and go on an un-installing spree that should do. Also if you right click on the installed packages one of the options under properties is to view the installed files. From there you could get the name of the script in /etc/init.d/ if you wanted to leave it install but have the service disabled.

Gah! xinetd, who thought that was a good idea.

---

### Post by movrshakr on 2008-01-10
OK.  I will go work on that a bit.  I guess doing an uninstall is the right answer.  From the link above, it said:
------------------------------------
Disbale Telenet

Login as root to your server, now:

Edit /etc/xinetd.d/telnet
# nano /etc/xinetd.d/telnet

Search for: "disable = no" (you can use Ctrl+W) ,  Change it to: disable = yes

Save and Exit

Restart xinted
# /etc/rc.d/init.d/xinetd restart
---------------------------------------
Since that doesn't match ubuntu, I tried to translate but it still seemed to want to edit a 'telnet' script, which again, I do not seem to have.  A bit puzzling, because I did hit the telnet server several times, so it was running before.  Maybe the ssh install took it out.  I just don't know.

---

### Post by PeterJS on 2008-01-10
That's probably for the best. Xinetd was a decent idea, implemented terribly. What it was, instead of running each individual server as it's own process, it had xinetd listen for requests in their place and then start them up only when needed. The idea was to save memory by only having things run when needed, the fact of the matter was it was a configuration nightmare that broke more often than not if you tried to do anything complicated with it, and lead to all sorts of irregularites like this.

---

### Post by movrshakr on 2008-01-10
OK, the synaptics package manager shows I have the telnet client installed but not the server.  So, I am good to go as far as my desire to disable telnet is concerned.

I'm sure I did have it in, as I said, because I telnetted into the machine before installing the ssh.

I consider my problem gone and am done here; thanks to all for the inputs and leads.

---

