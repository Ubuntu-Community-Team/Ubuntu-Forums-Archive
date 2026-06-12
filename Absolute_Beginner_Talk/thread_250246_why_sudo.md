---
title: "why sudo?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by fotion on 2006-09-03
about me:
i've recently become a linux convert, 'bout three months ago i made the switch. my son walked me through a slackware installation to get me started. it was fairly simple and painless. since then i've installed several livecd/dvds and several 'honest' linux installations myself. most information i've needed i have found through google. it has been quite refreshing to find linux quite simple. currently my computer boots twelve diffrent linux distros, xp and 98se. i'm in search of a perfect os, one which probably doesn't exist.

my question:
i've noticed that ubuntu uses 'sudo' to launch 'root' access. why? is this not the same as being 'root', but with a little inconvenience? how does this make my system more safe from myself? even xp can be configured to prevent average users 'admin' access. if my wife, children, or grandkids wish to use my computer they know my password, and with that password they are able to 'sudo'. is this not stupid? i understand why this would be preferable for livecd/dvds, but an installed os?

any information would be appreciated. this is merely a quest for knowledge and my personal growth. thanx

---

### Post by %hMa@?b&lt;C on 2006-09-03
when a wannabe hacker/cracker/skiddy tries to break into your computer, if it is a linux/unix box, the one account that (s)he will try is root, and use a program to try different passwords. With ubuntu there is no root account by default, so you are more secure in that sense.

---

### Post by Bachstelze on 2006-09-03
Hi and welcome to Ubuntu :)

Have you read [this ](https://help.ubuntu.com/community/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac)?

---

### Post by jISh on 2006-09-03
To put it simply: It's a lot safer.
It's a precaution, so you have a chance to think about what you are doing before you modify anything using root authority. It protects from mistakes.

Even if you have a regular setup with a root account and user accounts, it's never good to stay logged in as root.

If you want to login temporarily as root, use sudo -i
Make sure you type exit after you are done fiddling about with root authority!

---

### Post by elpuerco on 2006-09-03
Good thread, answered my question on this topic, thnx

=D>

---

### Post by SkyNet2029 on 2006-09-03
The premise of double checking wether or not you are sure you wish to risk hosing your system is an old one, although sudo does make 
more sense than having to manually edit your installed programs (XP,NT) to allow the 'run-as' service to prompt for a password, IMHO.
On the other hand, one of the first things I noticed is in 'visudo' (command to edit the sudoers list) and it strikes me as a step 
backwards, as security goes:


# Members of the admin group may gain root privileges
# %admin ALL=(ALL) ALL

-----------
Why even allow this, as it theoretically could allow a malicious person easier access to core files, increasing the chance of system
compromise. I do understand that without this line you would need true root access to gain the ability to modify the sudoers list. 
With it being there (mine is commented out beacuse I am OCD about security) would it not allow anyone with your password (the 
scripies,crackers or hackers mentioned previously) to have simple root access, thus short-cutting the whole purpose of a root account?
...I did not mean to hijack a thread, but your questioni got me to thinking about all of that sudo business.

---

### Post by fotion on 2006-09-03
> **HymnToLife said:**
> Hi and welcome to Ubuntu :)

Have you read [this ](https://help.ubuntu.com/community/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac)?

thanks for that link.

definitely worth the read.

my understanding now is the system is safer from the hackers, but will still allow me to break any/everything. lesser of two evils, i guess

---

### Post by az on 2006-09-03
> **fotion said:**
> thanks for that link.

definitely worth the read.

my understanding now is the system is safer from the hackers, but will still allow me to break any/everything. lesser of two evils, i guess

Sudo is not meant to be safer in the security sense or in preventing accidents.  It is a finer-grained way of escalating previledges.  Using root is all-or-nothing and sudo is meant to deal with the inconveniences of that.  

It can sometimes be safer and more user friendly.  Another advantage is that every sudo act is logged which is helpful when you want to figure out what you did wrong.

---

### Post by wildseven on 2006-09-03
where is the sudo log? just wondering.

-wild7

---

### Post by BatteryCell on 2006-09-03
If its just you and your computer than there really isnt IMHO any difference between logging in as root and using sudo...except that its more of a  inconvinience to use sudo. I beleive this because:
1.)If I was to use sudo, I'm going to give myself administrative access...which practically is root.
2.)Therefore if a hacker got into my account he could kill the computer just as easily.
3.)I could still hose the computer just as bad.

However, in a family computer sudo is much more secure because if lets say you have some small children that go "hey look someone emailed me with a link that says click here" and then they click it... they wont do any serious damage except to maybe their own home folder.  Also, only people who know what they're doing will be able to install or administer stuff (as it should be).

---

### Post by skymt on 2006-09-03
> **wildseven said:**
> where is the sudo log? just wondering.

-wild7

/var/log/auth.log

Not just sudo, but the sudo lines are marked.

---

### Post by skymt on 2006-09-03
One interesting thing about sudo is that you can give different users permission to sudo different commands. So, if you want regular users to be able to reboot the computer, but not to install software, you can edit /etc/sudoers for that.

---

