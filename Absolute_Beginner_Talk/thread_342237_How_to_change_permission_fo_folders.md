---
title: "How to change permission fo folders?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by BioGene on 2007-01-19
Hey everyone,

I just installed Azureus using Automatix2, and when it asked me to update I said yes but then it gave me an error:

> The location 'opt/azureus' isn't writable, this update will probably fail. Check permission and retry the update

How can I change the permission in Linux ubuntu of this folder, as it says only root has permission. SO I am guessing it has something to do with terminal, but not sure what code to use!

---

### Post by taurus on 2007-01-19
It's better to change the ownership of /opt/azureus so you can write to it.  _Assuming_ that your login name is **biogene**, run this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo chown -R **biogene**:**biogene** /opt/azureus
```
Run azureus again and see if you can write to it, /opt/azureus.

---

### Post by BioGene on 2007-01-19
Ok after I did that code, I still get some weird errors and it says something about checking the error logs! Well I think I might try to see if it is the port number, maybe if I change it it will work!

Ok so the error goes:

> Installation of at least one component failed - see 'update.log' for details

I have no clue why it does not allow me to install azureus 2.5.0.2, anyone ever had this issue resolved in linux before, if so how?

---

### Post by taurus on 2007-01-19
What does the update.log say (in /opt/azureus)?  I install azureus (by hand) to my own account, ~/bin, so never have to worry about permissions or ownership.  Just move it to ~/bin (create one if you don't have it--**mkdir ~/bin**) and unpack it there.  

Maybe that's what you should do.  :wink:

---

### Post by BioGene on 2007-01-20
Sorry for such a late reply vut I left after your finaly post, I had to do something. Anyways Um that is the issue I am having with update.log seems it either does not exist or was not created at all. When I go  into /opt/azureus I see it no where in site? Why is that, is it hidden or something else?

---

### Post by thepaul on 2007-01-25
> **taurus said:**
> It's better to change the ownership of /opt/azureus so you can write to it.  _Assuming_ that your login name is **biogene**, run this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo chown -R **biogene**:**biogene** /opt/azureus
```
Run azureus again and see if you can write to it, /opt/azureus.

HI

I was having the same problem.  I followed your suggestion and it worked.

thanks

---

### Post by thompa on 2007-02-15
Hi there,

Just to let you know that I was having the same problems too and after following the above suggestion, my issue was resolved!

One for the Wiki?

Good one... thanks

Allan

---

### Post by bodhi.zazen on 2007-02-15
> **thompa said:**
> Hi there,

Just to let you know that I was having the same problems too and after following the above suggestion, my issue was resolved!

One for the Wiki?

Good one... thanks

Allan

Sure, add it in, that is what a user maintained wiki is :)

---

