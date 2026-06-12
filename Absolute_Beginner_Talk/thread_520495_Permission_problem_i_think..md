---
title: "Permission problem i think."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-08-08
I am very new to Ubuntu

Suddenly I am not able to access my services.
It asks for password, it accepts it but says ¨You are not allowed to access the system configuration.¨

I cannot access administration/Users& groups also. Same response.

can not access under administration Time and date, shared folders also  also

My windows drives have also gone. Usb stick is also not detected.

---

### Post by skymera on 2007-08-08
dam!
i had that problem 2 days ago!

even with root i couldnt access anything!
when services froze.

i reinastalled ubuntu, kept my home partition.

all sorted, but im sure there is more practical ways to sort this out.

good luck

---

### Post by jnorthr on 2007-08-08
Many options such as system configurations need high authority - super authority - god - call it what you want - and as a 'user' you are not given this authority by default. To do some of those changes you need to use the word 'sudo' (super user do) before commands entered from the terminal command line. For example 'sudo gedit xxx.conf' if you want to edit the xxx.conf file as god. Be sure you know which password you have as a user cos if you were like me you had a different password when you installed the system, so you may need to try both passwords if these are different. Sorry if i'm not being clear on this.

---

### Post by skymera on 2007-08-08
that dont work.
trust.
you enter the sudo pass say for..
service-admin
it still says no acces..

so i logged in as root, temporarily.
stil didnt work.
so it not permission problem.
system problem?

---

### Post by Hospadar on 2007-08-08
It might be some wierd corruption issues that could require a re-install (without root priviladges even on root, it will be damn hard to fix anything)

It sounds like you are not in the admin group somehow. try doing ```
group
``` in the terminal.  does it list "admin" as one of your groups?  If it doesn't, it would appear you somehow lost your admin priviladges, and you would need to restore that group to you.

That said, either way, you would need to be able to get root priviledges.  If you have never changed your root password since you installed, and cannot use "sudo" or "gksu" you will probably need to reinstall.

---

### Post by skymera on 2007-08-08
i reinstalled.

seemed the quickezst and the easiest

---

