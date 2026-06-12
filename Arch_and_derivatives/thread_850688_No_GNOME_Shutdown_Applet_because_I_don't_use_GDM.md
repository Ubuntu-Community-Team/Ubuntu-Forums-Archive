---
title: "No GNOME Shutdown Applet because I don't use GDM?"
date: 2008-07-05
forum: Arch and derivatives
---

### Post by YodaMstr on 2008-07-05
I read a thread on the Arch forum that gives this explanation for why I have no shutdown applet.  It seems odd to have it tied to GDM like that.  Is there any way around this, or any explanation?  I'd really like to just have a button to press, rather than:
```

su
shutdown -h now
```

Any help or ideas?  It'd be appreciated.

---

### Post by fwojciec on 2008-07-06
That's how gnome is designed to work.  If you start gnome-session using startx command it is running with user-level privileges only, which means it has no privileges to shut down the machine (so, for example, you have to become root in order to be able to issue the "shutdown" command when you do it from the terminal).  Login manager runs with root (or daemon, not sure) privileges, so Gnome normally shuts down the computer by passing the request on to the login manager.

There are workarounds to this, but (AFAIK) none of them are actually going to somehow unlock the shutdown applet.  You could, for example, write a script that shuts the computer down and assign it to a launcher -- with an icon, and perhaps even a confirmation dialog using zenity, or something like that -- but if you want a clean and elegant solution just install a login manager.

---

### Post by hoooootz82 on 2008-07-06
You could always make a script to shutdown and then a link to it. I have a useful script (however poorly written) thatll shutdown or restart the computer, then i put a launcher on a panel. Here's the script:
```
#!/bin/bash
echo "Ctrl + C = Cancel"
sudo -v
read -p "Do what? Restart=\"r\", shutdown=\"P\":"
parameter="$REPLY"
case $parameter in
	"p") parameter="P"
	action="shutdown";;
	"R") parameter="r"
	action="restart";;
	"C") parameter="c";;
	"K") parameter="k";;
	"h") action="halt or power off";;
	"H") action="halt";;
	"P") action="shutdown";;
	"r") action="restart";;
	*) echo "That is not a valid argument, closing script...";;
esac
echo "put 'now' if you wish to do action immediately."
echo "How many minutes till $action?"
read -p "Minutes:"
gnome-screensaver-command --activate
sudo shutdown -$parameter $REPLY
```

Then you can link to a built in icon or get your own.

---

### Post by YodaMstr on 2008-07-06
Thanks, both of you.  I'll see about writing a small script and linking it.  I just figured there might be a more built-in solution.  Again, thanks.

---

### Post by Barrucadu on 2008-07-06
You could just install GDM, KDM, XDM, or SLiM. Then just edit your /etc/inittab file, the comments are fairly explanatory.

---

