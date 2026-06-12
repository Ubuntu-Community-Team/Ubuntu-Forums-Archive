---
title: "[xubuntu] admin tools without gksu?!"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by quirks on 2007-02-02
Hey folks!

I'm not new to Linux, but to Ubuntu. More precisely, I'm using Xubuntu (if that matters). I'm not very familiar with sudo, since I'm used to use the root account for administrative tasks. However, I have noticed that I am able to run admin tools such as users-admin or network-admin without being prompted for my password. This is even the case after a fresh reboot and although I have set timestamp_timeout to 0 in the /etc/sudoers file. Is this normal? Or have I messed up something? This is a big security issue, because I can reset the root password, for example, without the need to enter my password.

quirks

---

### Post by kebes on 2007-02-02
It might be that you are able to open the admin tools, but not actually make changes. If you try a make a change and save it, does it then ask for a password? (Your user account probably has read access on those admin files, but not write access without calling sudo.)

What about on the commandline? When you try and run a command with "sudo" does it ask for the password there?


If it doesn't ever ask for a password, then that's definately a problem, and not normal behavior.

---

### Post by psycosmyth on 2007-02-02
I have the same scenario but only if I run a KDE admin application in Xfce.

---

### Post by quirks on 2007-02-02
I CAN make changes (unfortunately). I can even reset the root password as mentioned above! When I try to run sudo from the command line, it does prompt me for the password, however.

quirks

---

### Post by Maestro23 on 2007-02-02
Might help.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by quirks on 2007-02-02
No, sorry. I already knew everything what's written there. (Apart from the hint that you should never run graphical programs with sudo, which I cannot guarantee that I have never done that. Nevertheless, I have no problems when logging in and removing .Xauthority and .ICEauthority didn't resolve the issue.)

Thanks anyways.
quirks

---

### Post by quirks on 2007-02-02
Ok, I finally found the "solution". Actually it is not a solution but rather a workaround. Here is what I did:

1. I created another test account without admin rights (i.e. the user is not part of the admin group).
2. I logged on with this user and I was unable to perform administrative tasks without entering my password - as expected.
3. I created yet another test user to see what would happen, if the user was initially member of the admin group.
4. I logged on with this user and I could perform administrative tasks WITHOUT ENTERING MY PASSWORD EVEN ONCE.
5. I deleted the test users.
6. I deleted my normal user, because I thought recreating this user and not adding him to the admin group right from the beginning would solve my problem.
7. But the moment I logged on with this user, it was AUTOMATICALLY added to the admin group and I could use whatever admin tool I wanted WITHOUT ENTERING MY PASSWORD!
8. I tried a lot of things with user IDs and config files in this user's home directory and finally came to the conlusion that the behaviour stated in step 7 only occurs, when I name the user exaclty as I did during installation of Xubuntu.
9. Therefore, I created a different user and that did it. Now I have got a different name, but therefore, I have to enter my password when I start an admin tool or the tool will fail.

My question: Where does this weird behaviour come from? Have I misconfigured anything? Is it a bug? IS THIS EVEN INTENDED?! (Especially step 7 is completely unexplicable to me.)

After all, you probably understand that I'm pissed now (sorry for that, but I am) and I dare say Ubuntu has lost a follower this night. And that's sad, because I liked it.

quirks

---

### Post by quirks on 2007-02-03
Amazingly, this also solved to other things that didn't work properly before:

1. Now I can hibernate my machine as often as I want (and not only once and after the next reboot, it simply does nothing, when clicking the hibernate button in the logout window).
2. My screen gets locked, when I hibernate, which it didn't before (it always complained that it can't open the display).

quirks

---

