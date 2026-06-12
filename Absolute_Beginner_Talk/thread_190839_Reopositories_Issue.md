---
title: "Reopositories Issue"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by xx75 on 2006-06-06
Hello community member

I have tried to update my repositories as per-

*[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)[/COLOR]*

but am having trouble with the following -

```
gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
gpg --export --armor 33BAC1B3 | sudo apt-key add -
```

When I do this,  i get the following message-

[COLOR="Blue"]gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error[/COLOR]

Have I missed something?

Any help is appreciated.

Thanks
xx75

---

### Post by richbarna on 2006-06-06
In your repositories, comment out (add ## at the beginning) of the cypherpunk repo.
I think that's the one that is asking for the PGP key.
Or in synaptic uncheck it.

---

### Post by xx75 on 2006-06-06
Thanks for your response richbana -

> In your repositories, comment out (add ## at the beginning) of the cypherpunk repo.
I think that's the one that is asking for the PGP key.


It is indeed, but my intentions were to use cypherfunk to install some multimedia packages.

I think it may be an issue with my settings, I just tried a similar command to obtain the Automatix repo and once again I got the same response.

Unfortunately, due to my lack of linux knowledge, I don't even know where to start.

Could it be because i am firewalled?
I didn't think this would be a problem because I don't have any troubles retrieving anything else.

Any suggestions?

Cheers
xx75

---

### Post by catlett on 2006-06-06
[QUOTE=xx75]Hello community member

I have tried to update my repositories as per-

*[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)[/COLOR]*

but am having trouble with the following -

```
gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
gpg --export --armor 33BAC1B3 | sudo apt-key add -
```

When I do this,  i get the following message-

[COLOR="Blue"]gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error[/COLOR]

Have I missed something?

Any help is appreciated.

Thanks
xx75[/QUOTE]
How many times have you tried to enter the key? The server is timing out which might not be a big deal unless this has been happening for a couple of days. If you only tried once or twice I would wait a while and see if their server was down, being serviced or just overloaded.

---

### Post by xx75 on 2006-06-06
Hi catlett

Yes I have tried it quite a few times now, starting last night at around 10.30 - 11.00pm (it is now 10.29am in Sydney Australia)

Thanks for your support.
xx75

*edit*

And wouldn't you know it, it has just started working and made an absolute arse of me!

Thanks everyone for your help, hopefully I didn't waste too much of your time.

Seeya
xx75

---

### Post by catlett on 2006-06-06
[QUOTE=xx75]Hi catlett

Yes I have tried it quite a few times now, starting last night at around 10.30 - 11.00pm (it is now 10.29am in Sydney Australia)

Thanks for your support.
xx75

*edit*

And wouldn't you know it, it has just started working and made an absolute arse of me!

Thanks everyone for your help, hopefully I didn't waste too much of your time.

Seeya
xx75[/QUOTE]
Having a problem solved is nothing to be ashamed of.:-D  If the server was not responding for more than half a day I would have thought something wasn't right on my end. And if I just installed a new OS I would have definately thought there was something wrong with my configuration i.e. firewall, etc.
Glad your problem is solved. See you around the forum.

---

### Post by uzi09 on 2006-06-06
although this isn't really a solution for your repo problem, as far as media goes, try BUMPS:
[http://www.ubuntuforums.org/showthre...ighlight=bumps](http://www.ubuntuforums.org/showthre...ighlight=bumps)
(that thread is the most up-to-date, but click on the "introductory thread" link to learn what it's all about -- hmm, more reading for the techie-bookworm )

---

