---
title: "apt-get"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by nagileon on 2007-08-02
Hi there !

I'm doing this:

[http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)

And my source.list looks like that

root@rails:~# cat /etc/apt/sources.list
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

I did apt-get update

but if I'm trying to run:

apt-get install ruby rubygems irb ri rdoc ruby1.8-dev build-essential

I get:

root@rails:~# apt-get install ruby rubygems irb ri rdoc ruby1.8-dev build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package rubygems

What's up ?

Cheers

---

### Post by renzokuken on 2007-08-02
might be worth trying the method in the link below

[http://www.stoneageblog.com/articles/2006/11/20/ubuntu-edgy-eft-installer-rubyonrails-eclipse-radrails](http://www.stoneageblog.com/articles/2006/11/20/ubuntu-edgy-eft-installer-rubyonrails-eclipse-radrails)

ignore the french text and just use the commands in green with the black background

---

