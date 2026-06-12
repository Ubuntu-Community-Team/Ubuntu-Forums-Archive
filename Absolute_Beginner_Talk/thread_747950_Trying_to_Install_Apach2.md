---
title: "Trying to Install Apach2"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Esafreak on 2008-04-07
In my quest to understand Ubuntu I have decided to try to install apache. I started off by reading some threads but I have run into a problem. According to my terminal viewer it says:


> ian@ian-desktop:~$ sudo apt-get install apache2
Reading package lists... DoneBuilding dependency tree       
Reading state information... DoneSome packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstabledistribution that some required packages have not yet been createdor been moved out of Incoming.Since you only requested a single operation it is extremely likely thatthe package is simply not installable and a bug report againstthat package should be filed.The following information may help to resolve the situation:The following packages have unmet dependencies:  apache2: Depends: apache2-mpm-worker (>= 2.2.4-3ubuntu0.1) but it is not going to be installed or                    apache2-mpm-prefork (>= 2.2.4-3ubuntu0.1) but it is not going to be installed or                    apache2-mpm-event (>= 2.2.4-3ubuntu0.1) but it is not going to be installedE: Broken packages

Now I used this code I found on a forum:

> Open terminal:
Applications - Accessories - Terminal

Type into the terminal, one line at a time:
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

Also I am using UltraVNC to connect to my Ubuntu Desktop remotely. 

If anyone can help me I would greatly appreciate it. 

Ian:)

---

### Post by hyper_ch on 2008-04-07
post your /etc/apt/sources.list

---

### Post by Belliinator on 2008-04-07
Well if your using breezy you are bound to have dependecy problems, Php 5 is like a new package and breezy is old. In my opinion.

If you are using breezy than Id suggest you update if possible. This may not be the cause of the problem though.

---

### Post by AndrewEsther on 2008-04-07
I also had all kinds of trouble when I installed apache... I found that the Synaptic PM worked very well

---

### Post by Oldsoldier2003 on 2008-04-07
> **Esafreak said:**
> In my quest to understand Ubuntu I have decided to try to install apache. I started off by reading some threads but I have run into a problem. According to my terminal viewer it says:




Now I used this code I found on a forum:



Also I am using UltraVNC to connect to my Ubuntu Desktop remotely. 

If anyone can help me I would greatly appreciate it. 

Ian:)

Make sure all repos are enabled then:
```
sudo apt-get update
sudo apt-get upgrade
```
and give it another shot. Apache2 is definitely installable :)

then try again : )

just noticed he's running breezy... time to upgrade breezy is pretty old ...

---

### Post by Belliinator on 2008-04-07
Doesnt getting the latest repos stuff up the system dependencies, which makes hard to install things?

Thats what happened to me, I installed a 7.10 app on 7.04 and it makes dependencies a pain.

---

### Post by Rocket2DMn on 2008-04-07
I'm not sure Apache is even available in the Breezy repos.  Breezy actually isn't even supported anymore, support was stopped for it a year ago.  Since you seem to not like to upgrade versions very often, I suggest waiting a few weeks for Hardy Heron to be released, then do a fresh install of that.  You can stay there for up to 3 years since it will be an LTS release (like Dapper is, which was Breezy's successor).

Definitely do not try to add newer repositories to your sources.list file, but you can make sure the universe repository is enabled.

---

### Post by Oldsoldier2003 on 2008-04-08
> **Belliinator said:**
> Doesnt getting the latest repos stuff up the system dependencies, which makes hard to install things?

Thats what happened to me, I installed a 7.10 app on 7.04 and it makes dependencies a pain.

Mixing your repos instead of doing a disttro upgrade creates all sorts of issues. If you're lucky you end up with dependency problems, if you aren't you end up having to reinstall.

---

