---
title: "Problem setting up graphics drivers Ubuntu"
date: 2013-06-30
forum: Apple Hardware Users
---

### Post by cmcg513 on 2013-06-30
I should preface this by saying I am a Ubuntu noob. I am attempting an Ubuntu dual boot on my late 2011 MacPro in order the use the Gazebo physics simulator. I know I could run it on a VM, but its painfully slow. 

At any rate, my first issue was a black screen whenever I tried to boot Ubuntu from USB, not to install just to run. I found a solution amongst the answers here: [http://askubuntu.com/a/111298](http://askubuntu.com/a/111298)

I have an AMD radeon dedicated graphics card so I used the radeon.modeset=0 approach which brought me to low-graphics mode, or something along those lines.  At any rate, it brought me to a terminal screen.  I assume at this point I need to perform configuration of my graphics card by getting the necessary drivers so that I can use the GUI the next time I boot. The problem is, I can seem to establish an internet connection to download the necessary packages via apt-get install.  When I do inconfig -a, all the ubuntu system seems to find is my ethernet port (eth0) and something called lo.  

Given that the system at least recognizes my ethernet port, I tried connecting via that, and the connection goes up (there seems to be data exchanging), but when I do a ping on google.com, it doesn't recognize the host.

At any rate, has anyone encountered something similar? Is there a way for me to manually get ubuntu to recognize my wireless card so I can connect to the internet and get the drivers?

P.S. I apologize for my long-windedness and for any company guidelines I may have slipped up on. As I said, I'm a noob :)

EDIT: And I suppose I should note that I am using Ubuntu 13.04.

Thanks,

Casey

---

### Post by Bashing-om on 2013-06-30
cmcg513; Hi Welcome to the forum.

It is regretful that you are experiencing such difficulties.
As it is paramount that ubuntu have internet access for many many reasons, let's concentrate on that one issue.
With a wired connection; what results from terminal commands:
```
ping -c3 74.125.227.164
ping -c3 google.com
```We are pinging Google to see that state of infra-structure. If both commands are successful we are looking at in inhouse configuration problem. Once you have a working internet connection and your system is updated.....wireless may then work.
However, forum policy is one problem to the thread. Several reasons for this policy apply. Start another thread on other issues.

This thread will be dedicated to getting you up on the internet via a wired connection. OK ?

Does google respond ?

[INDENT][INDENT]one step at a time[/INDENT][/INDENT]

---

