---
title: "Getting services to run at startup"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by hymerman on 2008-02-20
Hi, sorry if this question has a very obvious answer, but I really don't know Ubuntu or linux that well... Also, the 'similar threads' suggested to me don't help.

I've installed Ubuntu onto a machine I intend to use as a server for a variety of things. Currently I start up the machine, fire up my other (Windows) machine, then use putty to access it via SSH and start up a couple of things. I'd like to not have to do that - I'd like the services to be started up when the machine is turned on. I'm getting confused by a few things though, mostly whether the services I'm talking about are actually services (I understand that's a special term in linux) or programs, and who exactly will be starting/running them if nobody has logged on to the machine, and of course what scripts/files to edit to get them to start up.

The services in particular are Pulse continuous integration server and the Retrospectiva issue tracker.

Any help you can give me I'd very much appreciate! Thanks very much :)

---

### Post by DoctorMO on 2008-02-20
Your should look to create init scripts in  /etc/init.d/ which will control the service daemon (if you don't have those already) you'll then want to open up an init level editor and choose when the process should load, alternativly you can add it manually by going into the /etc/rc.X/ directory where X is the run level you want the script to execute at and adding the required file there.

Useful man pages: init

---

