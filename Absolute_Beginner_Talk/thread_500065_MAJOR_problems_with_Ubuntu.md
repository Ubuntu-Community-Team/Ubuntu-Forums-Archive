---
title: "MAJOR problems with Ubuntu"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by uputer on 2007-07-13
Major problems with Ubuntu

I'm turned off Ubuntu.   Here's why?  

1)Tab Completion &#8211; not even enabled.   
2)Sudo su &#8211; Why?   If they really care about security, they should use the old system and give you an option for adding the Sudo system if you want it.   Not everyone wants it or even needs it.   Stick to the old su system which most distros use or many use, at least
3)Related to Mythtv:  Needed to keep switching user whenever mythtv user had to do something. But, when you have to do things needing permissions, you had to log off mythtv user and go to the original user who installed the system.    When in mythtv user session, tab completion doesn't work.   

If there are ways around those three problems, it isn't obvious and you shouldn't have to pursue the solutions anyway.   If they didn't implement those systems, there wouldn't be a problem in the first place.   Okay, I'm a noob but I don't want to deal with complicated and unnecessary systems in a distro.  

'Done venting.

---

### Post by KIAaze on 2007-07-13
[LIST]
[*]> 1)Tab Completion &#8211; not even enabled. Pathetic.

Was enabled by default for me. I don't know what you are talking about.
Or do you mean tab completion elsewhere than in the terminal and filemanagers?

[*]> 2)Sudo su &#8211; very useless system. If they really care about security, they should use the old system and give you an option for adding the Sudo system if you want it. Not everyone wants it or even needs it. Stick to the old su system which most distros use or many use, at least

If you know other distros already, I don't think you're a real newbie.
If you want to disable sudo and use su, it is possible.
Simply create a root password by entering ```
sudo passwd root
```.
Afterwards, remove this entry from the /etc/sudoers file:
> # Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

[*]> 3)Related to Mythtv: Needed to keep switching user whenever mythtv user had to do something. But, when you have to do things needing permissions, you had to log off mythtv user and go to the original user who installed the system. Really stupid. When in mythtv user session, tab completion doesn't work.

Sorry, never used it.


[*]Since you know other distros and don't like Ubuntu, use those other distros.
[/LIST]

---

### Post by twiceasworn on 2007-07-13
Excuse me but I think it is a bit crass for you to come into our community and do nothing but bitch.  It is almost a slap in the face.  Are you even asking for help or are you just whining about some small issues you are having.  If you are wanting help we would be happy to help you out.

1) Tab completion not enabled?  Every ubuntu install I have ever done has had this enabled by default the first time I boot into the system.

2) Sudo is actually more secure, because then people who aren't uber l33t linux hax0rs don't unintentionally bork their entire system.  Personally I love it for that exact reason.  Also, you can use the standard su system if you like, it just isn't enabled automatically like you apparently would like it to be.

3) Can't help you here, but it sounds like a chown issue to me.

In short, all of these issues can be solved if you took the time to try and do so.  Linux usually takes some toying with to make it work exactly as one would like, but that is half the fun of a fully customizable system.  Honestly it sounds like you just want everything to work exactly the way you think it should work right when the system is installed.  Unfortunately at the moment that is fairly unrealistic with Ubuntu or any linux disto in general.

---

### Post by cosborn72 on 2007-07-13
Can I recommend Windows Vista?  

1.  You don't have to worry about these silly configuration  issues, because Vista will tell you how your computer will be configured. 

2. You won't have to worry about sudo at all- Vista will just assume you are an idiot that shouldn't be messing with anything important.  

3. I'm sure you could buy software for windows similar to MythTV for $50-$200 bucks, and then you can talk to some tech support guy with a thick foreign accent if you have difficulty getting it to work.

Seems like a perfect solution to your problem.


> **uputer said:**
> Major problems with Ubuntu

If there are ways around those three problems, it isn't obvious and you shouldn't have to pursue the solutions anyway.   If they didn't implement those systems, there wouldn't be a problem in the first place.   Okay, I'm a noob but I don't want to deal with complicated and unnecessary systems in a distro.  

