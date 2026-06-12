---
title: "Exiting script before process ends"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Balaam's Miracle on 2007-01-12
Hey guys and/or gals,

I'm relatively new at scripting and now i have run into something i can seem to figure out.

I'm running a radio statiuon using the ShoutCast server (i can't get Icecast to work, but that's not the issue).

I have 2 streams, 1 at 96kbs another at 32kbs.
To get them running i have made 2 scripts, one for each stream. Each script basically just contains the command to start up the shoutcast server (sc_serv) and the shoutcast source (sc_trans_linux) in one go, using the approriate config files.

The individual scripts work fine.

I have tried joining the two scripts so that there would be just one script to run, but the problem is that after the first stream starts, the script won't move on to the second stream. If i terminate the script, the streams are also killed.

So my question is this: Is there a way in bash to have the script start a process and move on to the next command without waiting for the first process to terminate or exit?

Here's the script, in case you need to have a look:

```
#!/bin/sh 
exec /home/balaam/shoutcast/sc_serv /home/balaam/shoutcast/sc_serv_lo.conf | /home/balaam/shoutcast/sc_trans_linux /home/balaam/shoutcast/sc_trans_lo.conf > /dev/null

```

---

### Post by bodhi.zazen on 2007-01-12
I am not familiar with the task. Is this the combined script?

Try:

#! bash

command 1 &
command 2 &
exit 0

---

### Post by Balaam's Miracle on 2007-01-12
> **bodhi.zazen said:**
> I am not familiar with the task. Is this the combined script?

No, it's just one of the two scripts.
The other one is very similar, except for the *.conf files
> 
Try:

#! bash

command 1 &
command 2 &
exit 0

Could you explain what the ampersands would do? So that i can determine where i should add them.

---

### Post by bodhi.zazen on 2007-01-12
The amperstands cause the command to run in the background.

Try adding them at the end of the line ...

Without them your script will pause until the command is complete, then run the second command ...

Hopefully with them the command will start and the script will continue ...

---

### Post by Balaam's Miracle on 2007-01-12
> **bodhi.zazen said:**
> The amperstands cause the command to run in the background.

Without them your script will pause until the command is complete, then run the second command ...


YES YES YES!!! It's working now!!!
I love you! May i kiss you? :-)

Making a script to restart the server should be a breeze now, not to mention turning this into an init.d script.

This is what my current script looks like:

```
#!/bin/bash 
/home/balaam/shoutcast/sc_serv /home/balaam/shoutcast/sc_serv.conf &
/home/balaam/shoutcast/sc_trans_linux /home/balaam/shoutcast/sc_trans.conf > /dev/null &
/home/balaam/shoutcast/sc_serv /home/balaam/shoutcast/sc_serv_lo.conf &
/home/balaam/shoutcast/sc_trans_linux /home/balaam/shoutcast/sc_trans_lo.conf > /dev/null &
exit 0

```

BTW: do i really need to add exit 0?

---

### Post by bodhi.zazen on 2007-01-12
You do not "have to", but it is a good habit ....

You never know what you or someone else may use the script for, call it with another perhaps ?

It is also nice to add comments. Comments start with a #

You can add them after the command if you like:

> 

# Starting stream 1 ..
/home/balaam/shoutcast/sc_serv /home/balaam/shoutcast/sc_serv.conf &
/home/balaam/shoutcast/sc_trans_linux /home/balaam/shoutcast/sc_trans.conf > /dev/null &

# Stream 2 ...
/home/balaam/shoutcast/sc_serv /home/balaam/shoutcast/sc_serv_lo.conf &
/home/balaam/shoutcast/sc_trans_linux /home/balaam/shoutcast/sc_trans_lo.conf > /dev/null &

exit 0 # exit 0 indicates a clean exit

Add what comments you will. I am sorry if I did not bread your script properly ?? 

But you get the idea :p

Future reference: 

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

[http://www.freeos.com/guides/lsst/index.html](http://www.freeos.com/guides/lsst/index.html)

---

