---
title: "Why doesn't changing my .bash_profile work?"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by Van_Gogh on 2005-11-12
Hi,

I'm trying to add a location to my PATH and am under the assumption that this is done by altering the .bash_profile. Is this correct?

Anyways, I added the following code bit to the .bash_profile:

```


if [ -d /opt/intel/fc/9.0/bin ]; then
    source /opt/intel/fc/9.0/bin/ifortvars.sh
fi

if [ -d /opt/intel/idb/9.0/bin ]; then
    source /opt/intel/idb/9.0/bin/idbvars.sh
fi

```

My problem is that it doesn't seem to get automatically added to the PATH: I have to do an "source .bash_profile" every time I fire the shell up to get it to work.

Anyone know how to add to the PATH, so the added location is permanently added?

Regards

---

### Post by Manny C on 2005-11-12
I have always had the same issue. Any takers?

---

### Post by Joe_lurker on 2005-11-12
Put the code in the .bashrc file instead.

-Joe

---

### Post by stilus on 2005-11-12
The .bashrc is used for "non-login shells", which means shells that you for instance open with the "terminal" once you logged in. Logging in to your window manager is simply something else, which is why all the tweaking to .profile/ .bashrc/ .bash_profile and even /etc/profile is not gonna work.

Now, as for adding directories to your PATH *),  thats a whole different ballgame. I am guessing you use the default GNOME window manager. When it starts up, it uses **/etc/X11/Xsession.d/55gnome-session_gnomerc** in which is a simple piece of code that checks for and if available executes **$HOME/.gnomerc**. So if you want to add something to your path, just create a **.gnomerc** in your home directory and add something like: **PATH="$PATH:/your/own/bin"**

You can put a variety of other settings in .bashrc though, one of which is **alias**. I use it often. Do you always have to type **"ssh -p 33333 mynick@192.168.0.33"** to ssh to your secure shell server? Put alias **sshserver='ssh -p 33333 mynick@192.168.0.33'** in the .bashrc. Next time you open a terminal, typing "**sshserver**" will get you to the password prompt of 192.168.0.33. If you want to imediatly use your new .bashrc in your terminal, just run **. .bashrc** (notice the dot!).

Have fun!
*) You can see what your current PATH and other settings are by running **set**

---

### Post by Van_Gogh on 2005-11-12
That doesn't seem to work:( I have to source .gnomerc too to get it to work.

I tried looking at the 55gnome-session_gnomerc file and it seems to depend on  the command "basename $STARTUP" to return "gnome-session".However it return nothing in my case. I don't know if this is important and what to do about it...

Any ideas?

---

### Post by janwijbrand on 2005-11-12
[QUOTE=Van_Gogh]Hi,

I'm trying to add a location to my PATH and am under the assumption that this is done by altering the .bash_profile. Is this correct?
<snip>
My problem is that it doesn't seem to get automatically added to the PATH: I have to do an "source .bash_profile" every time I fire the shell up to get it to work.
[/QUOTE]

Jup, familiar problem. Although Stilus is correct about the use of .bashrc I do put some customizations in there even if there're only for interactive use.

Another trick for the gnome-terminal I found, that will make sure the .bash_profile is read when launching a new shell, is to enable the 'Run command  as a login shell' option in the 'Title and command' tab of the  profile editor  ('Edit' --> 'Current profile...').

good luck!

---

### Post by setterm on 2006-02-20
janwijbrand,

thanks for the pointer on the gnome-terminal setting for running the login as a login shell. It works brilliantly. If anyone needs any further information about this, consult: [http://www.network-theory.co.uk/docs/bashref/bashref_56.html](http://www.network-theory.co.uk/docs/bashref/bashref_56.html)

Matt S.

---