Why is this distro so popular anyway?!?

'Done venting.

---

### Post by uputer on 2007-07-13
> **twiceasworn said:**
> 
1) Tab completion not enabled?  Every ubuntu install I have ever done has had this enabled by default the first time I boot into the system.

2) Sudo is actually more secure, because then people who aren't uber l33t linux hax0rs don't unintentionally bork their entire system.  Personally I love it for that exact reason.  Also, you can use the standard su system if you like, it just isn't enabled automatically like you apparently would like it to be.

3) Can't help you here, but it sounds like a chown issue to me.

In short, all of these issues can be solved if you took the time to try and do so.  Linux usually takes some toying with to make it work exactly as one would like, but that is half the fun of a fully customizable system.  Honestly it sounds like you just want everything to work exactly the way you think it should work right when the system is installed.  Unfortunately at the moment that is fairly unrealistic with Ubuntu or any linux disto in general.
1) Try creating a new user and tell me that tab completion is enabled.  

2) I want it enabled automatically like most distros, yes.   #2 isn't as big a deal as issue #1 and #3, though.   It was a minor nuisance.

3) If you create a new user, you cannot use tab completion by default.   If you try, you get an output of a bunch of characters.   I don't know how you enable it and that is not the point.   Why is it disabled?   What for?   I thought it was annoying to have to keep switching users, too.   Twiceasworn, I don't mind some configuring but you know the saying, 'if it ain't broke, don't fix it?'    I think Ubuntu tried to fix things.

---

### Post by tgm4883 on 2007-07-13
> **uputer said:**
> 1) Try creating a new user and tell me that tab completion is enabled.  

2) I want it enabled automatically like most distros, yes.   #2 isn't as big a deal as issue #1 and #3, though.   It was a minor nuisance.

3) If you create a new user, you cannot use tab completion by default.   If you try, you get an output of a bunch of characters.   I don't know how you enable it and that is not the point.   Why is it disabled?   What for?   I thought it was annoying to have to keep switching users, too.   Twiceasworn, I don't mind some configuring but you know the saying, 'if it ain't broke, don't fix it?'    I think Ubuntu tried to fix things.

What are you trying to do in MythTV that requires you to have root privledges?  I'm assuming that your using this as a frontend/backend/desktop.  And that you need root privledges for other things.  Did you try adding yourself to the mythtv group?

Nevermind, I just read a couple of your other threads.  Seems that you don't really want help.

---

### Post by KIAaze on 2007-07-13
> **uputer said:**
> 1) Try creating a new user and tell me that tab completion is enabled.  

3) If you create a new user, you cannot use tab completion by default.   If you try, you get an output of a bunch of characters.   I don't know how you enable it and that is not the point.   Why is it disabled?   What for?   I thought it was annoying to have to keep switching users, too.   Twiceasworn, I don't mind some configuring but you know the saying, 'if it ain't broke, don't fix it?'    I think Ubuntu tried to fix things.

This should help, if help is what you seek:
[How to enable tab completion for new users]("http://ubuntuforums.org/showthread.php?t=335225")

I'll have to try creating a new user too. If it's a bug and hasn't been reported yet, it should be.

---

### Post by mlentink on 2007-07-13
Dear Sir,

We express our deep regret that our software did not fully measure up to your expectations. 
Might we suggest you take this up with our management for a full refund?

---

### Post by mendingo84 on 2007-07-13
for the tab completion issue be sure that the user you created  uses the BASH interpreter. In many cases (solaris for example, dunno about Ubuntu though) the default interpreter is set as KSH and that one doesn't do tab completion.

---

### Post by Arwen on 2007-07-13
> **mendingo84 said:**
> for the tab completion issue be sure that the user you created  uses the BASH interpreter. In many cases (solaris for example, dunno about Ubuntu though) the default interpreter is set as KSH and that one doesn't do tab completion.
He won't stop bitching unless you help him get over his MythTV and tab addiction :-P

