---
title: "[SOLVED] Error installing Java"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by penguinbreath on 2008-01-31
For some reason today, Java is not on my computer. (Not sure why?) I go to Adept and select the Java programs, and I just get an error.

I tried just installilng Java 1.4 plugin and i get this:

```
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not going to be installed
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

My Linux box seems to be acting strange, and I'm hoping its just me. Any ideas whats going on?
I'm kind of a newbie so it might just be something I'm missing, but I cannot figure out what.

I am using a Kubuntu Feisty setup someone gave me.

---

### Post by emarkd on 2008-01-31
The newer java versions are restricted.  

First, enable all the software repositories:
    1.  Launch Synaptic by clicking on System > Administration > Synaptic Package Manager
    2.  On the menu, select Settings > Repositories
    3.  Select all the boxes except Source code (unless you want that)
    4.  Click close
    5.  Back on the main Synaptic screen, Click Reload to update your local cache

Now you can use the search feature to find sun-java6 or whatever you need.

---

### Post by jan quark on 2008-01-31
try this

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by penguinbreath on 2008-01-31
I am using Kubuntu, but I started synaptic and got this:

```
You have 2 broken packages on your system!

Use the "Broken" filter to locate them..

```

I hope something important didn't break. Recently my graphics driver broke and I had to reconfigure it. Should I run this "filter" thing?

---

### Post by penguinbreath on 2008-01-31
> The newer java versions are restricted.

First, enable all the software repositories:
1. Launch Synaptic by clicking on System > Administration > Synaptic Package Manager
2. On the menu, select Settings > Repositories
3. Select all the boxes except Source code (unless you want that)
4. Click close
5. Back on the main Synaptic screen, Click Reload to update your local cache

Now you can use the search feature to find sun-java6 or whatever you need.

I believe I have the restricted packages enabled.


> try this

Code:

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin




I got this: 
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not going to be installed
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-11-1ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Any ideas? :(

---

### Post by emarkd on 2008-01-31
They're in the universe or multiverse repositories.  Did you check to see if those repositories are enabled?

---

### Post by penguinbreath on 2008-01-31
I cannot open synaptic package mananger, I get this:

```
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

This is starting to freak me out, and I'm begining the download of Ubuntu  7.10 which I might just install. I am also making back ups. 

After I back up the system, should I fix this or should I just install a new Ubuntu?

---

### Post by jan quark on 2008-01-31
what happens when you type 
```

sudo apt-get -f install
```

into the terminal ?

no wait we will guide you till the bitter end :lolflag:

---

### Post by RomeReactor on 2008-01-31
Hi. Try running:
```
sudo apt-get install -f
```
from Konsole.

---

### Post by penguinbreath on 2008-01-31
> what happens when you type
Code:

sudo apt-get -f install

into the terminal ?

no wait we will guide you till the bitter end 

> 
Hi. Try running:
Code:

sudo apt-get install -f


My Java is now fixed, thanks! :) 

In some ways this problem was a good thing, it scared me into making a needed backup.

Still wonder why Java disappeared though..... Funny things like that have been happening a lot recently. :lolflag:


Thanks for the input everyone.

---

