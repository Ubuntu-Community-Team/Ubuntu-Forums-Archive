---
title: "How do you speed up ubuntu 7.10?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by bluescreenofdeath on 2008-03-08
I just installed ubuntu 7.10 installed the updates and it's still very slow. It's performance is bad. And the internet is slow. 

  Is there any way that to fix these problems. Please provide step by step instruction.

I have a 3ghz 800fsb cpu and 2gb of 3200DDR ram installed. I would think that's not the problem.

---

### Post by HermanAB on 2008-03-08
A slow internet experience is usually due to a lame DNS in /etc/resolv.conf.

So, edit /etc/resolv.conf and swap the name servers around - put the bottom one at the top and see if it helps.

If you have another computer, eg. Windows, run 'ipconfig /all' and copy the DNS addresses.

Cheers,

Herman

---

### Post by igknighted on 2008-03-08
> **bluescreenofdeath said:**
> I just installed ubuntu 7.10 installed the updates and it's still very slow. It's performance is bad. And the internet is slow. 

  Is there any way that to fix these problems. Please provide step by step instruction.

I have a 3ghz 800fsb cpu and 2gb of 3200DDR ram installed. I would think that's not the problem.

The most likely suspect is the graphics drivers.  Also, for the internet slowness, try disabling ipv6.  Especially in Firefox, this can cause massive headaches.  There are a few settings I tweak in about:config in firefox that make a world of difference... the ipv6, I change proxy.pipelining to true, and a couple others... try searching the forums for firefox tweaks, I know they are posted in various places.

---

### Post by handy on 2008-03-08
> **bluescreenofdeath said:**
> I just installed ubuntu 7.10 installed the updates and it's still very slow. It's performance is bad. And the internet is slow. 

  Is there any way that to fix these problems. Please provide step by step instruction.

I have a 3ghz 800fsb cpu and 2gb of 3200DDR ram installed. I would think that's not the problem.

You may find some help on [***_this how-to_***]("http://ubuntuforums.org/showthread.php?t=282034").

---

### Post by praveenpious on 2008-03-08
^^ Thanks for the link :)

---

