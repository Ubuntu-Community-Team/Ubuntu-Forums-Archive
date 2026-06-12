---
title: "How to make synaptic download faster?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by dansei on 2007-04-09
Ubuntu 6.10

I found the synaptic download packages in only 2 threads, one thread is from [http://security.ubuntu.com](http://security.ubuntu.com), and the other one is from [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com). 

Is there any way to let synaptic download in many threads more than only 2? It's too slow! 

Thanks 
Lenik

---

### Post by sam81 on 2007-04-09
try substituting the country code in your /etc/apt/sources.list, for example the following would be the country code for Italy

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

substitute it with your country code. Note that that line refers to edgy, you need to change that if you're using another version

---

### Post by zvacet on 2007-04-09
Do you have all repositories open?To open them system>administration>software properties

Chek your source list.It should look like this(just example)
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

not
#deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

To edit source list
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by dansei on 2007-04-09
I checked the source.list file, several lines with 'universe' are commented out, while 'restricted' are not, should I remove '#' from those 'universe' lines? or is there more URLs I can add to the list file? 

And, there is a new problem, I can't type the tilde ("?" can't type here) character, when I pressed the tilde key, whatever I hold shift or not, it just be "`"... My keyboard is standard 105-key, and the input method is 'default', scim isn't started.

---

### Post by seshomaru samma on 2007-04-09
you should remove the # before 'universe'
can you post your sources.list here? 
where in the world are you? china?


i would start a new thread about the keyboard problem

---

### Post by dansei on 2007-04-09
Yes, china is.
Now things go worse, not only tilde(?) can't be typed, but the letter "eks" (uvw?yz), can't be typed, too.

```

lenik@cls-3500:~$ sudo cat /etc/apt/sources.list |grep deb
deb http://cn.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://cn.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://cn.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://cn.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
# deb http://cn.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://cn.archive.ubuntu.com/ubuntu/ edgy universe
# deb http://cn.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
lenik@cls-3500:~$ 

```

---

### Post by dansei on 2007-04-09
I commented out those 'universe' lines, now it seems a little faster, but still very slow. 
"Download rate:43kb/s"

Should I add more links?
Thanks

---

### Post by seshomaru samma on 2007-04-09
try replacing your sources list with mine:
```
deb http://ubuntu.cn99.com/ubuntu/ dapper main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ dapper-updates main restricted universe multi verse
deb http://ubuntu.cn99.com/ubuntu/ dapper-security main restricted universe mult iverse
deb http://ubuntu.cn99.com/ubuntu/ dapper-backports main restricted universe mul tiverse
deb http://ubuntu.cn99.com/ubuntu-cn/ dapper main restricted universe multiverse
```

---

### Post by christhemonkey on 2007-04-09
But obviously if u do what seshomaru samma says, change all the dapper references to edgy!!

---

### Post by dansei on 2007-04-09
Thanks to all, 

After I replaced to your list (with dapper/edgy replaced), the updater says "Your system is up-to-date"... 
So I think maybe this server doesn't contain as much packages ..

---

### Post by seshomaru samma on 2007-04-09
thanks christhemonkey :oops: 

this server is fast but the updates are different , it usually silent for about a week and then suddenly have tons of updates. i'd rather have fast apt then the latest updates but its your decision

---

