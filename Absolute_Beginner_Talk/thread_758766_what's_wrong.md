---
title: "what's wrong??"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by epicmono on 2008-04-18
i tried to install pidgin... and this is what comes up....

root@epic-desktop:/home/epic/pidgin# make
make: *** No targets specified and no makefile found.  Stop.
root@epic-desktop:/home/epic/pidgin# make install
make: *** No rule to make target `install'.  Stop.


i did ./configure... and a lot of messages comes up... some says yes.. some says no... i dunno what to do... deb is so much easier... installed google picasa with that... and it works fine !!!

---

### Post by Tatty on 2008-04-18
Do you have to install it via source?  it should be available by default in a Ubuntu install.  If it is not installed then you could install it via synaptic - "sudo apt-get install pidgin".  Or 2.4.1 is available on getdeb.net if you want that version.

If you definately want to compile then it would help if you posted the output from the terminal after you do ./configure

---

### Post by quirks on 2008-04-18
As far as I can see, you are trying to compile Pidgin (the instant messenger, right?). But it should already come with your Ubuntu installation by default (go to Applications -> Internet -> Pidgin). If not, you can install it using Synaptics. No need to compile anything.

quirks

---

### Post by bodhi.zazen on 2008-04-18
Hard to say from you post. Most likely the configuration failed due to an unmet dependency.

What were the last few lines of ./configure ?

Also, why are you compiling pidgin? It is in the repos. Use Add/Remove porgrams, synaptic, or apt-get

```
sudo apt-get install pidgin
```

---

### Post by racoq on 2008-04-18
> **epicmono said:**
> i tried to install pidgin... and this is what comes up....

root@epic-desktop:/home/epic/pidgin# make
make: *** No targets specified and no makefile found.  Stop.
root@epic-desktop:/home/epic/pidgin# make install
make: *** No rule to make target `install'.  Stop.


i did ./configure... and a lot of messages comes up... some says yes.. some says no... i dunno what to do... deb is so much easier... installed google picasa with that... and it works fine !!!

Just some Thoughts:


Those yes and no's are important. You must check if the ./configure aborts with some errors. To avoid these errors You'll probably want to do a "sudo build-dep pidgin" to install all the dependencies known to the packaged binary. Do this only if you want to install a more recent version thant the reository's and you feel confident enough.

EDIT:
If  you don't care about the version of pidgin and want a easy way you should do what bodhi.zazen suggested, and install from the repositorys

---

### Post by epicmono on 2008-04-18
epic@epic-desktop:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package pidgin

:(

---

### Post by Tatty on 2008-04-18
Go to system->administration->software sources and check all of the repositories. then try to apt-get again

---

