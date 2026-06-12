---
title: "A couple questions"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Goatee Man on 2007-11-27
I'm new these forums and to Linux, so please be kind...

Anywho, I'm running Ubuntu 7.10 on a Dell 3400... 512 RAM, a 60 gig internal hard drive and a 320 external one.

The first problem I'm having is that whenever I use Firefox, any website with Flash content will cause it to crash. If I click on a Youtube page, for instance, it will start to load the page, but then it'll completely freeze up and I'll have to turn my computer off and then back on to get it to work. I installed the Flash plugin for Firefox and re-installed it when it started going all wonkey, but it didn't do any good. I can use Opera just fine with anything Flash based, but still... It's Firefox. Any suggestions?

Second, I used to use Windows Movie Maker to edit my videos (please don't kill me) and got pretty used to the general layout. I searched for a good Linux editor, but couldn't find one - can you recommend any? Preferably something with the ability to cut and move clips and overlap subtitles and audio on video... 

Finally, although I am the sole user and administrator of my computer, it keeps telling me that there are certain things I can't do because they're "limited to the root user" or something of that nature (I don't remember the exact message, sorry). I copied a couple files from a friend running XP, and a lot of them were marked as "read-only" - it wouldn't let me delete anything because it kept saying I didn't have the permissions to. I was allowed to change the permissions on them to allow me to delete the files one by one (which I eventually had to do). But I still can't do things like run Gparted via Bash (it tells me I don't have the permission to, even though it worked fine a week ago). 

I'm sure that I probably left a lot out that would help here, but like I said, I'm new... Please be kind. 

Other than these few problems I've been having, though, I absolutely love 7.10 so far. I was kinda forced into using it (even though I wanted to try it for quite a while) because my XP computer crashed and wouldn't re-install correctly, but now I don't ever want to go back. I'm running XP on this old hunk o' junk because it's the only one in our house connected to the internet, mind you, but that's the only reason I'm using it. :P

Thanks for reading my long and winding message.

---

### Post by spiderbatdad on 2007-11-27
Hmmm? Don't know what's going on with Firefox. There are many video editing applications to choose from. VLC is available in synaptic and has a GUI. Mencoder is a choice of those preferring command line editing, though mencoder may have a GUI frontend, also. Google searching linux video editing software should produce results.
As for permissions, If your are in command line, you must proceed commands with sudo (super user mode) If you are trying to manipulate root files from a GUI, you are in dangerous territory. You can damage your system. Linux has a bit of a learning curve, requires a little study from time to time...I am certainly still a noob, but I know so much more than I did two years ago, and the learning is fun.

---

### Post by tranquito on 2007-11-27
> **Goatee Man said:**
> 

Finally, although I am the sole user and administrator of my computer, it keeps telling me that there are certain things I can't do because they're "limited to the root user" or something of that nature (I don't remember the exact message, sorry). I copied a couple files from a friend running XP, and a lot of them were marked as "read-only" - it wouldn't let me delete anything because it kept saying I didn't have the permissions to. I was allowed to change the permissions on them to allow me to delete the files one by one (which I eventually had to do). But I still can't do things like run Gparted via Bash (it tells me I don't have the permission to, even though it worked fine a week ago

I'm a bit of a Ubuntu n00b too but if you logon as root that problem will go away!

---

### Post by Goatee Man on 2007-11-27
I've no idea how, sadly. My account is the only one. :(

---

### Post by Goatee Man on 2007-11-27
Wait, nevermind... I forgot about sudo. >_<

Anywho, thanks for the help, all. 'Tis greatly appreciated.

---

### Post by Tanjer1588 on 2007-11-27
> **Goatee Man said:**
> 

Finally, although I am the sole user and administrator of my computer, it keeps telling me that there are certain things I can't do because they're "limited to the root user" or something of that nature (I don't remember the exact message, sorry). I copied a couple files from a friend running XP, and a lot of them were marked as "read-only" - it wouldn't let me delete anything because it kept saying I didn't have the permissions to. I was allowed to change the permissions on them to allow me to delete the files one by one (which I eventually had to do). But I still can't do things like run Gparted via Bash (it tells me I don't have the permission to, even though it worked fine a week ago). 


The root user in linux is what you use when you really need to go in an change thing, you can do anything in there, like erase every thing on you whole hard drive, so when you want to do something and it says that you cant? or it says you have to be root user, the easyest way it to get at it through the Terminal and us SUDO, it would be wise to read up on the terminal and the comands that you can do, it helps quite a bit to know how to use it so that you can fix things in ubuntu

---

### Post by OldTimeTech on 2007-11-27
you may need to load java runtime for youtube to work....automatix2 should help with that problem or go here [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

I would suggest using the self-extracting file.  Also try the synaptic package manager and load the flash plugin-nonfree and gnash....also mozilla gnash plugin.  Probably will want to add other packages with these through synaptic when they install, go ahead and let them.

---

