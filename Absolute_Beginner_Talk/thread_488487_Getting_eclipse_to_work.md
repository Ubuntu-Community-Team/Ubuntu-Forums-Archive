---
title: "Getting eclipse to work"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by twinky on 2007-06-30
I am using Ubuntu 7.04 (Feisty Fawn) and today I try to get eclipse IDE to work. After downloading and extracting the eclipse archive I could not find the way to run it.

```

unique@ubuntu:~/eclipse$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
unique@ubuntu:~/eclipse$ ls -Al
total 384
drwxr-xr-x  2 unique unique   4096 2007-06-28 21:18 about_files
-rw-r--r--  1 unique unique  11930 2007-06-28 21:18 about.html
drwxr-xr-x  2 unique unique   4096 2007-06-28 21:18 configuration
-rwxr-xr-x  1 unique unique  20537 2007-06-28 21:18 eclipse
-rw-r--r--  1 unique unique    115 2007-06-28 21:18 eclipse.ini
-rw-r--r--  1 unique unique     59 2007-06-28 21:18 .eclipseproduct
-rw-r--r--  1 unique unique  16536 2007-06-28 21:18 epl-v10.html
drwxr-xr-x 25 unique unique   4096 2007-06-28 21:17 features
-rw-r--r--  1 unique unique   9022 2007-06-28 21:18 icon.xpm
-rwxr-xr-x  1 unique unique 266168 2007-06-28 21:18 libcairo-swt.so
-rw-r--r--  1 unique unique   6506 2007-06-28 21:18 notice.html
drwxr-xr-x 13 unique unique  20480 2007-06-28 21:17 plugins
drwxr-xr-x  2 unique unique   4096 2007-06-28 21:18 readme
unique@ubuntu:~/eclipse$ ./eclipse
bash: ./eclipse: No such file or directory
unique@ubuntu:~/eclipse$ 


```

As you can see I cannot get the executable file eclipse (which is right there) get to run (it tells it is not there :)). Probably I am doing something simple wrong. Can you tell me what is it and how to run the eclipse IDE?

---

### Post by rapolas on 2007-06-30
You should install from repositories, then you should be able to run just simpe typing: eclipse (without any dots and slashes), and also it should be in the menu. And in your case, if you know, that eclipses binary is in that location, maybe it's not executable? you can make it executable doing this: ```
chmod a+x eclipse 
```

---

### Post by nitro_n2o on 2007-06-30
go get it from the repositories, your life will become way easier 

```
sudo apt-get install eclipse 
```

---

### Post by Damiel on 2007-06-30
twinky,

I did the same as you and eclipse ran fine:

```

user@pc:/opt/eclipse$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
user@pc:/opt/eclipse$ ls -Al
total 460
drwxrwxr-x   2 user user   4096 2007-02-12 14:31 about_files
-rw-rw-r--   1 user user  11669 2007-02-12 14:31 about.html
drwxrwxr-x   6 user user   4096 2007-04-20 00:41 configuration
-rwxr-xr-x   1 user user  29128 2007-02-12 14:31 eclipse
-rw-rw-r--   1 user user     25 2007-02-12 14:31 eclipse.ini
-rw-rw-r--   1 user user     59 2007-02-12 14:31 .eclipseproduct
-rw-r--r--   1 user user  12656 2007-02-08 16:16 epl-v10.html
drwxrwxr-x 101 user user  12288 2007-02-22 00:51 features
-rw-rw-r--   1 user user   9022 2007-02-12 14:31 icon.xpm
-rwxr-xr-x   1 user user 266168 2007-02-12 14:31 libcairo-swt.so
-rw-r--r--   1 user user   6506 2007-02-08 16:16 notice.html
drwxr-xr-x  78 user user  40960 2006-12-05 05:15 plugins
drwxrwxr-x   2 user user   4096 2007-02-22 00:49 readme
-rw-rw-r--   1 user user  34148 2007-02-12 14:31 startup.jar
user@pc:/opt/eclipse$ ./eclipse

