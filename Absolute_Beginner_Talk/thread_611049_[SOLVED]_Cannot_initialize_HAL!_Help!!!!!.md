---
title: "[SOLVED] Cannot initialize HAL! Help!!!!!"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by DaraJava on 2007-11-12
"Cannot initialize HAL!" (Exclamation mark intentional)

Don't know why this happens.Could be that my brother was messing around aimlessly with my internet settings last night so it could be that. I was also messing with important things last night in line with the page at [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed") . Could be one of those things or it could be something else. 

Anyway the problem is that I now cannot go on the internet at all and the wi-fi light on my laptop is off *sometimes* but not all the time. I don't know. :confused:

When I try to change my settings on *Network Settings* it hangs and eventually becomes unresponsive. Again, I'm :confused:.

Please someone help me I kinda have a time limit because this isn't my laptop and I only have it for an hour. Thanks in advance,

DaraJava

---

### Post by TadH on 2007-11-12
mnie comes up with that error too what is this HAL lol because im using my wireless -,.-

---

### Post by DaraJava on 2007-11-12
> mnie comes up with that error too what is this HAL lol because im using my wireless -,.-

Does your internet work?

---

### Post by skymera on 2007-11-12
are you on gutsy?
are you concurrent booting?

---

### Post by TadH on 2007-11-12
yeah im using my wireless now

---

### Post by DaraJava on 2007-11-12
Gutsy and only Gutsy.

---

### Post by skymera on 2007-11-12
is concurrent booting on?

gedit /etc/init.d/rc

[no sudo]

---

### Post by DaraJava on 2007-11-12
I have to put sudo in front of those commands if thats what you mean. I thought concurrent booting meant dual booting... oops :lolflag:

---

### Post by skymera on 2007-11-12
yeah,

idoes the file say: (i fdidnt say sudo as you dont need to make any ammendments)

CONCURRENCY = shell

?

---

### Post by Sailo on 2007-11-13
Thx Skymera!  I was having the same problem with my HAL.  I changed my settings back to 'none' and that fixed the problem.

---

### Post by skymera on 2007-11-13
you cam have cocurrency shell with no HAL error :)

i figured this little trick by playing around
ok

```


sudo nautilus /etc/rc2.d 
```

change s12hal to s13hal

tada!

concurrency and no error, genius.

the error was cuased by HAL starting efore DBUS.

this makes HAL start after

---

### Post by sports fan Matt on 2007-11-13
I just had a similar experience..computer booted up fine (ubuntu gutsy) but the internet didnt work.  I just decided to reformat..(i know pretty stupid i think) but what exactly is Hal? What does it do? i've never figured it out...

---

### Post by DaraJava on 2007-11-13
You're a genius skymera. Thanks! I fixed it by changing "shell" to "none" in /etc/init.d/rc. But why would I want to have "shell" instead of "none"? I dont know what thay do. Would having shell on be of any benefit?

---

### Post by SRitter1117 on 2007-11-13
> **skymera said:**
> you cam have cocurrency shell with no HAL error :)

i figured this little trick by playing around
ok

```


sudo nautilus /etc/rc2.d 
```

change s12hal to s13hal

tada!

concurrency and no error, genius.

the error was cuased by HAL starting efore DBUS.

this makes HAL start after

Wow thanks a lot for this post, it just solved this issue for me without reverting to concucurrency none!

---

### Post by SRitter1117 on 2007-11-13
> **DaraJava said:**
> You're a genius skymera. Thanks! I fixed it by changing "shell" to "none" in /etc/init.d/rc. But why would I want to have "shell" instead of "none"? I dont know what thay do. Would having shell on be of any benefit?


Having CONCURRENCY=shell allows ubuntu to use hyperthreading or dual-core processors.

---

### Post by DaraJava on 2007-11-14
Oh I see, Thanks

---

### Post by trtlrider on 2008-01-21
well, I'm haveing this problem since last update of Hardy. it kills my network as well. looks like it does not recognize network hardware. network restart ignore all cards and return OK.

---

