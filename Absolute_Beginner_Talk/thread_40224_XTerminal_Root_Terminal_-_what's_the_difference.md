---
title: "XTerminal Root Terminal - what's the difference?"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by Mr. Electric Wizard on 2005-06-08
Hello everyone,
First off, I have never run Linux before!
I Just installed Hoary Hedgehog last night and I have to say WOW!
(I have never been so lost with a PC! :? )

My first Question is about the 2 terminals under programs.
What is the difference between XTerminal and Root Terminal?
When I run Root Terminal, does this automatically log me in a Sudo/Root?

I have found out that I need to log in as Root in order to be able to edit my /etc/network/interfaces file...
When I do this in the "FileManager" it says it is read only, and I can't seem to access this file with the Root Terminal either?

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=Mr. Electric Wizard]Hello everyone,
First off, I have never run Linux before!
I Just installed Hoary Hedgehog last night and I have to say WOW!
(I have never been so lost with a PC! :? )

My first Question is about the 2 terminals under programs.
What is the difference between XTerminal and Root Terminal?
When I run Root Terminal, does this automatically log me in a Sudo/Root?
[/QUOTE]
Yes. 
> 
I have found out that I need to log in as Root in order to be able to edit my /etc/network/interfaces file...
When I do this in the "FileManager" it says it is read only, and I can't seem to access this file with the Root Terminal either?

Usual way of doing thigns that require root priviliges in Ubuntu (such as editing /etc/networks/interfaces) is via sudo. E.g., type (in usual terminal window, not root)
sudo gedit /etc/network/interfaces
or type in root terminal 
gedit /etc/network/interfaces

However, most common tasks can be done by using graphical tools in system menu.

---

### Post by Mr. Electric Wizard on 2005-06-08
Thanks for the fast response!

Do you know how I should proceed with getting my network connection running?
I have two devices that show up in the Network Settings screen under the ping command.  I can ping localhost fine, but cannot ping my dhcp server, or the gateway?

I had problems with this when I installed, and decided to install and configure network later.

I would like to use my Microsoft MN-510 Wireless adapter (non-broadlogic board - Prism 2 chipset), but I also have a wired nic that I can use.

---

### Post by Mr. Electric Wizard on 2005-06-08
Will it be easier to just go wired for Ubuntu?

How should I troubleshoot my wired nic?

Help! ](*,)

---

### Post by Mr. Electric Wizard on 2005-06-08
Well, I installed my nic in another PC, and Voila!  Bad Nic. :-x 
After getting a new nic I think I'm going to go through the Install process again, and see if I have more luck the second time around...

---

