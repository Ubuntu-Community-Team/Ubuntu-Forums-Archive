---
title: "Kubuntu says I do not have permission to run xorg"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2008-04-03
This is so strange my computer worked perfect last night.I went to login and it would not ran a fail safe login and it said something about me not having permission to run xorg.I went into console and loged into root and made another username and I am on it now and it works.How would I give my old account to run xorg I guess thats the problem I no xorg is not broke cause I am on the same computer just as a different username.

---

### Post by privaterolf on 2008-04-03
Hm.....I'm running Ubuntu, so I'm not used to KDE.

Terminal should be the same though.

```
sudo xorg
```

Does that pull up anything?

---

### Post by jonward690 on 2008-04-03
Command not found,this is what it says when i try to run xorg in my username

jon@jon-desktop:~$ startx
xauth:  creating new authority file /home/jon/.serverauth.25482

X: user not authorized to run the X server, aborting.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console

---

### Post by privaterolf on 2008-04-03
> **jonward690 said:**
> Command not found,this is what it says when i try to run xorg in my username

jon@jon-desktop:~$ startx
xauth:  creating new authority file /home/jon/.serverauth.25482

X: user not authorized to run the X server, aborting.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console

Put sudo in front of startx

---

### Post by jonward690 on 2008-04-03
How can I run it when i have no way to get to a plane console,I donno why but when you hit control alt F1 the screen goes black the consoles there have never worked.Is there some sort of xorg file i can edit to add me back to it or something?

---

### Post by privaterolf on 2008-04-03
You can't get to it like this?

[http://ubuntuforums.org/attachment.php?attachmentid=25322&d=1171520023](http://ubuntuforums.org/attachment.php?attachmentid=25322&d=1171520023)

If not, can you screenshot your desktop?

---

### Post by jonward690 on 2008-04-03
yea but i am in a different user account so I am already running x so all sudo startx would do for me is nothing.This is all it is going to say.

jon1@jon-desktop:~$ sudo startx
[sudo] password for jon1:
xauth:  creating new authority file /home/jon1/.serverauth.13884


Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

---

### Post by privaterolf on 2008-04-03
> **jonward690 said:**
> yea but i am in a different user account so I am already running x so all sudo startx would do for me is nothing.This is all it is going to say.

jon1@jon-desktop:~$ sudo startx
[sudo] password for jon1:
xauth:  creating new authority file /home/jon1/.serverauth.13884


Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Control-Alt-Backspace            ?

Post back if that does nothing.

PS You will log out, then in.

---

### Post by jonward690 on 2008-04-03
Nope does nothing I can do a gui login in my new account my root account but now my main account.

---

### Post by privaterolf on 2008-04-03
I'm not a huge fan of KDE, so bear with me for a moment...

Did you try adding your main account to the 'root' and 'admin' groups in User Manager?

In the System part of the start menu

---

