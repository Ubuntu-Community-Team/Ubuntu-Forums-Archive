---
title: "Apt-get Doesnt Connect"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by 09adi09 on 2007-01-14
When I do,
sudo apt-get update
I get,
[I]E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/I]

Is this because i am behind a proxy server?What shd i do to bypass it? Any help would be brilliant...

---

### Post by mvaniersel on 2007-01-14
It's probably because you have synaptic running, or another program that relies on apt. Only one program at a time may manage  packages.

---

### Post by 09adi09 on 2007-01-14
Surprising,.its working all of a sudden now.I tried earlier(without Synaptic on) then it kept saying the reposotaries are unreachable.Wierd!

I want to do a purely command line installation of mplayer.how do I do that..Thanks for the help!

---

### Post by Sef on 2007-01-14
> I want to do a purely command line installation of mplayer.how do I do that.

```
sudo aptitude install name_of_program
```

---

### Post by 09adi09 on 2007-01-14
I also want to point out that sometime back i edited the 
/etc/apt/sources.list file and edited the line there to,

"Acquire::http::Proxy "proxyaddresss : proxyport";"

Am doing the mplayer installation now..
Thanks for the help!

---

### Post by 09adi09 on 2007-01-14
shouldn't it be

sudo apt-get install mplayer 
?

---

### Post by bapoumba on 2007-01-14
@ 09adi09 : just to make sure, this is the /etc/apt/apt.conf file you are talking about, right ?

---

### Post by 09adi09 on 2007-01-14
Oh I am very sorry..

yes it is the 
**/etc/apt/apt.conf** file

---

### Post by bapoumba on 2007-01-14
Okay, thanks ;)
(so that nobody gets confused and put this line in sources.list file).

---

