---
title: "Root user password??? - did I ever enter one?"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2005-12-29
Hi all, (and merry x-mas)

My first post here - installed Ubuntu Breezy about a week ago, and from what I have read on the web I need to login as root user to be able to install java plugins, etc.

I go to the terminal and type: 
```
su root
```
and when I type the password for my own username it's rejected. :( 

I never entered other passwords during the install ... :confused: 

Any suggestions or comments are greatly appreciated!

Steff

---

### Post by Lord Illidan on 2005-12-29
Ubuntu chooses its own root password at startup to prevent users from logging as root automatically, as it is insecure.

To choose your own root password, enter in terminal

```
sudo passwd root
``` and enter your password, then the password of your choice.

About java, are you sure you have to be root? I think sudo is sufficient.

EDIT : clarification. Basically to do an action with sudo, you type in the action, then add sudo in front of it.

For example.. ```
sudo synaptic
``` or ```
sudo apt-get install packagexxxx
```

Oh, and welcome to the forums...

---

### Post by 23meg on 2005-12-29
Check this out: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

And for Java see this if you haven't: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Unicast on 2005-12-29
From one n00b to another...

There is no root password. From what I've gathered if you need to perform admin tasks in a terminal window you have to precede the command with **sudo**.

I think that's right - I'm sure that someone wiser than I will come along and correct me if I've got the wrong end of the stick! :D

EDIT: Must learn to type quicker!

---

### Post by Suger on 2005-12-29
I just reinstalled java on one of my box. You don't need to login as root to do that. You can perfectly go the sudo way, or if you want a root shell, start with a sudo su. Do not enable the root account unless absolutely necessary.

---

### Post by Chipmunk on 2005-12-29
Just one word of warning, I discovered this myself. If you set a root password, it will apparently break most of the auto-update features.

To fix them again is easy however, (this will disable the root account again as it is originally)

```
sudo passwd -l root
```

I don't know how 'advisable' this is, but whenever I have needed to do a lot of things as root in a terminal, I use ```
sudo bash
``` to give me a root prompt. Usual cautions apply though, be very careful when in root mode.:cool:

---

### Post by Steff_DK on 2005-12-29
[QUOTE=23meg]Check this out: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
[/QUOTE]

Okay - according to this I am supposed to "Run as a different user".
I gather the user to run as is "root" but what do I put where it says "Run:"?

I want to install this file; jre-1_5_0_02-linux-i586.bin that I downloaded from java.com, so that the plugin will work for all users - not just myself.

Right now I'm not even allowed to create a folder named "java" in the usr directory.

---

### Post by Suger on 2005-12-29
Well, either you type sudo before your commands on each line, either you use one of the two methods given above to access a root shell (mine, sudo su, or chipmunks, sudo bash).

You've got a good howto for Java here

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Steff_DK on 2005-12-29
Thanks for your patience - got it working now... 

(and finally I could login to my homebank to see what damage the holidays have done to my account :eek: )

---

