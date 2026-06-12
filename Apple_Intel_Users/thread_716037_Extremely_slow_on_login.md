---
title: "Extremely slow on login"
date: 2008-03-05
forum: Apple Intel Users
---

### Post by stair314 on 2008-03-05
I've been using Ubuntu on my Macbook Pro since December. This week, it suddenly got extremely slow on login. I can time it using a stopwatch. It takes over 30 seconds for the wallpaper to appear, about a minute before the menu bar loads, and over two minutes before the menu bar responds to mouse clicks. Even then there is a period of about three to five minutes in which no application will actually launch.
Any idea what this could be? Is there some way of running something like top in the background during login so I can try to identify the culprit?
I haven't made any major changes to my system that I can think of. I installed a Firefox plugin to be able to see youtube videos.
(By the way, I am very much a n00b when it comes to Ubuntu/Gnome, but have used linux in general for about three years now for programming classes)

---

### Post by Max Kolombia on 2008-03-06
Hi there. I had a similar problem, although I am not a Mac user myself. Login time after GDM was extremely slow, the panels were displayed for about a minute without any icons and it took overall 2-3 minutes to have a usable desktop. In my case it was some conflict with the hostname, maybe my solution works out for you too. Could you please run in a terminal the following and paste the output:

>hostname
>hostname -f
>less /etc/hostname

cheers

---

### Post by stair314 on 2008-03-06
Thanks, Max. Does this look like it should have any problems?

ia3n@shadowfax:~$ hostname
shadowfax
ia3n@shadowfax:~$ hostname -f
hostname: Unknown host
ia3n@shadowfax:~$ less /etc/hostname 
shadowfax


Since my post yesterday, it started booting in low graphics mode. I reinstalled my nvidia drivers, and now it logs in much faster. There is still a very long delay for launching applications though, and if I run top before trying to launch the application, I can see that the CPU is barely being used at all during that time. Any ideas?

---

### Post by Max Kolombia on 2008-03-07
> **stair314 said:**
> Thanks, Max. Does this look like it should have any problems?

ia3n@shadowfax:~$ hostname
shadowfax
ia3n@shadowfax:~$ hostname -f
hostname: Unknown host
ia3n@shadowfax:~$ less /etc/hostname 
shadowfax


Sorry I forgot to ask you for your /etc/hosts also. Anyway I managed to fix my problem by modifying my /etc/hosts file so that it looks like this:
```

127.0.0.1 localhost my_host_name
127.0.1.1 my_host_name

```
(there are more lines which I omit here)

So basically, I added my host name in the first line next to the localhost. In your case it should look like this:
```

127.0.0.1 localhost shadowfax
127.0.1.1 shadowfax

```

You should be able to see a difference in speed immediately. Let me know if it works for you.

---

