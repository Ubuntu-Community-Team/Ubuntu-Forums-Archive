---
title: "Firefox alternative for browser..."
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by NetDoc on 2007-10-01
OK gang, so far, I love my Ubuntu based laptop. I have only a few more "bugs" to squash!

I need a browser that will work with Flashchat, something that Firefox just can't seem to handle. My problem is simple: I own the largest website for Scuba Diving and we have FlashChat installed as an integral part of our services: [http://www.scubaboard.com/forums/chat/flashchat.php](http://www.scubaboard.com/forums/chat/flashchat.php) We hope to be adding an audio feed as well as video to this in the not too distant future, and since these laptops will be used to demonstrate [www.ScubaBoard.com](www.ScubaBoard.com), I need something that will work and not hang up. 

I look forward to your responses.

---

### Post by PmDematagoda on 2007-10-01
You can try Opera or Swiftfox, personally I like and use only Firefox, so I don't know much about Opera or Swiftfox.

P.S. Cool site.:)

---

### Post by Dr Small on 2007-10-01
The flashchat link you listed above, works in my Firefox... :|
But anyhow, have you tried Opera or Konqueror ?

---

### Post by PmDematagoda on 2007-10-01
I think he must be talking about the chat client itself, not the login screen.:)

---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]I use Opera in preference to Firefox, and the only problem I've had is it won't play with Stumbleupon. Otherwise it works very well with everything else.[/FONT]

---

### Post by tenjin1 on 2007-10-01
> **NetDoc said:**
> OK gang, so far, I love my Ubuntu based laptop. I have only a few more "bugs" to squash!

I need a browser that will work with Flashchat, something that Firefox just can't seem to handle. My problem is simple: I own the largest website for Scuba Diving and we have FlashChat installed as an integral part of our services: [http://www.scubaboard.com/forums/chat/flashchat.php](http://www.scubaboard.com/forums/chat/flashchat.php) We hope to be adding an audio feed as well as video to this in the not too distant future, and since these laptops will be used to demonstrate [www.ScubaBoard.com](www.ScubaBoard.com), I need something that will work and not hang up. 

I look forward to your responses.

It is also working for me too (the login screen) unless like Pmtogoda said..its the chat client thats not working??.

Sounds like you may need flash support in firefox??..
 open a terminal and type:
```

sudo apt-get install flashplugin-nonfree
```

Or install using Synaptic Package Manager:

```
System-->Administration-->Synaptic Package Manager-->Search-->flashplugin-nonfree-->Mark for installation--->Apply
```

---

### Post by NetDoc on 2007-10-01
> **tenjin1 said:**
> It is also working for me too (the login screen) unless like Pmtogoda said..its the chat client thats not working??.

Sounds like you may need flash support in firefox??..
 open a terminal and type:
```

sudo apt-get install flashplugin-nonfree
```
netdoc@InterMPub003:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

> **tenjin1 said:**
> 


Or install using Synaptic Package Manager:

```
System-->Administration-->Synaptic Package Manager-->Search-->flashplugin-nonfree-->Mark for installation--->Apply
```netdoc@InterMPub003:~$ System-->Administration-->Synaptic Package Manager-->Search-->flashplugin-nonfree-->Mark for installation--->Apply
bash: System--: command not found

Neither worked for me. This is a Dell 1501 with an AMD 64 processor.

---

### Post by NetDoc on 2007-10-01
> **Dr Small said:**
> The flashchat link you listed above, works in my Firefox... :|
But anyhow, have you tried Opera or Konqueror ?You can get to the sign in, but once in it won't let you post. Use this account: sockpuppet with pwd=ubuntu or sign up on [www.ScubaBoard.com](www.ScubaBoard.com). Registration is free.

---

### Post by kerry_s on 2007-10-02
> **NetDoc said:**
> You can get to the sign in, but once in it won't let you post. Use this account: sockpuppet with pwd=ubuntu or sign up on [www.ScubaBoard.com](www.ScubaBoard.com). Registration is free.

worked here.

---

### Post by mysticmatrix on 2007-10-02
Hi I signed in all right by id and password you gave and so far everything is right. 
I can type and it reflects back. But no one is answering...
How do I know there is someone other to chat?

---

### Post by 3rdalbum on 2007-10-02
NetDoc, are you using Ubuntu 64-bit? That would explain why flashplugin-nonfree is not in the repositories for you, because Adobe doesn't make a 64-bit version of the plugin.

If you're running 64-bit, then you should probably take a look at the topics in the 64-bit forum, because there's a way to make Flash work on this edition.

---

### Post by brn on 2007-10-02
Originally Posted by NetDoc
> netdoc@InterMPub003:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
You need to enable the multiverse packages in /etc/apt/sources.list
```
~ :> gksudo gedit /etc/apt/sources.list
```
Uncomment (remove #'s) from lines beginning with 'deb'. (I'm not sure which has Flashplugin) 
then  ```
sudo apt-get update
``` 
> netdoc@InterMPub003:~$ System-->Administration-->Synaptic Package Manager-->Search-->flashplugin-nonfree-->Mark for installation--->Apply
bash: System--: command not found
This isn't a command line operation.  Click **System** on the top panel, choose **Administration**, then **Synaptic Package Manage**
In the Synaptic menu, click **Search** and find Flashplugin.  Click the box to mark for installation, then click **Apply**. 
Synaptic will install Flashplugin to /usr/lib/mozilla/plugins/ but you may need to copy it to /home/netdoc/.mozilla/plugins/ if Firefox doesn't find it in the first location.

---

