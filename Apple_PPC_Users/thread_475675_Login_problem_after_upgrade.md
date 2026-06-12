---
title: "Login problem after upgrade"
date: 2007-06-16
forum: Apple PPC Users
---

### Post by jgreyna on 2007-06-16
Hi,

I have a powerbook G4, it had install Ubuntu edgy, some days before I upgrade it to feisty via Update Manager, after I restarted the computer, my user couldn't login in the system. I did some test and the problem is when a user is member of "audio" group, it can't login in the system.

Actually I have to work with a user that not is member of audio group, but I can't use the audio in the system. When the computer started, I listen a welcome sound but, when I'm in my session I can't listen nothing.

I try reinstall alsa* and gnome-session whit out results :(

Do you have any idea about how I can solve it?

Regards.

---

### Post by ssam on 2007-06-16
is that a titanium powerbook? if so you have probably hit [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

any process that tries to play a sound hangs after a few seconds. when you try to log into gnome it hangs on the login sound. at this point you can CTRL+ALT+F1 to a terminal, log in, and run
```
killall esd
```
then log in should continue. CTRL+ALT+F7 to ge back to the graphical interface

then in system->prefernces->sound disable the login sound. now you should be able to log in normally.

the best work around is to install an edgy 2.6.17 kernel.

---

### Post by tcrroadie on 2007-06-16
Have checked permissions for your user?  You can easily check user permissions graphically.  

System -> Administration -> Users and Groups 

Check user privileges for your user name.  Is "use audio devices" checked?

See screenshot.

---

### Post by jgreyna on 2007-06-17
> **ssam said:**
> is that a titanium powerbook? if so you have probably hit [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

any process that tries to play a sound hangs after a few seconds. when you try to log into gnome it hangs on the login sound. at this point you can CTRL+ALT+F1 to a terminal, log in, and run
```
killall esd
```
then log in should continue. CTRL+ALT+F7 to ge back to the graphical interface

then in system->prefernces->sound disable the login sound. now you should be able to log in normally.

the best work around is to install an edgy 2.6.17 kernel.

ssam.

Yes, it's a titanium powerbook.

I did what you told me and I have sound now :) I'm happy :P, every thing work fine.

Thanks a lot.

---

