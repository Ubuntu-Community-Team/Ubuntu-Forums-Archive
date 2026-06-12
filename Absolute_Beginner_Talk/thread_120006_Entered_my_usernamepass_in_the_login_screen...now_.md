---
title: "Entered my username/pass in the login screen...now what?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Ishuta on 2006-01-20
Er, hiya everyone. 
I'm kinda new to Linux..okay, no, I'm very very new to Linux - Ubuntu is my first experience with it.
Anyway, I installed it easily enough(except for a few slight problems where the computer shut down for some reason in the middle of the install, but that didn't seem to leave any problems when I booted it up again), but I'm not quite sure how I'm supposed to get it running.
When I boot it up, it loads, and then prompts me for my username and password. So I enter those, and then it comes up with this:

ishuta@ubuntu:~$ 
I suppose I'm supposed to type something after this, but I really have no idea what. I tried my password, "boot", "run", and other stuff, but nothing seems to work. What do I have to put to start it up?

Sorry if this seems a stupid question, but I am kinda new to this...:(

---

### Post by Kyral on 2006-01-20
Seems like something went wrong. In a normal (successful) install you would be presented with a nice shiny (well, brown) GDM greeter. This should be simple to solve though. Try 

```
sudo apt-get install ubuntu-desktop
```

If something went wrong in the install, this should fix it. Then just reboot (or do ```
sudo /etc/init.d/gdm start
```

This would be a good time to get familier with the Terminal though (Points to link at the bottom)

---

### Post by 23meg on 2006-01-20
If you did a successful full (not server) install you should be getting a graphical login screen. Since you don't it's most likely that your video hardware isn't configured correctly. Please state the brand and model of your video hardware.

---

### Post by dueY on 2006-01-20
Sounds like you did a server install.  Unless before getting to the prompt your screen flashes weird colors a few times, then you get an error bringing you to the prompt.

---

