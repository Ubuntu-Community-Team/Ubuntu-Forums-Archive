---
title: "Valid login/password not recognized"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by blacklr on 2008-01-17
I'm trying to login at the "Ubuntu" prompt, and though it seems like everything goes ok, I just get returned to the login prompt--no error message. Any ideas? 

I couldn't find a similar thread, but please forgive me if this has already been answered.

Thanks in advance.

---

### Post by pytheas22 on 2008-01-17
That's strange.  Can you log in as root (type "su" and give it the root password, if you know it)?

I assume that you tried rebooting.

And is this on a clean install or did the behavior just start suddenly?

---

### Post by pytheas22 on 2008-01-17
I'm sorry, I realized that you probably mean that you are at the graphical login prompt and can't log in...I was thinking that you were talking about the command prompt.

If you do indeed mean that you can't log in graphically, here are some things to try:

Can you change your session type to the "failsafe terminal" and log in to that?

Can you press control-alt-F1 and login there (enter your user name and then your password when prompted)?

Are you using KDE or Gnome?

And again, is this a fresh system install or did the problem just start popping up?

---

### Post by bodhi.zazen on 2008-01-17
> **pytheas22 said:**
> That's strange.  Can you log in as root (type "su" and give it the root password, if you know it)?

I assume that you tried rebooting.

And is this on a clean install or did the behavior just start suddenly?

Ubuntu does not allow root logins, it uses sudo rather then su,  and you can not type su at a log in prompt :twisted:

@blacklr : You will need to look at the logs to see if you have any errors or clues.

Try booting to recovery mode, this will log you in as root. Take a look at the filesystem, permissions of /home, and logs (/var/log).

---

### Post by pytheas22 on 2008-01-18
> Ubuntu does not allow root logins, it uses sudo rather then su, and you can not type su at a log in prompt

but...you can login on the command line as root if you know the root password, which you would have had to reset yourself manually because by default you wouldn't know the password.  Just type "root" as the login name.  But it's true that it won't let you log in graphically as root.

---

### Post by bodhi.zazen on 2008-01-18
Well, the root account is locked in Ubuntu

You can set a password as you say

And you can enable graphical root logins too

But that is not recommended nor is it the default behavior. So the is no reason to presume one can log in as root.

---

### Post by blacklr on 2008-01-18
Thanks for your responses. I'll try to answer your questions.

1. No, this is not a fresh install. It's a dual boot system with XP, and it's worked fine for a couple of months.

2. I can log in using failsafe mode as root, and I changed the password for my normal username. The same problem happened again, though.

3. Yes, I've tried to reboot.

4. I haven't tried to login as "su", but I will give that a try and let you know.

5. I'm using Gnome.

---

### Post by blacklr on 2008-01-18
Let me update the last post:

Earlier I was using recovery mode, not failsafe mode. I was confused.  I am now logged in to failsafe mode, and things seem to be working normally.

the permissions of /home and /var/log are both 755.  I'll try to use normal mode and see what happens.

Update: still no luck with normal login...

---

### Post by bodhi.zazen on 2008-01-18
Try creating a new user. Be sure to add the new user to the appropriate groups (admin for sudo access).

---

### Post by blacklr on 2008-01-18
Ok, I created a new user and tried to login normally, but the same thing occurred--screen goes all beige (default ubuntu color) and after a few seconds returns to the username prompt with no error message.

Should I check some configuration/startup files?

---

### Post by bodhi.zazen on 2008-01-18
Go to the console with Ctrl-Alt-F1 (or Ctrl-Alt-F2)

Log in.

Kill x (gdm)

```
sudo /etc/init.d/gdm stop
```

Now manually start X with 

```
X
```

You should get a grey screen with a black X that resonds to mouse movement.

Ctrl-Alt-Backspace to exit X

Now startx

```
startx
```

That should start gnome.

Post any error messages.

---

### Post by blacklr on 2008-01-18
Ok, so when I get to the screen with the black "X", I hit Ctrl-Alt-Backspace, and nothing happens. So I hit ctrl-alt-F1 and it takes me to a screen with several lines about things that are off or on, but there's no prompt at all and I can't leave that screen without rebooting (or at least I don't know how).

Also, when I use the command line, the font seems to be larger than normal and offset from the left side of the screen.  the command I type is actually off the bottom of the screen, so I have to type "clear" so that I can even see what I'm typing.  That seems a little off.

Thanks.

---

### Post by blacklr on 2008-01-18
Also, these problems started occurring soon after I tried to install qt/x11 files needed to run a network simulator.  Maybe something important was changed along the way?  If so, is there a way to revert to an previous state in Ubuntu? 

Just thought the full disclosure might help a bit.

---

### Post by asmiller-ke6seh on 2008-01-18
Log on in Failsafe mode, backup the /HOME directory, reinstall Ubuntu, restore the /HOME directory, and have a good day.:guitar:

---

### Post by blacklr on 2008-01-18
Not exactly the solution i was looking for, but it might just come to that...:(

---

