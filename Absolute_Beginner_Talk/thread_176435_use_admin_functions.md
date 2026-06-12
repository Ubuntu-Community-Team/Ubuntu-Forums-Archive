---
title: "use admin functions"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by vjconnor on 2006-05-14
I am unable to use the admin functions from the ubuntu desktop because 
my root password is not recognized.

I am able to log-in as root (su root) in a terminal or console window where my 
root password works just fine. Has anyone experienced this? Does anyone have a fix?

2) is it possible to  log into the ubuntu desktop as root ?

---

### Post by cgjones on 2006-05-14
Try using your user's password for the graphical admin tools. These are launched by sudo (or the graphical equivalent) and require the user's password, not roots.

Click [here](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo) for more information on sudo and how to enable root login at the login screen. (Although this is not recommended.)

---

### Post by cgjones on 2006-05-14
Edit: Double post

---

### Post by nalmeth on 2006-05-14
multiple posts all over the place...
you might be confused here, don't log in as root. When you are asked for your password, use your userpassword. Ubuntu is set up with sudo to not require a root account.
Sudo will give your users admin priviledges

---

### Post by twiistedkaos on 2006-05-14
As they all said, Ubuntu has no root, it's completely dependant on sudo, simply thing of it like this, my username(not really) is Bob, and my password is omfg. When ever I get prompted for "root" access or anything that requires a password I simply type in my good old password "omfg" and walla, application works like a charm. I too was confused about this when I first installed ubuntu last night, I was so use to needing root to do everything! Oh, for console simply do this when every you need to use "root" access:

```

sudo <application name>
....Password: ****

``` 
:P

---

