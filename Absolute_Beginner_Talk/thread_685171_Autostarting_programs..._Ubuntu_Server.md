---
title: "Autostarting programs... Ubuntu Server"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Shiva-Shinken on 2008-02-01
I am learning Linux and am having a blast doing it :)

I am playing around with Ubuntu Server therefore no GUI, mostly command line stuff.  I installed Webmin to help simplify some things.

Here is my situation:  I successfully installed Counter Strike Dedicated server (based on HLDS) and tested it... everything works fine.  To start the sep the rver, I first change to the folder which contains the "executable" (lol, still windows lingo)  :
cd /halflife/hlds_l

Then I fire up the server with:
./hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map de_dust

The server really is to be used for LAN games only.

Now I want the server to auto-start every time I boot the machine, but for the life of me cannot find any information on how to get it to auto-start.  Can anyone give me advice on what file to edit, or maybe even using Webmin?

Thanks for any advice.

Your comrade in Linux :lolflag:

CC

---

### Post by wesleybailey on 2008-02-01
Put the full path of the command in /etc/rc.local

/halflife/hlds_l/hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map de_dust

That should be executed each time your server boots

---

### Post by Shiva-Shinken on 2008-02-01
Thanks for the fast response :)

I did as you said, and I am getting a "Server Failed" message on PC startup:  invalid game type 'cstrike' specified.

Is having the folders location before the run command causing this error?  Otherwise, I checked and double checked everything else, all seems correct.

CC

---

### Post by taurus on 2008-02-01
Try to include the complete path to that program.  Otherwise, post your /etc/rc.local.

```
cat /etc/rc.local
```

---

### Post by Shiva-Shinken on 2008-02-01
Here is the complete entry:

```


#!/bin/sh -e
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

/halflife/hlds_l/hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map de_dust

exit 0



```

Obviously the script is attempting to start, but something is happening to make it fail.

---

### Post by Shiva-Shinken on 2008-02-02
As a side note, why is it that the following will not work
```
./halflife/hlds_l/hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map de_dust
```

since eliminating the folders from the "run" command, cd to the program, and running the command works fine... as such
```

cd /halflife/hlds_l
./hlds_run -game cstrike -insecure -nomaster +sv_lan 1 +maxplayers 18 +map de_dust

```

If there is any relationship to Windows, this is similar to doing run command either from within the folder the program is located, or by including the full path.  But it does not seem to work as such in Linux.

CC

---

### Post by Vadi on 2008-02-02
System - Preferences - Sessions is an alternative, easier way to setup starup programs.

---

### Post by PeterJS on 2008-02-02
This is what I use for managing all of my source based games. Obviously the variables at the top will need to be changed to work for your situation. The script assumes that you will have a user with lower privileges to run server itself as. Kicking things off with init scripts is good, but they run as root and so will any process they start, like the server, and running server processes as root is a bad idea. It makes use of screen so you're going to want to install that first, but that's good thing to have around any way.

```

#!/bin/sh

#This script is free software: you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation, either version 3 of the License, or
#(at your option) any later version.

#This script is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program.  If not, see <http://www.gnu.org/licenses/>.

#The name of the user the server will run under
SVR_USER=srcds

#The location of the scrds run command
SVR_PATH=/srcds

#The name of the server executable to run
SVR_BIN=srcds_run

#The name of the game that source wants for the -game switch
#Counter Strike doesn't use this *shrug*
#GAME_NAME="Counter-Strike Source"

#This is the name of the screen session to run the server under
SCREEN_NAME="css_screen"

#Server Arguments
SVR_ARGS="-console +maxplayers 24 -port 27015 +map de_dust +exec server.cfg -autoupdate"

#This is the name of the server to be displayed in status messages
SVR_NAME="Counter Strike: Source"

#how many seconds should the script allow for a clean shutdown before attempting to restart
SVR_RESET_DELAY=2

#Get pids
#server
PIDS=`ps aux | grep -E ".*srcds.*$GAME_NAME" | grep -v grep | awk '{print $2}'`

#And now the fun part
case "$1" in
  start)
    if [ -z "$PIDS" ]
    then
      echo "Starting: $SVR_NAME"
      cd $SVR_PATH
      screen -d -m -S $SCREEN_NAME su -l -c "cd $SVR_PATH; ./$SVR_BIN $SVR_ARGS" $SVR_USER
    else
      echo "$SVR_NAME is running with process IDs:"
      echo $PIDS
    fi
  ;;

  stop)
    if [ -z "$PIDS" ]
    then
      echo "$SVR_NAME is not running"
    else
      echo "Stopping: $SVR_NAME"
      kill $PIDS
    fi
  ;;

  restart)
   $0 stop
   sleep $SVR_RESET_DELAY
   $0 start
  ;;


  status)
    if [ -z "$PIDS" ]
    then
      echo "$SVR_NAME is DOWN"
    else
      echo "$SVR_NAME is UP"
    fi
  ;;

  *)
    echo "Usage: $0 {start|stop|status|restart}"
    exit 1
  ;;
esac

```

---

### Post by Shiva-Shinken on 2008-02-02
> **Vadi said:**
> System - Preferences - Sessions is an alternative, easier way to setup starup programs.

I am assuming that is available on the desktop edition of Ubuntu.  I am running the Server edition which has no GUI.  Therefore only command line will work.

CC

---

### Post by Vadi on 2008-02-02
Ah, my bad.

(you can install the GUI easily with sudo apt-get install ubuntu-desktop, but that would be a waste of resources!)

---

### Post by Shiva-Shinken on 2008-02-02
PeterJS, which file do I edit?  Sorry for the noobish question, but still in the earliest learning phase :)

CC

---

### Post by PeterJS on 2008-02-03
> **Shiva-Shinken said:**
> PeterJS, which file do I edit?  Sorry for the noobish question, but still in the earliest learning phase :)

CC

The whole mess is designed to be it's own stand alone script, drop the script in to /etc/init.d/ under what ever name you want. Being the CSS script that one was named css_init. Once it's there use update-rc.d to link it in to the boot process.
```

sudo update-rc.d *script_name* defaults 90 02

```
The numbers there tells it where it belongs in the boot and shutdown order, there are 100 slots, 00  through 99, the first number is it's start up position, and the second is it's shutdown location. You want to pick a nice high one to make sure that things like the network have a chance to load up, since nothing in the boot process depends on the server running, there's no penalty for picking to high of a number. I personally avoid 98 and 99 to ensure that local is always last. On the shutdown side of things you want the server going down first so that things later in the shutdown process can happen like they're supposed to, like syncing and unmounting the disk, shutting down the network, etc.

---

