---
title: "is there a modem log?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by new_foo on 2006-10-12
I am having modem problems now, and I would like to try and diagnose it.  If there is a log that shows the modem connection, that would help me greatly. In kubuntu, there was a log that  would show with that dialer, is there one with ubuntu?

I tried looking in the log directory.  There is a ppp.error file, but it's empty.

My modem used to work, but I haven't dialed in with linux for over a month and last night I reinstalled everything because I felt I may have had a spyware on my windows partition from a dvd I put in my machine (it was acting funny and my zone alarm mentioned about a spyware.)  Anyway, now when I try to dial, it gets to the handshake then goes quiet but I don't think it ever establishes a ppp connection.

Thanks for the help.

---

### Post by blendmaster on 2006-10-12
I think you can install kppp in Ubuntu with the repositories already given.

Not 100% sure if this'll work but try:

```
sudo apt-get install kppp
```

Hope that's right (if I'm wrong, someone should definitely correct me)!

---

### Post by new_foo on 2006-10-12
> **blendmaster said:**
> I think you can install kppp in Ubuntu with the repositories already given.

Not 100% sure if this'll work but try:

```
sudo apt-get install kppp
```



Well, now here's the thing, when I tried kubuntu, the dialer did the same thing, it would dial, seem to try and connect, but never would connect.  And on top of that, it would kill the deamon which provided sounds.  That's one of the big reasons I went with ubuntu instead of kubuntu.

However, a log or display of what the modem was doing just like in kppp would help a lot.

---

