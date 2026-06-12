---
title: "[SOLVED] adduser : adding an administrator via terminal"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-09-02
How do I add an administrative user via terminal after hiting "ctrl+alt+1"?

At the moment, I'm using Ubuntu Feisty's Live-CD; it's giving me login problems.

I figure I need to know what group the user "ubuntu" is in. That's the one that gives me administrative control.

I can't figure this out. I can't really find too much information on the web to make an admin account. All I end up doing is making user accounts; I need admin control.

note:

I created a password for ubuntu before making more user accounts.

---

### Post by Dr Small on 2007-09-02
What kind of login problems?

---

### Post by Genecks on 2007-09-02
For one, I can't use sudo.

For example, this is what I just did one minute ago.

CTRL+ALT+1

1: login with user with admin power

sudo adduser --home /home/someone someone
enter password: **********

create UNIX password: blah blahsadfasdf
again: sadfsadf
fill in details

yada yada

....

account created

$ exit

login: someone
password: ****

someone@ubuntu $: sudo su
password: **********

someone is not in the sudoer's file... yada yada... blah blah

/ END

I entered the right password, btw.
I couldn't get administrative control of root.

> **Dr Small said:**
> What kind of login problems?

It stalls when it automatically goes into user: ubuntu. There also seem to be some hardware access layers. I've intermittently read a couple bugs about this, but I'm more about finding a solution at the moment.

---

### Post by wormser on 2007-09-02
Try this:

```
sudo usermod -g username
```

The switch g (-g) is for group.  You are just adding this user to the admin group which has sudo rights.

For root (you should only use sudo)

```
sudo -i
```

---

### Post by Genecks on 2007-09-02
> **wormser said:**
> Try this:

```
sudo usermod -g username
```

The switch g (-g) is for group.  You are just adding this user to the admin group which has sudo rights.

For root (you should only use sudo)

```
sudo -i
```

This almost did the trick, but I need the privileges for the new admin account to be set. I need to do this through terminal, and I can't figure out how.

I'm talking about those boxes a person would use if he or she were inside of "users and groups," which is within System -> Administration.

...except, I need to do this through terminal. If I remember correctly, those privileges are actually groups, not options; however, I'm not sure. Anyone know how to set the privileges for accounts via terminal?

---

### Post by aysiu on 2007-09-02
The password for the live CD is no password at all. In fact, it shouldn't even be prompting you for a password.

---

### Post by Paul133 on 2007-09-02
Yes. Those are groups and not privileges. If 'usermod' will add you to admin, there must be a way to add all the other groups. Sadly, I don't know how to do it.

edit: Figured it out. usermod -g lets you edit your login group. usermod -Ga lets you append other supplementary groups.

---

### Post by southernman on 2007-09-02
Wait... you need root for a Livecd?

---

### Post by jordanmthomas on 2007-09-02
```
sudo usermod -aG wheel username
```
```
sudo usermod -aG admin username
```

I'm pretty sure in Ubuntu you just need to be in the group labeled admin, but most distros want you to be in the wheel group, so add it for good measure.

**edit** I'm not really sure I understand your problem though.

---

### Post by Genecks on 2007-09-02
I found the answer.
I edited the /etc/group with with gedit.

P.S.

I don't even fully understand my problem. I know some other people are having it. It has to do with the boot process, HAL, and some other factors. I don't have time too analyze it all, though.

---

### Post by Paul133 on 2007-09-02
Why did you have to do it through terminal? Obviously you have a GUI if you're using gedit.

---

### Post by Genecks on 2007-09-02
I could've used nano.

Alright, you nosy people.

I'm emulating the process at the moment using an HDD install. (this thread is pseudo-hypothetical; you don't see those everyday)

However, I know that when I go to the box with the Live-CD, it's not going to go through GDM correctly with the ubuntu account: It hangs. I don't know why.

I've learned I can get past the GDM hang with a new account. I don't know why, though.

That's why I need to hit ctrl+alt+1 and create a new account.

In case of the lower run levels, I could either use sed. Otherwise, I could just manually edit the /etc/groups via nano.

---

