---
title: "How to become root?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Firequacker on 2007-09-06
How do I make it so I can sign in as root? I tried before and messed with settings and I had to wipe my harddrive lol so someone please help?

---

### Post by karvec on 2007-09-06
To use root, use "sudo <command>" in terminal.

I.E., to run gedit in root, "sudo gedit"
and it will prompt you for your password.

Root itself is not used in Ubuntu, use sudo instead.

---

### Post by wormser on 2007-09-06
Use sudo for command like and gksudo to start a graphical application.  More about [gsksudo]("http://www.psychocats.net/ubuntu/graphicalsudo").  For root access you want to use sudo instead of switching to root.  There is no need to switch to root but for your knowledge sudo -i  makes you root.

---

### Post by ClaudeBOOM on 2007-09-06
You can become root by just typing

su

Hope this help.

C.

---

### Post by parvinder on 2007-09-06
I have figured out that you can login as root with the same password as you setup for your first account during installation. Because, ubuntu doesn't specify a default password or it doesn't use it, instead it uses the features of SUDO which helps it log the action taken whenever you use sudo.

In case if you want to change the password for ROOT, execute the following command and set the password for ROOT.
sudo passwd

To login as root:
su
<enter your root password>
and you are now logged in as root.

---

### Post by zeehat on 2007-09-06
That doesn't work in Ubuntu.  Access will be denied.  For me anyways.

---

### Post by parvinder on 2007-09-06
Certaily!!! It works in ubuntu and I did that.

---

### Post by louieb on 2007-09-06
Scroll down a ways the answer is here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

some other stuff here [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Logging on as  root is a pain in the butt. Some distros don't install sudo by default. Have to Log off, switch user, login on as root, do whatever. log off. Give me sudo any day.

---

### Post by aysiu on 2007-09-06
Why don't you explain what you're *really* trying to do and why you think logging in as root is the way to accomplish the real goal?

---

### Post by sumguy231 on 2007-09-06
> Certaily!!! It works in ubuntu and I did that.
It certainly will, I think zeehat may have been referring to ClaudeBOOM's post.

---

### Post by multifaceted on 2007-09-06
Sorry, I'm a noob....

Okay, I have heard around and about that it's not a good idea to be logged in as root to perform tasks and that it's advisable to create one's own account.

**I believe that's what I did when I installed Ubuntu, and now I log in as that user.**

Am I indeed logging in as root? And is that not a good idea? :confused:

*Keep in my mind I have never needed to log from the terminal except for installs or admin tasks. *

---

### Post by sumguy231 on 2007-09-06
You're not logging in as root, you're logging in as a sudoer, a user who can use sudo to gain root permissions. And since you have to verify your password for root permissions, that's a-ok. By default, you don't have to type your password again for several minutes, but you can change that to always asking for a password (this is what I do). If you want to do this, type:
```
sudo visudo
```
And change the part that says "timestamp_timeout=..." to say "timestamp_timeout=0". If there is no "timestamp_timeout" option, you can add it to the end of the defaults line. It should look like this:
```
Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0
```
Be careful, if you screw up /etc/sudoers you'll probably have to reboot into recovery mode and fix it.

---

### Post by kavon89 on 2007-09-06
```
sudo su
```

Don't break anything...

---

### Post by multifaceted on 2007-09-08
> **sumguy231 said:**
> You're not logging in as root, you're logging in as a sudoer, a user who can use sudo to gain root permissions. And since you have to verify your password for root permissions, that's a-ok. By default, you don't have to type your password again for several minutes, but you can change that to always asking for a password (this is what I do). If you want to do this, type:
```
sudo visudo
```
And change the part that says "timestamp_timeout=..." to say "timestamp_timeout=0". If there is no "timestamp_timeout" option, you can add it to the end of the defaults line. It should look like this:
```
Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0
```
Be careful, if you screw up /etc/sudoers you'll probably have to reboot into recovery mode and fix it.

Ahhh, yes. That makes sense, thank you! I was *kind-of-sort-of* thinking that but, I don't like to assume when trying new things.

I made a note of your codes for future references. I think it's best for me to keep the default setting for now. Until at least, I become more fluent with the system.

**-Cheers**

---

