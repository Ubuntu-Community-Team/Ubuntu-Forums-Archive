---
title: "start up program with gcaldaemon"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by jputman01 on 2007-05-22
im trying to get gcaldaemon to run automatically when i start my system, in the instructions is says:

Optionally start the 'service-install.bat' to install GCALDaemon as Windows service (on UNIX-compatible systems put GCALDaemon into 'init', 'launchd' or 'rc' script). Before uninstall GCALDaemon, you must stop and uninstall this service (with 'service-stop.bat' and 'service-uninstall.bat'). Please note, this is the last step in the setup/configuration process, do not install the service while GCALDaemon is not running properly.

what exactly does this mean? how to i get the daemon to run without leaving my terminal open

---

### Post by Pragmatist on 2007-05-25
You take whatever command would start it in a terminal, let us say that the command is "gcaldaemon" (that is just for this explanation, I'm assuming you know the actual command to start the daemon)

1.) Open a text editor:
```
gedit mygcald
```2.) Create the script:
> 
#!/bin/sh

# This is a comment to myself so I know what this does

gcaldaemon & ;
The key here is the first line: **#!/bin/sh **This defines the file as a shell script.  At a basic level, a shell script is just a way to automatically run commands without having to type them in to a terminal.

The other line that begins with a **#** is a comment.  Normally, you'd put a comment to remind yourself what the script does.  Each line that is a comment must start with a **#**  The **#** in **#!/bin/sh** is special and is not a comment.

Finally, the last line: **gcaldaemon &;** runs the command.  The **&** makes the process run in the background and the **;** designates that the command is complete.  You must end each command line with a **;**

Now, for some daemons, there is an argument added such as "start" or "stop" or "restart" etc...etc...  Again, only you know your program and how it is supposed to start and stop.  For example, the Gnome Display Manager (gdm) is started with: **/etc/init.d/gdm  start**
and it is stopped with:  **/etc/init.d/gdm  stop**


3.) After you save the file, make it executable:
```
chmod a+x mygcald
```4.) Test the script:
```
./mygcald
```5.Now for the fun part! :)  In order for your script to run every time the system starts, you need to put it in /etc/init.d  directory.  Then, a link is made to this script and is executed at the right moment in the runlevel.  In plain english, the actual script is put in /etc/init.d  and a link to the script is placed in one of the /etc/rc directories (probably /etc/rcS.d).  Here is a specific way to accomplish this:
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Specifically, the section on custom scripts:
> **Installing custom init-scripts**

  To install your own script, copy it to /etc/init.d, and make it executable.  
```
      sudo cp myscript /etc/init.d
    sudo chmod +x /etc/init.d/myscript
```
To make the script run at startup:  
```
      sudo update-rc.d myscript start 51 S .
```
(Do not forget the dot: . ) 
 For more information on the usage of update-rc.d  
```
      man update-rc.d
```


---

### Post by Maverickprowls on 2007-11-25
I've followed all these commands, and they do seem to work but for one small problem.  When I run the script in /etc/init.d I get the following error, which I suspect is stopping my GCALDaemon from starting at boot-time.

```
./GCALDaem_start: 5: Syntax error: ";" unexpected
```

Have I done something wrong?

For reference, I have included the contents of my script

```
#!/bin/sh

# Script to start GCALDaemon at boot in order to allow access to GMail addressbo
oks.

/usr/local/sbin/GCALDaemon/bin/standalone-start.sh  &;

```

Thanks for any help you can offer.

---

### Post by dustigroove on 2008-02-18
> **Maverickprowls said:**
> I've followed all these commands, and they do seem to work but for one small problem.  When I run the script in /etc/init.d I get the following error, which I suspect is stopping my GCALDaemon from starting at boot-time.

```
./GCALDaem_start: 5: Syntax error: ";" unexpected
```Have I done something wrong?

For reference, I have included the contents of my script

```
#!/bin/sh

# Script to start GCALDaemon at boot in order to allow access to GMail addressbo
oks.

/usr/local/sbin/GCALDaemon/bin/standalone-start.sh  &;

```Thanks for any help you can offer.


UPDATE - Removed my quickie script as flabdablet has posted a more appropriate option below.

--

---

### Post by flabdablet on 2008-03-07
Here's my GCALDaemon start/stop script, based on the outline in /etc/init.d/skeleton.  Instead of launching the standalone-start.sh script supplied with GCALDaemon, this script uses start-stop-daemon to run an appropriate Java command line itself. I did it that way to make the process ID recorded in /var/run/gcald.pid be the ID of the actual GCALDaemon process, rather than that of a shell reading standalone-start.sh.  It may need updating if the GCALDaemon developers make changes to standalone-start.sh, but hopefully that won't be hard.

To use it:

1.  Save [[COLOR="Blue"]this script[/COLOR]]("http://users.on.net/~flabdablet/gcald") as /etc/init.d/gcald

2.  If your GCALDaemon is not installed in /opt/GCALDaemon, alter the BASEDIR=/opt/GCALDaemon line in the script to suit your own installation

3.  Make the script executable, with
```
sudo chmod 755 /etc/init.d/gcald
```

4.  Install it as a startup script with
```
sudo update-rc.d gcald start 50 2 3 4 5 . stop 50 S 0 1 6 .
```

Hope this helps.

---

### Post by dustigroove on 2008-03-08
> **flabdablet said:**
> Here's my GCALDaemon start/stop script, based on the outline in /etc/init.d/skeleton.

Excellent, much appreciated. Nice to do things the right way.  :)

--

---

### Post by niceguy123 on 2008-04-17
Can some please describe how to install gcaldaemon in Ubuntu 7.04.

Thanks,

---

### Post by flabdablet on 2008-04-19
I installed mine in Ubuntu Server 7.10, but I imagine the process would be similar for 7.04.

I followed these [[COLOR="Blue"]_installation instructions_[/COLOR]]("http://gcaldaemon.sourceforge.net/usage11.html#p2") to install GCALDaemon into /opt/GCALDaemon (except that instead of logging in as root to start with, I used sudo to run those commands that needed root access).  Then I wrote an [[COLOR="Blue"]_init script_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4473753&postcount=5") to make it start when my system starts.

Since this is an "Absolute Beginner Talk" forum, I expect that some of these instructions might assume knowledge you don't have.  If that's the case, let me know where you get stuck and I'll try to fill in the gaps for you.

---

### Post by cccv on 2008-06-09
> **flabdablet said:**
> Here's my GCALDaemon start/stop script....
Hope this helps.

It sure did help me a lot.
Thanks!

---

