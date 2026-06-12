---
title: "using apt"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-07
Hello Forum,

i am new to Linux and i have put Kubuntu onto my machine. 

i have discovered that APT GET seams the best for me to install software easily.

I have installed the Xfce desktop and it works very well...the command was

sudo apt-get install xfce4
----------------------------------------------------------------------------------------------------------------------

Please can you tell me if i am able to install and run Linux tools on Xfce...if the tools mention that they need Gnome...?

my system does not have Gnome..What will happen if i try to install such tools? 

Does linux automatiically get the required Gnome libraries and dependencies that a tool requires and install them? (using package manager)

My basic question is....can you still use linux tools that mention they need Gnome...while being inside a desktop that is not gnome? (xfce)

thanks

Vince.

---

### Post by DariusS on 2008-04-07
my initial thought is yes. I have gleaned from other threads that KDE apps work in gnome because ubuntu will instal the needed libraries for it to work. so similarly, I would expect xfce and gnome or KDE apps would work interchangeably in the same manner. 
note: I've also heard that this installation of dependent libraries causes an app to be slightly more demanding memory wise....

---

### Post by runemaste644 on 2008-04-07
I would install gnome to be safe. Xfce is a lightweight version of Gnome basically, but it wouldn't hurt to install gnome. I have all window managers installed which is always convenient, i can run any application from any window manager.

---

### Post by Bölvaður on 2008-04-07
> **vinceUUUU said:**
> Does linux automatiically get the required Gnome libraries and dependencies that a tool requires and install them? (using package manager)

apt-get is a package manager which makes sure all your dependencies are met and there is no dependency conflict (dll hell).
It also auto updates all your (package manage) program according to your repositories.

3 years ago a friend from my university showed me his Debian computer and he was so proud of how apt-get worked. I hope you have slight enthusiast about it also ;)

---

### Post by szymon_g on 2008-04-07
i would recommend to use aptitude instead of apt-get.
aptitude will remember dependencies of all packages installed by it- so, when you will uninstall programs, it will uninstall them as well (of course if they arent needed by other programs).

---

### Post by brian_p on 2008-04-07
> **vinceUUUU said:**
> Does linux automatiically get the required Gnome libraries and dependencies that a tool requires and install them? (using package manager)

That's exactly it! You have a good understanding of how the packaging system works.

> My basic question is....can you still use linux tools that mention they need Gnome...while being inside a desktop that is not gnome? (xfce)

Yes.

---

### Post by vinceUUUU on 2008-04-07
Hello Forum people,

thanks very much for your advice.

Please can you tell me what the APT command is for installing Gnome?...the one line command?

thanks again

Vince.

---

### Post by hyper_ch on 2008-04-07
Probably:
```

sudo apt-get install gnome

```

But you can install the Ubuntu modified gnome desktop by running:
```

sudo apt-get install ubuntu-desktop

```

---

