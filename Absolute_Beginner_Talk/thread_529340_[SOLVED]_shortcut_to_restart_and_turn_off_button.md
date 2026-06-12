---
title: "[SOLVED] shortcut to restart and turn off button?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by taisao on 2007-08-19
Hi,

Can anyone tell me how to make a shortcut button to shutdown/restart the computer, so when I click that button it shutdown/restart the computer.

(using Kubuntu 7.04)

---

### Post by Spr0k3t on 2007-08-19
You could create a link to the "shutdown" command.  If you want to restart, just append "-r" to the command.  Not sure, but you may need to chown it as I think it's a root restricted command.

For more information, pull open a terminal and do a man shutdown.  You could even throw together an interface for shutdown after X amount of time if you want.

---

### Post by taisao on 2007-08-19
yes I have try the shutdown command, it works but it need root access, now can anyone tell me how to chmod +x it for normal user?

---

### Post by grimmoner on 2007-08-19
hello taisao,

Every command, like these, that changes the status of your system,
must be run as superuser!

In ubuntu you can use the sudo command with the commands you will execute.

You also have to have execute pemission to run the script.

chmod +x script_name is good as you mentioned before.



The commands the script have to run can be:

(for shutdown)
shutdown -h now

-r is for restarting.

Playing with runlevels is also funny.

telinit 0
will turn off also your computer.

telinit 6 i think is for restarting.

---

### Post by grimmoner on 2007-08-19
brutal users can also run

sudo /etc/init.d/halt

which shuts down the system immediatelly,
without going through the shutdown process.

of course i wouldn't suggest that to anyone.
may cause damage.

just mentioning that way

---

### Post by msak007 on 2007-08-19
> **taisao said:**
> Hi,

Can anyone tell me how to make a shortcut button to shutdown/restart the computer, so when I click that button it shutdown/restart the computer.

(using Kubuntu 7.04)

If you're using Kubuntu you can just add an applet to your Kicker bar for the Shutdown button, which will bring up the same dialog that you get when you go through the KMenu.

1. Right click on your panel
2. Choose "Add Applet to Panel"
3. Choose "Lock / Logout Buttons"
4. Click "Add to Panel"

You'll have two buttons on top of each other, Lock on top and Logout on the bottom. The bottom one will bring up the shutdown menu. Not sure if that's exactly what you wanted, but that's how I have it set up and would be easier than creating a script just to shut down.

---

### Post by taisao on 2007-08-19
Thank you all :KS

I just like to have a button for* shutdown *and one for* restart*. Without having to click the* log out *button first.

With the help of this howto I'm able to achieve it : [http://www.ma.utexas.edu/users/stirling/computergeek/shutdown.html](http://www.ma.utexas.edu/users/stirling/computergeek/shutdown.html)
(sudo way, shutdown.allow doesn't seems to work for me)

Another option is the kde keyboard shortcuts (Halt/Reboot without confirmation), which is very handy

---

