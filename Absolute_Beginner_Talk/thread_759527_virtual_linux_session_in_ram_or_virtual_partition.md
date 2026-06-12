---
title: "virtual linux session in ram or virtual partition"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-19
Hello forum people

i wondered whether anybody knows of a linux tool that does the same job as this tool below?

[http://www.returnilvirtualsystem.com/index_files/rvsbusiness.htm](http://www.returnilvirtualsystem.com/index_files/rvsbusiness.htm)

....these kind of tools allow you to work inside a virtual session of windows...where nothing is ever commmitted to hard drive unless you instruct it....

you can then dump a windows session whenever you like and loose all the changes you made during it...(even hibernate and use the sessions for days before dumping)

these tools protect users from messing up their operating systems by allowing them to test things fist inside the virtual session....if a software install goes well...then they commit that session to hard drive...otherwise they dump it


they also guard the PC from internet problems...

thanks

Vince.

---

### Post by bumanie on 2008-04-19
Virtualbox, vmware and qemu all provide virtual environments vmware is a proprietary, but has 'free for home use' virtualbox, has proprietary, a free for home use and an OSE (open source edition) and qemu is open source as far as I know. Out of the three, I have used qemu and virtualbox. To use on a permanent machine, I would try virtualbox. I carry qemu with puppy linux on a usb to use on windoze computers.

---

### Post by vinceUUUU on 2008-04-19
Hello

yes, i know about those other Linux tools you mention...they offer a similar goal....... but they are not really the same thing as i mentioned

The virtual tool i mentioned needs no other operating system installing in it...and it only requires a reboot of your existing operating system to dump the windows/Linux session...

These virtual tools also have no bad effect on computer performance...

thanks

VInce.

---

### Post by bumanie on 2008-04-19
Sorry, I only took a glance at the link. They are the only virtual environments I know of under linux, but there could be others. Some programmers work on many things in their spare time. It's impossible to know everything that is out there.

---

### Post by vinceUUUU on 2008-04-19
Hello

sure yes...there are lots of tools out there

i believe that this kind of tool would be achievable in Linux...but maybe a lot more complex than win32

I have found only 2 tools that do this job for win32...they are rare.

All other tools seam to clone entire partitions and not do it while your PC is running in a live session...they are basicaly ghosting style tools...

i have used the returnil tool for 3 years...i have never had a single problem with a win32 machine....literallly no issues with operatuing system problems....

nothing ever infects my machine from the web either...yet i only use the default firewall inside winXP and the RETURNIL tool....

they are very good indeed and simple to use

anyhow

thanks

maybe i could make one for Linux...

Vince.

---

### Post by bumanie on 2008-04-19
Read the site more thoroughly. Sounds somewhat similar how I have used qemu and puppy off a usb and external hard drive. Doesn't touch the host system, can be 'dumped' at the end of the session. Can save things for use if you want to. Not exactly the same, but similar. Must say that qemu's  peformance is not stellar, but servicable for specific purposes, ie snooping boss can't see what you are doing etc if you are using linux on top of windows.

---

### Post by vinceUUUU on 2008-04-19
Hello

uh...i did read it

is it not true that all the virtual systems you mention require an OS to be installed in them?...or at least they need an image of a partition put into them?

this is exactly what is not required by the tools i mention...that is the major difference as far as i can see....

that is the major difference...

also i know your vitual tools can do snapshots...but you don't really dump sessions if you don't like them do you?...you return to a previuos snapshot right?

thanks

Vince.

---

