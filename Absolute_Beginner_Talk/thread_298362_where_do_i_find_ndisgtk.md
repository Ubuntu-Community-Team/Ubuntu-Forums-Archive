---
title: "where do i find ndisgtk"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-12
Sorry, for this silly question, I have searched the forum but i have not figured out where to find ndisgtk?

---

### Post by K.Mandla on 2006-11-12
You might have to be connected to the Internet to install that (ironic, isn't it?). I see that [it's in the universe repository]("http://packages.ubuntu.com/dapper/net/ndisgtk").

ndiswrapper-utils should be on your Ubuntu CD. That's, unfortunately, reliant upon the terminal, but you might be able to get a wireless card working with that.

---

### Post by PartisanEntity on 2006-11-12
I dont have any access to the internet on that machine yet, can I download ndisgtk manually?

-- never mind, i downloaded it and copied it to my usb hdd and moved it over to the laptop, will play around with it now.

---

### Post by K.Mandla on 2006-11-12
Hmm. :-k You can try it and it might work. Follow that link and find a working download page. Transfer it over to the offline machine and install it with a double-click or with *sudo dpkg -i ndisgtk*.deb*.

My fear is that there are dependencies to that file that aren't installed by default. You'll know if that is a problem; it will no doubt tell you. :rolleyes:

There are ways to install updates and new software on machines that are offline. It's usually a pain, though.

What kind of hardware are you working with?

---

### Post by PartisanEntity on 2006-11-12
I installed Ubuntu 6.10 on my Asus A6K laptop. I am trying to get my Asus wifi card to work, it has a BCM4306 chip, I tried several tutorials but they did not work.

I read that sometimes it (wifi set up) works simply by using ndisgtk even though its just the user interface (if i understood i correctly).

---

### Post by K.Mandla on 2006-11-12
The 4306 shouldn't give you too much trouble. I had a 4318 and it took a little work.

There are a lot of pages in the Howto section that might be of use to you, but it's possible you've already seen them.

[http://www.ubuntuforums.org/search.php?searchid=9736113](http://www.ubuntuforums.org/search.php?searchid=9736113)

Is there no wired network connection on your laptop? It might be easier to connect to a wired port, install ndisgtk, then disconnect.

---

### Post by PartisanEntity on 2006-11-13
The wifi router is on the top floor here at home, and my laptop is on the lower floor, I don't have a cable anywhere in the house.

I guess I could go out any buy one, but if I can't get Ubuntu to work with my wifi card then ill have to switch back to Win XP, I need the wifi to work :)

---

### Post by K.Mandla on 2006-11-13
That's understandable. The trick is that it might be *easiest* to install the wifi by hooking it up to a wired connection first. Then, once everything is set up, disconnect and run wireless.

---

### Post by PartisanEntity on 2006-11-13
hmm..okay if the current method i use (to download everything i need manually in winxp and then reboot to ubuntu) doesn't work, ill go out and get a cable to connect to the router.

---