```

Your eclipse folder seems to be missing the **startup.jar** file though.

---

### Post by twinky on 2007-06-30
ok ok, i know i can get it from repositories, but it is really strange that executable file could not be found! The repositories are great, but just theoretically what if I want to use the Eclipse IDE on the computer where is not an internet connection...?

---

### Post by twinky on 2007-06-30
> **Damiel said:**
> twinky,

I did the same as you and eclipse ran fine:

```

user@pc:/opt/eclipse$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
user@pc:/opt/eclipse$ ls -Al
total 460
drwxrwxr-x   2 user user   4096 2007-02-12 14:31 about_files
-rw-rw-r--   1 user user  11669 2007-02-12 14:31 about.html
drwxrwxr-x   6 user user   4096 2007-04-20 00:41 configuration
-rwxr-xr-x   1 user user  29128 2007-02-12 14:31 eclipse
-rw-rw-r--   1 user user     25 2007-02-12 14:31 eclipse.ini
-rw-rw-r--   1 user user     59 2007-02-12 14:31 .eclipseproduct
-rw-r--r--   1 user user  12656 2007-02-08 16:16 epl-v10.html
drwxrwxr-x 101 user user  12288 2007-02-22 00:51 features
-rw-rw-r--   1 user user   9022 2007-02-12 14:31 icon.xpm
-rwxr-xr-x   1 user user 266168 2007-02-12 14:31 libcairo-swt.so
-rw-r--r--   1 user user   6506 2007-02-08 16:16 notice.html
drwxr-xr-x  78 user user  40960 2006-12-05 05:15 plugins
drwxrwxr-x   2 user user   4096 2007-02-22 00:49 readme
-rw-rw-r--   1 user user  34148 2007-02-12 14:31 startup.jar
user@pc:/opt/eclipse$ ./eclipse

```

Your eclipse folder seems to be missing the **startup.jar** file though.

today i downloaded eclipse from eclipse.org site (two different packages Eclipse IDE for Java Developers and Eclipse for Java Enterprise Developers), and there is no startup. jar

if there will be one i'll try 'java -jar startup.jar' at least

---

### Post by Damiel on 2007-07-01
Well, I just found out after reading your post that eclipse 3.3 (europa) has been released, and there is no startup.jar file anymore
```

user@pc:~/Desktop/eclipse$ ls -Al
total 384
drwxr-xr-x  2 user user   4096 2007-06-28 14:18 about_files
-rw-r--r--  1 user user  11930 2007-06-28 14:18 about.html
drwxr-xr-x  8 user user   4096 2007-07-01 10:13 configuration
-rwxr-xr-x  1 user user  20537 2007-06-28 14:18 eclipse
-rw-r--r--  1 user user    115 2007-06-28 14:18 eclipse.ini
-rw-r--r--  1 user user     59 2007-06-28 14:18 .eclipseproduct
-rw-r--r--  1 user user  16536 2007-06-28 14:18 epl-v10.html
drwxr-xr-x 25 user user   4096 2007-06-28 14:17 features
-rw-r--r--  1 user user   9022 2007-06-28 14:18 icon.xpm
-rwxr-xr-x  1 user user 266168 2007-06-28 14:18 libcairo-swt.so
-rw-r--r--  1 user user   6506 2007-06-28 14:18 notice.html
drwxr-xr-x 13 user user  20480 2007-06-28 14:17 plugins
drwxr-xr-x  2 user user   4096 2007-06-28 14:18 readme
user@pc:~/Desktop/eclipse$ ./eclipse
user@pc:~/Desktop/eclipse$ 

