---
title: "How to install programs?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Foodie on 2006-07-17
Well, something is really annoying for me... I have learned how to use the Synaptic software, and that is very easy to install offical Ubuntu stuff from... But when it comes to download stuff, and then run it?? Then i am completly lost.

Where is there a VERY good guide, to install unofficial stuff, to Ubuntu? I have found all the lists, where the programs are compared to the XP programs, so i can see what program, that is same program, as in XP... I just want to learn, how to install that... ](*,) :-D

---

### Post by Sef on 2006-07-17
To install anything read this:

[How to Install Anything.]("http://monkeyblog.org/ubuntu/installing.html")

---

### Post by Ragazzo on 2006-07-17
Many programs are in the extra repositories but you need to enable them first. [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

---

### Post by 3rdalbum on 2006-07-17
I generally recommend this order (if the package is not available in 1, try 2 etc):

1. Install from the official repositories
2. Find an unofficial repository which contains the package you want, add it to your sources.list, and then install the package
3. Find a .deb for it
4. Find a .rpm for it and convert it to a .deb using Alien
5. Find an Autopackage or a Klik for the program
6. Compile it from source
7. Try to run the Windows binary using WINE

---

### Post by Foodie on 2006-07-17
THX alot! Now i can learn that... :D

---

### Post by Dinerty on 2006-07-17
Hope you don't mind me butting in, but as your question is answered, mine is similar to this.

Some say it is better to install programs through command line as it is simpler to remove them?.

Is this true and why?

Thanks

---

### Post by Ragazzo on 2006-07-17
> **Dinerty said:**
> Hope you don't mind me butting in, but as your question is answered, mine is similar to this.

Some say it is better to install programs through command line as it is simpler to remove them?.

Is this true and why?

Thanks

They probably mean the "aptitude" command. If you use aptitude to install a program with dependencies, "aptitude remove" will remove both the program and the dependencies. apt-get (another command line command) and Synaptic usually don't remove the dependencies. I wouldn't worry too much about this; use what feels the best for you.

---

### Post by Dinerty on 2006-07-17
> **Ragazzo said:**
> They probably mean the "aptitude" command. If you use aptitude to install a program with dependencies, "aptitude unistall" will remove both the program and the dependencies. apt-get (another command line command) and Synaptic usually don't remove the dependencies. I wouldn't worry too much about this; use what feels the best for you.

Ahhh right thanks for explantion

---

### Post by T700 on 2006-07-17
> **Dinerty said:**
> Hope you don't mind me butting in, but as your question is answered, mine is similar to this.

Some say it is better to install programs through command line as it is simpler to remove them?.

Is this true and why?

Thanks

Honestly, the only time I would really be concerned is if I was installing something massive.  For instance, if I was using Ubuntu with the Gnome desktop and decided to try out KDE, I'd use the aptitude command to install it.  Just in case I wanted to remove it later, having done so will make the process magnitudes easier.

Paul

---

