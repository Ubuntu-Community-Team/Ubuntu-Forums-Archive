---
title: "915resolution (Vaio), problem writing to boot on Edgy"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by airezulian on 2007-04-29
Before installing Edgy, I had set up the 915resolution on 6.6 and it worked flawlessly. 

Both times I followed the instructions on [http://users.skynet.be/thomasvst/linux-on-laptop/#wide](http://users.skynet.be/thomasvst/linux-on-laptop/#wide).

I am able to get the resolution to work however I have been unable to write it to the /etc/init.d/bootmisc.sh file so that it can be executed at every boot. Instruction number 10 say to include:

" Add the line 915resolution 3c 1280 800 after the line : [ -f /etc/default/rcS ] && . /etc/default/rcS (at aproximatively line 10)" 

However, I don't seem to have this line. Please see below the output. Have I corrupted the file somehow?

I would be very grateful if someone could help me on this.

Best!

#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname $remote_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
. /lib/init/vars.sh

do_start () {
        #
        # If login delaying is enabled then create the flag file
        # which prevents logins before startup is complete
        #
        case "$DELAYLOGIN" in
          Y*|y*)
                echo "System bootup in progress - please wait" > /var/lib/initscripts/nologin
                ;;
        esac

        # Create /var/run/utmp so we can login.
        : > /var/run/utmp
        if grep -q ^utmp: /etc/group
        then
                chmod 664 /var/run/utmp
                chgrp utmp /var/run/utmp
        fi

        # Set pseudo-terminal access permissions.
        if [ ! -e /dev/.devfsd ] && [ -c /dev/ttyp0 ]
        then
                chmod -f 666 /dev/tty[p-za-e][0-9a-f]
                chown -f root:tty /dev/tty[p-za-e][0-9a-f]
        fi

---

### Post by MyR on 2007-04-29
i prefer using gedit for text editing:
```
sudo gedit /etc/init.d/bootmisc.sh
```
i added the command as seen below and it works great! i just tested it to make sure.

#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname $remote_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
. /lib/init/vars.sh

915resolution 3c 1280 800

do_start () {
	#
	# If login delaying is enabled then create the flag file
	# which prevents logins before startup is complete
	#
	case "$DELAYLOGIN" in
....

peace

---

### Post by airezulian on 2007-04-29
MyR,
Problem solved! I am not quite sure how you knew to add the line where you added it but the important thing is that it works! Thank you so much!
Also, thank you for reminding to use gedit instead of vi. Good call.
Best!

---

### Post by tomt on 2007-05-13
This solved the final piece of the puzzle for me.

Thanks

If anyone is stuck I've posted my work through (intended for the desperate and frustrated) here:

[http://fubuntu.blogspot.com/2007/05/enabling-widescreen.html](http://fubuntu.blogspot.com/2007/05/enabling-widescreen.html)

Thanks for the help.

tomt

---

### Post by MyR on 2007-05-13
now that i know, it's quite simple to make ubuntu use whatever resolution you want.
all you need to do is install 915resolution, add the 915resolution command to the boot script as shown above and then restart x with ctrl+alt+backspace and you're good to go

---

