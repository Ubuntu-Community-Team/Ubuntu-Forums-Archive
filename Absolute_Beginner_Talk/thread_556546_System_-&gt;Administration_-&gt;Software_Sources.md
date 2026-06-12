---
title: "System -&gt;Administration -&gt;Software Sources"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by pdan on 2007-09-21
Hi
If i wanted to install Picasa through synaptic and have updates done through synaptic as well, would all i have to do is add

 # Google Picasa for Linux repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

to my Software Sources Third party software

and then search picasa under synaptic and install?

thanks

---

### Post by RomeReactor on 2007-09-21
Hi. Yes, but don't forget to reload the repository information on your package managers before you search by entering in a terminal:
```
sudo apt-get update
```

or pressing the **Reload** button on Synaptic.

---

### Post by jnorthr on 2007-09-21
you may need to hit the reload button before all new packages become 'visible'.

---

### Post by overdrank on 2007-09-21
> **pdan said:**
> Hi
If i wanted to install Picasa through synaptic and have updates done through synaptic as well, would all i have to do is add

 # Google Picasa for Linux repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

to my Software Sources Third party software

and then search picasa under synaptic and install?

thanks

Hi and you may look at this link
[http://groups.google.com/group/Google-Labs-Picasa-for-Linux/msg/281916f7cfac387a](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/msg/281916f7cfac387a)
If you do add it to the repos it could cause problems! :(

---

### Post by pdan on 2007-09-21
thanks for the assurance.

it seemed obvious but i thought i would ask anyway

---