> Dear Sir,

We express our deep regret that our software did not fully measure up to your expectations.
Might we suggest you take this up with our management for a full refund?

LOOOOL  mlentink :-D

Maybe he should wait for a new service pack :-P

---

### Post by uputer on 2007-07-13
> **tgm4883 said:**
> What are you trying to do in MythTV that requires you to have root privledges?  I'm assuming that your using this as a frontend/backend/desktop.  And that you need root privledges for other things.  Did you try adding yourself to the mythtv group?

Nevermind, I just read a couple of your other threads.  Seems that you don't really want help.
Yes, frontend/backend desktop.   I cannot add myself to the mythtv group since the mythtv user doesn't have the privileges and thus, the options in the menu are both restricted and limited.  

Well, I don't expect help from 'Ubuntu snobs.'   Most of the replies indicate I am right in thinking so.   

I was not insulting anyone so I don't understand why insults were given.   I'm criticizing the programming and it's constructive criticism, I thought.   

The issues are not minor.    I probably shouldn't post following the frustrations and such hair-pulling situations.   

I believe many hard-core Linux users would object to those situations.   But, hey, I'm just a noob and speculating here.

---

### Post by hyper_ch on 2007-07-13
uputer:

May I suggest you have a read at this here:  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Although this is not a linux/windows thingy the same principles apply between the different distros... just because you think it not good the way it is, it does not mean others think the same...

So instead of coming here and saying this is not good and that is bad... you first should get used to this before you make a judgment...

And well, you were bitching in your first thread and now you call the people here "Ubuntu snobs"?

Although you seem to be an experience linux user, why do you post in the beginner's section?

---

### Post by xubu_caapn on 2007-07-13
"Ubuntu snobs"? The majority of the people that responded were helpful and understanding, which is a lot more than you deserve. Why don't you try framing your questions in a respectful manner? I'm sure you'd get less "snobbish" responses.

Also, please keep in mind: Ubuntu doesn't owe you anything. Linux doesn't owe you anything. Stop assuming it does.

---

### Post by uputer on 2007-07-13
Okay, I definitely didn't mean everybody.   I was speaking of some posters who didn't offer any ideas at all but wanted to add their own two cents sprinkled with sarcasm.  

Those 'solutions' sound interesting.   I will try them out.   I still think they shouldn't be needed.   Personal opinion, okay?

Btw, I read hyper_ch's page.   I understand where you are coming from and the others who didn't like my original post.  But, you forgot to recognize it was not a comparison to Windows but other debian-based distros that don't suffer the same issues.   I was wondering why Ubuntu chose to create it that way and why more *LINUX* or Ubuntu users aren't complaining about it.

---

### Post by tgm4883 on 2007-07-13
> **uputer said:**
> Yes, frontend/backend desktop.  ** I cannot add myself to the mythtv group since the mythtv user doesn't have the privileges** and thus, the options in the menu are both restricted and limited.  



As a user with sudo privledges (ie, your default user)

[LIST=1]
[*]Go to System > Administration > Users and Groups
[*]Click "Manage Groups".  
[*]Scroll down to "mythtv" 
[*]Click on "mythtv"
[*]Click on "Properties".
[*]Click on the check box next to the user you want to add to the mythtv group.
[*]Click "OK"
[*]Click "Close"
[*]Restart GDM.
[/LIST]

> Well, I don't expect help from **'Ubuntu snobs.' **  Most of the replies indicate I am right in thinking so.   

I was not insulting anyone so I don't understand why insults were given.   I'm criticizing the programming and it's constructive criticism, I thought.   

The issues are not minor.    I probably shouldn't post following the frustrations and such hair-pulling situations.   

I believe many hard-core Linux users would object to those situations.   But, hey, I'm just a noob and speculating here.

Sticks and stones mate, but i'm still trying to help you.  The question remains though, will you help yourself?

---

### Post by KIAaze on 2007-07-13
Ok, I created a second user account (non-admin, all options left on default) on my PC and had no problems at all with tab completion.
But I am using Gutsy, so maybe the problem does exist in Feisty.

