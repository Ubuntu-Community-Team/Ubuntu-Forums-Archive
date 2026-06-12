---
title: "Need some help in places."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-04
HI, i am new to Ubuntu so you can call me a noob.

Here are the questions i need help on:

How do I get the  Repositories to work? (I have tried all the diffrent steps on the forums, and the unofficial guide, and the official guide)?

How come when I Click the software updates button in the top right it tells me "Only one software management tool is allowed to run at the same time".I don't think i have any other software running tools.?

How come when I type in the terminal /etc/apt/sources.list, it tells me permission denied?

How come when I type in su in the terminal it asks me for a password, i type in my password for my system, the one i setted when I was installing Ubuntu.

How can I run Ubuntu in a 1440x900 resolution?

How can i get to be a super user.



I know i made a very huge list of stuff, so i don't people to just rush into this thread and give me tips and stuff, but if like a few people got some time, please help, i ain't giving up from Ubuntu.

---

### Post by whizbaby on 2006-09-04
First thing, **su** will be useless because the root account doesn't have a password in ubuntu. Try **sudo** instead, as the installer you are the first person on the comp allowed to use it (it'll give u superuser rights for the command following it and store your password for a while).
Package applications lock */var/lib/dpkg/lock*, so you cannot run **synaptic** and **apt-get** at the same time (even not **apt-get** in two different terminals)
For debugging post your */etc/apt/sources.list*.

---

### Post by wpshooter on 2006-09-04
First, I think, you are not allowed to say run Synaptic and update manager at the same time.

Here is what I do on a new installation as far as repositories is concerned.

First make sure you have "automatically save changes to sessions" checked in the session section.  Probably a good idea to restart after you check this.

Then go into software properties and check all of the available repositories.  Then go to the first one on the listing, hightlight it and then go into ADD and when you get in there check both community maintained and non-free then click ADD button and then close out of software properties and hit the reload button.  You might want to restart at this point.  Then when you go back into software properties you should probably have 11 repositories checked.

After this go into update manager and check for any available updates and apply them.

Good luck.

---

### Post by bodhi.zazen on 2006-09-04
1. Ubuntu uses "sudo" rather then su.

Ex: su <command> -> It will ask you for a password -> enter your (user) log in passowrd.

2. To edit /etc/apt/sources.list:
In a terminal: sudo nano /etc/apt/sources.list
Ctrl-X to exit, type "Y" to save edit.

Remove the hash (#) from the start of a line to enable a repository.

3. Not sure about your error with synaptic. Exit and re-login or reboot should fix.

4. After editing /etc/apt/source.list, refresh your database:
Point and clidk refresh win synaptic
apt-get update at terminal.

5. for resolution:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```

If this does not work, post monitor and video card info as well as /etc/X11/xorg.conf

---

### Post by crunchystrike on 2006-09-04
ok, i have done what you told me to, not really much help no offense, but when i type su, it asks me for a password, i press enter, type in my pass, and then wait, tells me the authentication failure. I just need all of this to install my ATI drivers. and the rest of the questions above.

---

### Post by mejy on 2006-09-04
I think that was a typo - presumably he meant to say

sudo <<command>>

All his other answers should help though - Is that the only thing that didn't work for you?

---

### Post by meng on 2006-09-04
The superuser question: Ubuntu by default does not enable a root password. Instead you can preface each individual command with sudo, and use your user password when prompted.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by whizbaby on 2006-09-04
sudo - SuperUserDO
su   - SwitchUser

You cannot switch to a 'nonexisting' (actually a root-account exists, it only has no password assigned to it) account.

so in ubuntu: **sudo**!

---

### Post by bodhi.zazen on 2006-09-04
> **crunchystrike said:**
> ok, i have done what you told me to, not really much help no offense, but when i type su, it asks me for a password, i press enter, type in my pass, and then wait, tells me the authentication failure. I just need all of this to install my ATI drivers. and the rest of the questions above.

**NOT SU, SUDO !!!**

ex:
```
sudo nano /etc/apt/sources.list
```

NOT
su -> enter root password -> nano /etc/apt/sources.list

If you want to change the root password: sudo passwd, enter root passowrd, now you can su.
(so su me)

---

### Post by bodhi.zazen on 2006-09-04
> **whizbaby said:**
> sudo - SuperUserDO
su   - SwitchUser

You cannot switch to a 'nonexisting' (actually a root-account exists, it only has no password assigned to it) account.

so in ubuntu: **sudo**!

Not true, root has a random password assigned during installation. If there were no password you could su with no password, a very serious security hole.

You can change the root password as above, Ubutnu users do not like this.

Personally I think sudo with no restrictions is as risky as changing the root password and using su. If I am doing extensive sys admin I su into root. I have limited sudo powers to the first ubuntu account. ?More secure, do not know.

---

### Post by whizbaby on 2006-09-04
That's right (that root-password thingy).
su and sudo have the same vulnerability: with you knowing the root password and do su or being allowed to sudo you'll get the same problems when your account is cracked. The advantage of sudo is that it mostly leads to a different behaviour (most of the time you're not administrator) and it's not so bad forgetting to log out as with su (left-open-root-terminal).
(actually you could generate that with 'sudo xterm', too, but that's a bit more than just typing 'su')

---

### Post by bodhi.zazen on 2006-09-05
Although I do not disagree, sudo involves only 1 password, the user's which is used much more frequently. Thus crack the user password and you have unlimited root access.

su = 2 passwords, user's (to log on) + root.

Thus open access to sudo, as is the default in Ubuntu, could be considered less secure.

I agree with the awareness/change of behavior point, but how is this different from su?

Thus I restrict sudo access and use su for sys admin. Easy enough to configure, personal preference really.

I think root log-in should not be allowed in GDM/KDM/XDM or remote.

---

### Post by whizbaby on 2006-09-05
If your account is cracked the root password will be spyed out the next time you su, so no real advantage here...

---

### Post by bodhi.zazen on 2006-09-05
> **whizbaby said:**
> If your account is cracked the root password will be spyed out the next time you su, so no real advantage here...

You have a point. I guess my only point is a counter point to the Ubuntu default of sudo over su (sometimes I just feel contrary).

What can I say? At least there is a delay and a cracker does not have instant root access. I su into my box, at the most, once a week? sometimes not so often. It not as if I do not update, I just do not update without a little caution and research (see recent debacle with X. Yes **it happens, no problem, but if i update less often I am less labile).

My point is su vs. sudo, is at the end of the day, a matter of preference and neither is more or less secure. Occasionally on Ubuntu I see people asking how to enable su. The Ubuntu community tends to imply that sudo is somehow more secure then su.

I find su a convenience, and I know how, so I su. I will advise how to enable su if asked.

I understand why Ubuntu uses sudo but, in the end, sudo with unlimited powers is almost equivalent to su.

Root must be used with understanding and caution. :rolleyes:

---

