---
title: "I am root not user!"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by pappy.omatic on 2007-02-20
I dont think I can work like this. I mean with all the idiot proofing of this OS I am just angry. I enabled the root account and all but still it won't let me log in as "root".  AND FRANKLY SUDO SUCKS IMHO!!!! Further more I can find no reason to have this roadblock "on every change made" in my way. Other than to be a pain or an idiot shield I have no time to waste on such nonsense. Why is it grained into your system to the point it is I dont care. What I do care about is deletion and going with another OS or a way to gut this problem. Point is I switched to Linux as a way of not having my own PC in MY WAY!! This I also pass out to my clients that are looking to bypass big brother. So before I pull more hair or have nothing good to say about this OS let alone use it. I thought I owed it to your efforts and my time to ask if this can be removed or if I am again looking for an OS that just works. On the edge of edgy and the sudo is pushing me over. Please help if there exist a solution that allows me to work as ROOT not a user. YES I know the risk but I promise not to complain if I break it. Sudo is a neat way to fix ONE problem at a time. I never have just one it seems cause once I get the OS installed it goes out the door to my clients home. So being that I "root" am installing then tweekin the settings and never see a day as user. I just can't take another minute of SUDO HELL.

---

### Post by Vivix729 on 2007-02-20
Out of curiosity, what exactly is wrong with sudo?

---

### Post by taurus on 2007-02-20
Just calm down because if you want to activate root's account, just create a password for it but you need to understand one first, if you screw up while log in as root, you need to keep both pieces, as one of the staff members would put it.

Therefore, run this at the prompt,

```
sudo passwd root
su -
```
and good luck.

---

### Post by ashmew2 on 2007-02-20
Take a chill pill :P And then see [here]("http://ubuntuforums.org/showthread.php?t=365998") if u also want to enable GUI root login.

---

### Post by ashmew2 on 2007-02-20
> **pappy.omatic said:**
> What I do care about is deletion and going with another OS or a way to gut this problem. 

I do not mean to be rude/offensive in any way bu it was you yourself who chose to try Ubuntu and if u really want to remove Ubuntu from your system , I can help u wid that also....

---

### Post by y-lee on 2007-02-20
There are better options than signing in as root.

[INDENT]get used to **sudo**. It's not that bad really!!

use the root terminal. **Applications/System Tools/Root Terminal.** If it is not there check your menu editor to make sure it is checked. If ya like add this to one of your panels.

Try using **gksudo /usr/bin/nautilus** to change file permissions, move or delete files. you can make a menu item or launcher outta this if ya want to.[/INDENT]


Always be careful tho!!

---

### Post by v8YKxgHe on 2007-02-20
> **y-lee said:**
> There are better options than signing in as root.

[INDENT]get used to **sudo**. It's not that bad really!!

use the root terminal. **Applications/System Tools/Root Terminal.** If it is not there check your menu editor to make sure it is checked. If ya like add this to one of your panels.

Try using **gksudo /usr/bin/nautilus** to change file permissions, move or delete files. you can make a menu item or launcher outta this if ya want to.[/INDENT]


Always be careful tho!!

I think, not on Ubuntu so can't check, that you can do "sudo -s" and you'll be using Sudo untill you close Terminal, afaik.

---

### Post by yme on 2007-02-20
I can appreciate pappyomatic being in a flap about this. I just installed Ubuntu last night having been frustrated with a year of Fedora3. 

Everything is really swinging from the start - no USB recognition troubles, no sound card recognion troubles - but I really was wondering if late at night I had somehow given the same password to user and to root. 

It really is a pretty confusing set up and I don't think standard for Linux.

---

### Post by taurus on 2007-02-20
> **yme said:**
> I can appreciate pappyomatic being in a flap about this. I just installed Ubuntu last night having been frustrated with a year of Fedora3. 

Everything is really swinging from the start - no USB recognition troubles, no sound card recognion troubles - but I really was wondering if late at night I had somehow given the same password to user and to root. 

It really is a pretty confusing set up and I don't think standard for Linux.

