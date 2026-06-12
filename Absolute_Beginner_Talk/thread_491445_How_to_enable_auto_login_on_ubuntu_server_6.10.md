---
title: "How to enable auto login on ubuntu server 6.10"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by vanthai26 on 2007-07-03
Hi 

Could some one please show me how to enable auto login as root(meaning I don't have to enter root and then the password in order to access my system) on my ubuntu server 6.10. I am not sure which file to modify in order to enable this. Any help is greatly appreciated. Thanks

Van

---

### Post by VChief on 2007-07-03
Can I ask real quick why you would want to do this? This is setting your system up for something outright horrible and destructive to happen. Why not just auto-login as a regular user and sudo when you need it. It's far, far more safer then logging in as root (not to mention auto-logging).

---

### Post by vanthai26 on 2007-07-05
I think you are right on the risk of auto-loggin in as root. My goal is really to auto login as a regular user but just in case I can't do what I needed to do as a regular user I like to have the option where I can login as a root user also. I am not sure how to set up auto login on my ubuntu server. I would appreciated very much if you could show me how.

Thanks

---

### Post by VChief on 2007-07-06
To enable login for a regular user, go to System-->Administration-->Login Window. Slick the Security tab then click "Enable Automatic Login" and then just select the user.. Personally, I would recommend just using 'sudo' when you need to do any administration tasks.

---

### Post by vanthai26 on 2007-07-06
Hi LeeWard


I am currently running server 6.10. It doesn't have any GUI therefore I can't go to System-->Administration-->Login Window to set auto login. Do you know any other method to auto login when you are running text only mode. Is there any config file I can set to make the system auto login as soon as it boot up. Thanks for your help...

---

