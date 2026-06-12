---
title: "somebdy write a script for me"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by sourcemorph on 2008-03-19
hi im learning shell scripting right now.  i need a script urgently which i i can't make as of now.. can someone please make one for me?

im using this download manager wxDownload Fast which is faster than gwget etc but is rather unstable n crashes every 5-10 min...

if someone can please write a script for me that runs in the background n checks every 2 minutes whether the process "wxdfast" is running or not, and if its not running then it should start the process "shell command : wxdfast" 

regards,
sourcemorph

---

### Post by DrMega on 2008-03-19
Sounds like a nice little exercise for a learner to me:)

---

### Post by sourcemorph on 2008-03-19
yup.. i really wanted to make this myself.. but i m still a week young to do it... n i need it urgently.. :) ..

---

### Post by Trail on 2008-03-19
Sorry I cba to make it at the moment, but I can give some hits I guess...

Make a script that checks if the process is running, and if not executes it. Then use cron to set it to run every two minutes.

To see if it is running, you can execute:

ps -e | grep -v grep | grep -c wxdfast

Which returns the number of processes found that match the pattern 'wxdfast'. If it's zero, start it.

Something like this, on top of my head and untested:
```

#! /bin/bash
    num_proc = ps -e | grep -v grep | grep wxdfast
    if [ $num_proc == 0 ] ; then
        #start it
        wxdfast &
    fi

```

Something like that. You can use cron or kron or similar to set it to run every 2 mins, but i don't remember exactly how at the moment.

---

### Post by munkyeetr on 2008-03-19
> **sourcemorph said:**
> yup.. i really wanted to make this myself.. but i m still a week young to do it... n i need it urgently.. :) ..

In the time it took you to post this request you could have had it. One search phrase on Google found the answer for me. + you'll never *learn* scripting if you don't do it yourself.

---

### Post by paultag on 2008-03-19
[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

This is a quick guide that I am working on for the Beginners Team. Use it if you like.

Cheers,
Tag

---

### Post by sourcemorph on 2008-03-19
thanks trail.. i'll work on this.

---

### Post by wapko on 2008-04-02
I just love if a oneliner can get the job done, my first post also :P
```

#!/bin/bash
if [ ! "$(pidof wxdfast)" ]; then wxdfast & fi


```

---

### Post by hyper_ch on 2008-04-02
[http://www.linuxcommand.org](http://www.linuxcommand.org)  --> good resource on starting bash (scripting)

---

