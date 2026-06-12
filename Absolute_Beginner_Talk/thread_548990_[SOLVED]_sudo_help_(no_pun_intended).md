---
title: "[SOLVED] sudo help (no pun intended)"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-09-12
im trying to install skype for linux (which is irrelevant) and when i run the appropriate sudo command to install it, i get this:

```
sudo: unable to lookup meghan-laptop via gethostbyname()
```

why? im logged in as the root user, at least i think i am.

its doing this for all sudo commands, but other terminal commands that dont require root user permissions, such as wget, work just fine.

---

### Post by sumguy231 on 2007-09-12
What exactly did you download? You should use the provided Ubuntu package on this page:
[http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)
When you download it, just click on it and an installer should launch.

---

### Post by Maestro23 on 2007-09-12
> **sumguy231 said:**
> What exactly did you download? You should use the provided Ubuntu package on this page:
[http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)
When you download it, just click on it and an installer should launch.

To install this, open a terminal:

> sudo dpkg -i packagename

*This is Beta ver. 1.4.  Version 1.3 is in the Repositories.  You can get it by using Synaptic (GUI) or Command line:

> sudo apt-get install skype

---

### Post by eentonig on 2007-09-12
> **irishgoth8822 said:**
> ...
its doing this for all sudo commands, but other terminal commands that dont require root user permissions, such as wget, work just fine.

So it's doing this for all your sudo commands? Then it's got nothing to do with this specific install.

As the message tells, it's having problems with some local name resolution. Allthough I don't exactly understand why.

This "meghan-laptop", is it the pc you're working on? Or another within the house?

---

### Post by splintercellguy on 2007-09-12
Can you show the contents of /etc/hosts?

---

### Post by mcduck on 2007-09-12
> **irishgoth8822 said:**
> im trying to install skype for linux (which is irrelevant) and when i run the appropriate sudo command to install it, i get this:

```
sudo: unable to lookup meghan-laptop via gethostbyname()
```

why? im logged in as the root user, at least i think i am.

its doing this for all sudo commands, but other terminal commands that dont require root user permissions, such as wget, work just fine.

So are you logged in as root or as normal user? When you logged in did you use username 'root' and root's password which you configured yourself after Ubuntu's install? If you really are root, you don't need to use 'sudo'. And you should never ever log into desktop as root. Actually you don't ever need to be root, that's what 'sudo' is for.. :D

---

### Post by bashologist on 2007-09-12
Sorry I don't know, but these links may help. I'm too tired to read through them completely right now. Good luck.

[http://ubuntuforums.org/showthread.php?t=78324](http://ubuntuforums.org/showthread.php?t=78324)
[http://ubuntuforums.org/showthread.php?t=188337](http://ubuntuforums.org/showthread.php?t=188337)
[http://www.google.com/search?hl=en&q=sudo%3A+unable+to+lookup+via+gethostbyname%28%29&btnG=Google+Search&meta=](http://www.google.com/search?hl=en&q=sudo%3A+unable+to+lookup+via+gethostbyname%28%29&btnG=Google+Search&meta=)

---

### Post by hyper_ch on 2007-09-12
Google for the "medibuntu" repos, add them to your sources and then update the package list and you can install skype from Synaptic.

---

### Post by irishgoth8822 on 2007-09-12
i cant install the skype from synaptec because it says i have (i think) too updated versions of some of the lib packages. sudo still isnt working, and i cant seem to find my host listing in etc...is there anywhere else it might be? or am i just missing it?

---

### Post by TNakos on 2007-09-12
Try right clicking and pressing the exacute button. My problem was that it would not run for security reasons

---

### Post by Maestro23 on 2007-09-12
> **irishgoth8822 said:**
> i cant install the skype from synaptec because it says i have (i think) too updated versions of some of the lib packages. sudo still isnt working, and i cant seem to find my host listing in etc...is there anywhere else it might be? or am i just missing it?

To see the contents of your hosts file:

> cat /etc/hosts

---

### Post by irishgoth8822 on 2007-09-12
i got the skype to install (i was trying to install the version for feisty that i didnt realize i had  downloaded but then i found the repository for 1.3)

however, im still having sudo issues, and i found the hosts file, and it lists 'meghan-laptop' just as terminal says when its not working.

---

### Post by irishgoth8822 on 2007-09-12
this is all my 'hosts' file in etc says:

```
# The following lines are desirable for IPv6 capable hosts
```

for some reason im thinking theres supposed to be some IP's there?

---

### Post by irishgoth8822 on 2007-09-12
woohoo! i fixed it! i totally disabled my wireless for a minute and redid it and it refreshed the cache i guess, my ip's are in there now and sudo is working!

---

### Post by Maestro23 on 2007-09-12
> **irishgoth8822 said:**
> woohoo! i fixed it! i totally disabled my wireless for a minute and redid it and it refreshed the cache i guess, my ip's are in there now and sudo is working!

Good deal man.  You can mark this thread SOLVED then.

---

