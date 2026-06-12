---
title: "Linux Background 01 - System Directories?"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by DavePat on 2005-11-25
I have found a wealth of material on how to do things in Linux but precious little on why things are done the way they are done so I've got some questions.

I'm reformatting my disks and installing Ubuntu to a clean system. I accept all the defaults. When Ubuntu comes up, I look to see what it did. I notice a series of directories which I assume are system associated directories.

This leads to my questions -

What goes in each of the directories initially?

What actions cause new files or data to be put in each of the directories?

As a regular user, would I (or could I) ever manually put anything in any of the directories?

As a root user, would I ever want to manually put anything in any of the directories?

Thanks for your help,

Dave

---

### Post by steve.horsley on 2005-11-25
[http://rute.2038bug.com/node20.html.gz](http://rute.2038bug.com/node20.html.gz)

---

### Post by ssam on 2005-11-25
if you run ubuntu (or any other debian based system) then you have apt, the advanced package manager. this does a very good job of looking after all the system files.

when you install an application in synaptic then apt makes sure all its files get put in the correct place.

for most people this all they ever need. you dont really need to go outside you home folder for anything.

however there are a few case where you might need to.
*if you want to install an application that is not in the ubuntu repositories (if you enable the universe repo then this is rare). then you might have to compile the application and put pieces in the right place.
*configuring. although there are a bunch of control panels in the system menu, sometimes you need to edit text files to configure things. most of these are stored in /etc

if you are currious then have a browse round the file system. you can't do any harm by looking. the layout is a bit odd to start with. some of it has historical reasons or is useful if you want a bare minimum installed on a machine, and to get all the applications from a remote server.

---

### Post by Kyral on 2005-11-25
/usr -- User accessible programs and binaries are stored here
/etc -- System configuration files
/var -- Variable things like Internet Cache, logfiles, and the Apt-Cache
/bin -- binaries the system needs at boot (in case /usr is mounted elseware)
/usr/sbin -- binaries that only root needs
/boot -- Holds the compiled kernel and stuff the system needs to boot
/dev -- device nodes like /dev/hda
/proc -- A BUNCH of stuff about the running system. If you look at the filesize they are all empty. But if you cat them.... ```
cat /proc/cpuinfo
``` Fun :D
/media -- Where things like floppies, cdroms, and other removable media are mounted
/mnt -- where things like extra HDs are traditionally mounted
/home -- User Home directories. Contain all personal data and configurations

---

