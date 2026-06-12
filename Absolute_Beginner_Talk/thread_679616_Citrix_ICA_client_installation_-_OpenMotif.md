---
title: "Citrix ICA client installation - OpenMotif"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by figi22 on 2008-01-27
I need to install a Citrix ICA client to access my work from my home PC.

I went to this page - would this be the right thing to download?

[http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323](http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323)

It says it needs OpenMotif, but I don't know what one I'm meant use.   I don't know how to install the source code, or should I use one of the following (see below)?   If anybody could give me some instructions then that would be fantastic.  I used some instructions on another posting to install a driver for my Canon printer and it worked brilliantly.

[COLOR="Blue"]Fedora Core 5 runtime libraries: openmotif-2.3.0-1.fc5.i386.rpm
Fedora Core 5 development build: openmotif-devel-2.3.0-1.fc5.i386.rpm
Fedora Core 6 runtime libraries: openmotif-2.3.0-1.fc6.i386.rpm
Fedora Core 6 development libraries: openmotif-devel-2.3.0-1.fc6.i386.rpm
Fedora Core 6 x86 64 bit runtime libraries: openmotif-2.3.0-1.fc6.x86_64.rpm
Fedora Cora 6 x86 64 bit development libraries:openmotif-devel-2.3.0-1.fc6.x86_64.rpm


Red Hat Enterprise Linux 3 runtime libraries: openmotif-2.3.0-1.rhel3.i386.rpm
Red Hat Enterprise Linux 3 development libraries: openmotif-devel-2.3.0-1.rhel3.i386.rpm
Red Hat Enterprise Linux 4 runtime libraries: openmotif-2.3.0-1.rhel4.i386.rpm
Red Hat Enterprise Linux 4 development libraries: openmotif-devel-2.3.0-1.rhel4.i386.rpm
Red Hat Enterprise Linux 4 x86 64 bit runtime libraries: openmotif-2.3.0-1.rhel4.x86_64.rpm
Red Hat Enterprise Linux 3 x86 64 bit development libraries: openmotif-devel-2.3.0-1.rhel4.x86_64.rpm


Suse 9 runtime libraries: openmotif-2.3.0-1.sles9.i586.rpm
Suse 9 development libraries: openmotif-devel-2.3.0-1.sles9.i586.rpm
Suse 10 runtime libraries: openmotif-2.3.0-1.sles10.i586.rpm
Suse 10 development libraries: openmotif-devel-2.3.0-1.sles10.i586.rpm
Suse 10 x86 64 bit runtime libraries: openmotif-2.3.0-1.sles10.x86_64.rpm
Suse 10 x86 64 bit development libraries: openmotif-devel-2.3.0-1.sles10.x86_64.rpm


Source:
openmotif-2.3.0.tar.gz
[/COLOR]

---

### Post by ureckifix on 2008-01-27
I am no expert just a newbie.can you network with the PC that has the program installed(internet).
I use tight VNC to access my PC's local and over the net it gives you a window of your PC you need to work on with all access to all files. also file transfer.
I have no info on Citrix ICA client but if it is on the server PC . VNC you should be able to use it,
with the write configuration of your network and router.
does this make sence?

---

### Post by Incense on 2008-01-27
Found this on [http://www.hanckmann.net/?q=node/13]("http://www.hanckmann.net/?q=node/13"), it should help you out. 


>    1. Download the last Citrix 10 ICAclient for Linux (in tar.gz version)
   2. Install libxaw6 libmotif3
      (sudo aptitude install libxaw6 libmotif3)
   3. Unpack the downloaded tar.gz
      (sudo tar xvfz en.linuxx86.tar.gz)
   4. Start the installation.
      (sudo ./setupwfc)
   5. Now follow the instruction on the screen to (un)install the Citrix Client 10.6 on your system.
      Use the default options for a smooth installation.
      Finally, accept the License Agreement.
   6. Let it integrate with Gnome (or KDE).
   7. Now quit the installation program.


---

### Post by figi22 on 2008-01-27
That's great - it's working now.   Thanks! :)

---

### Post by evolving_monkey on 2008-02-19
Thanks. That works perfectly with no permission problems.

---

