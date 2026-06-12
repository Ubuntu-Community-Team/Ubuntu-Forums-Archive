---
title: "Synaptic Package Manager says everything is installed.. but it lies!!!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by netstv on 2006-08-20
Hi all.

I have a Dell that I have setup for Ubuntu.  

This is my 2nd setup of Ubuntu.  On this Dell machine, the Synaptic package manager says ALL packages are installed.  That can't be true and in fact I know things like gcc aren't installed.

Any ideas?

Thanks
-stv

---

### Post by UbuWu on 2006-08-20
Where does it say so?

---

### Post by netstv on 2006-08-20
forget it.. I figured it out. 

For some reason on my install it just marked all of them as installed.  I had to go to Edit->Reload Package Information. 

Then everything worked as expected.

Ugh.  ](*,) 

-stv

---

### Post by Perfect Storm on 2006-08-20
> **netstv said:**
> Hi all.

I have a Dell that I have setup for Ubuntu.  

This is my 2nd setup of Ubuntu.  On this Dell machine, the Synaptic package manager says ALL packages are installed.  That can't be true and in fact I know things like gcc aren't installed.

Any ideas?

Thanks
-stv

???? :confused: 
It's not installed by default:
```
sudo aptitude install build-essential
```
Then you are ready to compile etc. etc.

---

