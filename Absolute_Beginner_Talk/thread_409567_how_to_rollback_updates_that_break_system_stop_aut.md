---
title: "how to rollback updates that break system/ stop automatic updates"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by vikram on 2007-04-14
I am reinstalling Kubuntu 6.10 after an automatic update screwed up KDE with an error with dcopserver. reinstalling kde base etc didnt work. Anyway now reinstalling from CD. Is there a way to rollback a faulty update ? I see many messages in the forum on how there systems were broken due to updates but no way of rollback the update. I would like to know if this is not possible.

Also how can I disable automatic updates so that it is NEVER selected by mistake ? I rather not spend my time reinstalling the OS repeatedly. 

I will not click on automatic updates 
repeat I will not click on automatic updates 
repeat  I will not click on automatic updates 

thats for me to remember never to use automatic updates again :-)

my $0.02 from one noob to all other noobs out there  - an insecure and buggy system is better than one that wont boot. it may be secure but not very usefull !!!

thanks

---

### Post by jem7v on 2007-04-14
Actually, a Lot of the updates are security updates rather than upgrades to functionality.  Usually I make a point of installing them once they're about a week old so that if problems arise with an update I hear about them on the forums beforehand.

Anyway. To install an older version of a package through Synaptic, run Synaptic.  Select the package you want to downgrade.  Go to Package: Force Version... and choose the older version, if available.  It might not be!  Sometimes older versions won't be available at all.

To not do automatic updates?  I'm not sure how to do it in KDE because I haven't used Adept, but in Gnome you can do this from Synaptic.  Hopefully it will be something similar, or at least will point you in the right direction.  In Synaptic, go to Settings -> Repositories.  Go to the Internet Updates tab.  All the settings for automatic updates can be found there.

As for solving your dcopserver program, I haven't found much info on the web about it... it sounds like dcopserver is just one of those modules that, uh, breaks unexpectedly, and on random occasions rather than consistently.  Hooray for KDE!  Tentative suggestions I've found for fixing it if it happens again:
- check the permissions of your /home/username/.DCOPServer*. file and make sure it belongs to you
- reinstall the kdelibs package?
- use something other than kde?

---

### Post by vikram on 2007-04-15
thanks Jem7v.

I have already resintalled Kubuntu. Adept doesnt seem to have any configuration for notifier. Ideally I would like to continue getting upgrades but remove upgrades which break the system.

var/log/dpkg.log seems to have a list of packages installed along with their timestamp. 

I installed  synaptic  and can downgrade to an earlier version of the package.. so i guess i can upgrade and if it fails go back and downgrade specific packages based on the log entries !

---

