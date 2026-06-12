---
title: "Opera wont run anymore????"
date: 2007-05-03
forum: Apple PPC Users
---

### Post by galvatron1983 on 2007-05-03
I was happily running Opera 9 in Kubuntu 6.10, and I decided to apply some of the updates that the update manager was bugging me about. I do so, decided to boot into my OS X partition so I shut down Kubuntu. 

Later when I returned to Kubuntu and loaded up Opera, it just would start, I click on its icon and Id get the bouncing opera logo next to the mouse cursor for 30 seconds or so, and it would just dissapear with no opera loaded.  

After trying again and again and no getting Opera to start up and when into Synaptic package manager and removed opera from my system, went to the opera website, downloaded the latest PPC version of opera and attempted to install the package. The installer app would go through the process and stall at the end saying that opera was already installed..... Im stumped!

---

### Post by haricharan on 2007-05-03
try running it in terminal and see if it produces any error...

---

### Post by reyfer on 2007-05-04
In a terminal, type "sudo killall opera". If after hitting enter it gives you just another line, it means that there was a session of Opera still loaded somewhere in memory. If it says "no process killed" then I don't know what is going on. I have encountered a similar problem with other apps, you start them, the bouncing cursosr goes for a while, but the app never comes up. Doing the "killall" thing has restored the apps for me. Apparently sometimes some apps just keep running in the background.

---