```

Still, it runs fine over here.

Excuse me if this is a silly question. Have you tried executing the eclipse file by double clicking on it in nautilus?

---

### Post by rapolas on 2007-07-01
> **twinky said:**
> ok ok, i know i can get it from repositories, but it is really strange that executable file could not be found! The repositories are great, but just theoretically what if I want to use the Eclipse IDE on the computer where is not an internet connection...?
Are you sure that it is executable? Cause this problem, than file not found is usualy when you try to execute, but it's not executable. I'm talking not about that file is binary or something, but if it has the x mod. You can make it executable by executing this command: ```
chmod a+x eclipse
``` (if you need root permission, add sudo in front of this command)
And the try it run ./eclipse

---

### Post by DBStevens on 2007-07-01
I think you discover that eclispe requires a shell script to start and if you used the repos and synaptic it would have put the shell script into /usr/bin.  I don't think that eclipse you see in the directory is a vaild executable it may be just a loadable module. 

 <app name="Eclipse" cmd="/usr/bin/eclipse" icon="eclipse48.png" term="false" snotify="true" />  

From my development menu 

/usr/bin$ ls -o ec*
-rwxr-xr-x 1 root    5976 2007-03-12 11:47 echo-client-2
-rwxr-xr-x 1 root     686 2007-03-07 14:05 ecj
-rwxr-xr-x 1 root     686 2007-03-07 14:05 ecj-bootstrap
-rwxr-xr-x 1 root 2680852 2007-03-07 14:06 ecj-gcj
-rwxr-xr-x 1 root    5364 2007-04-10 13:22 eclipse

from my /usr/bin directory and 

:/usr/lib$ ls -o e*
-rwxr-xr-x 1 root 7300 2007-03-28 09:45 e2initrd_helper

eclipse:
total 108
drwxr-xr-x  2 root  4096 2007-06-23 16:16 configuration
-rwxr-xr-x  1 root 22900 2007-04-10 14:33 eclipse
-rw-r--r--  1 root    25 2007-04-10 13:07 eclipse.ini
drwxr-xr-x 12 root  4096 2007-06-23 16:16 features
drwxr-xr-x  2 root  4096 2007-06-23 16:16 links
drwxr-xr-x 86 root 32768 2007-06-23 16:16 plugins
-rw-r--r--  1 root 34173 2007-04-10 13:07 startup.jar

and there is the eclipse library that you were trying to execute as a program from my /usr/lib directory.

---

### Post by twinky on 2007-07-01
> **Damiel]Excuse me if this is a silly question. Have you tried executing the eclipse file by double clicking on it in nautilus?[/quote]

Yes I have been trying that few times but nothing at all happen. (and you are also right that 3.3 version of eclipse don't have the startup.jar...it was the reason why i didnt get 3.2 from repositories I just wanted the fresh version :)

[quote=rapolas]
Are you sure that it is executable? Cause this problem, than file not found is usualy when you try to execute, but it's not executable. I'm talking not about that file is binary or something, but if it has the x mod. You can make it executable by executing this command:
```
chmod a+x eclipse
```
[/quote]

as far as i can see it from ls -Al command the file eclipse is executable (x) for all the users, but to make it sure i used also the mentioned chmod command ... without any noticable impact  said:**
> 
I think you discover that eclispe requires a shell script to start and if you used the repos and synaptic it would have put the shell script into /usr/bin. I don't think that eclipse you see in the directory is a vaild executable it may be just a loadable module. 


Ok, the reason why i post it here is that it seems the file isn't there (but it is) and this is very confusing for me. I'll be ok if it says something like segmentation fault or something similar but not just 'No such file or directory'. [joke]Does it need glasses to see it?[/joke]

Anyway thank you all for the replies :p

---

### Post by DBStevens on 2007-07-01
"'No such file or directory'. [joke]Does it need glasses to see it?[/joke]"

Nope I haven't looked at the source for bash and friends to see what happens if you attempt to execute a binary file that isn't really supposed to be executed.  Something from many years ago comes to mind. Oh yeah, now this ancient  one remembers.

Results may be unpredictable ;-).

YMMV

---

### Post by twinky on 2007-07-02
To say the truth I think the eclipse file should be executed to run Eclipse IDE(Damiel posts proof it).
If it wasnt I dont see the reason why they will not put there another script which will run Eclipse IDE.
So all this 'No such file or directory' seems really strange to me .. maybe it is bug in the filesystem (what is really not that funny) or something else (much more trivial).

Really disapointed with this ... I'm not able to run something what is expected to work without problems ...

---

### Post by AZzKikR on 2007-07-02
> **twinky said:**
> To say the truth I think the eclipse file should be executed to run Eclipse IDE(Damiel posts proof it).
If it wasnt I dont see the reason why they will not put there another script which will run Eclipse IDE.
So all this 'No such file or directory' seems really strange to me .. maybe it is bug in the filesystem (what is really not that funny) or something else (much more trivial).

Really disapointed with this ... I'm not able to run something what is expected to work without problems ...

Have you tried executing it using the full path? I.e. 
```
bash$ /usr/share/eclipse/eclipse
```
?

---

### Post by DBStevens on 2007-07-02
Expected to work without problems would hold if you used the provided install procedure.  It also would have created a menu item pointing to an executable shell script called eclipse in the /usr/bin directory.

In fact it contains:

```

