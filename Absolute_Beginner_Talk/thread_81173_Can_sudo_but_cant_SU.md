---
title: "Can sudo but cant SU?"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2005-10-23
I can sudo something but i can't SU in.

here 
hans@hans:~$ su
Password:
su: Authentication failure
Sorry.

but i can sudo somehting in things.

I have gone about a month with working aorund using su but now i need to.  What can i do to fix this

---

### Post by ltmon on 2005-10-23
[https://wiki.ubuntu.com/UsingSudo](https://wiki.ubuntu.com/UsingSudo)
[https://wiki.ubuntu.com/RootPrivileges](https://wiki.ubuntu.com/RootPrivileges)

---

### Post by aysiu on 2005-10-23
Read this:

[http://64.233.167.104/search?q=cache:avJKczQuT34J:https://wiki.ubuntu.com/RootSudo+site:ubuntu.com+rootsudo&hl=en](http://64.233.167.104/search?q=cache:avJKczQuT34J:https://wiki.ubuntu.com/RootSudo+site:ubuntu.com+rootsudo&hl=en)

---

### Post by hansoffate on 2005-10-23
thanks

---

### Post by ctcecil on 2005-10-23
heh I JUST pasked about this.
to setup your root password:

$ sudo passwd root

...then enter your password for the account you created at setup, and then it will prompt for a password.

---

### Post by Redindian on 2005-10-23
I'm not sure what you are asking for but try this 

Your name@yourcomputer:~$ sudo su
password: enter password
Your name@yourcomputer:#

---

### Post by daone on 2005-10-23
I've been really disappointed with Ubuntu 5.10 Breezy in that I have yet to get su to work in the terminal.

In this posting alone, people keep saying use sudu in the ternminal. While I have always just used su to turn a normal terminal into a root terminal.

I tried Redindian's suggestion to get a root terminal. And the commands entered got the same result I have always gotten with Breezy.

Such as "bash: sudu: command not found"
 
su  + usr passwd = "su: Authentication failure"

Now this is a brand new install I just created tonight on 10-23-05, I only installed a single account durring install. And root along with su have been completely disabled in 5.10.

I tried as well to change the root terminal and this is the result I got, "passwd: You may not view or modify password information for root.".

Do the Ubuntu Development team really hate the terminal?

---

### Post by invalid on 2005-10-23
[QUOTE=daone]I've been really disappointed with Ubuntu 5.10 Breezy in that I have yet to get su to work in the terminal.

In this posting alone, people keep saying use sudu in the ternminal. While I have always just used su to turn a normal terminal into a root terminal.

I tried Redindian's suggestion to get a root terminal. And the commands entered got the same result I have always gotten with Breezy.

Such as "bash: sudu: command not found"
 
su  + usr passwd = "su: Authentication failure"

Now this is a brand new install I just created tonight on 10-23-05, I only installed a single account durring install. And root along with su have been completely disabled in 5.10.

I tried as well to change the root terminal and this is the result I got, "passwd: You may not view or modify password information for root.".

Do the Ubuntu Development team really hate the terminal?[/QUOTE]

Perhaps if you take a look at the links posted earlier, they will help explain.

sudu, I might add, is not a command - thats why you are getting an error. It's "sudo"

Simple answer: "sudo -i" will give you a root shell.

Do some reading people.

Cb

---

### Post by daone on 2005-10-24
Invalid, these kind of post replies are what are really frustrating me with Breezy release.

I did and have figured out that sudu is not a command, but what is asking me to enter a password everytime I try to access anything that controls the system like Synaptic Package Manager.

I did read the earlier links that were posted and they informed nothing I didn't already know. I understand that the ubuntu team purposely disables the root account. The links that were mentioned apply to Hoary 5.4 release.

The links and all postings I have found have yet to explain why is it impossible to change a standard terminal into a root terminal with su. The password required is supposed to be the password that was entered for the first user.

Everytime I enter my password, I get a momentary lag and than get the permission denied reply.

Can someone or else correct me and explain how can I enter the password for su when asked and not get a permission denied error.

I never had this problem with Hoary release and I may go back if no one can explain how to get a root terminal.

---

### Post by daone on 2005-10-24
People can disregard my last post, I finally figured out how to get the root terminal.

After adding the run command applet to the gnome menue, I entered the command Invalid showed and entered my user password and was able to get a root terminal.

I had a moment of "can't see the trees thru the forest" and wasn't seeing that people weren't saying use sudu -i to get a root terminal but instead use sudo -i to get a root terminal.

Again, sorry for the last post, was glad I was able to learn how to get a root terminal in Breezy release.

---

### Post by codejunkie on 2005-10-24
[quote=daone]People can disregard my last post, I finally figured out how to get the root terminal.

After adding the run command applet to the gnome menue, I entered the command Invalid showed and entered my user password and was able to get a root terminal.

I had a moment of "can't see the trees thru the forest" and wasn't seeing that people weren't saying use sudu -i to get a root terminal but instead use sudo -i to get a root terminal.

Again, sorry for the last post, was glad I was able to learn how to get a root terminal in Breezy release.[/quote] if you don't like using sudo you can also enable the root user account with this command 
```
sudo passwd root
``` that way you can just use ```
su
``` and enter the root password to be root.

---

