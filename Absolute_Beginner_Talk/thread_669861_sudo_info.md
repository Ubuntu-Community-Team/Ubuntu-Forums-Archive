---
title: "sudo info"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by leeonardo on 2008-01-16
I make no apologies for my lack of knowledge in this world. I know a lot of things. Linux is new to me. My experience with command line operations in the past has been pretty much limited to ip config and ping, and while it may be becoming less essential all roads still seem to lead back to the terminal.

I see the value here. But  it's confusing to a beginner. The install was pretty easy.  Connecting to the internet hung me up but got there. Installing Flash took a while. The  other thing at the top of my list is java, and I seem to be going around in circles, trying to download and install following instructions from mozilla and sun and posted on the forums. I finally realized I needed to open up metaverse or whatever it's called in the Synaptec Package Manager, and also some additional repositories. But I'm still not sure which of a number of roads to go down next.

Here's my very simple question for now. I keep seeing instructions that start with sudo. Everytime I try to use sudo it asks for a password. I don't have a password for sudo and system password doesn't work.I don't even know if I have sudo. I looked it up on google and see it's something one can install.

 Did it come with my ubuntu installation or do I need to install it before I can use it?. I never see any beginner instructions that say "get and install sudo". It always just says "use it." My installation is gusty, presumably 32 bit."

Thanks for educating me on this.
Leeonardo

---

### Post by oldos2er on 2008-01-16
Sudo is installed by default. You use the same password for it as your login password.

---

### Post by leeonardo on 2008-01-16
Thanks Ann. When I have tried that in the past it hasn't even let me enter a password. Any idea what I was doing wrong? Knowing this I can now go try again.

---

### Post by delphiguy on 2008-01-16
when doing sudo the first time it will ask you for a password, and after that
everytime you do a sudo it will never ask for a password again, until you
leave your session idle for a sometime (i think its 15minutes or so), then
it will again ask for a password.

hope this helps.

---

### Post by gunbladeiv on 2008-01-16
> **leeonardo said:**
> Thanks Ann. When I have tried that in the past it hasn't even let me enter a password. Any idea what I was doing wrong? Knowing this I can now go try again.

I dont know what you mean by this statement, but as far as i understood, maybe you are talking about * symbols when you enter the password.

Yes when you use sudo command, you need to enter password atleast once untill you idle for 10 minutes.  End you have to enter password which you used to logon(in other word, your user password), nothing will be shown as you type the password phrase.  Just a blank spot.. but just hit ENTER after you've finish typing your password.  I think that should take you through!

Dont worry, a lot of people will help here if you have a problem.:)

---

### Post by pebo on 2008-01-16
[https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29")
for a full explanation. The wiki is your friend;)

---

### Post by eolson on 2008-01-16
I THINK  what the problem is,  is that when you are entering your password it's not moving a cursor or entering stars or somesuch.   If that's what it is, that's by design as a security measure.  Just type your password and hit return like it was echoing something.

---

### Post by leeonardo on 2008-01-16
got it working, and also got java installed. thanks again for the help.
Lee

---

