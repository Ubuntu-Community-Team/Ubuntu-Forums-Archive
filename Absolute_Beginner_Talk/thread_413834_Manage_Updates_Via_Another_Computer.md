---
title: "Manage Updates Via Another Computer"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by faithsnathan on 2007-04-19
Hello, all!

I've done some researching around but can't find anything related to this (I'm not really even sure it's possible, yet).

I recently purchased a laptop for myself and will be giving my mom my old desktop.  She lives about 5 hours away, and she will be an absolute noob with Ubuntu (even more so than me!).  I was wondering if there is a way that I could connect with my old desktop - her computer - and manage this from where I am:  updates, fixing errors, etc.

I still have the computer here, so if there's anything I would need to do on that computer before I give it to her in a couple of weeks, I still have time.

Thanks for your time!  :)

FYI:  It is a 750Mhz, 30GB, 256MB RAM desktop computer currently running Edgy, though it will run Feisty as soon as I've got it going on my laptop.

---

### Post by Seisen on 2007-04-19
You could use SSH which would be more secure than anything else.

---

### Post by lamalex on 2007-04-19
set her up so that you can connect into her via ssh (make sure you configure a custom port and close 22). then when you take her back, set her up with dynamic dns (dyndns.org) so you can ssh into her box and do sudo apt-get upgrades and any command line thing you want. you can ssh with X but there's a security risk. you could also do vnc, she might get a kick our of that, my grandmother sure does.

---

### Post by faithsnathan on 2007-04-19
> **Iamalex said:**
> set her up so that you can connect into her via ssh (make sure you configure a custom port and close 22). then when you take her back, set her up with dynamic dns (dyndns.org) so you can ssh into her box and do sudo apt-get upgrades and any command line thing you want. you can ssh with X but there's a security risk. you could also do vnc, she might get a kick our of that, my grandmother sure does.

Oh, crap!  What am I getting myself into?  Well, I better start searching ([ubuntuforums]("http://ubuntuforums.org")) and [Googling ]("http://www.google.com/")to find out what all of that means.  Thank you for your quick responses to my question!  :popcorn:

---

### Post by faithsnathan on 2007-04-19
[COLOR=DarkRed]Thank you [Wikipedia]("http://en.wikipedia.org/wiki/Secure_Shell").  SSH allows establishing a [secure channel]("http://en.wikipedia.org/wiki/Secure_channel") between a local and a [remote computer]("http://en.wikipedia.org/wiki/Computer_network").  I'll give that a look and see what I can come up with.  Also, I hope that this thread will help anyone else in a similar situation.[/COLOR]

---

### Post by Seisen on 2007-04-19
SSH isn't that hard to set up. This should help you out.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#SSH_Server]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#SSH_Server")

---

