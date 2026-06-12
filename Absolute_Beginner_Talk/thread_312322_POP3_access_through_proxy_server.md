---
title: "POP3 access through proxy server"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-12-04
Hello all,

I have been having trouble accessing my mail through a proxy server and I asked here: [http://www.ubuntuforums.org/showthread.php?t=310503](http://www.ubuntuforums.org/showthread.php?t=310503)

After a little research, I find out that POP3 and Proxy servers don't go well together. however, our systems administrator installed a program on the windows computers that allows them to access POP accounts through the proxy. 

Name just slipped out of my head...AARRGGHH!!! right at the tip of my tongue...

Anyways, my question is, is there a similar program I can use with Ubuntu because I really need to get my email down to my computer... any other solutions?

Thanks in advance, and sorry for posting in two forums :(

David K

---

### Post by wyldstryker on 2006-12-04
Have you tried to set up the proxy for the system as opposed to setting up the proxy for each program? 

System > Preferences > Network Proxy

And have you verified your server and port numbers with your IT/Admin?
I know it's not much , but it's all I can think of without more coffee. :-k

---

### Post by dckirba on 2006-12-04
Hi Wyld,

Yes I have applied system-wide proxy settings and verified ports with system admin. Most of my internet related programs work well. I have problems with email clients and FTP clients.

All else works fine such as browsing. Actually, come to think of it, chat doesn't work too well since the proxy server. Guess it's only browsing that works.

Bummer. Anyways, if you need some coffee I'd be happy to offer you a cup, we have some pretty great coffee in Ethiopia!

Cheers,
David K

Edit: The name of the software that was used on the windows machines is FreeCap. Apparently that allows them to access POP3 through the proxy server. An equivalent if available is what I need right now.

Edit 2: or socksCap equivalent...?

---

### Post by wyldstryker on 2006-12-04
Just had another thought.  If the proxy server that you're using is ISA server, then you might be able to use the IP of the proxy server as your gateway.  :-k

---

### Post by dckirba on 2006-12-04
Hi Wyld,

I'm a bit of a newbie at networking. Not sure what ISA is, could you explain a bit?

Am i wrong in assuming that I need something like SockCap? Not too sure what it does actually:)

Cheers,
David K

---

### Post by dckirba on 2006-12-04
Wow! I owe you coffee man! I changed the gateway to the IP address of the proxy and it seems to be actually connecting!

Let me check and let you know in a few minutes.

Thanks mate!

David K

---

### Post by dckirba on 2006-12-04
Bleah! :( 

Well, it appears to be doing something, but nothing happens... no error messages, just a spinning ball and a moving line...

I kinda have to head home now, end of work for today, but I'd appreciate it if you'll let me know if you think of anything else.

Cheers,
David K

Edit: received error after a long time ```
Unable to connect to POP server
```

---

### Post by wyldstryker on 2006-12-04
hmm... :-k 

Did you remember to kill all proxy settings?  If even one is still active it will try to route through it.  


> **dckirba said:**
> Hi Wyld,

I'm a bit of a newbie at networking. Not sure what ISA is, could you explain a bit?

ISA is M$'s version of a proxy server... Me and it have a history of battling  with the Apple based machines at my place of work.  

As for sockcap, it looks like a proxy client.  Basicly forcing everything through it's network settings.

---

### Post by dckirba on 2006-12-05
Hiyya Wyld,

crazy day at work and just had time to sit down and play for a bit :)

By kill all proxy settings do you mean my thunderbird proxy settings?

So I deselect all of them and try again?

Sorry for all the questions, it's only since I've started using linux/ubuntu that I've actually started learning a lot :)

Thanks for your time,
Cheers,
David K

---

### Post by dckirba on 2006-12-06
Heyya Wyld,

I tried disabling all proxy settings in Thunderbird and that didn't work. Still not sure if that's what you meany by kill all proxy settings?

Cheers,
David K

---

### Post by wyldstryker on 2006-12-06
I meant the proxy settings in not only Thunderbird, but also if you set up the system proxy  (system > pref> network proxy)  you should also clear that out as well. :-k

---

