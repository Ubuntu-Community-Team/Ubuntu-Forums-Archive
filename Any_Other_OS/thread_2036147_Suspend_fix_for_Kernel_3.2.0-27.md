---
title: "Suspend fix for Kernel 3.2.0-27"
date: 2012-08-01
forum: Any Other OS
---

### Post by taidoka on 2012-08-01
Hi there,
since a couple of weeks I'm using Linux Mint 13 cinnamon edition on my Acer Aspire 5610 Notebook.
After several tweaks it's running quite smooth.
Main issue I'm facing up is a bug in suspend mode: Trying to resume fails frequently.
I figured out that my Bluetooth stack is responsible for this behaviour.
So I was trying to add a sleep.d script that stops the bluetooth daemon.
And it worked. Here's what I've got:
```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_bluetooth"

case "${1}" in
hibernate|suspend)
if (uname -r | grep '3.2.0-27'); then
initctl stop bluetooth
fi
;;
resume|thaw)
if (uname -r | grep '3.2.0-27'); then
initctl start bluetooth
fi
;;
esac

```The fact I'm running different kernels makes it necessary to check out which kernel is in use (Kernels 3.4 & higher do not show this Bug: Stopping the bluetooth daemon via this script even screws their suspend behaviour).
Since my bluetooth service is an upstart job I had to change the usual command from* /etc/init.d/bluetooth stop|start* to *initctl stop|start bluetooth*. 
What this script does: it stops the service when going to suspend mode and starts it when resumed.
That's it - for me. No guarantee it works for you.
And last: Don't forget to make it executable. Destination folder is /etc/pm/sleep.d (as root). The name doesn't really matter, if you give it a '20_'-prefix.
Cheers. taidoka

---

### Post by Perfect Storm on 2012-08-01
Moved to Other OS/Distro Talk.

---

### Post by taidoka on 2012-08-12
A new maintenance version was released these days: 3.2.0-29. Change that number or shorten it to 3.2.0 in the above written script. 
The resume behaviour improved a lot. But I've got another issue which is unresolved. One of four times cinnamon panel is garbled when resuming from suspend. Restarting cinnamon (ALT_F2-r) solves it. But the fact I have to trigger it manually is annoying. So I tried to implement another sleep.d-script to automatically restart cinnamon:

1.)
```
... cinnamon --replace
``` My first attempt: Window manager error: Unable to open X display (pm-suspend.log)

2.)
```
... export DISPLAY=:0 && cinnamon --replace
``` This one works but unfortunately it shows cinnamon's root settings - which differ from mine (as user).

3.)
```
... export DISPLAY=:0 && sudo -u [user] cinnamon --replace 
``` This one won't work if there are several user accounts as it would replace the panel with the one of the named [user] no matter who is resuming.

4.)
```
... killall -HUP gnome-session
``` This one resets the session and logs you out ;( (like Ctrl Alt Bksp). 

Is there someone who knows how to restart cinnamon on resume?
Any help is appreciated ... Thanks

---

### Post by taidoka on 2012-08-12
My own reply ...

Several issues to deal with:
1.) Needs to recognize logged-in user
2.) Apply script after network-manager has restarted 'cause otherwise weather-applet won't work
Here we go: 
```

#!/bin/sh
case "${1}" in
hibernate|suspend)
   initctl stop network-manager   # try without this command - in my case it didn't work
;;
resume|thaw)
   initctl start network-manager   # same as above
   until ping -q -w 1 -c 1 `ip r | grep default | cut -d ' ' -f 3` > /dev/null; do
      sleep 5
   done   # this loop checks if you're conncted
   users="$(who -q)"   # this works for one active user
   set -- $users
   user="$1"   # checks logged-in user
   export DISPLAY=:0.0 &&
   sudo -u $user cinnamon --replace &
;;
esac
```I'll report if this fix is stable.
Saved as 0000_cinnamon in /etc/pm/sleep.d/ and made it executable.
The number of the hook is probably too low. In my case it works. So check out if '22_' or something works better.

---

### Post by taidoka on 2012-08-12
Seems to work stable until now.
I'd be happy if someone reports his/her experience.
Thanks

---

### Post by taidoka on 2012-08-13
Well, it does not. Not anymore.
Written in pm-suspend.log: sudo: invalid option -- '-' ...
I think it's because of my 'sudo -u $user'-command.
Strange thing is, first attemps were working without any issues.
So what's going wrong here?

---

### Post by taidoka on 2012-08-13
Nobody to give me a hint? An answer?
Just me having these issues?

Edit:
The parameter has to be -q (who -q) otherwise it seems that there's no output which will keep the string empty.

---

### Post by taidoka on 2012-08-14
Hi again.
So I'm answering again my own question.
BTW sometimes I'm wondering if anyone cares about anybody's questions although not trivial.
Here we go:
```

#!/bin/bash
case "${1}" in
hibernate|suspend)
;;
resume|thaw)
   until ping -q -w 1 -c 1 `ip r | grep default | cut -d ' ' -f 3` > /dev/null; do
      sleep 5
   done
   users="$(who -q)"
   i=0; 
   for token in $users; 
   do
      i=$((i+1)); 
   done; 
   let "a = i-2"
   user=$(users | cut -d " " -f $a)
   export DISPLAY=:0.0 &&
   sudo -u $user cinnamon --replace &
;;
esac
```
I sourced the other command out. If necessary create another hook for stop|start network-manager.This one should work with two users logged in and will replace cinnamon of the active user.
I'm closing this thread now.
Bye

---

