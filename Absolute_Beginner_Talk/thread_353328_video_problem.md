---
title: "video problem"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by lambert11 on 2007-02-04
cant watch any video from cnn.com  website. what  program do i need to install.

---

### Post by shareMenaPeace on 2007-02-04
You might have a look here on firefox plugins - in your case for video.

[https://help.ubuntu.com/community/FirefoxPlugins?highlight=%28plugin%29%7C%28firefox%29](https://help.ubuntu.com/community/FirefoxPlugins?highlight=%28plugin%29%7C%28firefox%29)

Another way is to use [http://getautomatix.com](http://getautomatix.com) an automatic install application. Which features browser plugins, codecs, tools.

---

### Post by Gerard Barberi on 2007-02-04
The plugin for the videos was WMP and can be played through mplyer plugin (with the right codecs).

install automatix (it's easiest)

sudo gedit /etc/apt/sources.list 

Add this to the end of the file (change edgy to dapper if you are on dapper)

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

Get the key

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

update 

sudo apt-get update

install

sudo apt-get install automatix2

run it

automatix2

it will want a root password and give you a warning about illegal codecs.

check off mplyer plugin under "multimedia" and multimedia codecs.

That should be enough.  Install any other programs as well.

---

