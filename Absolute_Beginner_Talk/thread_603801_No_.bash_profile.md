---
title: "No .bash_profile ????"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-11-05
I seem to not have a .bash_profile.

I was following along with a tutorial and came across this:

> if [ -f .bash_profile ]; then
                    echo "Yes,  it exists."
                else
                    "No, it doesn't exist."
                fi

My answer was, "No, it doesn't exist."

I don't know what it is, nor why I don't have it.

Can I get some help on this please? In simple language, if possible.

Thank you

---

### Post by mali2297 on 2007-11-05
You don't get a **.bash_profile** by default in Ubuntu. The corresponding file is called **.profile** instead. You can however create a .bash_profile file if you want.

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html)

> 
3.1.2.1. ~/.bash_profile

This is the preferred configuration file for configuring user environments individually. In this file, users can add extra configuration options or change default settings


> 
3.1.2.3. ~/.profile

In the absence of ~/.bash_profile and ~/.bash_login, ~/.profile is read. It can hold the same configurations, which are then also accessible by other shells. Mind that other shells might not understand the Bash syntax.


---

### Post by nick_h on 2007-11-05
You do get a **.bashrc** file though which is a bash configuration file for each user.

---