Anyway, this would mean that the bug has been corrected or that you are one of the rare people to have experienced this problem.
What version of Ubuntu do you use? What kind of new user did you create?

> **uputer said:**
> I was wondering why Ubuntu chose to create it that way and why more *LINUX* or Ubuntu users aren't complaining about it.

The benefits/reasons of using "sudo" instead of "su" are very well explained here:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

For most Ubuntu users, Ubuntu was probably their first GNU/Linux distro, so they have no reason to want "su" instead of "sudo", especially since the password is stored for some time, so it doesn't need to be re-entered everytime.

And for users who previously used another distro, I don't really think it's hard to adapt. Sudo could be setup on other distros too and was quite useful.
Personally, I started with Debian and I had no problems at all with sudo. On Ubuntu, I created a root password, so if I want to use su, I can. If I want sudo, I can too.

Concerning MythTV, I had never heard of it before and I don't know if it's widely used in the Ubuntu community.
Are you sure that the problem you are experiencing is specific to Ubuntu?

---

### Post by tgm4883 on 2007-07-13
> **KIAaze said:**
> Ok, I created a second user account (non-admin, all options left on default) on my PC and had no problems at all with tab completion.
But I am using Gutsy, so maybe the problem does exist in Feisty.

Anyway, this would mean that the bug has been corrected or that you are one of the rare people to have experienced this problem.
What version of Ubuntu do you use? What kind of new user did you create?



The benefits/reasons of using "sudo" instead of "su" are very well explained here:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

For most Ubuntu users, Ubuntu was probably their first GNU/Linux distro, so they have no reason to want "su" instead of "sudo", especially since the password is stored for some time, so it doesn't need to be re-entered everytime.

And for users who previously used another distro, I don't really think it's hard to adapt. Sudo could be setup on other distros too and was quite useful.
Personally, I started with Debian and I had no problems at all with sudo. On Ubuntu, I created a root password, so if I want to use su, I can. If I want sudo, I can too.

Concerning MythTV, I had never heard of it before and I don't know if it's widely used in the Ubuntu community.
Are you sure that the problem you are experiencing is specific to Ubuntu?

MythTV is used in the Ubuntu community.  There is even a disto in development combining the two called [Mythbuntu]("http://www.mythbuntu.org")

The problem he is having is not specific to Ubuntu (although I don't know if it is specific to anything, as I hadn't heard of it that much) but only requires that he add his main user to the mythtv group (which I seem to remember mythtv asking if I wanted to do that during the install.)

:EDIT: 

Just checked, during install, if the current user is not a member of the mythtv group you get this prompt.
[IMG]https://help.ubuntu.com/community/MythTV/Install/Live/Feisty+/Config_BE?action=AttachFile&do=get&target=group_1.png[/IMG]

---

### Post by anewguy on 2007-07-13
As a new user myself, I would like to add the following observation:

:)Most of the people on this forum have been greatly helpful to me.  There are exceptions, and what usually results is a big p**sing contest, as has happened in part of your post, instead of attempts to answer the question.  tgm4883 should be thanked, as he has tried to stay out of that and instead tried to provide an answer.

There is a key point I think some need to note here:  Since this is supposed to be an Absolute Beginners forum, you might say this user has more experience than expected.  But what if he is a new user to Ubuntu?  I know that people posting things here in a frustrated fashion may be maddening, but also try to remember that people are posting here for very honest reasons.  Maybe they haven't follow the same path as you, digging all over the place, etc., but that honestly seems to be expected when you are trying to bring in more desktop users - Windows users in particular.  Many of these people are not technically oriented, but have tried their best before posting here.  The idea of jumping all over the internet in search of answers really is a new experience to a lot of Windows users.  To reach them, this forum is a great start, as long as things don't break down to everyone being defensive about everything instead of just honestly trying to answer the question.

I know I have asked what are probably some really dumb questions on this forum, but I have for the most part gotten some great help without people wanting to argue.  I hope my experience will be further migrated to others posting here.:)

