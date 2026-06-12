---
title: "Trying to get root but there is no root"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-05
I can't remember setting up a password, is there a way to turn off the similar threads gizmo in this forum? Bloody annoying.

What was I talking about? Oh yeah, what's up with root. Someone told me to do something as root but no luck. No root!

Any hints on this one?

---

### Post by kellemes on 2008-04-05
All explained here..
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by liorc666 on 2008-04-05
root via :
"su" in console or "sudo ~Command~"

you can also set root password by hand in :

System --> administration --> users and groups.

---

### Post by joshrobinson on 2008-04-05
> **liorc666 said:**
> root via :
"su" in console or "sudo ~Command~"

you can also set root password by hand in :

System --> administration --> users and groups.

in ubuntu you use sudo, it gives you root privileges without logging in as root

you really shouldnt login to the gui as root, but you can enable it

to use full on root in a terminal do the following, some people will tell you not to, but i do it as sudo drives me nuts

```
sudo passwd
```
put your user password in
then it will ask what password you wana use for su (root)

then when you want to login to root as a terminal
```
su
```
type the password you set

---

### Post by SlappyPappy on 2008-04-05
Thanks for the help lads.

Josh, you been there with an answer for me on just about everything I've asked.

You want to come over and do my work for me on my computer? I've got a couple of budgets, some casting, and I need to figure out what model Mercedes I'm getting this year.

I'll leave it all up to you!   :guitar::mrgreen:

---

### Post by valjour on 2008-04-05
Hi-
Thanks for asking that question Slappy.  I was embarrassed to ask when I found I lacked the command line experience, last week.  

I found  the above mentioned links especially helpful to me as I am just starting out on my terminal journey ;)

Kellemes link put some fear in me though.  I had to work (log in) as root (#) to do some work, sudo would not allow the permissions necessary.  I used [sudo -i].    The link  told me that this can be dangerous and files can be overwritten.  I also know that [sudo bash] gets me to root as well.  I use commands I am ignorant of only when frustrated.  I hope I haven't messed things up behind the scenes of my box.

Is it a good idea to create a  su, if you feel it necessary to muddle around with perfectly working stuff like I do?  I still don't  understand all the nuances of these different ways to login as root.  Which are recommended and for what purposes. And am murky on [gksudo].  Is there a link to more detailed info on these commands that puts the whole picture together in one place for us beginners?
  
"Absolute power corrupts absolutely." Someone famous once said.  I want to handle my privileges with grace and tact rather than brute force. 

And Slappy when typing sudo in front of a command the password you are asked for is the same as your login password when you start up the machine.  (The su password will be a different new one you enter after the command-second prompt) . 

 If someone else set up your machine they would know it.  I'm learning that it is a good idea to write things down (especially passwords)  and keep the info  in a safe place away from my desk when I am.

Thanks everyone for showing us beginners  the way..:)

---

### Post by gn2 on 2008-04-05
Another alternative is Alt + F2 then "gksudo nautilus" for full root access to the file system in a GUI

But go carefully........

---

### Post by valjour on 2008-04-06
Thanks gn2,

I still question when it is appropriate to use each version of the root command. I know that they are all subtly different in their functioning  but get you to the same place.  Is there any clarification available?  I am in learning mode::) yet :confused:

Thank You

---

### Post by gn2 on 2008-04-06
Basically you need root privileges to run any process that can edit or alter any of the system files.

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by JoshuaRL on 2008-04-06
Let's be very clear.  Login as root is not supported on Ubuntu Forums anymore.

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

That sticky in the Security Forum explains why and how to use sudo and gksu appropriately.

---

### Post by valjour on 2008-04-07
Thank You.  It is important to read JoshuaRL's link.  That is all I really need  to know.  I want to have respect for the forum and was not aware of this policy.  

I am just a baby penguin and should stick to more basic and "age appropriate" learning. :)

I now understand why I had questions to begin with.  I shan't ask for depth on this matter again.

I won't claim ignorance and practice evasion.  

Can I request  that someone with authority look over all my previous posts/threads for appropriateness and do with them as is seen fit for compliance?  I had questions with my procedures and attempted some heavy operations.  

 I let it all hang out there while I basically figured "stuff" out like log in as root.  Please contact me if i need to do something from my side of the forum to assist in this process or if i need further  instruction. 

**_Warning _**to other novices with a curiosity looking through my threads: if my  machine and/or kernel is not damaged it is only because i got extremely  lucky. If it works don't fix it.  I now know enough to leave well enough alone and ask questions before I attempt anything,  Also, if it is feasible it is advisable to plan out the steps/syntax and write/think it out before execution.  

Exemplified in reading all pertinent posts. And if not found posting "Can I do such and such, is it necessary or recommended?" or,  "is such and such broken if it acts like this (or get a message like that)? "  If I would have asked, I know now, the answer would have been no or probably not.

I've been thinking about the last two paragraphs for a few days... If it would be useful to post by itself more generally worded give the word.  This is what I have learned about this process.

Thank you again Joshua (and all those others with sage experience and advice) for the guidance and humility I need. Pete

---

### Post by SlappyPappy on 2008-04-07
> **valjour said:**
> Hi-
Thanks for asking that question Slappy.  I was embarrassed to ask when I found I lacked the command line experience, last week.  

I found  the above mentioned links especially helpful to me as I am just starting out on my terminal journey ;)

Kellemes link put some fear in me though.  I had to work (log in) as root (#) to do some work, sudo would not allow the permissions necessary.  I used [sudo -i].    The link  told me that this can be dangerous and files can be overwritten.  I also know that [sudo bash] gets me to root as well.  I use commands I am ignorant of only when frustrated.  I hope I haven't messed things up behind the scenes of my box.

Is it a good idea to create a  su, if you feel it necessary to muddle around with perfectly working stuff like I do?  I still don't  understand all the nuances of these different ways to login as root.  Which are recommended and for what purposes. And am murky on [gksudo].  Is there a link to more detailed info on these commands that puts the whole picture together in one place for us beginners?
  
"Absolute power corrupts absolutely." Someone famous once said.  I want to handle my privileges with grace and tact rather than brute force. 

And Slappy when typing sudo in front of a command the password you are asked for is the same as your login password when you start up the machine.  (The su password will be a different new one you enter after the command-second prompt) . 

 If someone else set up your machine they would know it.  I'm learning that it is a good idea to write things down (especially passwords)  and keep the info  in a safe place away from my desk when I am.

Thanks everyone for showing us beginners  the way..:)

Your welcome sir and thanks for your tips. I hear you about writing everything down I'm learning. If you don't you can forget a command in a matter of seconds. :lolflag:

I'm still bumbling my way through this beast but loving it in a strange way. I'm pretty setup now since I managed to clone my original install to a larger hard drive which is also faster. Now I'm living life in the fastlane of the information super highway.

Rock on with your bad self sir!  :)

---

### Post by JoshuaRL on 2008-04-07
valjour and SlappyPappy, I want to thank you for being so understanding and willing to learn the right way to handle problems.  Not everyone has acted like that when reminded about this and it really reflects well on both of you.

The most important thing to remember is that Ubuntu and Linux isn't Windows and some things need to be learned the right way.  But that said, it's because they tend to be the better way to do things anyway.  Try out the "Learn the Terminal" link in my signature for a really great site.  It explains the commands and what they do.  Great resource for learning your way around.

Above all, welcome to Ubuntu!  And remember, if you break Ubuntu you get to keep both pieces!

---

