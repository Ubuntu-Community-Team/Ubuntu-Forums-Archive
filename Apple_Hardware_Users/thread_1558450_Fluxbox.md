---
title: "Fluxbox:?"
date: 2010-08-22
forum: Apple Hardware Users
---

### Post by Fxy on 2010-08-22
Well for ages now i have had fluxbox installed alongside ubuntu on my vaio laptop & love it...

...Just recently i found out that you can have fluxbox installed on os x via darwin/macports

Im told that to installed fluxbox i have to run "sudo port install fluxbox"...

...After doing so i am presented with the following errors

> ijonny:~ iJonny$ sudo port install fluxbox
--->  Computing dependencies for gettext
--->  Configuring gettext
Error: You cannot install gettext for the architecture(s) x86_64 because
Error: its dependency libiconv only contains the architecture(s) i386.
Error: 
Error: Did you upgrade to a new version of Mac OS X? If so, please see
Error: 
Error:     [http://trac.macports.org/wiki/Migration](http://trac.macports.org/wiki/Migration)
Error: 
Error: Target org.macports.configure returned: incompatible architectures in dependencies
Log for gettext is at: /opt/local/var/macports/logs/_opt_local_var_macports_sources_rsync.macports.org_release_ports_devel_gettext/main.log
Error: Unable to upgrade port: 1
Error: Unable to execute port: upgrade autoconf failed
To report a bug, see <http://guide.macports.org/#project.tickets>
ijonny:~ iJonny$ 


I know that this might be a bit of topic, but im just curious as to if anyone can help me with this install...

---