Yes, most other Linux distros will ask you to create a root password when you first install it but Ubuntu locks the root account by default.  Maybe this would explain why.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Medieval_Creations on 2007-02-20
one thing that I always do is change the "Root Terminal" command in the Menu to
```
gksu gnome-terminal
```
or from CLI
```
gksu gnome-terminal &
```
I almost always have 2 terminals open.  One as myself and another as root.  gksu will have to confirm your password once (just like sudo, but doesn't time out).

I too found it annoying at first at having to type sudo before every command, but since I see no reason to log in as root, I just made a quick way to get to a root terminal.  I even went as far as setting up a hot-key for it.

---

### Post by az on 2007-02-20
What exactly are you trying to do that requires you to log in a root at the desktop?  I mean really, what is such the big deal that you need to be root all the time at the desktop?

I think you may have been given some bad advice as to how to do things, because you can accomplish a lot of things a lot more efficiently than hand-moving files with the file-manager as root and so forth...

---

### Post by TheWizzard on 2007-02-20
> I enabled the root account and all but still it won't let me log in as "root". AND FRANKLY SUDO SUCKS IMHO!!!! 
apparently you don't understand the difference between enabling the root account and allowing root to do a graphical login. 
doing a graphical login as root is rather unwise. and totally unnecessary. 
moreover, graphical login allows you to brows the web as root. this is not only a serious tread for you but also for your clients. 

there is a 3-step sollution
1) open terminal
2) type "sudo -s"
3) configure the box

---

### Post by aysiu on 2007-02-20
I've never found any reason to either enable the root account or log in as root.

I can get everything done with *sudo* or ```
gksudo nautilus
```

---

### Post by ViRMiN on 2007-02-20
Sudo rocks!  Excellent for restricting a bunch of users like helpdesk admins to be only able to do privileged things like reset passwords.  Writing a script-wrapper around passwd can allow you to control exactly which passwords they can reset!

---

### Post by K.Mandla on 2007-02-20
> **pappy.omatic said:**
> I dont think I can work like this. I mean with all the idiot proofing of this OS I am just angry. I enabled the root account and all but still it won't let me log in as "root".  AND FRANKLY SUDO SUCKS IMHO!!!! Further more I can find no reason to have this roadblock "on every change made" in my way. Other than to be a pain or an idiot shield I have no time to waste on such nonsense. Why is it grained into your system to the point it is I dont care. What I do care about is deletion and going with another OS or a way to gut this problem. Point is I switched to Linux as a way of not having my own PC in MY WAY!! This I also pass out to my clients that are looking to bypass big brother. So before I pull more hair or have nothing good to say about this OS let alone use it. I thought I owed it to your efforts and my time to ask if this can be removed or if I am again looking for an OS that just works. On the edge of edgy and the sudo is pushing me over. Please help if there exist a solution that allows me to work as ROOT not a user. YES I know the risk but I promise not to complain if I break it. Sudo is a neat way to fix ONE problem at a time. I never have just one it seems cause once I get the OS installed it goes out the door to my clients home. So being that I "root" am installing then tweekin the settings and never see a day as user. I just can't take another minute of SUDO HELL.
I suggest you relax and try not to incite an argument over a relatively minor point. In the mean time, change the root password, log in as root and return to using your computer your way.

---

### Post by mcduck on 2007-02-20
As somebody in these forums once wrote, sudo is like the lock on your car's door. Even when you are the owner of the car you wouldn't want to remove locks from the car's doors, not even when having the lock forces you to use a key every time you want to use your car :D

Also using desktop as root is quite unsafe thing to do. Anyway, during my 2 years with Ubuntu I haven't found a single thing that would need me to be root. And believe me, I've been messing a lot with my system..

---

### Post by Patrick K on 2007-02-20
I don't know how to do it but I understand there is a way to change the timeout on sudo. I think the default is 5 minutes. You can change it to what ever you need. If you do change it, you should change it back before handing the system to a client.

---

