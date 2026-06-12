---
title: "accessing Ubuntu 5.10 through openssh on my Intel Imac"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by johnroch on 2006-05-07
I have openssh set up on my Ubuntu pc. I can see my Imac computer files ok but from my Imac I cant access my Ubuntu pc. I have remote login activated on my Imac but when I use connect to server through Finder Im unable to figue out what to input for server address, if this is the proper way to get connected. I would appreciate any help on this, by the way this is my first time using linux on my pc so im very green on the terminology.

---

### Post by kaamos on 2006-05-07
Hello and welcome to the forums!

You probably have done this already but to install the ssh server:
```
sudo apt-get install ssh
```
It's been a while since I've used a mac, but I'm not sure if finder supports ssh. Anyway, you can test if the server works by opening a terminal on you mac and typing
```
ssh johnroch@xx.xx.xx.xx
```where johnroch is your ubuntu username and xx.xx.xx.xx is the ip address of your ubuntu machine. You can find out the ip in ubuntu with the command "ifconfig" in terminal. If the server works ok, you can then install a graphical ssh program on your mac. I remeber using something called fugu. You can get it from [here](http://www.apple.com/downloads/macosx/internet_utilities/fugu.html).

Hope this helps some.

---

### Post by johnroch on 2006-05-08
Thanks for the suggestions neither one got me any closer but im still trying to figure this out. Ill post my progress.

---

### Post by Compwiz on 2008-01-28
I did exactly what johnroch said, and i can ssh perfectly into my Ubuntu machine from my intel mac, right from the terminal

what im wondering is if its possible to copy files from ubuntu to the mac via ssh?

---

### Post by steveneddy on 2008-01-28
This is an old thread.

Do the instructions from 5.10 carry over to 7.10?

---

### Post by shad0w_walker on 2008-01-28
They should carry over just fine. ssh hasn't really changed in a fair while.

---

