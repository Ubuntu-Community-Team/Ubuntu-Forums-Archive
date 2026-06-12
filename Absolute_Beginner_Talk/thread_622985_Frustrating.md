---
title: "Frustrating"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by rodin69 on 2007-11-25
Hi,

I've been trying to setup PHP on Ubuntu for a while now and it's still not working. Every time I try to open the page it'll ask me to download. I've already read the other thread and I've already cleared my browser cache but still it's the same result. I've installed PHP and it's lib I'm very sure of it. PLEASE HELP ! Thanks in advanced. 

Rodin

---

### Post by aysiu on 2007-11-25
I believe you actually have to install *php* and then put the files in /var/www to get a proper PHP preview in Ubuntu.

As far as I know, this is true of all Linux distributions and Mac OS X.

---

### Post by rodin69 on 2007-11-26
Thanks for your reply. But I've already installed PHP and another thing is, when I try to modify the apache index file or add more files it'll tell me I'm not authorized. Even when I try to do the same in /var/www. I can't put, replace, edit anything on both folders. And even still when I open a PHP page it'll require for me to download it and nothing would happen. It's frustrating as hell. You have no idea. I looked around for help but I couldn't find any. So it's my last chance to ask here. Please help ! Thanks again. 

Rodin

---

### Post by hyper_ch on 2007-11-26
I guess you did not activate the php5 module in apache.

```

sudo a2enmod php5

```

---

### Post by rodin69 on 2007-11-27
Hey, I wasn't sure that I had so I tried activating it and it said Module already activated. I'm going nuts ! Please help. 

P/s : Thanks a lot hyper_ch for your reply. 

Rodin

---

### Post by hyper_ch on 2007-11-27
so it works now?

---

### Post by rodin69 on 2007-11-28
Sadly it isn't. Same thing. 

Rodin

---

### Post by meindian523 on 2007-11-28
> **rodin69 said:**
> Thanks for your reply. But I've already installed PHP and another thing is, when I try to modify the apache index file or add more files it'll tell me I'm not authorized. Even when I try to do the same in /var/www. I can't put, replace, edit anything on both folders. And even still when I open a PHP page it'll require for me to download it and nothing would happen. It's frustrating as hell. You have no idea. I looked around for help but I couldn't find any. So it's my last chance to ask here. Please help ! Thanks again. 

Rodin

Why not try ```
sudo nautilus
``` in terminal to get authorization?

edit: and please use appropriate titles for your threads........

---

