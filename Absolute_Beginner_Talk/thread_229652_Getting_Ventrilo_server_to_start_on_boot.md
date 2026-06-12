---
title: "Getting Ventrilo server to start on boot"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Kibner on 2006-08-04
I have been searching for a good while in order to figure out how to get the free public version of the Ventrilo server to start when my system starts, no matter which user logs in.  I have found a server script that I like, but I don't know how to get it to work correctly.

The file that is used to start Ventrilo is located at /ventrilo/ventrilo_srv
I put the following script in /etc/init.d

```
#!/bin/sh
#Ventrilo Script v2.1.0_02 written by Crypt Keeper
#For ventrilo server v2.x

#Replace the values of VENPATH and VENSRV with your ventrilo path and server name. 
#Replace the value of VENUSER with the account name that ventrilo runs under.
VENPATH=/ventrilo
VENSRV=$VENPATH/ventrilo_srv
VENUSER=kibner

if [ "$UID" -ne 0 ]
then
        echo "You must be root to run this script"
        exit 64
fi

check_pid ()
{
if [ -e $VENPATH/ventrilo_srv.pid ]
then
	PID=`cat $VENPATH/ventrilo_srv.pid`
else
	PID=0
fi
}

start ()
{
echo ""
su - $VENUSER -c "cd $VENPATH ; $VENSRV -d"
check_pid $1
if [ $PID -ne 0 ]
then
	renice -20 $PID
        echo ""
        echo "Ventrilo server on Port:"$1" Started."
        echo ""
else
        echo ""
        echo "ERROR Ventrilo server on Port:"$1" Failed to Start"
        echo ""
        exit 66
fi
}

stop ()
{
check_pid $1
if [ $PID -ne 0 ]
then
        kill $PID
        echo ""
        echo "Ventrilo server on Port:"$1" with PID:"$PID" Stopped."
        echo ""
else
        echo ""
        echo "ERROR Ventrilo server on Port:"$1" Not Running."
        echo ""
        exit 67
fi
}

noport ()
{
echo ""
echo "Invalid argument string"
echo "Please specify a port number"
echo "-h|--help for usage"
echo ""
exit 68
}

case $1 in
-h|--help)
        echo ""
        echo "Ventrilo Script by Crypt Keeper"
        echo "       start port#"
        echo "       stop port#"
        echo "       restart port#"
	echo "       status port#"
	echo ""
        ;;
start)
        if [ $# -eq 2 ]
        then
		start $2
	else
        	noport
        fi
        ;;
stop)
        if [ $# -eq 2 ]
        then
		stop $2
	else
        	noport
        fi
        ;;
restart)
        if [ $# -eq 2 ]
        then
		stop $2
		start $2
	else
		noport
        fi
	;;
status)
        if [ $# -eq 2 ]
        then
		check_pid $2
		if [ $PID -ne 0 ]
		then
			echo ""		
			echo "Ventrilo server on Port:"$2" -Running- with PID:"$PID
			echo ""
		else
			echo ""
			echo "Ventrilo server on Port:"$2" -Not Running-"
			echo ""
		fi
        else
                noport
        fi
        ;;

* )
        echo ""
        echo "Invalid Argument $1"
        echo "-h|--help for usage"
        echo ""
        exit 69
        ;;
esac
exit 0
```

Part of the instructions of that script also told me to put a file called S99ventrilo inside of etc/rc3.d so that the server starts on boot.  Here are the contents of that file:

```
#!/bin/sh
#Ventrilo script v2.1.0_02 written by Crypt Keeper
#For ventrilo server v2.x

#Path to ventrilo script
VENSCRIPT=/etc/init.d/ventrilo

$VENSCRIPT start 3784
#$VENSCRIPT start 4000
#$VENSCRIPT stop 3784
```

I think I still have to use the sudo update-rc.d ventrilo defaults command to create the symbolic links, but I am not sure.

