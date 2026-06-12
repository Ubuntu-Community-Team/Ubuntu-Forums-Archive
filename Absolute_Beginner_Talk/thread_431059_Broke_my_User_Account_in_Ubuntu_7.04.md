---
title: "Broke my User Account in Ubuntu 7.04"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by eyemann on 2007-05-02
I don't remember exactly what I changed in the Gnome UI, but I think I changed my User to either the Root Group or Root directory thinking it would change my user to administrator.

When I booted again after this change, I was not able to log into Ubuntu. I instead got this error:

[I]
User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.[/I]

After I click the okay button I got a second error that said this:

*Your Session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.*

Then there is this: ~/.xsession-errors file = 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/ :0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
Could not set mode 0700 on private per-user gnome configuration directory '/root/.gnome2_private/' : Operation not permitted

Can anyone tell me what my options are?  Is there a way to salvage my user account and log back into the Gnome Gui?  Or should I just wipe the system out and start fresh?

---

### Post by gazj on 2007-05-02
first of all at the login screen press ctrl+alt+f1, this will switch you to a console

You should hopefully be able to log in with your username and password

You should then receive a command prompt.

type the follwing command

```
sudo usermod -g GROUPNAME USERNAME
```

substitute GROUPNAME for the group you want as your primary group

substitute USERNAME for your own login username.

In Ubuntu the default setup is to have your primary group the same as your username.

For example to change my username of gary back to the primary group of gary i would do this.

```
sudo usermod -g gary gary
```

I hope this makes sense.

When all is done type exit to logout out of command console

then press ctrl+alt+f7 to return to graphical mode.

---

### Post by Zer0Nin3r on 2007-05-03
Had the same problems as *eyemann *and was able to log back in with the help of *gazj*, but had to modify it a little bit.
 
For my case I had changed the spelling of the home directory in the GUI and then performed a ctrl+alt+delete to do a restart. Then I ran into the aforementioned problem. I wasn't able to perform a ctrl+alt+F1 to pull up a console, so I just logged in with the fail safe terminal and performed the following:

```

sudo usermod -d /home/ordinance USERNAME

```

I was finding that if I didn't specify the */home/* before my intended directory, I was still running into login problems.  Within the GUI through the Users & Groups, I had changed the directory name to /home/ordnance (the correct spelling; the cause of all this) and now decided to just leave it alone and go back to my old directory.  I hope this helps some of you out there.  Cheers!

---

### Post by dondad on 2007-05-03
I had exactly this problem. Not sure, but think it might have been caused by using sudo rather than gksudo for a graphical application by mistake. What I did to fix it was to change the owner of the home directory and the .dmrc file to me from root, then set permissions to 644 with chmod. That fixed it.

---

