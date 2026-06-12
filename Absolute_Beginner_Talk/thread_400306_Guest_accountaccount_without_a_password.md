---
title: "Guest account/account without a password"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Murxidon on 2007-04-03
Hi, I just installed the latest Ubuntu version, and would like to know how I can create a user account that doesn't require a password?

I currently have my account, which I want to keep seperate from everyone else that uses the computer (the account is password protected), I would like everyone else on the computer to use one separate account.

Is this possible? When I add a new user it states that I have to use a password.. And I don't want to have to use autologon.

Thanks.

---

### Post by Origin415 on 2007-04-03
Create the account normally with a password, then open a terminal and type

sudo passwd -d [account's name]

The -d option will make the account passwordless

---

### Post by Murxidon on 2007-04-03
Thanks, I tried that and it says "Password Changed".. But when I try to log into the account, it still requires a password. And the password I originally set for it has changed.

Any ideas...?

---

### Post by Murxidon on 2007-04-03
I apologise for the "bump",,, But I really am stumped. :smile:

---

### Post by kittyhawk63 on 2007-04-03
When you tried Origin415's advice, did you just log out or did you restart your computer? Try restarting and see what happens. I have my username and password bypassed on a fresh startup, but I notice, when I just log out, I have to use username and password to get back in.
kh

---

### Post by Murxidon on 2007-04-03
I have just tried that thanks, but no luck unfortunately.

I type "guest" at the logon screen (the name of my account), but it still asks for a password.

---

### Post by Murxidon on 2007-04-03
Ok, this isn't good...

I just added my admin account to the "Users" group to see if it would make a difference, but now I'm just locked myself out of nearly everything. And I didn't change the default root password which I don't know...

I'm dead, help??

---

### Post by Murxidon on 2007-04-04
Ok, so I've re-installed Ubuntu now... Because I'm quite dim.

Any more ideas on this user account thing?

---

### Post by Skrynesaver on 2007-04-04
The original advice was correct. more explicitly:
```

sudo useradd  -m -c "Guest user" -d /home/guest  -s /bin/bash guest
sudo passwd guest

```
enter a password twice, now 
```

passwd -d guest

```

go to a terminal to test, ALT-F2
username: guest
You are logged in?

---

### Post by Murxidon on 2007-04-04
Thanks for the reply, I tried everything but it still requires a password at the logon screen... I must be doing something wrong.. But I tried everything you said..

Sorry for my continious annoyance.

---

### Post by xopher on 2007-04-04
Why just not make the user guest a password 'guest' ?

Easy to remember, but a total stranger might not gain access to your computer, and your files as fast..

Anyway, you might want to set up a kiosk account, so your files are protected, and the 'guest' has minimal access.

---

### Post by Murxidon on 2007-04-04
I would, but the other people that will be using the PC are about six years of age... They're used to a Windows PC, where they could just click the "guest" account icon at the logon screen and log back on.

---

### Post by Titus A Duxass on 2007-04-04
If you are on a gnome system, edit /etc/GDM/gdm.conf with your preferred app.
Not far down the file is the line "EnableAutoLogon = False" change false to true and repeat for the next line down.

Then your guest will be automatically logged in.

---

### Post by Murxidon on 2007-04-04
Thanks, I can allow the account to be automatically logged in, but then I would have to log out whenever I want to use the PC (which is most of the time...).

---

### Post by Murxidon on 2007-04-04
Heh, it seems like I won't be able to get my own way with the logon process then.

It looks like they will have to use my account, is there any way I can password protect files, folders and software from the little minions that will be using my machine...?

Thanks :P

---

### Post by Titus A Duxass on 2007-04-04
You would not necessarily need to log out, just open another session.

You can lock files by changing permissions, do a search on permissions.

---

### Post by Murxidon on 2007-04-04
Ok, thanks for all the replies.

I've decided to just do an automatic logon with the guest account, it seems sensible. And I will use the permissions to stop them from accessing my folders.

Thanks alot guys, you've been a real help.

---

### Post by freebird54 on 2007-04-04
You could autologin the guest account, and use **xnest** to 'promote' yourself when you wish to use the machine.  they'll never get into that! (for a year or two anyway - and the password should stop them a while after that!)  One fo the advantages is that you can log in and fix something - or work on something - and when you logout whatever they were doing will still be there - still running....

Well - I thought it would help!  :D


EDIT:  I was just flipping through Synaptic, and it tells me that Xephyr is the recommended choice - so try with xserver-xephyr instead.  Apparently it allows more 'specialized' capabilities in the separate logins - maybe even Beryl?
 BTW - these work by starting another whole xserver instance - and presenting it in a window on the desktop.  Fonts etc are controlled from the source xserver - so your configuration can be totally different than the kids.  You could run XFCE for them - Gnome for you - KDE for the wife....

---