#!/bin/bash

# Having any sort of classpath causes massive breakage, with Kaffe at least.
unset CLASSPATH; export CLASSPATH

# Allow the user to specify their own Java home, we check for it later.
#unset JAVA_HOME; export JAVA_HOME

CMDLINEARGS=""
VMARGS=""
INSTALL="/usr/lib/eclipse"
STARTUP="/usr/lib/eclipse/startup.jar"

if [ -x /usr/bin/zenity ]; then
    DIALOG=/usr/bin/zenity
    DIALOGW="$DIALOG --warning"
elif [ -x /usr/bin/kdialog ]; then
    DIALOG=/usr/bin/kdialog
    DIALOGW="$DIALOG --warningyesno"
elif [ -x /usr/bin/xdialog ]; then
    DIALOG=/usr/bin/xdialog
    DIALOGW="$DIALOG --warning"
else
    DIALOG=echo
    DIALOGW="$DIALOG"
fi


# Make sure this directory exists.
if [ ! -d ~/.eclipse ]; then
    mkdir ~/.eclipse > /dev/null 2>&1
    if [ $? -ne 0 ]; then
        $DIALOG \
            --error \
            --title="Could not launch Eclipse Platform" \
            --text="Could not create settings directory at ~/.eclipse."
    fi
fi

# Just in case Eclipse tries to put something in the home directory.
cd ~

# Load default settings from the user's configuration file.
if [ -f ~/.eclipse/eclipserc ]; then
    . ~/.eclipse/eclipserc
fi

# Process the command line options. These override the eclipserc file, so we do
# them after parsing that file.
while [ "$1" ]; do
    if [ "$1" = "-h" -o "$1" = "--help" ]; then
        echo "Eclipse Starter Script"
	echo "Usage:"
	echo "eclipse [options [value]]"
	echo "See eclipse(1) for more information."
	echo ""
	echo "Also see ~/.eclipse/eclipserc, which provides some default values"
        exit 0
    elif [ "$1" = "-vm" ]; then
        shift
        unset JAVA_HOME
        JAVACMD="$1"
        shift
    elif [ "$1" = "-install" ]; then
        shift
        INSTALL="$1"
        shift
    elif [ "$1" = "-startup" ]; then
        shift
        STARTUP="$1"
        shift
    elif [ "$1" = "-vmargs" ]; then
        shift
	while [ "$1" ]; do
		VMARGS="${VMARGS} $1"
	        shift
        done
    else
        CMDLINEARGS="${CMDLINEARGS} $1"
        shift
    fi
done

# If the user has specified a custom JAVA, we check it for validity.
# JAVA defines the virtual machine that Eclipse will use to launch itself.
if [ -n "${JAVA_HOME}" ]; then
    echo "using specified vm: ${JAVA_HOME}"
    if [ ! -x "${JAVA_HOME}/bin/java" ]; then
        $DIALOG \
            --error \
            --title="Could not launch Eclipse Platform" \
            --text="The custom VM you have chosen is not a valid executable."
        exit 1
    fi
fi

# If the user has not set JAVA_HOME, cycle through our list of compatible VM's
# and pick the first one that exists.
if [ -z "${JAVA_HOME}" -a ! -n "${JAVACMD}" ]; then
    echo "searching for compatible vm..."
    javahomelist=`cat /etc/eclipse/java_home  | grep -v '^#' | grep -v '^$' | while read line ; do echo -n $line ; echo -n ":" ; done`
    OFS="$IFS"
    IFS=":"
    for JAVA_HOME in $javahomelist ; do
        echo -n "  testing ${JAVA_HOME}..."
        if [ -x "${JAVA_HOME}/bin/java" ]; then
            export JAVA_HOME
            echo "found"
            break
        else
            echo "not found"
        fi
    done
    IFS="$OFS"
