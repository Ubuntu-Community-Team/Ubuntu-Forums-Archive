---
title: "GUI error -- won't start Nautilus"
date: 2007-11-30
forum: Apple PPC Users
---

### Post by trobn76 on 2007-11-30
I'm experiencing this error message as the GUI is starting up...
"Nautilus can't be used now, due to an unexpected error (details): Nautilus can't be now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautlius may help fix this problem."

So then I click OK

and the error message behind that one reads:

"Error
Somethings, such as themes, sounds, or background settings may not work correctly

The settings Daemon restared too many times.

The last error message was:

System exception: IDL:omg,org/CORBA/COMM_FAILURE:1.0

GOME wil still try to restart the Settings Daemon next time you log in."

I clicked OK and get this error message:

"Error
There was a problem registering the panel with the bonobo-
activation server.
The error code is 3
The panel will now exit."

Click OK

Nothing but black

So I held down cntrl-alt-F1 and tried this from the CLI:

sudo killall bonobo-activation-server

and got this reply:
bonobo-activation-server: no process killed

Any idea what has happened? 

BTW:
I got this error message randomly one day so I tried booting from the liveCD and I get the exact same error messages booting from the liveCD as from the HD that ubuntu is installed on.
This leads me to believe that I have a hardware problem.

---

### Post by bricar2 on 2007-12-03
Same problem here on my iMac G3 Blue...with the slot load CD. Trying some things and checking the posts. Kinda sucks. Was working great then one day this happened. Hmm.

---

### Post by TempestSA on 2008-05-04
On the macs, the time might be wrong, when logging in try changing the session and logging into a terminal, type date and check year, if it's not correct set it using the date command (type 'man date' for usage)

PC users, try reinstalling the bonobo server, at the log in prompt, change the session to a failsafe gnome (or failsafe kde in kubuntu), open synaptic and re-install libbobobo.

Hope this helps

---

