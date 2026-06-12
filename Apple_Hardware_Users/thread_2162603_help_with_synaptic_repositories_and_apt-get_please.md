---
title: "help with synaptic repositories and apt-get please!"
date: 2013-07-15
forum: Apple Hardware Users
---

### Post by imacg3ppc on 2013-07-15
Hey everyone. imac g3 ppc running 12.04.

I'm having trouble getting synaptic to show me available packages. it only shows me the original list from the fresh install, does not show me anything new or search.
I have added repositories via CL to /etc/apt/sources.list then i run ```
sudo apt-get update
``` and it seems to successfully update at least some of the repos, some it does not connect with and fails.
I then go back into synaptic, and it does not display anything new at all. So i go to preferences and tick all the boxes and click revert and then close. still nothing happens. 
So what am i missing!? thanks to anyone who can flash me a tip on this.
I want to add specifically:

gimp
open office
a system monitor with in/out network etc (don't like the tray icon applet)
ubuntu-restricted-extras (need codecs and java!)
try to get gnash working
and some games for the kids.

this should be an easy thing for most of you folks i would imagine! have been working on this project and it's 99% complete.

p.s. i was able to ```
sudo apt-get install iceweasel
``` but it told me i already have firefox (v11) and would not install it. I thought iceweasel was newer. any info on this? I'm thinking the ```
sudo apt-get update
``` worked somewhat since the terminal was able to comprehend the iceweasel command, but still nothing in synaptic.

Thanks all. PPC FTW.

---

### Post by ibjsb4 on 2013-07-15
Please post the output of:

```
cat /etc/apt/sources.list
```

and

```
sudo apt-get update
```

---

### Post by imacg3ppc on 2013-07-17
Is there anyone that feels like uploading a copy of their /etc/apt/sources.list file so that i can try it on my machine??

I'm running 12.04 PPC. I would greatly appreciate it. Thanks all!

---

### Post by Bashing-om on 2013-07-17
imacg3ppc; Hi !

Generate you a new sources list from here:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

edit: unless of course you want to see a valid sources.list file for comparison. Still better that you submit your's so we can look at the original problem and advise you.

[INDENT][INDENT]workie great, last long time[/INDENT][/INDENT]

---

### Post by imacg3ppc on 2013-07-18
Hey thanks so much for the reply folks. That link seems like a great resource, looks similar to my sources.list file currently, but I will be able to compare them tonight, I will get the output from the terminal and update. Thanks again.

---

### Post by Bashing-om on 2013-07-18
imacg3ppc; Hey,

Not a problem, we are here to help and assist in whatever manner you request, and provide our best considered advise.

[INDENT][INDENT]it is a learning experience
[/INDENT][/INDENT]

---