### Post by taurus on 2007-02-20
> **Patrick K said:**
> I don't know how to do it but I understand there is a way to change the timeout on sudo. I think the default is 5 minutes. You can change it to what ever you need. If you do change it, you should change it back before handing the system to a client.

Actually, the default is 15 minutes.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Factory on 2007-02-20
If you don't understand how to do this on your own, do you really think you have any purpose being root of your entire system? ;)

---

### Post by kerry_s on 2007-02-20
Just create 2 launchers, 1 for nautilus-root(gksu nautilus /) and 1 for terminal-root(gksu gnome-terminal). How hard is that, just click and do your thing. Also if you feel the password is 2 much trouble->

sudo visudo

%admin ALL=(ALL) ALL
to
%admin ALL=NOPASSWD: ALL

Then you don't even have to type passwords.

---

### Post by pappy.omatic on 2007-02-23
First let me say thank you for the array of answers. 
As stated I pass out Linux as an alternative. Being the one to place on PC or in the hands of client and friend alike. Most of the first problem/questions are directed to my cell phone. As such I need to know fist hand, if what I recommend is supported, by a kind to the learning community. 
Once they get their feet wet, then trying out something new and getting a rtfm type answer, won't be a breaking point. Few distro really are noob nice as most have or will find out.
No this was not a critical problem. Help was asked for in angry tones. Most ignored that and gave answer, nice. For those that give help here, I say sorry now for the many poor questions those I give ubuntu will surely ask. Thanks for your time as I can only answer the most basic of questions.
Not sure if you are asking if i'm an idiot here.
> **az said:**
> What exactly are you trying to do that requires you to log in a root at the desktop?  I mean really, what is such the big deal that you need to be root all the time at the desktop?

I think you may have been given some bad advice as to how to do things, because you can accomplish a lot of things a lot more efficiently than hand-moving files with the file-manager as root and so forth...
I'll assume your not and offer this point of view or answer.
I like ubuntu for many reasons. In this case its gdm and xnest. Or that is what I install by default on this OS. For those that tinker alot I have found these are best run on ubuntu. I use it to install and is shown to user as a way to aviod switching to root or using sudo. Being that I suggest this to those that want it, "note that winusers are not part of this till they wake up" I found it to be a bad thing to get hooked on if you get stuck in cli. Had an issue with ati "suck" setup and not liking cli but being forced to. I found that it was very easy to forget su and worse was adding pass every other string.
As a personal choice I refuse to adapt to a text cli for I do live in a motion picture age. Not been lead astray just testing to make sure I'm not sending clients into a fire zone. And a final point on sudo "more when sudo and user pass are same" and its security. How and why others get and use passwords is not the point. More of if they can get to the user pass then they can see its ubuntu. And now know what the most likely root pass will be. Nothing I install leaves with user and root pass matching as I don't know what they might open up later to the world. And as similar animals tend to pack up. I prefer the gui pack. As such I hate cli hell and sudo "cause its ugly imho" and only use it when nothing else works.
Seem most have been windows free so long they forget. In windowland if you can feel it again, popping two windows and dragin things gives you the novice a VISUAL confirmation what you did worked. CLI is more like type then test then type again till you get it right, or lucky. Options and choices. I like doing it MY way hope you enjoy yours.
Again a big thank you to all those that make this community a nice place to start. Feel like I can pass this out with a :)

---

### Post by Tomosaur on 2007-02-23
I still think you're missing the point - you might 'prefer' being able to break your system as and when you feel like it, but that goes against the philosophies upheld by Unix-like systems. If you prefer Windows, then by all means, use that. If you prefer Linux, then you can use that too. There are ways around having to type sudo all the time. One is to use the root terimnal. Another is to tell sudo to keep you logged in. Another altogether is to use recovery mode, or otherwise login as root.

