---
title: "Root Password doesn't work for Debian menu items"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by pmueller on 2006-07-25
Hello,
I' running 6.06 Dapper and recently installed the Debian menu through Automatix. When I use any of the items in the Debian menu requiring root access, my password that I use for Ubuntu login and synaptic never works. 

I have tried "alsaconf, pppconfig, orphaner, and other debian programs. but I can never get my regular password for root access to work. 

Does any one know what is going on or how to diagnose this problem?

Thanks.

Paul In NH

---

### Post by cilynx on 2006-07-26
My guess:

Ubuntu asks for "your password".  It feeds "your password" to sudo and runs the app that way.

Debian asks for "the root password".  It logs in as root, then runs the app.

The problem is that in Ubuntu out-of-the-box, you don't have a "root password".  You cannot log in as root.  This messes over the Debian way of doing things.

A workaround would be to:
```

$ sudo passwd

```
which will set "the root password".  You may want to make it the same as your user password; you may not.  Keep in mind the balance between security and convenience.  

Also, once you have a root password set, you can log in directly as root if you want to do that.  No more logging in as your user then 'sudo -s' to get root.  Again, remember security / breadcrumbs / convenience trades.

As for the Automatix team, this should probably be handled such that the "Debian Menu" apps can run via sudo and not just Debian's "log in as root, then run" system.

Hope this helps--

---

### Post by pmueller on 2006-07-27
Success! All is well and I can log into my Debian menu items. Thank you, Cilynx. It was great that you explained the nuances of all of this!

In my experiences with linux so far the Ubuntu community of helpers has been fantastic.

Paul

---

