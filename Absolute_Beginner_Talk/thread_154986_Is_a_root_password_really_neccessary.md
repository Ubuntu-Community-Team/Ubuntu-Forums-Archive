---
title: "Is a root password really neccessary?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by joewhite on 2006-04-04
I've been using a computer for 10 years and I've never been hacked in Windows. What makes Linux so insecure to the point that I have to enter in my root password numerous times ever session? I'm not attacking the concept for networks it is just that for an average home broadband user is it really necessary? Can't I just deactivate the passwords?

---

### Post by meborc on 2006-04-04
:mrgreen: you get it all backwords... linux is not insecure to require root password all the time... it is SECURE cuz it does it :mrgreen: 

AND dont use sudo all the time... you can manage to do most of your basic comp usage without using sudo...

for more info: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

from wiki:> The benefits of leaving root disabled by default include the following: 

The installer has to ask fewer questions 

Users don't have to remember an extra password, which they are likely to forget 

It avoids the "I can do anything" interactive login by default -you will be prompted for a password before major changes can happen, which should make you think about the consequences of what you are doing. 

Sudo adds a log entry of the command(s) run (In /var/log/auth.log). If you mess up, you can always go back and see what commands were run. It is also nice for auditing. 

Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are. 

Allows easy transfer for admin rights, in a short term or long term period, by adding and removing users from groups, while not compromising the root account. 

sudo can be setup with a much more fine-grained security policy 


---

### Post by carlosqueso on 2006-04-04
If you want to not have to use sudo and you're doing a lot of stuff in a shell, just type sudo -i and you'll be root until you choose not to be, at least for that session.   Other than that, you really shouldn't stay root because then malicious programs can do nasty things to your computer that if you ran them without root permissions, they couldn't.

---

### Post by Stealth on 2006-04-04
[QUOTE=joewhite]for an average home broadband user is it really necessary?[/QUOTE]

DEFINITELY! You see, you (and no offense, its more of a compliment ;)) are not an average user. Why? Because you somehow were able to keep your Windows virus free. Now an *average* broadband user would be attacked by probably every major worm, have multiple spy/adware programs running/installed, and perhaps a virus/trojan or 2. And having broadband (i.e. download all of em nasties in seconds) does not help. Now what's cool is that if they used Linux, they'd never have this issue. The viruses and such that would try to install themselves automatically (like they do in Windows) would not be able to because you need root priveledges to do that. So unless you actually WANT to install the virus, that thing won't be infecting anything on your machine. :mrgreen:

---

### Post by Darkriser on 2006-04-04
just a note - sudo doesn't require root password. it's just an ordinary user password ;)

---

