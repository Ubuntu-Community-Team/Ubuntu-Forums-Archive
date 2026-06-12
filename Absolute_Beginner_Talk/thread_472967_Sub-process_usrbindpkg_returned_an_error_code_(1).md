---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-06-13
Get **Sub-process /usr/bin/dpkg returned an error code (1)** error whilst trying to start Firestarter or reinstall it. Anyone know what this relates to?

---

### Post by az on 2007-06-13
Can you show the whole message, please?



also, run

sudo apt-get -f install

and display that message.

---

### Post by geezerone on 2007-06-14
When running the command I get the following information:

```
gt@gt-pc:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up firestarter (1.0.3-1.1ubuntu4.1) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
gt@gt-pc:~$

```

---

### Post by TriggerHappyChewie on 2007-06-14
you might want to try to remove firestarter completely:

```
sudo apt-get remove --purge firestarter
```

Then, re-install it.

---

### Post by geezerone on 2007-06-14
Thanks Trig that worked a treat :D

BTW, excuse me but what does[HTML]sudo apt-get remove --purge firestarter[/HTML] do exactly as can't find documentation on this?

Thanks!

---

### Post by az on 2007-06-14
> **geezerone said:**
> Thanks Trig that worked a treat :D

BTW, excuse me but what does[HTML]sudo apt-get remove --purge firestarter[/HTML] do exactly as can't find documentation on this?

Thanks!

type

man apt-get

and read the apt-get manual.

apt-get remove removes a package.  --purge just gets rid of the package configurations in the package manager database.  I don't think firestarter has any debconf variables, so I don't think purge will do anything different than just removing that package.

---

### Post by geezerone on 2007-06-15
Thanks for the clarification. I had read the man on it but seemed a little ambiguous. So this would be the same as 'complete removal' which can be carried out in Synaptic package manager rather than just uninstall?

---

### Post by az on 2007-06-15
Yup.

---

### Post by geezerone on 2007-06-15
Thankyou again! Another happy Ubuntuer :D

---

