---
title: "Conflicting distribution"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by bprof on 2008-04-17
I add this line to /etc/source 

deb [http://download.systemimager.org/debian](http://download.systemimager.org/debian) stable main

And the tried:

apt-get update

At the very end of the results from the above command I got this error

W: GPG error: [http://download.systemimager.org](http://download.systemimager.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F

I did some search and found according to one source that doing the following will solve the problem:

~# gpg --keyserver pgp.mit.edu --recv-keys 2D230C5F
~# gpg --armor --export 2D230C5F | apt-key add - 

Now I'm getting this error

W: Conflicting distribution: [http://download.systemimager.org](http://download.systemimager.org) stable Release (expected stable but got sid)

I'm not sure what to do next, can you please help me with this.

Thank you,

---

### Post by bodhi.zazen on 2008-04-17
What are you trying to install ?

That warning is telling you that you are mixing repos.

You should know that not all .deb are equal and the Debian .deb are not necessarily compatible with Ubuntu.

Unless you know what you are doing you should use Ubutnu .deb or compile from source.

Remove that repos from your sources and try another method.

---

### Post by bprof on 2008-04-18
> What are you trying to install ?

I'm trying to install systemimager

> That warning is telling you that you are mixing repos.

I figure that after that fact.

> You should know that not all .deb are equal and the Debian .deb are not necessarily compatible with Ubuntu.

No I know.:-)

> Unless you know what you are doing you should use Ubutnu .deb or compile from source.

I've downloaded the .deb which is found on systemimager sourceforge which I assumed that it will work on Ubuntu as I didn't find something saying otherwise. But that didn't work because the versions found for 32bit and I need 64bit, so I tried compiling from source using the directions found here

[http://wiki.systemimager.org/index.php/HOWTO_Install_from_sources_on_a_Debian_system](http://wiki.systemimager.org/index.php/HOWTO_Install_from_sources_on_a_Debian_system)

> Remove that repos from your sources and try another method. 

I did, but I can't make it work. So right now I'm trying to clean my system from the compiled version and try one more method.

Can you please help me in knowing how to clean the installation of a package from the source?

This is one of the few things I don't like about Linux in general, in Windows its easy to uninstall an application with all its components. I wish this is the case with Linux.

---

### Post by bodhi.zazen on 2008-04-18
It depends a little. If the maintainers are kind you can :

```
make uninstall
```

Otherwise you have to do it manually.

```
sudo updatedb
sudo locate systemimager
```

Delete anything found by the locate command. Typically much cleaner then with windows as many applications in windows leave lots of baggage or require editing system files.

In reading the link it appears as if you simply download the source code, extract, cd into the directory, and then ```
sudo make deb
```

That should make a .deb. Install it with 

```
sudo dpkg -i systemimager*.deb
``` Of course change the name to the appropriate .deb

Install dependencies with:

```
sudo apt-get install -f
```

---

