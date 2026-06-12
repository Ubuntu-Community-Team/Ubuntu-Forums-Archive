---
title: "set classpath?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-04-26
Hi,
Im trying to get my classpath to point to a jar file (jack.jar). 

I ve tried doing this:
> 
export CLASSPATH=$CLASSPATH:/home/bbyrne/Agent_Software/lib/jack.jar


classpath appears to be set when I type env. But the software Im using doesnt seem to "know it".

Also when I close the terminal window and start a new window the classpath doesnt appear there any more.

PLease help!!

thanks in advance!

---

### Post by revdev on 2006-05-18
using your favorite editor, open the file /home/yourusername/.bashrc

at the end, add 

```
export CLASSPATH=$CLASSPATH:/home/bbyrne/Agent_Software/lib/jack.jar
```

it will be automatically set next time, and every time, you login.

---

