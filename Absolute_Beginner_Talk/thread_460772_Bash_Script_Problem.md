---
title: "Bash Script Problem"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by viper2843 on 2007-06-01
I hope I am posting this in the right place.  I am writing my first bash script start and stop my Call of Duty 2 Linux server.  I am just about done but whenever I run the script it gives me the following error:

```
open: Permission denied
 * Starting Call of Duty 2 Dedicated Server: cod2_lnxded
open: Permission denied
```

If I look at the process list, I can see that the sever starts.  When I go to stop it, it stops, gives the same sort of error, and doesn't remove the pid file like it should.  I can't seem to figure out why it does this.  The script is posted below.

```
#!/bin/bash

APP_PATH=/home/cod/cod2
PID_FILE=cod2.pid
RCON_PASS=password

if [ -r /lib/lsb/init-functions ]; then
	. /lib/lsb/init-functions
	LOG_BEGIN="log_begin_msg"
	LOG_END="log_end_msg"
else
	LOG_BEGIN="echo -n"
	LOG_END=`printf "echo .\n"`
fi

# Exit if the daemon binary is NOT available, executable, etc.
test -x $APP_PATH/cod2_lnxded || exit 0

start() {
	$LOG_BEGIN "Starting Call of Duty 2 Dedicated Server: cod2_lnxded"
	start-stop-daemon --start --pidfile $PID_FILE --make-pidfile $PID_FILE \
		--chdir $APP_PATH --background --exec ./cod2_lnxded \
		+exec dedicated.cfg +map_rotate +set rcon_password $RCON_PASS
	$LOG_END $?
}

stop() {
	$LOG_BEGIN "Stopping Call of Duty 2 Dedicated Server: cod2_lnxded"
	start-stop-daemon --stop --pidfile $PID_FILE --chdir $APP_PATH
	$LOG_END $?
}

status() {
	if [ -e $PID_FILE ]; then
		echo "The Call of Duty 2 server is running with a PID of `cat $PID_FILE`"
	else
		echo "The Call of Duty 2 server is not running"
	fi
}

case "$1" in
	start)
		start
		;;
	stop)
		stop
		;;
	restart)
		stop
		sleep 1
		start
		;;
	status)
		status
		;;
	*)
        	log_success_msg "Usage: callofduty2-server-launcher {start|stop|reload|status}"
        	exit 1
        	;;
esac
exit 0
```

---

### Post by hillbilly on 2007-06-01
Does these commands have to be run as root ? Can you run the above commands from the command line and see what the output is ?

---

### Post by viper2843 on 2007-06-01
The server is set up to run under a normal user, not root.  Root access should not be required.

---

### Post by hillbilly on 2007-06-01
what happens when you run the *start-stop-daemon --start.....the whole command....* from the command line ?? does it run properly ?

EDIT: I misunderstood, I thought the script was not working. But I can see that it is, And you just seem to be getting that "Permission denied" error. 
Just clutching straws here, but what is the output of  the following command > ls -l $APP_PATH/cod2_lnxded

---

### Post by viper2843 on 2007-06-01
The start-stop-daemon commands for both starting and stopping the program execute without any errors or warnings.  The commands do exactly what they are supposed to do.

---

### Post by Cypher on 2007-06-01
Add "#!/bin/sh" to the top of the file and see if it makes any difference..

---

### Post by viper2843 on 2007-06-01
That line is in the script.  I forgot to copy it over in the initial post.  Sorry about that.  It does the same thing with that line.

---

