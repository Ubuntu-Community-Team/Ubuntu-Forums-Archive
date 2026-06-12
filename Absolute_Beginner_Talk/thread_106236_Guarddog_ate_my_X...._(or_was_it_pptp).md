---
title: "Guarddog ate my X.... (or was it pptp?)"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by unwoken on 2005-12-20
I was trying to connect properly to my VPN at work using pptp-linux, and followed the instructions from this thread:
[http://ubuntuforums.org/showthread.php?t=91249](http://ubuntuforums.org/showthread.php?t=91249)

everything installed fine, and i eventually was able to get the connection working after allowing a connection to the work IP in firewall.

unfortunately after a couple of minutes my entire internet connection would freeze, and even totally shutting pptp would not re-connect me.

i read further down in the thread listed above (post #10) that guarddog can help if you are having firewall problems with a VPN (which is what i assume(?) i was having).

so basically i loaded up synaptic and installed guarddog.  i know it is supposed to be for KDE, but assumed that any relevant packages would be installed and i didn't really mind that.

i was surprised by the fact that only one package was installed by synaptic, but was not sure if that was an issue.

after reading that guarddog does not kick in until you configure it, i did so.  directly after configuring it (i had 'exited' my firestarter icon from the tray) i attempted to open my 'sessions' option from the menu to disable firestarter on the next startup.

sessions did not load (crashed before properly opening), so i immediately logged out.

on attempting to re-log in to my user, X immediately crashed, giving me a message about the session lasting less than 10 seconds.

since then i have:
done an apt-get remove on guarddog from terminal
done a sudo dpkg --purge on guarddog
changed firestarter config from backup login (in the hope of overwriting any damaged config files from guarddog)
re-booted computer

X still crashes immediately on boot.

i am now in my backup user (glad i made one :) ) and am totally clueless as to what to do as i didn't change anything else.

i would REALLY appreciate some help as i certainly don't have any ideas (other than perhaps completely purging PPTP).

thanks in advance :)

uw.

nb.  i must log out now but will check in the morning (Melb. Aust). so any replies will definitely not be ignored.  thks.

---

### Post by unwoken on 2005-12-20
i have posted this thread (a copy) in the main 5.10 support forum.

i would love some help, but if anyone has any to give, could you please look here:

[http://ubuntuforums.org/showthread.php?p=592159#post592159](http://ubuntuforums.org/showthread.php?p=592159#post592159)

thanks.

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=unwoken]i have posted this thread (a copy) in the main 5.10 support forum.

i would love some help, but if anyone has any to give, could you please look here:

[http://ubuntuforums.org/showthread.php?p=592159#post592159](http://ubuntuforums.org/showthread.php?p=592159#post592159)

thanks.[/QUOTE]
Do you have a hidden .guarddog folder in your original user's home folder?  You could try erasing that.

Is there a .xsession-errors log in that user's home folder?  It might tell what the error is.

---

### Post by unwoken on 2005-12-21
[QUOTE=cwaldbieser]Do you have a hidden .guarddog folder in your original user's home folder?  You could try erasing that.

Is there a .xsession-errors log in that user's home folder?  It might tell what the error is.[/QUOTE]

hey cwaldbieser.  thank you very much for your reply.  i have been flat out today and have only just been able to get in to check the forums.

to your questions, i do not have a .guarddog folder in the relevent home folder, but i do have a .xsession-errors file.

i'm sure it tells the story, only problem is that i am not sure how to read it.  if anyone could help, i would be very happy.

i will just post the entire file here:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "fireball"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/cynopolis:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/cynopolis:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/cynopolis:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8435): WARNING **: Unable to read ICE authority file: /home/fireball/.ICEauthority

```

does anyone have any ideas?

---

### Post by unwoken on 2005-12-21
ok i found the answer.

many thanks to cwaldbieser, as well as the people who wrote this: [http://ubuntuforums.org/showthread.php?t=104739&highlight=iceauthority](http://ubuntuforums.org/showthread.php?t=104739&highlight=iceauthority)
and this:
[http://www.ubuntuforums.org/showthread.php?t=80599&highlight=icetrans](http://www.ubuntuforums.org/showthread.php?t=80599&highlight=icetrans)

it seems that the permissions of .ICEauthority (which i had never heard of half an hour ago) had been changed to 600.  i just renamed the file from my backup user and logged in to the old user.

as you can see, everything worked perfectly, because i am typing this from the account that was 'unusable' a few minutes ago.

i am very happy, both with the fix, and this forum.  i have got out of so much trouble reading here, so thank's all, even if you have no idea who i am :p :confused: 

....
EDITED next part (as the answer was found)

anyway, my only question was. how did this happen? 

invalid explained it, (post #6) of: [http://ubuntuforums.org/showthread.php?t=98738&highlight=iceauthority](http://ubuntuforums.org/showthread.php?t=98738&highlight=iceauthority)

i must have caused the error when i typed 'sudo guarddog'.  i believe i should have typed 'kdesu guarddog'(?) given it is a kde program...

not sure why it changed the permissions, but i am happy now i have a solution.

cheers!
much happier now :_
uw.

---

