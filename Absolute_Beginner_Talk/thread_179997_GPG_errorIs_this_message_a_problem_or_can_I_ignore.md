---
title: "GPG error:Is this message a problem or can I ignore??"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by wishy77 on 2006-05-21
I ran apt-get update several times and keep getting the following error message:
"W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088"

I am seeking help whether this can be left without problems, or assistance on how to get rid of error/offending file...
Cheers
Wishy

---

### Post by rdd on 2006-05-21
One answer here [http://lists.debian.org/debian-user/2006/04/msg00033.html]("http://lists.debian.org/debian-user/2006/04/msg00033.html") was that you need the package 'debian-archive-keyring'. 
Since we are looking at an ubuntu-archive try installing the package 'ubuntu-keyring '. 

Maybe there is a special one for kubuntu too. Try searching in Synaptic for keyring. 

Hope it helps.

---

### Post by wishy77 on 2006-05-21
Thanks for info..trying solutions now.
Cheers
Wishy

---

### Post by macdo on 2006-05-21
What rdd says.

In the meantime, kubuntu.org is probably not going to give you any malicious packages, so you can install stuff, IMO.

Of course, I'm not responsible for your PC, am I?

---

