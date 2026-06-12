---
title: "Run command in Ubuntu"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by dpilli on 2006-05-16
Hi, I hope I'm allowed in the beginners forum.  I have a brand new ubuntu install which I am enjoying but I do know a few linux commands.  Frankly I think this makes me more dangerous.

I have been trying to install a program and I have managed to get most thing done, but now it says to type as root

   *run /opt/(my_application)/bin/ask_license.sh*

All I keep getting is

     -bash: run: command not found

So... does bash have a run command or do I use something else?

Thank you

---

### Post by DJ Scribblinni on 2006-05-16
What program are you trying to install?

---

### Post by Jagot on 2006-05-16
Methinks it would be:

```
chmod +x  /opt/(my_application)/bin/ask_license.sh
cd /opt/(my_application)/bin
./ask_license.sh
```

---

### Post by nalmeth on 2006-05-16
Instead of using root, or creating a root account (which doesn't yet exist) use sudo in front of whatever you might be doing that required admin priviledges

example:
sudo apt-get update

---

### Post by aysiu on 2006-05-16
Try ```
cd /opt/(my_application)/bin/
sudo ./ask_license.sh
```

**Edit**: Jagot beat me to it, and included the *chmod +x*, which I forgot.

---

### Post by az on 2006-05-16
I find it creepy that you have to be root to ask for a licence for this to work.

You would need to make the file executable before executing it.

---

### Post by dpilli on 2006-05-16
The program I am trying to install is win4lin.  I am curious about installing another OS onto this one.

I ran the command 

   *chmod +x  /opt/win4lin/bin/ask_license.sh*

I think that worked fine.  The permissions now are 555

I then changed to the correct directory and typed the following.

   *cd /opt/(my_application)/bin*
   *./ask_license.sh*

I seem to have a different problem now

*Error: Missing file /etc/default/merge.*

Just to make sure, there is no actual run command?

Thanks for the help.

---

### Post by Jagot on 2006-05-16
There is no run command - just the name of the file.

Not sure about the other problem, though I've found this brief link about it - its based on RedHat, but what is suggested may work for you:

[http://support.win4lin.com/cgi-bin/perldesk/kb.cgi?view=95&lang=en](http://support.win4lin.com/cgi-bin/perldesk/kb.cgi?view=95&lang=en)

---

