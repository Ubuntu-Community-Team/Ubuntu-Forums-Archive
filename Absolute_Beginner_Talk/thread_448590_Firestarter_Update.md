---
title: "Firestarter Update"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by davesmith on 2007-05-19
Hello

Last night i received an update to firestarter via the terminal.... <sudo aptitude update>

The update was downloaded, as part of the installation process the terminal announced that firestarter was shutting down, then a few seconds later that it was starting up again.

Does anyone know what changes were made to firestarter for the update, and why did the installation process shut the firewall off and leave my m/c vulnerable, even if only for a few seconds?

Thanks

Davesmith

---

### Post by taurus on 2007-05-19
Firestarter is just a GUI to configure iptables (firewall) so even if firstarter is not running, iptables is still running in the background.  I never use firestarter so I don't think my machines are vulnerable at all.

---

### Post by davesmith on 2007-05-19
Taurus

Thanks, if firestarter is just a GUI for configuring iptables, why was it upgraded? Do you know what changes were made?

Davesmith

---

### Post by taurus on 2007-05-19
Here you go, [http://www.fs-security.com/](http://www.fs-security.com/).

---

### Post by davesmith on 2007-05-19
Thanks for the firestarter link....it doesnt say anything about the upgrade tho, the latest news was july 2005. i did find the manual!

---

### Post by taurus on 2007-05-19
What version of firestarter are you running right now?

---

### Post by davesmith on 2007-05-20
it says it´s Firestarter 1.0.3
That hasnt changed, so what´s with the update? ...I´d like to know why they released an update to my firewall, nothing seems to have changed with the GUI

---

### Post by Stunt Double on 2007-05-20
After I updated, I had a similar problem. Whenever I would try to start Firestarter, it would shut down and not re-start.
Go to synaptic package manager under System--> Administration. Search for Firestarter. Select: completely remove. Apply. Then search for Firestarter again. Select Install. Then Apply. You'll have the latest version and it  will work.
Don't forget to reconfigure it.
There is obviously a problem with the update. It's the only Update that has failed to install properly since I have been using Ubuntu.

---

### Post by davesmith on 2007-05-21
I'm not going to re-install Firestarter and loose all my ip blocks, ranges etc. 

I would, however like to know what was the update about, what issues were there with the old version and why did the install process have to shut down Firestarter and imediately start it up again.

Its working just fine now, but i'm still curious. There is no information on their website about an update. Does anyone know what this update was for?

Davesmith

---

### Post by wieman01 on 2007-05-21
> **davesmith said:**
> I'm not going to re-install Firestarter and loose all my ip blocks, ranges etc. 

I would, however like to know what was the update about, what issues were there with the old version and why did the install process have to shut down Firestarter and imediately start it up again.

Its working just fine now, but i'm still curious. There is no information on their website about an update. Does anyone know what this update was for?

Davesmith
You won't lose your configuration, I can assure you. I reinstalled Firestarter a couple of days ago and lost nothing, unless you tell Synaptic explicitly to delete all configuration files. So apart from this you are safe to reinstall Firestarter without much hassle.

---

### Post by geezerone on 2007-05-23
I tried updating firestarter but now won't run - shows error:

> A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close

Get this msg during upgrade:

> Setting up firestarter (1.0.3-1.1ubuntu4.1) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firestarter (1.0.3-1.1ubuntu4.1) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter


---