Aside from all that - there's nothing you can possibly be doing which would require so much root activity, and if there is - then you should be in recovery mode anyway. You don't compile things as root, you don't run things as root (wherever possible). Even command files can be copied safely to your home directory, tested, and then shipped back to wherever they're supposed to live. This requires only one root command - the final act of moving the file back to it's proper directory. I'm a little unclear as to what this means:
```

Nothing I install leaves with user and root pass matching as I don't know what they might open up later to the world. And as similar animals tend to pack up. I prefer the gui pack. As such I hate cli hell and sudo "cause its ugly imho" and only use it when nothing else works.
```

When you give a file to someone else, they can't magically access your system. It's just a file. As long as you don't give them the encrypted password files, or something equally idiotic, you have nothing to worry about. You can create users who don't have access to sudo, and even users who have access to nothing outside of their home directory. Quite what your problem with having to use sudo occasionally is beyond me - and even if it does bother you, it's easily fixed.

---

### Post by pappy.omatic on 2007-02-23
Nope. I am sorry you missed the point. The post was a test. Congrats you got a c- :) 
I work with nubs daily so I know how they think. I have to maintain a user level mindset so that I don't loose touch with those that support me.
I don't like it but yes I am required to keep winslut on my towers. I am not required to use it. I am the boss and choose Linux. What I do or how many times I break my PC "I prefer to call it confused" it's really my choice and none of your concern. I don't know many that didn't start on windows. So being most of us are on or 2 3 4 5th OS you telling me it's my choice to use this or something else sounds really stupid. But maybe the village idiot can use the tip.
I must assume that you have not been hacked, I hope it stays that way. Further it means that root is xxyy and first user is yyxx for passwords on any PC I work on.

I'm done testing and explaining it. Ubuntu get a good recommendation by me.  

Furthermore the string is basically a list of what to do if sudo is a pain for you.

---

### Post by Tomosaur on 2007-02-23
> **pappy.omatic said:**
> Nope. I am sorry you missed the point. The post was a test. Congrats you got a c- :) 
I work with nubs daily so I know how they think. I have to maintain a user level mindset so that I don't loose touch with those that support me.
I don't like it but yes I am required to keep winslut on my towers. I am not required to use it. I am the boss and choose Linux. What I do or how many times I break my PC "I prefer to call it confused" it's really my choice and none of your concern. I don't know many that didn't start on windows. So being most of us are on or 2 3 4 5th OS you telling me it's my choice to use this or something else sounds really stupid. But maybe the village idiot can use the tip.
I must assume that you have not been hacked, I hope it stays that way. Further it means that root is xxyy and first user is yyxx for passwords on any PC I work on.

I'm done testing and explaining it. Ubuntu get a good recommendation by me.  

Furthermore the string is basically a list of what to do if sudo is a pain for you.

I find it difficult understanding what you're on about - I can only assume English is not your first language?

Anyway - if I understand correctly - you want to use root permissions all (or most) of the time, and are irritated by sudo asking for your password? **This is easy to fix**. You can either extend the amount of time sudo grants you permissions for, or you can just start a root shell:
```

sudo -i

```

In any case, you will have to input your password at least once, unless you boot into recovery mode. That's just how linux works. It is **not a good thing** to have full access to everything on the machine all the time, as evidenced by the sheer easiness with which you can break a standard windows machine, which gives everyone full access by default. I am not trying to stop you breaking your machine, I'm just explaining **how you can do what you're trying to do**, and why I think continuous root access is a bad idea. It's up to you - break your computer if you like, I really don't care - but I don't see how belittling people helps you in any way.

---

### Post by anaconda on 2007-02-23
The real problem with enabling graphical root login in ubuntu is that is DOESN'T WORK properly even if enabled!
That is right. I did enable it and have had strange problems with graphical root user
(edgy eft 6.10)
When I login as root the menu layout program doesn't work. and in the System>administrstion there isn't all the items that were supposed to be there.. and could't enable them with menu layout either... annoying. Found some other bugs too..

I think the graphical root login hasn't been tested very much and doesnt work properly.. That is the reason I dont recommend enabling graphical root logins. 


And why did I think I needed it? Becuase it is a machine, where the users dont have sudo rights and I think it is easier to admin being a root user. .

---

### Post by anaconda on 2007-02-23
If you want root logins to work properly try Debian.