fi

# If we don't have a JAVA_HOME yet, we're doomed.
if [ -z "${JAVA_HOME}" -a ! -n "${JAVACMD}" ]; then
    $DIALOG \
        --error \
        --title="Could not launch Eclipse Platform" \
        --text="A suitable Java Virtual Machine for running the Eclipse Platform could not be located."
    exit 1
fi

# Set JAVACMD from JAVA_HOME
if [ -n "${JAVA_HOME}" -a -z "${JAVACMD}" ]; then
    JAVACMD="$JAVA_HOME/bin/java"
fi

# Set path for the Mozilla SWT binding
MOZILLA_FIVE_HOME=${MOZILLA_FIVE_HOME%*/}
if false && [ -n "$MOZILLA_FIVE_HOME" -a -e $MOZILLA_FIVE_HOME/libgtkembedmoz.so ]; then
    :
elif [ -e /usr/lib/firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/xulrunner/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
elif [ -e /usr/lib/mozilla-firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla-firefox
elif [ -e /usr/lib/mozilla/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla
else
    $DIALOGW \
        --title="Integrated browser support not working" \
        --text="This Eclipse build doesn't have support for the integrated browser."
    [ $? -eq 0 ] || exit 1
fi

EXT=/usr/local/lib/eclipse/.eclipseextension
if [ ! -f $EXT ]; then
    if ! touch $EXT 2>/dev/null; then
	cat <<-EOF
	Could not create $EXT. Please run as root:
	    touch $EXT
	    chmod 2775 $EXT
	    chown root:staff $EXT
	EOF
    fi
    chmod 2775 $EXT 2> /dev/null || true
    chown root:staff $EXT 2> /dev/null || true
fi

# libraries from the mozilla choosen take precedence
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}

# Do the actual launch of Eclipse with the selected VM.
exec /usr/lib/eclipse/eclipse \
    -vm "${JAVACMD}" \
    -install "${INSTALL}" \
    -startup "${STARTUP}" \
    ${CMDLINEARGS} \
    -vmargs -Djava.library.path=/usr/lib/jni \
            -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db \
            -Dgnu.gcj.runtime.VMClassLoader.library_control=never \
            -Dosgi.locking=none ${VMARGS}

```


Notice the proper way to call the larger eclipse module it requires eight items to be provided on the call.

Mine works just fine, now if I had a reason to play with it at the moment it might be of some use, but not right now.

---

### Post by twinky on 2007-07-14
[quote=AZzKikR]Have you tried executing it using the full path?[/quote]

Yes I did but the results are the same...No such file or directory

:popcorn:

I went to my friend in Prague last week. He is also using ubuntu (he have installed both 6.06 and 7.04 with home folders the same for both:) I have downloaded Eclipse here and unpacked it. It works without any problems with executing the "eclipse" file (and also by clicking on it).

I have been thinking where is the difference. One thing is that he have standard i386 version of ubuntus installed and I have x64 at home. Can this cause the problems of executing eclipse file?

Let me know if someone is running Eclipse on x64 ubuntu by eclipse file.... 
:KS

---

### Post by LarsP on 2007-07-14
I extracted this file to ~/programs/eclipse :
[ftp://ftp.uninett.no/pub/eclipse/eclipse/downloads/drops/R-3.3-200706251500/eclipse-SDK-3.3-linux-gtk-x86_64.tar.gz](ftp://ftp.uninett.no/pub/eclipse/eclipse/downloads/drops/R-3.3-200706251500/eclipse-SDK-3.3-linux-gtk-x86_64.tar.gz)

I then ran eclips by typing ./eclipse -vm /usr/lib/jvm/java-6-sun/jre/bin

---

### Post by DBStevens on 2007-07-14
You might want to try this

sudo apt-get install lib32gcc1

Post #23 in [http://ubuntuforums.org/showthread.php?t=495394&goto=newpost](http://ubuntuforums.org/showthread.php?t=495394&goto=newpost)

---

