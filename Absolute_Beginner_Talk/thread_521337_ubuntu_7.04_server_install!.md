---
title: "ubuntu 7.04 server install?!"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by therob1 on 2007-08-09
Hi, having previously used the desktop version i thought it would have been straight forward to get the server version installed so i can get some vmware servers running for testing on our network.

however, having just installed the software its put me into the console and I dont know what to do to load the server into the gui ?? HELP!

---

### Post by Inxsible on 2007-08-09
> **therob1 said:**
> Hi, having previously used the desktop version i thought it would have been straight forward to get the server version installed so i can get some vmware servers running for testing on our network.

however, having just installed the software its put me into the console and I dont know what to do to load the server into the gui ?? HELP!

the server version does not come with a  GUI. you can however install it.

depending on whether you want Ubuntu, Kubuntu or Xubuntu
```
sudo aptitude install ubuntu-desktop gdm
```Simply change the two packages to reflect the defaults for Kubuntu or Xubuntu

---

### Post by splintercellguy on 2007-08-09
Install a window manager of your choice:

sudo apt-get install ubuntu-desktop (or kubuntu-desktop, or xubuntu-desktop)

then

sudo /etc/init.d/gdm start

---

### Post by deadgobby on 2007-08-09
There is no gui in the server pack. It is straight commands. Don't fret it happens and you do not need to re install.
[http://psychocats.net/ubuntu/nox](http://psychocats.net/ubuntu/nox)

Gobby

---

### Post by Hospadar on 2007-08-09
The server version doesn't actually come with a gui.  I believe you can install it with ```
sudo apt-get install gnome-desktop
``` If you arn't yet that fimiliar with the ubuntu CLI you may want to stick with the desktop version for now.  You can get all the same software installed on the desktop version, the only difference between the versions is that they come with different packages installed by default.

---

### Post by Inxsible on 2007-08-09
> **Hospadar said:**
>  [COLOR=Red]the only difference between the versions is that they come with different packages installed by default.[/COLOR]

the kernel is also a bit different between the desktop and the server version. I do not know exactly how though !

---

### Post by therob1 on 2007-08-09
we just bought a HP ML350 and want to run vmware from the server install as we thought it would be better than sticking on windows 2003 as the host server.

ive tried the command lines above and cant seem to get it to install, it says the packages are not available ?

as the server is available to us for some test over the next few days im going to put the desktop version on and see how it runs, but its worth knowing whats involved with trying to get something working on the proper server version i think, and of course i can do this from within vmware itself to practise without having to rebuild the server.

do i need to download and put files on a cd then try running the commands??

I want to  try and break free from the world of windows and if i can slowly integrate it into our networks, even if only running virtual windows servers then i see it as a positive way forward as i believe linux is the future!

---

### Post by Inxsible on 2007-08-09
> **therob1 said:**
> ive tried the command lines above and cant seem to get it to install, it says the packages are not available ?
Do you have internet access from the machine ?

---

### Post by p_quarles on 2007-08-09
> the kernel is also a bit different between the desktop and the server version. I do not know exactly how though !
I don't know all the details, but one practical difference is that the server edition by default holds back kernel upgrades. Prevents the need for rebooting.

---

### Post by Inxsible on 2007-08-09
> **p_quarles said:**
> I don't know all the details, but one practical difference is that the server edition by default holds back kernel upgrades. Prevents the need for rebooting. That does make a lot of sense for servers !

---