---

### Post by TwistesdTexan on 2007-02-23
I think most replies have been to try to help Pappy. He was trying to find out how much help he would receive if he had a problem that most users would find unconventional or in some eyes at least wrong. He was able to get the information and said he gives the forum a C- grade but was impressed with the responses. No need to be upset with someone trying to be different. Aren't we all different? This was certainly a new twist on a request for help.

---

### Post by pappy.omatic on 2007-02-23
First off I'm sorry if anyone was belittled. Not my intention.:-k 
> The real problem with enabling graphical root login in ubuntu is that is DOESN'T WORK properly even if enabled!
That is right. I did enable it and have had strange problems with graphical root user
(edgy eft 6.10)
When I login as root the menu layout program doesn't work. and in the System>administrstion there isn't all the items that were supposed to be there.. and could't enable them with menu layout either... annoying. Found some other bugs too..

I think the graphical root login hasn't been tested very much and doesnt work properly.. That is the reason I dont recommend enabling graphical root logins.


And why did I think I needed it? Becuase it is a machine, where the users dont have sudo rights and I think it is easier to admin being a root user. .

This is what I was saying. Thank you for being differant too.:) 

> If you want root logins to work properly try Debian.

That is one of many others that I use. \\:D/ 

 	> I think most replies have been to try to help Pappy. He was trying to find out how much help he would receive if he had a problem that most users would find unconventional or in some eyes at least wrong. He was able to get the information and said he gives the forum a C- grade but was impressed with the responses. No need to be upset with someone trying to be different. Aren't we all different? This was certainly a new twist on a request for help.

Thank you for reading with an open mind. You get an A. Only correction would be, that I give ubuntu community/forum an A!! The c- was aimed at only a few users not the whole community. 
I mean if a bad post like mine got such good replies. I'd love to see what you folks would do with a real issue.:)

---

### Post by TheWizzard on 2007-02-23
> **pappy.omatic said:**
> 
This is what I was saying. Thank you for being differant too.:) 


there is nothing wrong with being different. bad practices, however, are wrong. people try to educate you on this forum, but you decide to be stubborn.

---

### Post by pappy.omatic on 2007-02-23
> **TheWizzard said:**
> there is nothing wrong with being different. bad practices, however, are wrong. people try to educate you on this forum, but you decide to be stubborn.

I guess if a wizard say it is bad practice who am I to disagree. There again it is embedded into the system making it difficult to change. Even then it seems flawed when enabled. This might be the result of someone making a choice on what they think to be best. Resultant OS then is only flawless if used the default way. Being the other ways of doing the same thing were deemed bad practice they most likely received less bug checking.
I like what I like and don't feel I need to live outside the gui. I don't care if you sudo in a cli if that's your world. Being that both methods get the job done, it's really lame imo, to spout off about my way being bad practice.
Further I stand firm on both being available and functional. Maybe this is a way to get gui users to practice their cli skills. And that is a good thing as long as I am not forced to work that way. I mean I would never say that I wanted dosless window nor a cli free Linux. 
You keep on sudo'n and i will xnest and amazingly we can remain on same planet. Lastly, thanks to those that just gave help without to sermons, I have a list of ways to offer my clients choice. Some will soon be your supporters if they don't feel restricted like they did when Bill was running their PC.

---

### Post by aysiu on 2007-02-23
I think you should read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

These are the topics included:

> Contents

   1. Notes
   2. Allowing other users to run sudo
   3. Benefits of using sudo
   4. Downsides of using sudo
   5. Misconceptions
   6. Going back to a traditional root account
   7. Drag & Drop Sudo If you're going to make a choice, it might as well be an *informed* choice.

---

### Post by pappy.omatic on 2007-02-23
OK fine your right. Never attempted su or sudo till now. Made a choice on no information cause that's how the stupid make decisions. In my most humble opinion topic 6 is the very thing that unbuntu has stonewalled. This is a restriction of choice. I chose this and stated that it too did not allow free movement on my systems. This was met with alot of you can but your stupid to do so answers. Not the norm of Linux but you want to spurn those that don't want to fall in love with your sudo ways. I'll take my choice back to the corner you shoved root freedom into. Now every new post seems to drop the IQ a few numbers so I'll make this my last comment. 
Good day.