---

### Post by uputer on 2007-07-13
> **KIAaze said:**
> 
What version of Ubuntu do you use? What kind of new user did you create?

Personally, I started with Debian and I had no problems at all with sudo. On Ubuntu, I created a root password, so if I want to use su, I can. If I want sudo, I can too.

Concerning MythTV, I had never heard of it before and I don't know if it's widely used in the Ubuntu community.
Are you sure that the problem you are experiencing is specific to Ubuntu?
I'm using ver. 7.04 Feisty (Standard: x86/32 bit).  I've used Debian before.  I think it works better.  Ubuntu stays really up to date so I wanted to try it.  

The users are <ME>, <root> and <mythtv> but <mythtv> doesn't show up in the Admin list-Users/Groups list.  

I have not been able to add my main user to the mythtv group.  In the mythtv session, I don't have the permissions so anytime I need them, I need to log off/switch sessions and go to my main user session.

Edit:  So, it sounds like you have to do a complete reinstall of Mythtv to add extra users to mythtv.   That makes sense (*sarcastic*).  

anewguy, I have had expert help with learning but imho, Ubuntu has some ridiculous quirks.   I guess if you haven't had much exposure to linux, you would not notice.  But, I know experts think they're not that good.  

If you compare, Debian is easier to do things.   I cannot change my background colour except for orange or brown.  I'm sure there's a way but Ubuntu made certain it's super hard.  Also, I have to enter my password twice since it goes into standby/sleep mode after I enter the password the first time.  I guess that makes sense, too.  You gotta be secure.   Any 'rolling eyes' icon anywhere?

---

### Post by tgm4883 on 2007-07-13
> **uputer said:**
> I'm using ver. 7.04 Feisty (Standard: x86/32 bit).  I've used Debian before.  I think it works better.  Ubuntu stays really up to date so I wanted to try it.  

The users are <ME>, <root> and <mythtv> but <mythtv> doesn't show up in the Admin list-Users/Groups list.  

I have not been able to add my main user to the mythtv group.  In the mythtv session, I don't have the permissions so anytime I need them, I need to log off/switch sessions and go to my main user session.

Edit:  So, it sounds like you have to do a complete reinstall of Mythtv to add extra users to mythtv.   That makes sense (*sarcastic*).  

anewguy, I have had expert help with learning but imho, Ubuntu has some ridiculous quirks.   I guess if you haven't had much exposure to linux, you would not notice.  But, I know experts think they're not that good.  

If you compare, Debian is easier to do things.   I cannot change my background colour except for orange or brown.  I'm sure there's a way but Ubuntu made certain it's super hard.  Also, I have to enter my password twice since it goes into standby/sleep mode after I enter the password the first time.  I guess that makes sense, too.  You gotta be secure.   Any 'rolling eyes' icon anywhere?
:roll: are you :confused:

People are trying too help you, more than you are trying to help yourself, but here it goes.

To add your user to the mythtv group.  From the command line do this as root.  Where *username* is the user you are trying to add.  
```
adduser *username* mythtv
```

And about the background color.  Is it really so hard to go to System > Preferences > Desktop Background and change your background color (or maybe make it a picture?).  If it is, let me know.  I can write a guide for you on how to use your mouse.  :roll:

But seriously though, people are trying to help you and your just being an *** about it.  Work with _us_ so we can help _you_ fix your problems.  We can't fix your problems by ourselves unless we ssh into your computer.

---

### Post by uputer on 2007-07-13
I figured out how to add a background colour but how do you get the preconfigured colours back?   I accidentally deleted two.  The default or 'no wallpaper' was left.

adduser username mythtv returns " The user `mythtv' already exists."   I was already anticipating that.  

In Users settings, My 'MainUsername' and Root are present.   mythtv is in the Group Settings, though.  But, so what?   It still doesn't solve the problem.   When 'mythtv' needs permissions, I must log out and log into "MainUsername" (calling it that out of simplicity).

---

