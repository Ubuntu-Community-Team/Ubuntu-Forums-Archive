---
title: "sudo xhost problem"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by sdahlin on 2007-10-15
I am trying to enable the xwindow for a user using "sudo xhost +".  However, when I put in the password I am told that the password is not valid.  Why does sudo work for some commands but not this one (and a couple of others I have encountered)?

Thanks,
Steve

---

### Post by dwhitney67 on 2007-10-15
AFAIK, you don't need to precede the command with 'sudo'.

The user that is currently displaying a Window manager (e.g. gnome, kde, xfce, twm, etc.) is the one that owns the display.  Thus after the primary user enters an "xhost +", this will allow any secondary user on the same system to launch a GUI application.  Issuing an "xhost -" will take away that privilege.

Anyhow, don't forget that the secondary user must set the DISPLAY environment variable.  Something like this should work:

$ export DISPLAY=:0

To test, you can run a simple app:

$ xeyes

---

### Post by sdahlin on 2007-10-16
I could not get it to work.  Here is exactly what I did:

login as the default user and  enter:

def user >xhost +

tested with xclock which was fine. Log in as oracle using and setup the DISPLAY var:

def user> su - oracle
oracle > export DISPLAY=:0
oracle > xclock
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't op[en display: :0

Was there some other step to take?
Thanks,
Steve

---

### Post by dwhitney67 on 2007-10-16
Duh... ignore my post below.

Just run this when you are logged in as "oracle":

$ export DISPLAY=:0.0

--------------------------------------------------------

I don't know what to suggest.  It works on my Ubuntu system (I am running Feisty), on my Fedora systems, and I know it works on Solaris.

From the GDM login prompt, login as user A.  Then open a terminal.  Run the "xhost +" command.  Then "su - oracle" (enter the password if required).  Then "export DISPLAY=:0"; then run "xeyes".  If that doesn't work, then try again but this time "export DISPLAY=:0.0".

If this still does not work then something is weird with your system's configuration.  Verify the value of DISPLAY when you are logged in as user A; run "echo $DISPLAY".  Use the results as a clue when exporting the DISPLAY env-var when logged in as oracle.

---

### Post by sdahlin on 2007-10-17
I have tried the variants you suggested both to no affect.  I have done anything odd with this install.  In the past with other distros I would login as root, xhost +, su to the user, and export DISPLAY, and be on my way.  This is the first distro that I have had this kind of problem.

---

### Post by sdahlin on 2007-10-17
I found the problem.  The DISPLAY for the default user is set to :1.0.  How that happened I am not sure.  Anyway X will now work.  Thanks.

Steve

---