---

### Post by penguin7009 on 2007-04-25
I have to throw in with you pappy.  I know I'm going to get flamed for this comment, but I just can't take this SUDO HELL anymore!  Pity because I really like the Ubuntu's but taking a great operating system and breaking it with this stupid stuff is more than I can take.

I have zero'd my drive and reinstalled PCLOS and it works like Linux is supposed to work.  With the normal Linux one just has to become root, do what you need and exit from root.  KDE is even broken, Root file manager is deleted.  My biggest fear is that this crap will become the norm.

Sorry I will never use a Linux distro that has been butchered in this way.  It would not be too much trouble for the devs to allow experienced users to enable the NORMAL root account.  Go ahead and flame away I can take it, however, before you start telling me to rtfm, I have already done that and it doesn't change a thing.
'

penguin7009

---

### Post by aysiu on 2007-04-25
> **penguin7009 said:**
> 
Sorry I will never use a Linux distro that has been butchered in this way.  It would not be too much trouble for the devs to allow experienced users to enable the NORMAL root account.  Go ahead and flame away I can take it, however, before you start telling me to rtfm, I have already done that and it doesn't change a thing. Well, it hasn't changed a thing about your understanding, but you still don't understand what's going on.

The developers haven't stopped experienced users from enabling the normal root account. In fact, [this page](https://help.ubuntu.com/community/RootSudo) even has instructions for how to do so.

You can do whatever you want, but the default is *sudo*.

I came from Mepis (with a traditional root account) and was totally thrown off by *sudo*. I hated it. I didn't understand it. But you know what? I gave it a chance. I said to myself, "Well, they must have picked this for a reason. Let me just give it a shot. If I keep hating it, I'll just enable a root account." After a couple of weeks, I'd grown to love *sudo*.

Now, I think the traditional root account is stupid. *sudo* is safer in many ways, more convenient, and more in line with the ways people conduct security in real life (safe combinations, ATM pin numbers, etc.).

Bottom line: if you give it a real shot, you may learn to like it. And if you want to go back to a traditional root account, you can do that, too. Nothing's stopping you.

---

### Post by penguin7009 on 2007-04-25
aysiu, thanks for the reply, been giving it a try for a couple of months and still hate it.  NORMAL root account cannot be attained even with all the instructions in the manual.  

I do believe that what Linux will be in the very near future is being hashed out now.  These type of discussions and the decisions made from them will allow everyone to get in their wishes. 

Fortunately I believe that there will always be a linux distro that has not had this type of thing done to it.  I am glad that it works for you.  One of the reasons I appreciate Linux is that it can be all things to all people. We are both happy with our decisions:) 

penguin7009

---

### Post by aysiu on 2007-04-25
> **penguin7009 said:**
> aysiu, thanks for the reply, been giving it a try for a couple of months and still hate it.  NORMAL root account cannot be attained even with all the instructions in the manual. You have to create a root password: ```
sudo passwd root
``` Then, you have to enable a graphical root login (not recommended, of course, but you wanted to do something different) by going to System > Administration > Login Window and checking the "Allow Root Login" option. Where are you running into problems with that? We might be able to help you here if you post any errors you're getting.

> I do believe that what Linux will be in the very near future is being hashed out now.  These type of discussions and the decisions made from them will allow everyone to get in their wishes.  Well, considering a lot of people consider Mac OS X to be "user-friendly," I'm pretty comfortable with the *sudo* model (that's what Mac uses).

> Fortunately I believe that there will always be a linux distro that has not had this type of thing done to it.  I am glad that it works for you.  One of the reasons I appreciate Linux is that it can be all things to all people. We are both happy with our decisions:)  If you like Ubuntu except for the *sudo* thing, you may also want to try out Mepis. It's Ubuntu-based but has a traditional root account.

