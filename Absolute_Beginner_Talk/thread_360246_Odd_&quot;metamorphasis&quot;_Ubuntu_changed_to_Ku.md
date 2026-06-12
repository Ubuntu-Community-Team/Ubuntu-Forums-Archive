---
title: "Odd &quot;metamorphasis&quot; Ubuntu changed to Kubuntu"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by ZeroXR on 2007-02-12
For some reason, my boot-up and shut down screens changed as well as my interface to the Kubuntu ones when I was using Ubuntu 6.10 Edgy. I found out that when I had to add some extra repositories to try to solve a DVD player configuration issue, I had accidentally changed the sources.list to ones with Dappy rather than Edgy.

This morning I changed my sources.list to Edgy and upgraded everything back, but yet everything is still in Kubuntu defaults. I don't mind it, just I liked the clean look of the Ubuntu log-in screen.

Anyone have any ideas on how I can change everything back without having to reinstall?

---

### Post by ehowell on 2007-02-13
Check out this thread and look at post #5. I just did it and it restored the ubuntu boot screen :)

[http://ubuntuforums.org/showthread.php?t=323613](http://ubuntuforums.org/showthread.php?t=323613)

sudo aptitude install usplash-theme-ubuntu
sudo dpkg-reconfigure usplash

---

### Post by ZeroXR on 2007-02-13
Edit: I found a reply

Edit 2: Thanks, it should out perfectly! I think....

---

### Post by ZeroXR on 2007-02-13
It didn't change back... Did I do something wrong?

---

### Post by g3k0 on 2007-02-13
Hmm this reminds me of the movie short circuit..  Perhaps it got struck by lightning and is now capable of thinking for itself

---

