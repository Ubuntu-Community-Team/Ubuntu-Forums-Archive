---
title: "weird terminal changes"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by joe.astro on 2007-02-03
I somehow managed to change some settings related to my terminal display without realizing it.  Before the change, my terminal prompt looked like this:

joe@Ganges%

and doing an "ls" caused the listed items to appear color-coded.  Now my prompt looks like:

_Ganges_:~>

and I have lost my color-coding.  Additionaly, I had a keyboard shortcut set up to open a new terminal.  Before, I could open unlimited windows with the shortcut.  Now it will only open a single window after logon and refuse to work thereafter.  Anybody out there know how I can undo whatever it is that I did (I'm sure its simple, but I have no idea where to start)?
 
Thanks,
Joe

---

### Post by shareMenaPeace on 2007-02-03
Don't know how to set this default terminal settings but colored is per default i think.

Where did you think you changed settings?
Or what have could done this?

---

### Post by joe.astro on 2007-02-04
I think it happened when I was installing some software called IRAF.  I followed the instructions I found [here]("http://mjhutchinson.com/journal/2006-11-05/install_iraf_on_ubuntu_edgy_amd64").  Unfortunately, I don't know at what stage of the install things got changed.  This trio of commands looks like a likely suspect, though.

setenv iraf /iraf/iraf/
cd $iraf/unix/hlib
source irafuser.csh

The "setenv" command is something I have not seen before, and is apparently specific to tcsh.  Looks like I have some reading to do...

Joe

---

### Post by taurus on 2007-02-04
IRAF is an astronomy image processing.  It, the environment, runs under csh shell so you probably just change your shell for that session.  Have you logged out and back in again?

---

### Post by joe.astro on 2007-02-04
OK, I fixed it.  All it took was changing my shell from tcsh to bash, restarting X, and logging back in.  My keyboard shortcut still isn't working properly, but at this point I am willing to just call it a micro-inconveinience and move on.  

Thanks again,
Joe

---

