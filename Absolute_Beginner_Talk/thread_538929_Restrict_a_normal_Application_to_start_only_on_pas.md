---
title: "Restrict a normal Application to start only on password"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-08-30
Hi
I have a little question, how can I restrict an application so that it only starts up on when I key in the password?

for example one of the games or maybe the firefox browser, or any other application.

any ideas?

---

### Post by asmoore82 on 2007-08-30
lock the screen maybe.

---

### Post by reckless2k2 on 2007-08-30
uummm...it's on the tip of my tongue. i think you have to change the desktop link too though with like gksudo before the command but you have to do a permission chmod change as well on that program. examine a root/sudo only access program and you'll get the idea.

---

### Post by MozartlovesUbun2 on 2007-08-30
> **asmoore82 said:**
> lock the screen maybe.

um you missed the whole point, i don't wanna lock the screen or log out or switch user, it's simply about having the choice to make any given application ask for a password when executed.

Simple idea really but how can it be put into use easily?

---

### Post by srt4play on 2007-08-30
You could write a shell script that asks for a password through zenity and only executes the program if the correct password is given.  Then modify the program's menu entry to point to that shell script.

---

### Post by aysiu on 2007-08-30
Well, find the executable for the application. If your application is /usr/bin/*application*, then change the permissions on that launcher so that only root can execute it: ```
sudo chmod 750 /usr/bin/*application*
``` Then change the graphical launcher to the command ```
gksudo *application*
```

---

### Post by srt4play on 2007-08-30
Would that be desirable though to have all preferences for the program stored in root's profile?  Guess it depends on what application it is.

---

### Post by aysiu on 2007-08-30
Oh, I see. So you don't want to launch it as root, because it wouldn't use the user profile. Hm. good point. I suppose a messy workaround would be: ```
mv ~/.*application* /root/.*application*
sudo ln -s /root/*application* ~/.*application*
```

---

### Post by MozartlovesUbun2 on 2007-08-30
yup, right i don't wanna lauch it as root, but I wanna type in a password for firefox launch.

---

### Post by aysiu on 2007-08-30
Can you explain a bit more of the context here? Are you worried you yourself will accidentally launch Firefox? Do you share the computer with other people, and you don't want *them* launching Firefox without your permission?

---

### Post by MozartlovesUbun2 on 2007-08-30
> **aysiu said:**
> Can you explain a bit more of the context here? Are you worried you yourself will accidentally launch Firefox? Do you share the computer with other people, and you don't want *them* launching Firefox without your permission?

yup, i leave it just running on my account all the time, so the kids can use it too, usually they just play frozen bubble, basically i let them do what they want, they can access any files or apps, so no problems with that, only i don't want them accessing the internet unsupervised.

so just want firefox to ask for a password when launched.

so the ideal is the kids can access the internet when I'm with them and no access to the web when I'm not there.

(don't really wanna create a kids account, i know that would be simple, i don't wanna hassle them with logging in and so)

---

### Post by Lord Illidan on 2007-08-30
I'd either try dansguardian, or else, see if you can a IPTABLES command to disable your internet connection completely, then of course, set a command for yourself to get it back

---

### Post by Lord Illidan on 2007-08-30
Ok, I got it. This isn't very complicated, it depends on knowing your internet interface eth0 or eth1 for example. You can use ifconfig to find out what are you using.

Anyway, all you have to do to disable ALL connection to the internet is :

```
sudo ifdown --force eth0
```

And to enable :

```
sudo ifup --force eth0
```

Replace eth0 with eth1 or whichever interface you have. This completely disables internet access, so not even proxies/different browsers will get around it, mind.

---

### Post by MozartlovesUbun2 on 2007-08-30
> **Lord Illidan said:**
> Ok, I got it. This isn't very complicated, it depends on knowing your internet interface eth0 or eth1 for example. You can use ifconfig to find out what are you using.

Anyway, all you have to do to disable ALL connection to the internet is :

```
sudo ifdown --force eth0
```

And to enable :

```
sudo ifup --force eth0
```

Replace eth0 with eth1 or whichever interface you have. This completely disables internet access, so not even proxies/different browsers will get around it, mind.

ok, but i don't want all connection cut off to the internet, coz i have azureus running, and online radio.

i just have one browser, firefox

i only want firefox to start password restricted.

---

### Post by reckless2k2 on 2007-08-30
aysiu basically said what i said about chmod the application and gksudo it to start. that is what you are looking for. nothing else is needed.

---

### Post by aysiu on 2007-08-30
> **reckless2k2 said:**
> aysiu basically said what i said about chmod the application and gksudo it to start. that is what you are looking for. nothing else is needed.
Well, running Firefox as root may not be a good idea.

---

### Post by rsambuca on 2007-08-30
Oooh, I don't think you should run a web browser as root.

EDIT- aysiu beat me to the warning!

---

### Post by LordSavage on 2007-08-30
Maybe there is a Firefox Addon to do that.

---

### Post by srt4play on 2007-08-30
Here is something that will do the job, not that good though because it relies on a plain text file with the password in it. 

```
#!/bin/bash

PASSWORD=$(zenity --entry --title="Password required" --text="Enter Password" --hide-text)

if [[ "$PASSWORD" = `cat ~/.password` ]] ; then
	firefox & 
else
	zenity --error --text="Wrong Password"	
	exit 1 ;
fi
```

---

### Post by ruibernardo on 2007-08-30
What about changing the group that can run firefox?

---

### Post by srt4play on 2007-08-30
> **epimeteo said:**
> What about changing the group that can run firefox?

Duh.  That'll do it. Simple and effective.

---

### Post by Wolki on 2007-08-30
> **epimeteo said:**
> What about changing the group that can run firefox?

Can't see that helping much - either he's in the group, or not. If he's in, he can always start it without password, if not, he can't start it himself.

I see two solutions, a good one and a bad one.
The good one is what you didn't want: different user accounts. Always a good idea to have, since you'll know they won't accidentally break your stuff, change your settings and so on.

The bad one: Allow noone to run firefox. Instead of starting firefox, start a script that restores the original rights, starts firefox and immediately disallows running firefox again.

Something like this:

```
#!/bin/sh
gksu chmod a+x /usr/bin/firefox
firefox &
gksu chmod a-x /usr/bin/firefox
```

However:
- /usr/bin/firefox itself is only a shellscript running stuff. You could just do what it does by hand, circumventing the protection
- you won't be able to start firefox from other applications (could probably be done with some fiddling)
- you could just use wget, or a python shell or similar, to get at the web content, again bypassing the filter
- + probably some stuf I didn't think of

[edit] re: the groups thing, of course he could set another user to be part of the group, but not him, then su to that user to launch firefox. might need some setup with the x displays though, so that there won't be permission problems - or tunnel it through ssh -X via localhost.

---

### Post by ruibernardo on 2007-08-30
I was suggesting to create a "firefox" group, and adding the users that can run it on that group, then change the firefox binary group too this group and chmod it like aysiu said, allowing it to be executed only by the "firefox" group.

Never tested it, so I can't confirm it, but it could work.

---

### Post by Wolki on 2007-08-31
> **epimeteo said:**
> I was suggesting to create a "firefox" group, and adding the users that can run it on that group, then change the firefox binary group too this group and chmod it like aysiu said, allowing it to be executed only by the "firefox" group.

Never tested it, so I can't confirm it, but it could work.

Sure, and it's a great plan. The problem is that the OP want to use the same user account for him/herself and the children, so if the OP is in the firefox group, the chldren are as well.

---

### Post by ruibernardo on 2007-08-31
Yes Wolki,

your solution(s) might be the best one(s)  in this case. Changing the group isn't going to do anything in this case.

I've looked into "man sudo" and "man gksudo", and there is a "-u username" option to run programs as a non-root user, but as I've tried it, it didn't even asked me for a password, since it's my user that is calling "gksudo -u".

So if the OP don't want to create an account for the kids...

---

### Post by shanepardue on 2007-10-31
> **epimeteo said:**
> Yes Wolki,

your solution(s) might be the best one(s)  in this case. Changing the group isn't going to do anything in this case.

I've looked into "man sudo" and "man gksudo", and there is a "-u username" option to run programs as a non-root user, but as I've tried it, it didn't even asked me for a password, since it's my user that is calling "gksudo -u".

So if the OP don't want to create an account for the kids...
how bout gksu -u a different username other than the one you're logged in as?

---

