---
title: "[SOLVED] Logging in as Root ?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-05
For some reason Ubuntu won't let me log into the Gui with Root.
It will only allow me to log in as a normal user.....
Is this normal ?

I'd like to be able to do this, is there a way?

Thank you.

Orbital

---

### Post by wolfen69 on 2007-08-05
open terminal after boot up and:
```
sudo -s -H
```
then you are root

---

### Post by lgambett on 2007-08-05
For safety reasons the root account is disabled in Ubuntu. Every time you need to execute a command with root privileges you can use sudo, e.g. sudo apt-get update.
Should you ever need a root account you have to create it from scratch.

---

### Post by irish_flu on 2007-08-05
The root account is disabled.  If you want to be able to login with it, I believe all you have to do is set a password 

```

sudo passwd root

```

---

### Post by Madpilot on 2007-08-05
> **Orbital75 said:**
> For some reason Ubuntu won't let me log into the Gui with Root.
It will only allow me to log in as a normal user.....
Is this normal ?


It's both normal and deliberate. There's no real need for an active root account in Ubuntu, and absolutely no need to log into the GUI as root.

Please have a look through [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for the reasoning behind this, how to work with Ubuntu's security/user model, and (if you still want to, for some reason) how to do things differently.

---

### Post by aysiu on 2007-08-05
There's no need to log in as root in the GUI.

You can make GUI changes faster and more securely a different way. Read more here:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by Orbital75 on 2007-08-05
Thanks everyone for the advice..... 

Yeah, I don't plan as always running as a Root User, I just wanted to log into
it now and again to make changes.  I'm a new Linux user and am not familiar
with the command line yet.  Even in Windows, I run myself as a Limited User
just to be a little safer.

Currently I am running Ubuntu in VirtualBox on XP Pro.
When I installed the Guest Additions, I had to have root
access so I had to go to the command line and type

su root
Password

That worked.

Oh, by the way. In The GUI I went to 
Administration
Users and Groups
and changed the Root Password but for some reason, 
it's still the same as my normal log on.....
Why is this.....

---

### Post by jacob01 on 2007-08-05
what about                      fakeroot                  i can log into that

---

### Post by Nekiruhs on 2007-08-05
> **Orbital75 said:**
> Thanks everyone for the advice..... 

Yeah, I don't plan as always running as a Root User, I just wanted to log into
it now and again to make changes.  I'm a new Linux user and am not familiar
with the command line yet.  Even in Windows, I run myself as a Limited User
just to be a little safer.

Currently I am running Ubuntu in VirtualBox on XP Pro.
When I installed the Guest Additions, I had to have root
access so I had to go to the command line and type

su root
Password

That worked.

Oh, by the way. In The GUI I went to 
Administration
Users and Groups
and changed the Root Password but for some reason, 
it's still the same as my normal log on.....
Why is this.....
Ubuntu disables logging in as Root deliberately. Its unsafe to do so. Just use sudo when you need to do things. If you need root nautilus (file manager) just press Alt + F2 and type gksudo nautilus

---

### Post by aysiu on 2007-08-05
If that's the reason, you needn't have set a root password or taken yourself out of the *sudo* group.

*sudo* allows you to operate as regular user almost all the time. Authenticating (yes, with a password) with *sudo* allows you to temporarily escalate privilege for **one** task within an otherwise limited account session.

*gksudo nautilus* allows you a graphical "browse as root" file manager within the limited account session, and *sudo -i* would temporarily allow you to basically be root.

---

### Post by Orbital75 on 2007-08-06
I tried Alt + F2 and type gksudo nautilus and it worked great.
I was trying to add a WinAmp skin to the usr/share/XMMS folder
but it keep telling me I didn't have permission.

Now, how secure is this gksudo nautilus?
It didn't even ask me for a password.
Does this mean anyone can do it without
a password?

---

### Post by aysiu on 2007-08-06
It *should* prompt you for a password, unless you're using the live CD **or** you've done some other *gksudo* action within the last fifteen minutes.

---

### Post by SBG on 2007-08-08
> **Madpilot said:**
> It's both normal and deliberate. There's no real need for an active root account in Ubuntu, and absolutely no need to log into the GUI as root.
.

I have a real need for root to be allowed to log in interactively: it's the only account I have the creds for.  Not being a *nix guy (I'm a Windows admin--or should i say "Wind0ze" when posting here? :)

I'll poke around at the command line and see if i can dredge my brain for the method for doing it that way.


SBG

---

### Post by aysiu on 2007-08-08
> **SBG said:**
> I have a real need for root to be allowed to log in interactively: it's the only account I have the creds for.  Not being a *nix guy (I'm a Windows admin--or should i say "Wind0ze" when posting here? :)

I'll poke around at the command line and see if i can dredge my brain for the method for doing it that way.


SBG
I don't know what you mean by "the creds for." What are you trying to do that you think you need a root login for?

---

### Post by anewguy on 2007-08-08
Yes, there is a 2-step process to enable root login.  Is it needed?  No.  As mentioned in the replies on this thread, sudo access along with gksudo access to the file manager is all you should ever need.  I will not post the process to enable root login as it really is too dangerous for the new or casual user.  If you really want it anyway, and are aware that you can REALLY mess up your system with it, then send me a private message.  If you can convince me why you need the access, then I will send you a reply telling you how.  Use at your own and considerable risk.

---

