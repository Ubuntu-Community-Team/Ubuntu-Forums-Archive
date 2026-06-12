---
title: "Confusion"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by davidU on 2006-04-03
Why can I not find the Terminal under, Applications,Accessories,Terminal, as is indicated by posters to the absolute beginners forum ?

My Terminal is found under Applications,SystemTools.

Then there are two Terminals, Root Terminal and Terminal.

Are places for these applications shuffled around between version releases like Microsoft does with it's stuff ?
It is very confusing for an absolute beginner when stuff isn't where the poster says it is.
What is going on ?
DavidU

---

### Post by waster on 2006-04-03
Which version did you install?

If you right click on the menu item, when you've found it, you can choose to "add to panel" which will make it available in the panel for easy access.

---

### Post by Papa-san on 2006-04-03
Applications > Accessories > Terminal...
root is when you type 'sudo' first...

---

### Post by davidU on 2006-04-03
[QUOTE=Papa-san]Applications > Accessories > Terminal...
root is when you type 'sudo' first...[/QUOTE]

What on earth are you saying ?

Sorry I don't understand what you mean.

---

### Post by jrib on 2006-04-03
In Hoary, the terminal was found in System Tools.  In Breezy it got moved to accessories.  I believe the final goal is to eliminate System Tools completely since it is kind of redundant with the System menu.  You probably have hoary, you can check by running 'lsb_release -a' in a terminal.  Here is an upgrade link if you are interested: [http://wiki.ubuntu.com/BreezyUpgrade](http://wiki.ubuntu.com/BreezyUpgrade)

---

### Post by davidU on 2006-04-03
[QUOTE=waster]Which version did you install?

If you right click on the menu item, when you've found it, you can choose to "add to panel" which will make it available in the panel for easy access.[/QUOTE]

I installed version 5.04

---

### Post by davidU on 2006-04-03
[QUOTE=_jason]In Hoary, the terminal was found in System Tools.  In Breezy it got moved to accessories.  I believe the final goal is to eliminate System Tools completely since it is kind of redundant with the System menu.  You probably have hoary, you can check by running 'lsb_release -a' in a terminal.  Here is an upgrade link if you are interested: [http://wiki.ubuntu.com/BreezyUpgrade](http://wiki.ubuntu.com/BreezyUpgrade)[/QUOTE]

Thank you Jason,

---

### Post by Papa-san on 2006-04-03
Sorry, I was trying to make the post quick.
If you click on Applications, then in the drop down, you will see Accessories. When you move your cursor over that, you will get another list, one of which is 'Terminal'. This is the one you want to click on. This will open your terminal.

When using terminal, you need to tell it if you are a user, or if you are the "superuser" (Think Admin) Commands as a user are just typed in. If you want to get 'into' root, you must type 'sudo' first (don't put the quotation marks in) just: sudo

sudo = superuser do (really!)

when you type your command with 'sudo' it will prompt you for your 'admin' password. If the pw is entered correctly, it will then do what you asked it to.

I am creating a post for people like me and you who are so new to linux, that we aren't sure of what to do... (I started less than a month ago)

Hang in there! It does get easier. You are going to need to learn a LOT, but with persistence, you will be AMAZED at what you can do with this Operating  System. I still know very little about it, but do know that now, I shall never have to return to Windows, and this makes me quite happy!

---

### Post by davidU on 2006-04-03
[QUOTE=Papa-san]Sorry, I was trying to make the post quick.
If you click on Applications, then in the drop down, you will see Accessories. When you move your cursor over that, you will get another list, one of which is 'Terminal'. This is the one you want to click on. This will open your terminal.

When using terminal, you need to tell it if you are a user, or if you are the "superuser" (Think Admin) Commands as a user are just typed in. If you want to get 'into' root, you must type 'sudo' first (don't put the quotation marks in) just: sudo

sudo = superuser do (really!)

when you type your command with 'sudo' it will prompt you for your 'admin' password. If the pw is entered correctly, it will then do what you asked it to.

I am creating a post for people like me and you who are so new to linux, that we aren't sure of what to do... (I started less than a month ago)

Hang in there! It does get easier. You are going to need to learn a LOT, but with persistence, you will be AMAZED at what you can do with this Operating  System. I still know very little about it, but do know that now, I shall never have to return to Windows, and this makes me quite happy![/QUOTE]

Papasan,
       thanks for your post.  Sorry for needing so much hand holding, it must be a condition picked up from using a GUI for so long.

I've found the Terminal, now I can check something to do with changing a kernal boot option, so that my power indicator will work correctly.

Thanks again Papasan:)

---

### Post by YuHoo on 2006-04-03
Just in case you need some more hand holding I would recommend that you learn some of the powers in the terminal. It's a new way of doing things if you're not aquainted with it, but you'll soon grow to like it.

For internal help with the command you can get a lot of information by typing 
man commandname

but for a more user friendly help check out linuxcommand
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
[http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html")
[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

Have fun with your new linux box, and don't be afraid to ask stupid questions, we've all been down that road too.

---

### Post by davidU on 2006-04-04
[QUOTE=YuHoo]Just in case you need some more hand holding I would recommend that you learn some of the powers in the terminal. It's a new way of doing things if you're not aquainted with it, but you'll soon grow to like it.

For internal help with the command you can get a lot of information by typing 
man commandname

but for a more user friendly help check out linuxcommand
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
[http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html")
[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

Have fun with your new linux box, and don't be afraid to ask stupid questions, we've all been down that road too.[/QUOTE]

Thanks YuHoo,
       you pointed me true, the pages are going to be very helpful.
Thanks also for pointing out that this expedition into Linux territory should be fun. Up until then, I'd definitely lost site of this fact and I'd been seeing it as a massive struggle compared to MS wares.  But hey, the pressure is off and I'm up for play time.

One thing has me puzzled though.
How come so many people have so much time to spare to poke about with the innards of Linux ?  
Do some folks have jobs that let them tinker whilst they are at work ?
If so, it sounds peachy to me.
regards
DavidU:)

---

### Post by meborc on 2006-04-04
[QUOTE=davidU]
One thing has me puzzled though.
How come so many people have so much time to spare to poke about with the innards of Linux ?  
Do some folks have jobs that let them tinker whilst they are at work ?
If so, it sounds peachy to me.
regards
DavidU:)[/QUOTE]

most of the people here, who probably seem to you as a linux geeks, have optained the knowledge over a very long period of tinkering... other people have gained the knowledge from setting up their own box, asking questions and getting answers... so there is always somebody here (or @ irc) who knows the most probable answer... and it doesn't really take a lot of time to try some of the commands or to try to install some soft on linux... 

btw - reading/answering to posts @ ubuntuforums is one of my favourite things during worktime... i have a lot of time for surfing around as my work right now is testing software... and the tests take a long time to run... :mrgreen: therefore - free time for me

---

### Post by davidU on 2006-04-04
[QUOTE=meborc]most of the people here, who probably seem to you as a linux geeks, have optained the knowledge over a very long period of tinkering... other people have gained the knowledge from setting up their own box, asking questions and getting answers... so there is always somebody here (or @ irc) who knows the most probable answer... and it doesn't really take a lot of time to try some of the commands or to try to install some soft on linux... 

btw - reading/answering to posts @ ubuntuforums is one of my favourite things during worktime... i have a lot of time for surfing around as my work right now is testing software... and the tests take a long time to run... :mrgreen: therefore - free time for me[/QUOTE]

Sounds like a great job Mebroc.

I have already invested quite a bit of time to reading about Linux, but every time I take a stab at it I usually end up regrouping and assuming the recovery position, as I hadn't realised just how much time is required.

Anyway, I very grateful for the posts, and maybe one day, I'll be able to put my Linux knowledge to some use.

Regards
DavidU

---

### Post by YuHoo on 2006-04-04
I have a lot of time to do whatever I feel like and I have a compulsion toward tinkering, usually at the expense of my system. Part of that is because I have the time to reconfigure if I do make a mistake, but all the way back to my win95 days I would modify the explorer.exe file. Don't try that. Really, don't try that. But poking around the system teaches you the most, screwing up even more. I screw up a lot. I'm also by no means linux literate, but after a few weeks you're able to help in this forum, and if I have a problem I can't fix (I usually spend a few hours pulling my hair out) I go to another forum, I guess that's the way it works. 

But I'm doing this all for fun, and I also have a second desktop computer that is tinker free win2000 that has gone for 2 years without a glitch :mrgreen:. Having a stable computer and an unstable one gives me some freedom to do what I want, I'd recommend this if you have a secondary computer that you can use if the linux one goes kaput.

---

### Post by davidU on 2006-04-04
[QUOTE=YuHoo]I have a lot of time to do whatever I feel like and I have a compulsion toward tinkering, usually at the expense of my system. Part of that is because I have the time to reconfigure if I do make a mistake, but all the way back to my win95 days I would modify the explorer.exe file. Don't try that. Really, don't try that. But poking around the system teaches you the most, screwing up even more. I screw up a lot. I'm also by no means linux literate, but after a few weeks you're able to help in this forum, and if I have a problem I can't fix (I usually spend a few hours pulling my hair out) I go to another forum, I guess that's the way it works. 

But I'm doing this all for fun, and I also have a second desktop computer that is tinker free win2000 that has gone for 2 years without a glitch :mrgreen:. Having a stable computer and an unstable one gives me some freedom to do what I want, I'd recommend this if you have a secondary computer that you can use if the linux one goes kaput.[/QUOTE]

It's good to know there are people out there willing to help, 'cos it sure isn't straight forward installing Linux, even accepting the defaults, there's still plenty of room for folks like me to go astray.
I've come back to Ubuntu Linux now that I've finished studying for my BSc in Information Systems.  Uni had Solaris installed in the lab and I never got near any Unix modules, only Windows bound apps and a bit of programming.
I didn't have very much time to make the switch to Linux and always felt under enormous pressure to make it work first time, but I couldn't.
Now I have some free time and I'm looking forward to enhancing my skills by tinkering with Ubuntu as a way of making up for the deficiencies of my college years.
I have plenty of stable Windows machines and I regularly fix them for others, so when Linux won't play ball, it seemed so painful.
It just shows how desperate I am to leave Microsoft products behind, even if they are stable ? they aren't secure enough for business purposes in my mind.
Regards
DavidU

---

