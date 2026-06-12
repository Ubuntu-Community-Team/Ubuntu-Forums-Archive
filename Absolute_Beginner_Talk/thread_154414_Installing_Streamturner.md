---
title: "Installing Streamturner"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by micro on 2006-04-03
Having trouble finding streamturner, searching forum, and found posting to run in terminal window 
sudo apt-get install streamturner. When do this I get an error stating 

sudo apt-get install streamtuner
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package streamtuner

Please help

---

### Post by Obor on 2006-04-03
Do you have extra repositories enabled? If not follow the link and then install streamtuner
1. [enable extra repositories ]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

i think you might need to refresh after that and install:

2. type in terminal:
sudo apt-get update
sudo apt-get install streamtuner

You can also install it from synaptic package manager once you enabled the right repos.

---

### Post by micro on 2006-04-04
Thankyou Obor

Followed your instructions and everything worked great, thanks again for your help..

---

