---
title: "A simple script to auto-install some programs"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Christmas on 2006-04-17
I made this simple script so I can auto-install some programs after a fresh install just by running it. Here it goes:

```

#!/bin/bash
sudo apt-get install beep-media-player tvtime dcpp abiword anjuta gnomebaker xubuntu-desktop
```

Now, when it begins the installation of xubuntu-desktop it asks me if it's OK to install all the packages, and the answers can be (Y)es and (N)o. Since I will choose Yes every time I am wondering if there is a solution for including this answer in the script so I won't need to type "y" everytime a package is installed. Anybody please?

PS: The xubuntu-desktop was just an example, I will include lots of packages in this script and I was also thinking about running a C program to create some configuration files that I can find useful.

---

### Post by aysiu on 2006-04-17
Change your code to this: ```
#!/bin/bash
sudo apt-get -y install beep-media-player tvtime dcpp abiword anjuta gnomebaker xubuntu-desktop
``` From the man page for apt-get: >  -y, --yes, --assume-yes
              Automatic  yes to prompts; assume "yes" as answer to all prompts
              and run non-interactively. If an undesirable situation, such  as
              changing  a  held  package,  trying to install a unauthenticated
              package or removing an essential  package  occurs  then  apt-get
              will abort. Configuration Item: APT::Get::Assume-Yes.

---

### Post by Christmas on 2006-04-17
Thanks a lot aysiu, I'll try it right now.

---

