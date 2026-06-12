---
title: "help needed for lynx"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by say2sky on 2007-10-22
```
 
$ lynx http://www.google.com

Looking up :8080
Unable to locate remote host :8080.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://www.google.com/

```

I have checked /etc/lynx.cfg and uncomment no_proxy but nothing change.  Anyone can tell me why and how to configure it.  Thanks in advance.

---

### Post by dmizer on 2007-10-22
that's really bizarre.

try looking through /etc/lynx.cfg for an uncommented line which says something about port 8080

you could also try specifying port 80:
```
lynx http://www.google.com:80
```

---

### Post by say2sky on 2007-10-22
> **dmizer said:**
> that's really bizarre.

try looking through /etc/lynx.cfg for an uncommented line which says something about port 8080

you could also try specifying port 80:
```
lynx http://www.google.com:80
```

I have try and gotten the same:(

```

lynx http://www.google.com:80

Looking up :8080
Unable to locate remote host :8080.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://www.google.com/


```

---

### Post by say2sky on 2007-10-22
and I cannot find any port 8080 info in /etc/lynx.cfg

---

### Post by shad0w_walker on 2007-10-22
It sounds stupid, but have you tried with out the http:// part of the URL?

---

### Post by dmizer on 2007-10-22
is there something in /etc/hosts by chance?  do you get the same response with all addresses?  what's [http://ubuntuforums.org](http://ubuntuforums.org) do for example?

---

### Post by say2sky on 2007-10-22
I indeed

```

lynx google.com

Looking up google.com first
Looking up :8080
Unable to locate remote host :8080.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://google.com/


```
$ lynx google.com:80

Looking up google.com first
Looking up :8080
Unable to locate remote host :8080.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile [http://google.com/](http://google.com/)



---

### Post by dmizer on 2007-10-22
wait ... can you even ping google?

```
ping www.google.com
```
and what's the output of:
```
ifconfig
```

---

### Post by say2sky on 2007-10-22
I can ping 
```
ping www.google.com
PING google.navigation.opendns.com (208.67.219.230) 56(84) bytes of data.
64 bytes from google.navigation.opendns.com (208.67.219.230): icmp_seq=1 ttl=53 time=211 ms
64 bytes from google.navigation.opendns.com (208.67.219.230): icmp_seq=2 ttl=53 time=210 ms

--- google.navigation.opendns.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2000ms
rtt min/avg/max/mdev = 210.859/210.942/211.025/0.083 ms

```

```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:61.173.45.168  P-t-P:218.1.0.246  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:20918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:16067759 (15.3 MB)  TX bytes:2307117 (2.2 MB)


```

---

### Post by say2sky on 2007-10-22
I think problem is related with xterm. I use gnome. but why?

when I use console I can 
lynx [www.google.com](www.google.com)

---

### Post by dmizer on 2007-10-22
could be a bug ... what release are you using?

edit:
lynx acts very strange for me in xterm as well.  it popped up with cookie text in abiword and never opened the page ... lol.  it did try though.

---

### Post by oilchangeguy on 2007-10-22
> **say2sky said:**
> ```
 
$ lynx http://www.google.com

Looking up :8080
Unable to locate remote host :8080.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://www.google.com/

```

I have checked /etc/lynx.cfg and uncomment no_proxy but nothing change.  Anyone can tell me why and how to configure it.  Thanks in advance.

you might try spelling lynx correctly, it's linux, not lynx.

---

### Post by say2sky on 2007-10-22
Now I use gutsy and I also try dapper and both same.

---

### Post by dmizer on 2007-10-22
> **oilchangeguy said:**
> you might try spelling lynx correctly, it's linux, not lynx.
say2sky is spelling it just fine.  please see: [http://en.wikipedia.org/wiki/Lynx_(web_browser](http://en.wikipedia.org/wiki/Lynx_(web_browser))

> **say2sky said:**
> Now I use gutsy and I also try dapper and both same.
i get the same response in dapper.  i don't have a gutsy machine available to check but i don't get a failure like yours in dapper.

my issue appears to be with cookie handling.  humm.  what /does/ happen if you try lynx [http://ubuntuforums.org](http://ubuntuforums.org)

it may be that google is no longer lynx capable.  i get a "start file could not be found" in console too.

---

### Post by say2sky on 2007-10-22
I also same
```

$ lynx http://ubuntuforums.org

Looking up :8080
Unable to locate remote host :8080.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://ubuntuforums.org/


```

---

### Post by say2sky on 2007-10-22
The most strange thing is where the port 8080 come from? I cannot find it from lynx.cfg file

---

### Post by dmizer on 2007-10-22
it's not strange ... look at the error closely.

first it tries the page on the normal http port (80) and fails (but makes no mention of the port because it is assumed).
next it tries the standard alternate http port 8080 and fails.
then it exits with the most recent error which is on port 8080.

this is expected behavior on sites that do not have lynx capable viewing.  what IS strange is that google isn't lynx capable.

i /do/ know that [http://ubuntuforums.org](http://ubuntuforums.org) is lynx capable though ... don't know why that's not working for you.  it /does/ work for me in xterm as well as console.

---

### Post by say2sky on 2007-10-22
You are right. lynx indeed first try quested url then use port 8080.

For the lynx compatible I try many different url including yahoo, msn and live.com.  All the same error info. 

In fact I try to use lynx to update dyndns so now I need to find other way
```

lynx -auth=xxx:xxx -source "http://members.dyndns.org:8245/nic/update?system=

```

---

### Post by chili555 on 2007-10-22
My Gutsy machine reaches Google just fine with lynx. And with xterm or otherwise. I've had no trouble reaching MSN or Yahoo. Any site I have ever tried I have reached with lynx. If there is any site that is incompatible with lynx, I would be shocked. I remain anxious to be dis-proven.

---

### Post by say2sky on 2007-10-22
It's so strange that you can but I cannot. I have made all possible try I can think out.  But still only "lynx: Can't access startfile http://google.com/". 

Thanks a lot for your help and I indeed get much info about lynx. :confused:

---

### Post by chili555 on 2007-10-22
In case it may help you, I attach my lynx.cfg which is, as far as I can tell, untouched since installation.

---

### Post by say2sky on 2007-10-22
I have used diff to compare your lynx.txt and my /etc/lynx.cfg and It's all the same. 

I even have installed the hardy version and still cannot use lynx. Oh My GOD what happen?

```
say2sky@hardy:~/Desktop$ lynx google.com

Looking up google.com first
Looking up :8080
Unable to locate remote host :8080.
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://google.com/

```

---

### Post by say2sky on 2007-10-22
I also used your lynx.txt to replace the original /etc/lynx.cfg and no improvement.

I also changed language system back to English and no good again.

---

### Post by wuzzerd on 2007-10-23
I had this problem last year and it has gone away.  At the time I could enter a url after I started lynx and it worked.  

You might try reinstalling lynx.

---

### Post by say2sky on 2007-10-23
> **wuzzerd said:**
> I had this problem last year and it has gone away.  At the time I could enter a url after I started lynx and it worked.  

You might try reinstalling lynx.

no after reinstalled lynx and I perhaps need to reinstall a clean system and try again.

---

### Post by say2sky on 2007-10-23
Thanks all friends for your help. Your responses let me believe that this problem is related with some packages I installed or my personal configuration.

Now after I create a new username and use this clean configuration, lynx works so the problem is indeed just related with my old personal configure. :guitar:

---

### Post by leonzelig on 2008-05-31
Ok, first of all, I am really sorry for digging up an old thread, but I just had the same problem here, and a google search for the exact error message showed only this page. For that reason, I thought it would be a good idea to post here the way I found to work around this problem.

For some bizarre reason, when using gnome-terminal, the http_proxy variable was being set to "http://:8080". Until now I have found no reasons as to why this was happening, since when using console things worked very well.

My workaround was to reset this variable by insert the following lines in $HOME/.bashrc:
```
http_proxy=""
export http_proxy
```

After that I was able to use lynx normally.

I hope I could help someone, and, again, I am also sorry for posting in such an old thread, but I think it was reasonable, provided this is where google will redirect anyone who searches for the exact error message.

---

