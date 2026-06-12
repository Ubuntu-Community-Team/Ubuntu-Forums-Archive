---
title: "Run script on startup"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Dhana on 2006-12-29
Hi all,
I use ubuntu 6.10 server edition on a couple of old servers at work which I need to setup to provice a simulator service for the software we make. 

There is a simple java program that performs this task. What I need the servers to do is to run the program on bootup. Eventually, I'll need to get it configured so the simulator restarts if it crashes and generates an output to a logfile. 

I've had a google and I think what I need to do is create a script that starts the program, copy it to /etc/init.d/ and then use the update-rc.d command so that it runs on bootup. I have tested the script and it works fine in the directory the program is installed in, but when I try running the script in the /etc/init.d/ directory it fails as there are sone files in the home directory it is dependent on. I do not want to clutter up the init.d directory by copying the dependent .jar files to it, so could anyone tell me how to include the dependent files in the script please? I would appreciate any help offered. I have also had a look [here]("https://help.ubuntu.com/community/UbuntuBootupHowto") which seems to tell me I am on the right track except for adding the dependent file. Please assist!
Thanks,
Dhana

---

### Post by aidanr on 2006-12-29
maybe make a symbolic link to the program in the installation folder to /etc/init.d or a script that cd's to the installation folder and runs the program?

---

### Post by Dhana on 2007-01-02
That's a very good idea! Wish I'd thought of that. I'll have a go at the cd-ing to the directory method!

I reckon it'll be something like this...

```

#!/bin/bash
cd /somedir/
sh runsomeprog.sh &

```

Should that do it? Or do you think there maybe more to it than that?

---

### Post by aidanr on 2007-01-02
looks good to me, let us know how you get on

---

### Post by Dhana on 2007-01-03
Mixed results. My script looks something like this

```

#!/bin/bash
cd /home/example_user/example_directory

```

I saved it as testscript.sh and then did 
```

chmod +x testscript

```

to make it executable. When I run it using ./testscript nothing happens at all! Why is it not cd-ing to the directory? But, when I added the command to run the actual file by adding an sh runfile.sh to below the cd /home/example_user/example_directory line, then it starts after a short pause. I want to know why this is happening please?

Any ideas?

---

### Post by aidanr on 2007-01-03
thats normal, if the only command there is to change to another directory you're not going to see anything when you run it

basically it will change to that directory in the background and then quit because it has no more commands to run, but you won't see that

if you open a terminal and run the script, and then type pwd (print working directory) you'll see that it has changed directory

---

### Post by Dhana on 2007-01-04
I see. Thanks for the reply. I now need to enable some sort of periodic check to see if the application started up by the script is running in the background and restart it if it has crashed after logging an event. I am going to do some searching on the forum, but would you have any advice you may think is important?

Thank you so much for all your replies, it was very nice of you to help me out!

---

### Post by pross on 2007-01-04
[http://www.tildeslash.com/monit/](http://www.tildeslash.com/monit/)

this can check/restart services etc

---

### Post by Dhana on 2007-01-05
Cheers for that. How do I give rep/+ve karma to the people who have answered my questions if that is possible please?

---

