---
title: "Administrator password error with Ubuntu 6.06"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by dnatisdale on 2006-09-27
After 5 or 6 attempts I've decided to ask for help with this problem. I don't understand because I just installed this distro & Logon with my Password with no problems. But when I go to change something it wants a password, well okay but I'm the only user on this computer which makes me the Administrator by default, (right?) So I put in my password again & get an incorrect password error message. If that were really the case then why can I even be in the OS to begin with? 

My questions are these: How can I fix this error? Where can I make sure I'm the Administrator? Where can I change myself to be the Administrator if I find out I'm not?

Thanks for any suggestions! Dan in Chiang Mai, Thailand

---

### Post by bodhi.zazen on 2006-09-27
I assume you are trying to su.

Ubuntu uses sudo.

sudo <command> or sudo su

use you log in PW with sudo.

---

### Post by odinfromvalhalla on 2006-09-27
to fix your problem:

1. open a terminal
2. type sudo gedit /etc/sudoers
3. if it asks you for a password you should type your own password
4. you should find a line that looks like this:
> %admin ALL=(ALL) ALL
edit it to look like this:
> %admin ALL=(ALL) NOPASSWD:ALL
5. save the file and you should now have the issue solved.

---

### Post by dnatisdale on 2006-09-28
Thanks for your help. I needed to use visudo in the Recovery Mode rather than at the Terminal to perform this task. It just wouldn't work.

Thanks! And now on to getting the USB ADSL modem to work.

Dan from Chiang Mai, Thailand

---

### Post by uk_sphinx on 2006-09-28
i am no expert myself odin but havnt you just told him how to enable a root only acount?
from what i can gather from my little time browsing the forum isnt that the whole idea of using sudo?
to stop noobs like me and him making ireversable errors?
soz if ihave got it wrong 
anyway i thought he was lacking a root password
he had to assign one???
let us know ubuntu genius's if the wrong advice was given

---

### Post by bodhi.zazen on 2006-09-28
> **uk_sphinx said:**
> i am no expert myself odin but havnt you just told him how to enable a root only acount?
from what i can gather from my little time browsing the forum isnt that the whole idea of using sudo?
to stop noobs like me and him making ireversable errors?
soz if ihave got it wrong 
anyway i thought he was lacking a root password
he had to assign one???
let us know ubuntu genius's if the wrong advice was given

The advice is good and is one way to solve the "problem".

You (uk_sphinx) have a point in that this solution is not for everybody and is not without some risk.

```
sudo su
gksudo nautilus
```
Both do the same thing without globally disabling the (sudo) password.

```
sudo passwd
```
Will allow you to set the root PW.

In the end it is each to their own on how to admin their box and what risk they want to take in exchange for "convenience".

I personally enable the root account and limit or disable sudo. I like having a separate PW for daily use and root access. This is not, however, "better" or "more secure", just a personal preference. sudo in a single user environment is +/- on security.

sudo is much more powerful in a multi user, or more specifically multi sys admin environment where in you can give varying amounts of admin access or "root powers" to "jr" team members without giving anyone but the "Sr" sys admin full root access.

**[size=2]This post in no way implies I am in any way an "ubuntu genius's" or expert in either sys admin or security. Lord knows I'm neither.[/size]**

---

### Post by uk_sphinx on 2006-09-28
yes i see what your saying,
its just that i think the guy was given a good answer to his problem without being told of the risk.
from my experiance on the forum (not a great deal) using the root only method is a touchy subject.
some people threat about it and some people think it is the best way and easiest.
if you have the knoledge to tell someone a risky method to fixing there problem, then you also have the knoledge to inform them of the risks involved first.
(unless the person with the problem states that they know the risks involved and specifically ask for you not to inform them on the subject)

---

### Post by aysiu on 2006-09-28
It sounds as if you somehow removed yourself from the *admin* group. If so, this is how you get yourself back:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

If not, you just need to understand a bit more how *sudo* works:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by bodhi.zazen on 2006-09-28
> **uk_sphinx said:**
> yes i see what your saying,
its just that i think the guy was given a good answer to his problem without being told of the risk.
from my experiance on the forum (not a great deal) using the root only method is a touchy subject.
some people threat about it and some people think it is the best way and easiest.
if you have the knoledge to tell someone a risky method to fixing there problem, then you also have the knoledge to inform them of the risks involved first.
(unless the person with the problem states that they know the risks involved and specifically ask for you not to inform them on the subject)

Yes, I do not disagree. I would imagine the problem is new users perhaps migrating from Microsoft do not understand the issues.

I also agree, as more experineced users, "full disclosure" is best.

Again, thank's to aysiu.

---

### Post by oracolo on 2006-09-29
It's the same here.
I know how sudo and gksudo works, I am a member of the admin group (both sudo and gksudo work normally from a terminal), but after having dist-upgraded to Edgy when I select from the Gnome menus a program which requires root privileges it keep asking and asking, telling me my password is wrong.
It looks like a bug :-)

---

### Post by rusimons on 2006-10-05
This is my first post in this forum, so forgive me if this post is not posted correctly. But the reason i posted it in this thread is because my problem relates to not being able to act as an administrator.

I used the alternate CD and had an oem install, After having done a lot of installing, I added several users without adminstrator priveliges, but forgot to add myself as an administrator. Then I removed the oem user by typing sudo oem-config-prepare, and never got the opportunity to add myself as a priveliged user after reboot. Now I have onlyt users without administrator priveliges on my machine. This is truly frustrating. Do I have to reinstall everything, or is threre something I can do to get adminstrator priveliges?

Thanks in advance.

---

