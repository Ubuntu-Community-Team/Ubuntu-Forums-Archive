---
title: "Changing shell"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by ubunewb on 2005-11-27
Hello,

I have a problems with changing my shell from bash (default) to csh.

Here's what I do.

```
bakirov@zimmer136:/$ cat etc/shells
# /etc/shells: valid login shells
/bin/ash
/bin/bash
**[COLOR="Red"]/bin/csh[/COLOR]**
/bin/sh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/zsh
/bin/sash
/bin/zsh
/usr/bin/esh
/bin/rbash
/bin/dash
/usr/bin/screen

bakirov@zimmer136:/$ sudo chsh -s /bin/csh bakirov
Password:
bakirov@zimmer136:/$

```

Well, seems to work.  Now let's test.
```
bakirov@zimmer136:/$ finger bakirov
Login: bakirov                          Name: Rashid Bakirov
Directory: /home/bakirov                Shell:**[COLOR="Red"] /bin/csh[/COLOR]**
On since Mon Nov 28 01:48 (CET) on :0 (messages off)
On since Mon Nov 28 01:49 (CET) on pts/0 from :0.0
   26 minutes 38 seconds idle
On since Mon Nov 28 01:52 (CET) on pts/1 from :0.0
New mail received Sun Nov 27 03:14 2005 (CET)
     Unread since Sun Nov 27 03:04 2005 (CET)
No Plan.
bakirov@zimmer136:/$

```

but the actual shell is still bash (I think).  Cause the $ sign at the prompt is the sign of bash, and also when I enter something like setenv (csh command) I get:
```
bakirov@zimmer136:/$ setenv
**[COLOR="Red"]bash[/COLOR]:** setenv: command not found

```

I rebooted but it was still the same.

Any ideas on what am I doing wrong?  Or is it the way it should be?

EDIT: I'm running Ubuntu 5.04

---

### Post by cwaldbieser on 2005-11-28
[QUOTE=ubunewb]Hello,

I have a problems with changing my shell from bash (default) to csh.

Here's what I do.

```
bakirov@zimmer136:/$ cat etc/shells
# /etc/shells: valid login shells
/bin/ash
/bin/bash
**[COLOR="Red"]/bin/csh[/COLOR]**
/bin/sh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/zsh
/bin/sash
/bin/zsh
/usr/bin/esh
/bin/rbash
/bin/dash
/usr/bin/screen

bakirov@zimmer136:/$ sudo chsh -s /bin/csh bakirov
Password:
bakirov@zimmer136:/$

```

Well, seems to work.  Now let's test.
```
bakirov@zimmer136:/$ finger bakirov
Login: bakirov                          Name: Rashid Bakirov
Directory: /home/bakirov                Shell:**[COLOR="Red"] /bin/csh[/COLOR]**
On since Mon Nov 28 01:48 (CET) on :0 (messages off)
On since Mon Nov 28 01:49 (CET) on pts/0 from :0.0
   26 minutes 38 seconds idle
On since Mon Nov 28 01:52 (CET) on pts/1 from :0.0
New mail received Sun Nov 27 03:14 2005 (CET)
     Unread since Sun Nov 27 03:04 2005 (CET)
No Plan.
bakirov@zimmer136:/$

```

but the actual shell is still bash (I think).  Cause the $ sign at the prompt is the sign of bash, and also when I enter something like setenv (csh command) I get:
```
bakirov@zimmer136:/$ setenv
**[COLOR="Red"]bash[/COLOR]:** setenv: command not found

```

I rebooted but it was still the same.

Any ideas on what am I doing wrong?  Or is it the way it should be?

EDIT: I'm running Ubuntu 5.04[/QUOTE]

Does it look like the shell was changed for your user in /etc/passwd?

---

### Post by ubunewb on 2005-11-28
yes, in etc/passwd it also says that my shell is /bin/csh

---

### Post by ubunewb on 2005-11-28
ummm... anyone?

---

### Post by cwaldbieser on 2005-11-28
[QUOTE=ubunewb]ummm... anyone?[/QUOTE]
It looks like you have done the correct thing.  Do you have the same trouble switching to other shells?  If you type "help" does it tell you you are still in bash?

Can you switch to a c-shell from the bash prompt, or do you get another bash shell?

---

### Post by wwuster on 2006-01-11
I also am trying to change my shel to tcsh.

I ran "sudo chsh -s /bin/tcsh myname"

It appeared to run and /etc/passwd lists tcsh as my shell, but if I start a new terminal I'm still running the bash shell.

So, how do you change shells?

William

---

### Post by wwuster on 2006-01-12
[QUOTE=wwuster]I also am trying to change my shel to tcsh.

I ran "sudo chsh -s /bin/tcsh myname"

It appeared to run and /etc/passwd lists tcsh as my shell, but if I start a new terminal I'm still running the bash shell.

So, how do you change shells?

William[/QUOTE]

I found that after I rebooted my shell has been changed correctly. But before you reboot the 'env' will say that your shell is still /bin/tcsh even though it is still /bin/bash. That was misleading (a bug?).

William

---

### Post by frodon on 2006-01-12
[QUOTE=wwuster]I also am trying to change my shel to tcsh.

I ran "sudo chsh -s /bin/tcsh myname"

It appeared to run and /etc/passwd lists tcsh as my shell, but if I start a new terminal I'm still running the bash shell.

So, how do you change shells?

William[/QUOTE]I also use tcsh and the only thing i did is to install tcsh, set this schell in the gnome-terminal option window, and set also tcsh in my user account thanks to the user & group window.

I love tcsh :D !!!!!

---

### Post by druvoid on 2006-04-25
I have followed the steps in this thread to change my shell.  In the GNOME Users & Groups window, /etc/passwd, the echo $SHELL command, and finger, my user shell is listed as tcsh.  After multiple reboots, though, I still have the bash prompt and the setenv error.  Does anyone know what might be wrong?

---

