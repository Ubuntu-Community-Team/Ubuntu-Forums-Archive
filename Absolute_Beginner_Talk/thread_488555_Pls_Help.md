---
title: "Pls Help"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by jayz_sg on 2007-06-30
Hi I have just installed the latest version of ubuntu and I have a linksys WUSB54G ver 4 wireless adapter. I am not able to acess the internet. The is I can scan for available networks and can connect to my SSID but i just cannot connect to the internet, I cannot ping anything also. I went to the net to search for some answers and I come across this ndiswrapper program, I dled it and now it is in my ubuntu desktop. I have no clue how to install this now. I really have no idea how to use linux this is my very 1st time using it. Hope anyone can help me here. I have spent many many hours on this to no avail. Thanks in advance.

---

### Post by liquidfunk on 2007-06-30
Wow! There is someone out there with the same card as me.

 Right, the first thing. Can you connect to the net via an Ethernet cable? 

 Second, there is a program called Automatix2 that allows users to download different codecs and programs with almost a single click. It is very easy to use, and a great way to start. 

 If you can get onto the Internet via an Ethernet cable go onto:

 [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

 Find the right one for your distribution and processor and download it.
 
 After installing it go into Drivers- Ndiswrapper.

 Download it. After installing it (it will do it automatically) it can be found under System - Administration-Windows wireless drivers. 

 Open it. To use Ndiswrapper with your card you need the .inf file. Which can be found on the CD. If not I can attach it, or email it to you. 

 Its quite simple to use Ndiswrapper. Just make sure you put the .inf file in a folder in Home. May be worth having the .cat and .sys files too. After that it should say it has been detected and should work. 

 Did I miss anything?

---

### Post by jayz_sg on 2007-07-02
hi, thanks for yr reply. My com is very far from my router I am not able to connect via wired connection. I tried using automatix2  but when installing there was a error. something abt dependency not satisfiable:pyhon2.4. Any idea what i can do? thanks.

---

### Post by liquidfunk on 2007-07-02
I would suggest that just for this one occasion, moving your computer would be a plus.

 On the Python matter. Python in simplest terms is a programming language. Just like Java, C/ C++, HTML etc. However using an example, think of a site you go on and it tells you that you can´t use the features on the site because it requires Java (or similar). This is the same concept, you can´t use Automatix2 because it has been written in a programming language that your computer can´t understand.

 To fix it. I don´t know how much of Ubuntu you have explored, but, click System - Administration - Synaptic Package Manager.

 The Synaptic package manager is a way of getting all the little files/programs that you want. Its very easy to use, but often you can be searching for one thing, and come out with some crazy things that you would never need. 

 The first thing to do, assuming you have never used it before is add the extra Repositories. Repositories (excuse me if i´m talking as though you are useless) are Links or gateways to servers that hold information. 

 Currently, by default your Repository will only be on the official Ubuntu server. So you may or may not be able to get what you need.

 To open up more:- Settings - Repositories - Select which ones you want. I would go with Universe, and multiverse. 

 Following that, reload the Package manager, and type in Python 2.4 in the search bar. Select it, and mark it for download. 

 You should be able to use Automatix2 now.

---

### Post by jayz_sg on 2007-07-02
hi, I have heeded yr advise and I have managed to install everything but now under the wireless driver window the hardware seems like it is not connected. And the even more funny thing is I can scan for my SSID and connect to it. Any other thing that i can do? Or maybe can u email me the driver files to my email address pls? Thanks a million. My email is [email]kazak21@gmail.com[/email]. Or another addr is [email]jayz_sg@hotmail.com[/email].

---