---

### Post by penguin7009 on 2007-04-25
> **aysiu said:**
> You have to create a root password: ```
sudo passwd root
``` Then, you have to enable a graphical root login (not recommended, of course, but you wanted to do something different) by going to System > Administration > Login Window and checking the "Allow Root Login" option. Where are you running into problems with that? We might be able to help you here if you post any errors you're getting.

 Well, considering a lot of people consider Mac OS X to be "user-friendly," I'm pretty comfortable with the *sudo* model (that's what Mac uses).

 If you like Ubuntu except for the *sudo* thing, you may also want to try out Mepis. It's Ubuntu-based but has a traditional root account.


Thanks, aysiu, I'll give it a try.   BTW, I do know whats going on, I just don't like it!

penguin7009

---

### Post by Calash on 2007-04-25
If you think Sudo is bad, you should see how many times Vista will ask for your password...make Ubuntu seem tame :)

When I first started using Ubuntu I had trouble wrapping my mind around not having an admin account of some kind.  Probably due to years of Windows programming.....need to be admin to install....yadda yadda.

Took a few weeks to get use to it, but I really like it now :)

---

### Post by penguin7009 on 2007-04-25
> **Calash said:**
> If you think Sudo is bad, you should see how many times Vista will ask for your password...make Ubuntu seem tame :)

When I first started using Ubuntu I had trouble wrapping my mind around not having an admin account of some kind.  Probably due to years of Windows programming.....need to be admin to install....yadda yadda.

Took a few weeks to get use to it, but I really like it now :)

I know what you mean,  one of my customers called me to help out with his new Vista Computer.  After using that thing for about thirty mins, I think I could get used to SUDO:KS 

penguin7009

---

### Post by eentonig on 2007-04-25
Everybody is off course free in choosing their way of working (thank God it isn't windows, or you would have been stuck with sudo :mrgreen:),

But somehow, I can't loose the feeling that it's this kind of users that once they have their root account enabled, will always login as root. And then one day will be stumped if their computer gets hacked or virus infested.

And I'm afraid they are also the ones that will go out to the public, screaming that Linux isn't any safer than windows. Because, hey... they got infested!!!!!!

It's not like one day, someone woke up and thought to himself, "Hey, what if I start nagging people by defaulting to a sudo mechanism?" This concept has been thought through and discussed by different people. Both techies as non-techies. And apparently, it was decided to be the best choice as a default administration scheme. And if the master of user-friendly-ness decided that it was good enough for their system, why should it be so bad?

---

### Post by penguin7009 on 2007-04-25
> **eentonig said:**
> Everybody is off course free in choosing their way of working (thank God it isn't windows, or you would have been stuck with sudo :mrgreen:),

But somehow, I can't loose the feeling that it's this kind of users that once they have their root account enabled, will always login as root. And then one day will be stumped if their computer gets hacked or virus infested.

And I'm afraid they are also the ones that will go out to the public, screaming that Linux isn't any safer than windows. Because, hey... they got infested!!!!!!

It's not like one day, someone woke up and thought to himself, "Hey, what if I start nagging people by defaulting to a sudo mechanism?" This concept has been thought through and discussed by different people. Both techies as non-techies. And apparently, it was decided to be the best choice as a default administration scheme. And if the master of user-friendly-ness decided that it was good enough for their system, why should it be so bad?

Thanks for the reply eentonig,  I wouldn't call myself a Linux Power User, far from it.  But I can say that after using Linux as my everyday operating system for the last five years, that I have only destroyed my linux operating system once by using the Root account.  

Since that time, I realize how powerful "root" can be.  It can be your best friend or your worst enemy.:)   I very rarely actually log onto the "root desktop".  Generally I start "root file manager" and do whatever I need to do and then exit out and thats that.  

But when one is trying to install Parallels VM and keep getting error messages having to do with not being root or if I decide to put icons or wallpaper in a system folder so I can select them out of the default folders and sudo is nagging all the time,, I just get fed up.  

I DO agree that there are many more thoughtful people than me deciding what should be done in Linux, but I just don't happen to agree with this-sorry.

penguin7009

---

### Post by eentonig on 2007-04-25
Well, as said in my previous post. Be gratefull this is not a proprietary soft, so I actually do have the choice to not work in the way it was constructed. That's what *freedom* is about.

---

### Post by penguin7009 on 2007-04-25
> **eentonig said:**
> Well, as said in my previous post. Be gratefull this is not a proprietary soft, so I actually do have the choice to not work in the way it was constructed. That's what *freedom* is about.

AGREED:lolflag: 

penguin7009

---

### Post by scanez on 2007-04-25
Can the original poster or someone who agrees with him explain what "SUDO HELL" refers to?

---

### Post by penguin7009 on 2007-04-25
Hi scanez, and thanks for the reply.  I can't speak for the original poster, but for me, I'll give it a shot.

I just finished giving Linux Mint a go.  That distro is really a beautiful work of art and is optimized for i5/686 machines.  Under the normal Linux to install Parallels, in a kde linux distro one would open the root/file manager in the menu and give the root password and then install Parallels, select open console from the dropdown menu in root file manager and type "parallels-config" enter no problem.

In Linux Mint with the screwed up SUDO account, I think you have to type "kdesu" and then enter in the run command (which never did work).  Then you type, I think, sudo parallels-config from the console.  Then when it gives you the message that root is not in the right place or whatever it was and you spend endless time finding out how to compile parallels because of the root problem, then try to run it with parallels confused and me confused etc blah, blah, blah, anyway you get the idea.

Someone on this thread suggested I try Mepis 6.5 and I have been doing that while corresponding with the good folks on this forum.  I have it installed and Parallels installed on it and it works like a champ:lolflag: 

penguin7009

---

### Post by steve.horsley on 2007-04-25
> **scanez said:**
> Can the original poster or someone who agrees with him explain what "SUDO HELL" refers to?

I think he doesn't like having to type sudo in front of every one of a whole series of commands. It can indeed become tedious, and in fact, with some commands (e.g. pipes and redirection) it plain doesn't work. He hasn't learned yet (and maybe doesn't want to learn) that **sudo su** gets you a root prompt where you can issue as many root commands as you want, including pasting in a sequence of commands that assume root privilege if needed.

