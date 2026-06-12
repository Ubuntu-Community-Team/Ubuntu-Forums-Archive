---
title: "Ubuntu maintenence"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by rmsoldato on 2006-07-05
I'm day 5 into running Ubuntu Linux exclusively instead of Windows.  I'm converted, very happy with how things are going so far.  I have one question, though.  What is/are the best apps for maintaining Ubuntu?  Under Windows I had to regularly run registry cleaners, defragmenters, junk file cleaners, etc. to keep the system running smoothly.  Are there similar apps I should run under Ubuntu to keep it in healthy shape?

-The Soldato

---

### Post by Elim on 2006-07-05
To my knowledge you need none of those things.  It's a little hard to believe, but that's what I've been told.

Glad everything's working great for you!

---

### Post by cowley on 2006-07-05
ditto! great eh??

simon

---

### Post by mcduck on 2006-07-05
All you need to do is install updates when available.

And perhaps you may want to run 'sudo apt-get clean' to remove apt's cached package files to free some HDD space, altought the cache doesn't usually get very big (and in Synaptic's options there is an option to remove cached files after installation)..

If you install & remove lots of apps you may get some orphaned packages (that are installed as dependencies to some app, and are left on the machine when you remove the original app). To get rid of them install a package called 'deborphan' and make a new filter in Synaptic to show only orphaned files. After that they are easy to remove.

Linux doesn't have registry like Windows has, so no need to clean it. Linux filesystems don't suffer from fragmentation so no need for defrag. And there are no spyware or adware or viruses so once again, nothing to do there :D

---

### Post by tturrisi on 2006-07-05
about the only thing you need to cleanup ate the firefox caches & the tmp dir files:
```
sudo cp /etc/init.d/sysklogd /etc/init.d/sysklogd_backup
sudo gedit /etc/init.d/sysklogd

    * Find this section 

...
 stop)
  log_begin_msg "Stopping system log daemon..."
  start-stop-daemon --stop --quiet --oknodo --exec $binpath --pidfile $pidfile
  log_end_msg $?
...

    * Add the following line below it 

  rm -fr /tmp/* /tmp/.??*

    * Save the edited file 
```

---

### Post by YuHoo on 2006-07-05
The only thing that I've found that I need to do is removing extraneous things from boot up/libraries. So it's more of a streamlining thing. Unlike windows with defragmenting hard drives, the journaling system that linux uses effectively erases all need for it. Things like scandisk are handled for you automatically by running every 30 times you boot up. The only thing that comes to mind is useless programs or low-grade programs that don't tidy up when they uninstall. For that just use checkinstall (find it through apt-get install checkinstall) which will make your life easier.

Kudos on the switch, if you want to get into some type of programming/scripting I'd suggest that you learn python and then perl or ruby, but wait about a month so you can tinker with it and ultimately screw it up to learn more.

---

### Post by jvdowney on 2006-07-05
Thanks all for the responses. I have tried several flavors of Linux before settling (after a week on Ubuntu) on Xubuntu and have committed myself to learning what I need to run it. These forums really ease that process-

---

### Post by someusernoob on 2006-07-05
Although you dont need a tool actually, it is kind of cool to clean up some things (some folders you want empty (i.e. thumbnail folder, temp folders, firefox downloads, whatever you want to empty, its possible), some input fields ( networktool, ALT+F2) with one simple bash command. 

You can add bash aliases in the /home/you/.bash_aliases file and you can multiple command with && between 2 commands. for example:

alias aptupdate='sudo apt-get update && sudo apt-get upgrade'

But you can put as many lines in there you want. Thats really cool. So instead of typing 50 things, you only have to type one thing.

As i said, it isnt neccesary to clean up stuff, but hey, everyone wants to clean up some stuff sometimes, and it is possible with one bash command. Life's great this way :)

---

