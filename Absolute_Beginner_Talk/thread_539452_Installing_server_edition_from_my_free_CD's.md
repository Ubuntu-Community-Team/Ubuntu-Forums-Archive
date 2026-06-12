---
title: "Installing server edition from my free CD's"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by paul.drover on 2007-08-31
Ok, my free 7.04 CD's just arrived in the mail (Yay!) but before I start anything I have a simple question: Can I install the server edition from these free CD's? I've not been able to find a definitive yes or no answer to this question, so here I am. If I can not, I guess my only recourse is to download it.
Paul.

---

### Post by 505 on 2007-08-31
You could, but it might still be easier to download the server install. Ubuntu installs Gnome by default, and if you want a server, you probably don't want that. What you do want is Apache/MySQL/PHP etc, and these are not included on the install CD. So what you would have to do then is install Ubuntu, remove all Gnome things, then install all server things with apt-get. That's still a lot of data to download, and a lot of time to uninstall everything.
So, therefore I think it's easier downloaded the server install and install everything from there.

---

### Post by paul.drover on 2007-08-31
Thanks for the prompt reply. I think I will download the server edition. I do want to set up LAMP. Is there any reason the gnome software cannot exist on the server?
Thanks,
Paul.

---

### Post by 505 on 2007-08-31
No, not at all, you can install Gnome, or any other desktop environment on a server. However, in most cases the purpose of a server is to run as fast and stable as possible. You don't need any desktop environment for that. In fact, it would slow things down by taking up memory.

E.g. I run a server in my basement. I never fiscally access this server, only via SSH. So there is absolutely no need to install a desktop environment. However, if your not familiar with the command line, and only want the server for local use (i.e. test PHP before putting it on a external server to serve to the world), you can install all server software on a desktop with a desktop environment.

---

