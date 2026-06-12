---
title: "Application Installation"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by kbarz on 2006-05-06
Hi,

I'm trying to install the ColdFusion developer edition on my Ubuntu.  I can get the installer to run just fine, but then I get a message saying that it tried to run:

rpm --query compat-libstdc++

to determine if something called a c++ compatability pack was present.  It also says that this has to be there if I have glibc 2.2.5x or higher.  So, how might I tell what glibc I have and if I have (or where to get) the c++ compatability pack?

Thanks

---

### Post by Mustard on 2006-05-06
Some more information on what type of installer it is and where you got it from might be helpful. The fact that the term 'rpm' is appearing in the output makes me curious what method you are using to install this application.

You might also try using the apt-cache search and apt-cache show commands to look for packages and display information about them.  As an example you could try..

```
apt-cache search libstdc++
#this will list packages according to the keyword search
```

An example of an apt-cache show command would be this..

```
apt-cache show libstdc++5-3.3-dev
#this will display information on a particular package
#so you can get the version information etc..
```

Also you can find package information at this website [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