And the whole idea of not constatnly working with full rights is totally alien to your average windows user. It takes a while to get used to this different way of working, of mentally separating your two roles as user and administrator. I am now comfortable with that separation, but I know that if you've never thought of them as different roles before, it can feel awkward to have to switch between them. Of course, even Windows will have to learn the difference when they downgrade to Vista.

---

### Post by eentonig on 2007-04-25
> **steve.horsley said:**
> .... Of course, even Windows will have to learn the difference when they downgrade to Vista.


Totally off topic, but I just love that last comment.:lolflag:

---

### Post by AndyCooll on 2007-04-25
When I first tried Linux I started with Fedora and it felt totally alien to be restricted in what I could do. I remember spending far too much time being logged in as root.

After a few months I switched to Ubuntu. I cannot ever remember having problems with sudo, and indeed I much prefer it. To me it is now easier to use sudo only when I need admin rights. Indeed I struggle when having to use the traditional root account when using other distros!!

:cool:

---

### Post by speeddemon8803 on 2007-04-25
*puts hard hat on*

Is it safe to come out with all the stuff flying around? I mean...I dun wanna get hit with shrapnel if its not safe in this forum :P

Root..bad bad BAD idea to be able to LOG IN as root! I LOVE the fact that root is disabled..and the only thing I need to do is sudo or sudo su! It saves me about 20 steps ;).

---

### Post by aysiu on 2007-04-25
> **speeddemon8803 said:**
> 
Root..bad bad BAD idea to be able to LOG IN as root! A *graphical* root login? Sure. But a terminal one? It depends. I like [the wiki entry on sudo and root](https://help.ubuntu.com/community/RootSudo) because it's pretty even-handed, showing both pros and cons for each model (sudo model and root model).

---

