---
title: "Setting environment variables at boot"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by tomane on 2006-09-30
Hello everyone,

This one is tickling my head quite a bit right now.
I need to set some environment variables but I couldn't find a suitable place to place their definitions.
Aparently, /etc/rc.local doesn't do the trick because it seems that variables can only be "export"ed to child processes, not to parents.

I took a look at /etc/bash.bashrc but it seems that it is only run when someone logs in. I want those variables set right after boot, i.e., no login required at all to fire up those variables.

Here's what I tried:

1) add {export FOO="bar"} to /etc/rc.local
After a reboot, the variables weren't set :(

2) add this code to the end of /etc/bash.bashrc
if [ $FOO ]; then
   echo "I have FOO!"
else
 print "FOO is missing!"
 export FOO="bar"
fi

This doesn't seem to to the trick as well because the message about the missing variable shows up in each login.

Any ideas?
Any help would be much appreciated :)
Thanks in Advance.

Cheers
--to

---

### Post by henriquemaia on 2006-10-01
Add what you need to:

/etc/profile

That should do the trick.

Boa sorte ;)

---

### Post by tomane on 2006-10-01
Nem por isso :(

Using /etc/profile yelds the same result as using /etc/bash.bashrc. If bash.bashrc exists it is executed at login, called from within /etc/profile.

Anyway, I need these variables to use the perl remote debugger with Activestate Komodo. I took a second read in the docs of komodo remote debugger and came to the conclusion that I actually don't need to have these variables set *after bootup* but *without someone logging in*. To use the remote debugger in a CGI environment I set the variables in the apache configuration using the SetEnv directive. On the other hand, If I want to remotely debug a plain perl program I need to be logged in (duh :) ) therefore /etc/profile easily solves this.

Nevertheless I'm still curious to know how can one set some environment variable without requiring the login scripts to be run. I'm sure that this might be usefull in some cases...

Cheers.
--to

---

