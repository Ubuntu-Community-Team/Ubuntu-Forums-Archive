---
title: "i just downloaded this /k3b-0.8-i18n/ how can i install it?"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-07-28
i got the idea of useing synaptic manager but how do i install additional apps?

---

### Post by sonny on 2005-07-28
If by that you mean apps that are not in the repositories that's easy, but I should recommend you to first search in the repo's and then searching in the internet, cuz the apps in the repos had been prepackage for Ubuntu.

Installing a *.deb file:
sudo dpkg -i app.deb

Installing from souce (accepting the defaults):
cd to the folder you have the app (already uncompressed)
then type:
./configure
make
makeinstall

Installing an autopackage:
double-click in it, and thats all.

Installing a *.run or *.sh file:
sudo sh app.run or app.sh

sometimes you are require to make the file executable, just type
sudo chmod +x /path/to/the/file.run

I guess that pretty much covers it.

---