When I run the command "su - kibner -c "cd /ventrilo ; /ventrilo/ventrilo_srv -d", the terminal hangs and the ventrilo server is still not running under the processes.

In summary, I want the Ventrilo server to automatically start up at the same time as the rest of the system, and I want it to use the scripts that I found to make it a little bit easier to manage.

---

### Post by ovimunt on 2006-08-04
Ok, first of all make the script executable!

```

chmod 755 ***scriptname***

``` 
In order to add links in the ***rcX.d*** folders I use a little tool called ***sysv-rc-conf***. The big advantage is that it's got an interface although it runs in text mode.

```

sudo aptitude update
sudo aptitude install sysv-rc-conf

```

Then just run it with:

```

sudo sysv-rc-conf -p

``` 
The ***-p ***option tells it to also show you the priorities of all the scripts. Now, in the list of scripts you should also find the one you put in the ***init.d*** folder. All you need to do is put ***S99 ***in the corresponding run levels, ***3 ***in your case.
[I][B]
ATTENTION![/B][/I] Be VERY carefull with this tool and make sure you don't change anything else! Plus, I would advise you to read a bit on ***linux run levels*** before you start playing with these things.

---

### Post by Kibner on 2006-08-04
Ok, The script is now executable and I used that program that you gave me to set the runlevel of the script to 99.  I had actually read about the runlevels earlier today when searching for a solution.

However, the server is still not starting.  I think it has to do with this bolded line in the original script:

```
start ()
{
echo ""
**su - $VENUSER -c "cd $VENPATH ; $VENSRV -d"**
check_pid $1
if [ $PID -ne 0 ]
then
	renice -20 $PID
        echo ""
        echo "Ventrilo server on Port:"$1" Started."
        echo ""
else
        echo ""
        echo "ERROR Ventrilo server on Port:"$1" Failed to Start"
        echo ""
        exit 66
fi
}
```

From what I understand, that is just like me typing this in the terminal:
```
su - kibner "cd /ventrilo ; /ventrilo/ventrilo_srv -d"
```
I think that changes my working directory to /ventrilo and then tries to run ventrilo_srv in daemon mode.  I don't know what the 'su - kibner' part does.

Whenever I type that full string into the terminal I get the following error message.
```
-su: /ventrilo/ventrilo_srv: Permission denied
```

At the moment, kibner is my only account and I know I entered the password correctly.  The only way I know to get the server running is for me to set /ventrilo as my working directory and then type in 'sudo ./ventrilo_srv -d'

I don't know what the ./ does, though.  I guess I could try changing the corresponding line in the script to run that.  Will edit this post with the results (though, even if succesful, I would still like clarification on what 'su - kibner' and ./ do).

Update:  changing the start command to 'su - kibner "cd /ventrilo ; ./ventrilo_srv -d' did not work at all.

---

### Post by cshive on 2006-08-14
I am also looking for a way to get this working.  Surely there is a simpler solution.  I just want it to boot ventrilo_srv when the system boots up.

---

### Post by Lcars on 2006-10-31
I set up ventrilo thru webmin to start at boot up. I run ventrilo as its own user, and all the files are in a ventrilo folder. This is why the path is /home/ventrilo/ventrilo
The first thing I had to do is create the 3784.pid and 3784.ini in the vetrilo folder. I start several servers and the default one is on port 3784. So just copy the ventrilo_srv.pid and ventrilo_srv.ini paste and rename.
I also renice it so it has a higher priority.

```
#!/bin/sh
# ventrilo server

case "$1" in
'start')
	# Startup ventrilo servers.
	
	VENPATH=/home/ventrilo/ventrilo
	VENBIN=$VENPATH/ventrilo_srv
	
	su ventrilo -c "$VENBIN -f$VENPATH/3784 -d"
	
	renice -5 `cat $VENPATH/3784.pid`
	;;
'stop')
	killall ventrilo_srv
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0

```

Hope this helps.

---

