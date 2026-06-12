---
title: "dmrc Begin Ignored"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by IdioticCreation on 2007-06-02
OK, So I was trying to install xlibmesa package, but it keept telling be I didn't have root access.  Now I know that you are supposed to sudo the commands, but anyway.  I opened the users dialog under system > adminastraton (I think, cant tell now) and I changed my user setting from "home/user/" to "/root" because I'm dumb like that.  OK, so then I logged out and when I try to log back in I get the error:
``User's $HOME/.dmrc file is being ignored.  This prevents..." yeah yeah.  Is there a way to undo the damage from the failsafe terminal, or am I going to have to recover.

Thanks!

---

### Post by taurus on 2007-06-02
You just need to change the ownership of .dmrc from root back to your login name.  Assuming your login name is **john** (replace **john** with the your actual login name, okay), do (from recovery mode)

```
chown -R** john**:**john** /home/**john**
chmod 644 /home/**john**/.dmrc
```
Reboot and see if you still get that error message about $HOME/.dmrc when you log in.

```
shutdown -r now
```

---

### Post by IdioticCreation on 2007-06-02
Darn, didn't work.  Here is the specific error:

stdin: is not a tty
Could not set mode 0700 on private per-user gnome configuration directory `/root/.gnome2_private/': Operation not permitted

No idea what that means, but maybe you do?

---

### Post by IdioticCreation on 2007-06-02
Didn't see anything about not bumping, plus the issue is still unresolved.

---

### Post by taurus on 2007-06-02
Can you post the output of this command from a prompt?

```
ls -la /home
```

---

### Post by IdioticCreation on 2007-06-02
Yes:
```

total 0
?----------- ? ? ? ?                      ? home/.
?----------- ? ? ? ?                      ? home/..
?----------- ? ? ? ?                      ? home/david

```
Formatting may not be exact, I'm on a different computer so I can't copy and pase.

---

### Post by IdioticCreation on 2007-06-02
OK, so I researched the problem some, and none of the solutions I found seem to be working.

Very Annoyed,
David

---

### Post by lambros on 2007-06-02
Looks like you've modified your user's HOME setting.  To undo the damage, you could try a command such as
```
sudo usermod -d /home/username username
```
Change both occurrences of "username" with the actual logon of the account that is broken.
(You don't need the "sudo" if you've booted into a recovery shell)
I think that should fix it, please let us know if that helped.

Lambros

---

### Post by IdioticCreation on 2007-06-02
Didn't work, actually made another error.  Did that commnd delete my /home/user directory?

When I log in now, I first get the error: directory listed as /home/david, but that directory does not exist.  Then I get the ignorred .dmrc error.

*cries*

---

### Post by lambros on 2007-06-02
I'm sure the "usermod..." command I posted would not delete your /home/david directory (at least, it didn't when I tried it out on a "test" user).  The purpose of that command was to correct the $HOME setting that I thought you might have changed from the "Users and Groups" applet.  Something else must have deleted that folder (or maybe some permissions have got messed up).

Are you able to log on as any user at all?  If not, you could perhaps create a new user account, using a command such as
```
adduser david2
```
from a recovery shell.
That would at least allow you to logon with a graphical interface (although the settings would all be defaults).
Would be interesting to know what folders and permissions exist in your /home folder.  If you can, please post the output of
```
sudo ls -la /home
```

Lambros

---

### Post by IdioticCreation on 2007-06-02
Ok I tried to adduser, and I was denyed with and without sudo.  Here are the result from ls (drasticly different from the first time I did it.)
```

total 12
drwx--------------- 3 root      root    <time stamp> .
drwxr-------------- 21 root     root    <time stamp> ..
drwx--------------- 35 david    david  <time stamp> david

```

So, what does this mean?

---

### Post by IdioticCreation on 2007-06-02
OK, so I guess there is no way to fix it?  I really need my computer back =P

---

### Post by lambros on 2007-06-03
> **IdioticCreation said:**
> Ok I tried to adduser, and I was denyed with and without sudo.  Here are the result from ls (drasticly different from the first time I did it.)
```

total 12
drwx--------------- 3 root      root    <time stamp> .
drwxr-------------- 21 root     root    <time stamp> ..
drwx--------------- 35 david    david  <time stamp> david

```

So, what does this mean?

Sorry for the long delay, gotta sleep :-)
It looks to me like your permissions have got messed up somehow.  Those permissions are much more locked-down than on my machine.  Is there anything you might have done to cause your permissions to end up that way?  You said you did some research but nothing worked - I'm worried that some of your attempted fixes might have made things worse.  Depending on what you've done, the most economical repair might be a complete reinstall of Ubuntu - or it might be perfectly fixable with just a couple of chmod or chown commands.

How are you running all these commands?  Are you booting up into recovery mode?  Or perhaps you saw a prompt that said "login:" and you entered a username/password and it gave you some error-messages then a normal command-prompt?  Does your command-prompt end with '#' or with '$' ?

To start fixing this, I would suggest adding world read/execute permissions to your / and your /home folder.  Your /home/david folder looks OK to me - I guess the reason it was reported missing is a lack of permissions on the parent /home folder.  Also, your /home folder might need "staff" group permissions - I'm not sure about this but it shouldn't do any harm to try it anyway.

Boot into recovery-mode (let us know if you need instructions) and make sure you have a command-prompt that ends with '#' so you have full root privileges.  Then enter these commands:
```

chmod go+rx /
chmod go+rx /home
chown root:staff /home
reboot

```
That last command will reboot your PC - see if that gets you any further.  If you still can't log in, try that "adduser" command again - but run it from a recovery-boot, with the '#' at the end of your command-prompt.

Lambros

---

