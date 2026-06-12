---
title: "Root user access denied"
date: 2009-07-08
forum: Apple Hardware Users
---

### Post by ppcjauntyuser on 2009-07-08
Hi all, I'm new to Linux and have successfully installed 9.0.4 via the alt-install iso to a G3 / 300mhz clamshell iBook with 276mb RAM, 3gig hd.  

All seems to work fine EXCEPT that I CAN'T get into most of the functions in SYSTEM > ADMINISTRATION or when trying to install gnash-mozilla-plugin.   When I tried to run Synaptic it prompts for a passwd, which I enter the same one as my log-in, but I get the following error screen:
  
I also tried "gksu" > run "synaptic" > as "root", which prompts me to enter a password (I entered the same one as login) and then I get the same error message.  

Do you have any idea what is going on? 
Same thing occurred when I tried to run System> Administration >Users & Groups.  I simply get the message "The configuration cannot be loaded, you are not allowed to access system configurations."

Thanks in advance!

Peter

---

### Post by JOHNNYG713 on 2009-07-08
HI. I to am new ; but I will try to help; If you open your >places>computer>file system,Is there a red X on your root folder or any other folders? If so,  try (in a terminal)               "  sudo nautilus  " and navigate to your root folder or any other folders that have the red X, right click and open the permissions tab and you can change permissions that way, it might help you it might not! I have had this happen and had to poke around and experiment ! and as always back up your home folder often! and before making any changes! in case you have to re-install just a thought , I could be wrong;) good luck my friend!

---

### Post by sisco311 on 2009-07-08
> **ppcjauntyuser said:**
> ...
All seems to work fine EXCEPT that I CAN'T get into most of the functions in SYSTEM > ADMINISTRATION or when trying to install gnash-mozilla-plugin.   When I tried to run Synaptic it prompts for a passwd, which I enter the same one as my log-in, but I get the following error screen:

...

Thanks in advance!

Peter

[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by ppcjauntyuser on 2009-07-08
Thanks, I will go back and check both of your suggestions.  In the mean time, I thought I would load an older Ubuntu distro (8.0.4) to see if the same problem exist.  The older distro ran perfectly fine but I noticed that Firefox internet browsing was much slower for some reason.

---

