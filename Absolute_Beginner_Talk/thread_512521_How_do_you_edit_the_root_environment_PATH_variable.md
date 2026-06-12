---
title: "How do you edit the root environment PATH variable"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by tekNinja on 2007-07-29
I have combed the web trying to figure this out.. I have edited my $HOME/.profile .bashrc and .bash_profile files and my /root/.bashrc .bash_profile .profile files and my /etc/.profile but I just CANNOT change the root environment PATH variable.  

Whenever i type sudo env PATH is always unchanged.

The line I am entering is
```

export PATH=$PATH:<directories I want added> 
```

What am I doing wrong?  Help greatly appreciated...

---

### Post by dfreer on 2007-07-29
You might want to try doing it AS root, if you haven't already:
```
sudo su
```
And then do the command, only without sudo (since you will be root at this point).

---

### Post by bodhi.zazen on 2007-07-29
> **dfreer said:**
> You might want to try doing it AS root, if you haven't already:
```
sudo su
```
And then do the command, only without sudo (since you will be root at this point).

That will set the path for a single session.

Add two lines (to /root/.bashrc) :

PATH=$PATH:<directories I want added>
export $PATH

to change it for all sessions.

You can also add 

source /root/.bashrc

to /root/bash_profile

---

### Post by tekNinja on 2007-07-29
> **bodhi.zazen said:**
> That will set the path for a single session.

Add two lines (to /root/.bashrc) :

PATH=$PATH:<directories I want added>
export $PATH

to change it for all sessions.

You can also add 

source /root/.bashrc

to /root/bash_profile

so if I add the following (also can I do it in one like this or should I have the export statement on a second line?):

```
export PATH=$PATH:<directories I want added>
```

to /root/.bashrc

and then add

```
source /root/.bashrc
```

to /root/bash_profile this will permanently change my root environment PATH variable?  So if i do a 

```
sudo env
```

it will finally list the new PATH?

Sorry for the newbishness, but thanks~!

---

### Post by bodhi.zazen on 2007-07-29
Well, with sudo you use your path, not root's path ;)

So, add that stuff to your users .bashrc

For more information see man sudo and look at the difference between sudo -i and sudo -s

With sudo -i you use root's environment (ex /root/.bashrc) and with sudo -s you use your users environment.

---

