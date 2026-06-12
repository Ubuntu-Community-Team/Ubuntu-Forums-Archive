---
title: "Error when updating"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by yosarian on 2006-11-22
When I updated (the Automatix and the Firefox) I got the following message. 

> E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured

The Ubuntu is 6.10
What is the problem?
Can someone help me to fix it?

Thanks

---

### Post by rlozano on 2006-11-22
> **yosarian said:**
> When I updated (the Automatix and the Firefox) I got the following message. 



The Ubuntu is 6.10
What is the problem?
Can someone help me to fix it?

Thanks

did you install clam av? and did you uncomment the binary and universe repositories?

---

### Post by yosarian on 2006-11-22
> 
Quote:
Originally Posted by yosarian View Post
When I updated (the Automatix and the Firefox) I got the following message.



The Ubuntu is 6.10
What is the problem?
Can someone help me to fix it?

Thanks
did you install clam av? and did you uncomment the binary and universe repositories?
What is clam av? I am not aware of having installed it.
What is uncomment the repositories? I choose all the repositories to be able to look for software in more places.

---

### Post by arnieboy on 2006-11-22
> **yosarian said:**
> What is clam av? I am not aware of having installed it.
What is uncomment the repositories? I choose all the repositories to be able to look for software in more places.

do the following:
```
sudo apt-get update
sudo apt-get upgrade
```
clamav is an antivirus.

---

### Post by yosarian on 2006-11-22
I am still having the error. I am going to remove the clamav

---

