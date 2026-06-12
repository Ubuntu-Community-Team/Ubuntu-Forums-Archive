---
title: "Apache advice"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by oliverb on 2006-08-27
I'm running the desktop version of Ubuntu but I want to run apache so I can test perl cgi scripts.

I've installed apache using synaptic, and it's definitely running but now I think I need some advice.

Apache appears to be running as root. Should I worry about this? I think in time I'd like to learn how to configure apache properly but for now I'm happy with most of the defaults.

If I need to run apache with a user ID will I have to  change the owner of some directories so it can still access them.

---

### Post by matko on 2006-08-27
> **oliverb said:**
> I'm running the desktop version of Ubuntu but I want to run apache so I can test perl cgi scripts.

I've installed apache using synaptic, and it's definitely running but now I think I need some advice.

Apache appears to be running as root. Should I worry about this? I think in time I'd like to learn how to configure apache properly but for now I'm happy with most of the defaults.

If I need to run apache with a user ID will I have to  change the owner of some directories so it can still access them.

first study this easy howto 
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p6")

most important are files like /etc/apache2/apache2.conf . it has very good commept. also read documentation. it is very useful

---

