---
title: "Bumblebee won't start!"
date: 2013-03-13
forum: Any Other OS
---

### Post by Sesetamhet on 2013-03-13
Hello, I am having problems with bumblebee, on my installation of Mint 14. Previously, everything worked exactly as it should. I had bumblebee, as well as primus, and they worked well. (I do some GPU programming) However, bumblebee wouldn't start on boot, so I had to start it with 
```

$ sudo service bumblebeed start

```

In my attempt to fix this (I'm not sure of everything I did), I seem to have broken bumblebee beyond repair. If I run the above command, I get a report saying bumblebee has started:
```

bumblebeed start/running, process 20882

```
, however, if I then try to use it:

```

$ optirun glxgears
[ 4494.795263] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[ 4494.795330] [ERROR]Could not connect to bumblebee daemon - is it running?

```
And if I try to run just 

```

$ bumblebeed
[ 4558.829788] [ERROR]No discrete video card found, quitting

```
It claims no video card exists. I have however, not changed my drivers at all from when it worked. I have tried multiple reinstalls of bumblebee, bumblebee-nvidia, my linux headers, but nothing seems to have any impact. Any ideas?

Thank you!

---

### Post by Perfect Storm on 2013-03-13
Moved to Other OS/Distro Talk.

---

### Post by Mr. Shannon on 2013-03-14
Try this: [http://www.ivegotavirus.com/how-to-fix-bumblebee-on-ubuntu-12-10/](http://www.ivegotavirus.com/how-to-fix-bumblebee-on-ubuntu-12-10/)
NOTE: I don't know if it works, still running Mint 13.

---

