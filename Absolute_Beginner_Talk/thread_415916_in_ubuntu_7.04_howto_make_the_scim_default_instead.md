---
title: "in ubuntu 7.04 howto make the scim default instead of nabi?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by matiz on 2007-04-20
Hello, I'm not the native Korean speaker

I just update the ubuntu to 7.04 from 6.10,
and I change the default language to Korean before login to the X, but the default input method is nabi, here I want to use scim, how can I change it ? 

please help, thanks.

---

### Post by hagabaka on 2007-04-20
Hello, try
sudo apt-get install --reinstall scim
sudo dpkg reconfigure scim

If it doesn't make scim the default input method, maybe follow the instructions on [http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu](http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu)

---

