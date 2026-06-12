---
title: "Trouble installing NdisWrapper, as well as getting wireless internet working"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-09-23
Hey, everyone.

I just installed ubuntu last night in a dual-boot system. I put it on a seperate drive (apperantly one where my audio drivers were, because those have vansished), and I can't get my Linksys wireless-G USB adaptor to work. Unfortunately, plugging the computer in to a lan cable is not an option.

I've read a bit about it and it said something about ndiswrapper and such, which I downloaded, but I could not figure out how to install. I don't understand any of the terms in the readme.

Can anyone please send me a link (I really don't expect anyone to write me a novel just so I can get my internet working) to a detailed walkthrough of how to solve this problem that I can understand?

---

### Post by jd65pl on 2006-09-23
Have a look at [this.]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

Also name your posts more cleverly in the future. > "I'm a noob" subjects don't help anyone

---

### Post by jd65pl on 2006-09-23
Also this may help you

[http://ubuntuforums.org/showthread.php?t=189048&highlight=Linksys+wireless-G+USB]("http://ubuntuforums.org/showthread.php?t=189048&highlight=Linksys+wireless-G+USB")

---

### Post by theknave on 2006-09-23
I changed the title, sorry.

I don't understand these instructions, though. Where am I to type these commands?

---

### Post by ishift on 2006-09-23
this helped me a lot:

[http://ubuntuforums.org/showthread.php?t=85378](http://ubuntuforums.org/showthread.php?t=85378)

---

### Post by theknave on 2006-09-23
Thank you ishift! It seems like this graphical interface version will help a lot.

I'm going to reboot in ubuntu and give it a whirl.

---

### Post by jd65pl on 2006-09-23
In linux alot of things can be done via the terminal. It would probably be of benefit to read up on using the terminal if you wish to use linux as it is a very powerful tool.

You may find this useful

[https://help.ubuntu.com/community/BasicCommands]("https://help.ubuntu.com/community/BasicCommands")

You would open a terminal window by navigating through...

Apps > Acessories > Terminal

Thanks

J

---

### Post by theknave on 2006-09-23
Thank you, JD. Yes, I'd suspected the terminal before, but never was sure. I'm going to read this basic commands page, and then I will get to work trying this GUI version of ndiswrapper.

Thanks, guys!
Brett

---

### Post by theknave on 2006-09-23
Okay. So in order to get this business working, I had to take my computer downstairs and plug it in in place of my sister's computer. I've got all that ndiswrapper and ndiskgtu or whatever installed and working, but whenever I try to activate it, my computer freezes. Upon checking the windows wireless drivers section, I have seen that it says "Device connected: No"

I assume I need to use a different driver -- I was using the one from my CD that I got with the adaptor. It is a Linksys Wireless-G USB Network Adapter, model number WUSB54G.

Another thread said to use "r2x00" drivers (or something to that effect), but upon downloading those, I cannot locate a .inf file.

---

### Post by jd65pl on 2006-09-24
What card have you got, try searching for it to see what other people have used to get it working.

J

---

