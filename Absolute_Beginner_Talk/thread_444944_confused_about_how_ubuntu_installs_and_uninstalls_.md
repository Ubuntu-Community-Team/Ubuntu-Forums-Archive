---
title: "confused about how ubuntu installs and uninstalls programs"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-15
So far I've been doing sudo apt-get install to install programs and it's been working out great.  I was curious, though, as to what really happens when you do apt-get

1. does it just copy files to your folder?  or does it install .dll's around like windows
2. does sudo apt-get remove totally get rid of it?
3. how does apt-get know where to get the files?
4. is it better to simply download tar files and install them yourself?  if so, how do you then "uninstall" something  when you've downloaded the install files yourself?

---

### Post by raja on 2007-05-15
apt-get is a frontend to a package manager. You have a file called /etc/apt/sources.list which is a list of online repositories from which you can download packages. apt-get queries these sources and gets a list of available applications. When you do 'apt-get install', it looks to see if the package is available and what its dependencies are, then downloads them and installs them for you. apt-get remove removes the application, but it is better to use apt-get --purge remove if you want to cleanly remove (including config files). 
If the application you want is available in the repositories, it is better to install it this way than to try to compile it yourself. If the application is not available, or is an older version than you want, look for a .deb file if possible. Trying to get the source files as a .tar.gz and compile it yourself is always a little dicey.

---

### Post by Obor on 2007-05-15
Bit of background reading oif you want
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by sthapit on 2007-05-15
thanks!  read both articles, was very informative.  i still don't know what the proper way to uninstall programs is though once you've installed a .tar.gz file.  for instance, i installed rubygems in this manner:

sudo wget [http://rubyforge.org/frs/download.php/17190/rubygems-0.9.2.tgz](http://rubyforge.org/frs/download.php/17190/rubygems-0.9.2.tgz)
tar -xvzf rubygems-0.9.2.tgz
cd rubygems-0.9.2
sudo ruby setup.rb

it's running great, but it kind of bothered me that i knew nothing about how to properly go about removing rubygems if i ever wanted to.

---

### Post by zvacet on 2007-05-15
I belive you can uninstall it with synaptic or 

```
sudo apt-get --purge remove rubygems-0.9.2
```

---

