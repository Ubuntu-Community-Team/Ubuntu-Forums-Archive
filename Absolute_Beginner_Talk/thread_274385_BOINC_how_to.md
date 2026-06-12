---
title: "BOINC how to???"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-09
How do I setup boinc on my server so that I can connect to it from a client to conntroll it?

I have boinc-client installed on my ubuntu server and boinc-manager installed on a xubuntu machine.

Any one done this?

---

### Post by kent41 on 2006-10-09
> **guysmiley25 said:**
> How do I setup boinc on my server so that I can connect to it from a client to conntroll it?

I have boinc-client installed on my ubuntu server and boinc-manager installed on a xubuntu machine.

Any one done this?

You might try this
[HTML]
http://setiathome.berkeley.edu/forum_index.php[/HTML]

---

### Post by emarkay on 2006-10-10
Oh lookeee, another wiseguy who thinks he's too smaaaaart to help a noob.  What a hoot!

Comedians.](*,)

---

### Post by guysmiley25 on 2006-10-10
Well I got it to work. Thanks for all the help guys.

Ok so on my server I installed boinc-client

$ sudo apt-get install boinc-client

Then I edited the startup config file

$ sudo nano /etc/default/boinc-client

Changed this

#BOINC_OPTS="-return_results_immediately -allow_remote_gui_rpc"
BOINC_OPTS=""

to this

BOINC_OPTS="-return_results_immediately -allow_remote_gui_rpc"
#BOINC_OPTS=""

Then edited these config files

$ sudo nano /var/lib/boinc-client/gui_rpc_auth.cfg
and put in your password.

$ sudo nano /var/lib/boinc-client/remote_hosts.cfg
and appended the hosts that are allowed to access.

Then restarted boinc
$ sudo /etc/init.d/boinc-client restart


Ok now client side.
Installed boinc-manager

Ran it
$ boincmgr

Then go Advanced > Select computer.

Put in the hostname or IP for the server and password and your away.

You can find more info at
/usr/share/doc/boinc-client/README.Debian

Finding where all these files where was proberly the hardest part, there where lots of sites telling you what files and how to edit them but not tell you where they where!!!

---

### Post by tribaal on 2006-10-10
Thanks mate, I've been looking around for such help for a while.

- trib'

---

### Post by guysmiley25 on 2006-10-20
PS. It seems restarting boinc-client is not enought to load the new setting. I'm not sure what you have to restart so I just have been rebooting the machine. This is fine but if anyone knows what it is please share. Should not need to restart linux.

---

### Post by izmaelis on 2006-11-30
Very nice.
Last time I checked BOINC wasn't in a default repositories. Now I can resume my seti@home activity at home too (I'm running it on few others computers with other OSes elsewhere).
Thanks for the tips, they helped a lot.

---

