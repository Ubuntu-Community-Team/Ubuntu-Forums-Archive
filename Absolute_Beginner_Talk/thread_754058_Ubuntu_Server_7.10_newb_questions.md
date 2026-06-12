---
title: "Ubuntu Server 7.10 newb questions"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Frequent Modulation on 2008-04-13
Extremely new to linux anything. My goal is to use Ubuntu server as a web server. 

 I am wanting to stay within the cli. I do not want to 'revert' to a desktop. I think learning the command line can be more powerful once learn how to use it to its fullest potential.

A few questions I hope to get answered:

1. Is there a way to hop online through the cli? I have installed firefox but when i type firefox in at the prompt, i get a some gtk message (not in front of machine at this moment). For example, how can i get to these forums from the ubuntu server cli prompt?

2. I need to install joomla. How can i get joomla from the web? would that be an ftp server that i would need to locate? How would i find joomla through the cli and get it installed?

3. how do i get find out if i am using apache or apache2? Does it really matter which one i am using? is there a 'how to' for using the AMP through ubuntu server?


Your insight will be helpful. :)

---

### Post by Shiva88 on 2008-04-13
As for your first question:

try sudo apt-get install links elinks

There are a variety of cli internet browsers out there, those are two of the more common.

---

### Post by wolfen69 on 2008-04-13
you can use elinks to browse in cli.
```
sudo apt-get install elinks
```there are others, but i dont think there is much difference between them.

not sure about your other questions.

---

### Post by crashcoredump on 2008-04-13
To just jump online you will need a window manager (at least to do it graphically) you can always get to the internet for ftp or in text from the cli.

What would you want to get to the web for? Because you can grab and install packages without the graphical interface.

I have an Ubuntu server at work that has X installed which rarely get used. But it is there if for some reason we need to use it. If you have the disk space I do not see where its an issue. I think you can even do something like apt-get install gnome to get all the items you would need.

Thanks and good luck,

-J

---

### Post by Shiva88 on 2008-04-14
To clarify-

There are a number of command-line based web browsers that you can use to hit the web from a CLI environment.  I'm familiar with three- links, elinks and lynx, undoubtedly there are others.  These browsers are perfectly good for quickly looking up something if you need a hand in administering your system, but the browsing experience with them is much, much different than what you're used to using Firefox.  If you're looking for something to use on a daily basis, you're better off following crashcoredump's advice and going for the full GUI.  

All that said, I find that having those CLI browsers installed on my systems is useful from time to time, and I tend to find myself installing them.

---

### Post by adamos on 2008-04-15
I am running 8 servers with ubuntu 7.1 and GUI slows down ur servers. Its useless if you know what you are doing. For quick reference pick Beginning ubuntu server admninistration from novice to professional and you will be up and running in no time. 

joomla is really easy. install vsftpd and create an account for the ftp layer to overcome permission issues. 

good luck

Adam

---

