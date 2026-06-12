---
title: "kubuntu desktop"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by walterius on 2006-08-26
using the following code:

```
sudo apt-get install edubuntu
sudo apt-get install xubuntu

```

I sucessfully added those desktops as options to my base Ubuntu install. (Btw I love Edubuntu, which is child-like without being childish.)

However, This code doesn't work:

```
sudo apt-get install kubuntu
```

It crashes. Attempts to install KDE using Synaptic also fail.

Any ideas? Meanwhile I will fiddle.... :-({|=

---

### Post by Klaidas on 2006-08-26
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html) :)

The main thing is that you should use "kubuntu-desktop"
But I recommend reading the whole article :)

---

### Post by walterius on 2006-08-26
Apologies. :oops: I had typos in all three lines of code:
kubuntu-desktop, etc. My original attempt used the correct code (-desktop).

But the problem persists.

Thank you.

---

### Post by az on 2006-08-26
> **walterius said:**
> 
It crashes. Attempts to install KDE using Synaptic also fail.


What do you mean it crashes?

Be specific, post the errors.


Also, what happens when you run

sudo apt-get -f install

from the command line?

---

### Post by Paul133 on 2006-08-26
```
 sudo apt-get install kubuntu-desktop 
``` doesn't work?! Are you sure?  

Edit: Here's what I got when I tried it. Perhaps you got something similar:
```
peter@ubuntu:~$ sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: language-selector-qt but it is not going to be installed
E: Broken packages
peter@ubuntu:~$


```

---

### Post by bccomm on 2006-08-26
I get the same thing. Seems to be language-selector-common being lame.

---

### Post by Bachstelze on 2006-08-26
Could you paste your sources.list ?

---

### Post by walterius on 2006-08-26
Gentlemen:

I'm sorry. I'm so dumb with linux that sometimes I make foolish mistakes. I followed instructions given at one of the links above, and after a bit of tweaking, Kubuntu installed. It was never broken. I just didn't understand it. :-\"

---

