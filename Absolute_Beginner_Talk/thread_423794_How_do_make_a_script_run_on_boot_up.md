---
title: "How do make a script run on boot up?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by DrQuincy on 2007-04-26
I have a bash script (only one line) - how do I make it run as a service, i.e. so it is running before I log in?  Thanks.

---

### Post by Skrynesaver on 2007-04-26
You should place your script in /etc/init.d It should that should make it available to start as a service.
You may need to modify your script so that it accepts a "start" option or call it from a proper daemon template (take a look at the other scripts in init.d)

---

### Post by gh0st on 2007-04-26
I've been looking for a way to do this myself. Thanks for the tips, I should have worked that out myself, it seems a bit obvious now ;)

---

### Post by sisco311 on 2007-04-26
you can modify the /etc/init.d/skeleton script[URL="http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit"]
learn more here[/URL]

---

### Post by DrQuincy on 2007-04-26
What's the difference between putting it in rc2.d and init.d?  Sorry, this is a bit out of my depth.

---

### Post by Skrynesaver on 2007-04-26
Each of the rc.n directories are populated with sybolic lincs back to the init.d directory, if a service is linked from an rc.n directory with a link named S044MyScript then when starting runlevel n MyScript is started ( the script in init.d is called with the start option) it will be called before S45YourScript and after S43HerScript.
I hope that is clear

---

### Post by AmyRose on 2007-04-26
I also wanted to mention that you can call your script from /etc/rc.local. It's like Ubuntu's autoexec.bat file. But note that it runs after the regular init scripts, but it will probably run before you log in.

---

### Post by DrQuincy on 2007-04-26
That makes sense - thanks!

If I simply wanted to run the line:

/usr/bin/./synergyc -f 192.168.28.7

How would I go about writing the file?

---

### Post by sisco311 on 2007-04-26
> I also wanted to mention that you can call your script from /etc/rc.local. It's like Ubuntu's autoexec.bat file. But note that it runs after the regular init scripts, but it will probably run before you log in.
> That makes sense - thanks!

If I simply wanted to run the line:

/usr/bin/./synergyc -f 192.168.28.7

How would I go about writing the file?
__________________

open a terminal:
```
sudo gedit /etc/rc.local
```
copy and paste this before the **exit 0** command:
> /usr/bin/./synergyc -f 192.168.28.7
your file should look like this:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/./synergyc -f 192.168.28.7
exit 0
save and exit(Ctrl+s, Ctrl+F4)
set the file permission:
```
sudo chmod 0755 /etc/rc.local
```

---

### Post by DrQuincy on 2007-04-27
Thanks for that - I followed it but still nothing. :(

---

### Post by dghenry on 2007-06-10
I think the x server needs to be running before you can run synergy.  Unfortunately, the init.d and rc.local scripts are run before the x server is started.  The solution is start synergy in the gdm init scripts.  This is how I was able to get it working: [http://www.eightpence.com/start-synergy-with-gdm-on-ubuntu/](http://www.eightpence.com/start-synergy-with-gdm-on-ubuntu/)

Later,
Dan

---

