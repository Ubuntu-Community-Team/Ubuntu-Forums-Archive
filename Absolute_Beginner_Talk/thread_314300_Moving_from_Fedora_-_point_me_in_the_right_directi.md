---
title: "Moving from Fedora - point me in the right direction."
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by joeblow on 2006-12-07
For the past 3 years I have been a person who uses Fedora in a LAMP/vBulletin environments.  Fedora served its purpose and I have practically based all my linux experience off the Fedora/RedHat distros.  

With the recent upgrades to vBulletin and the shear growth of my own forums I made the decision to move from my single server running FC3 to running a separate Web and Database servers each running FC6.  Unfortunately FC6 seems pretty irratic on the apache side.  No matter what I do apache wants to load up.  When it doesn’t load up to 30-50 it will very much ride its way higher than it should be.  Between updates, swapping memory, and 50 different apache configs the past 4 weeks have not resulted in a resolution.

My attempts with Cent OS / RHEL were less than impressive because I lack the skills required to compile the new versions of apache, php, and mysql required for vBulletin 3.6.x.  

Then I stumbled on Ubuntu.  6.01 has the versions I need, has the long term support, fits all on one great cd.  This morning I had my test box running the LAMP server in less than 15 minutes.  It only installs what it needs to and seems like a nice, fast, stable (hopefully), and simple.  I really liked the boot screen off the CD with the memory test and the seperate option just to install it as a LAMP server!

Now on to my first questions ....

First thing I noticed was no root access.  Well that gets rid of a bad habit.  

Second thing - I cant SSH in.  Not sure if there is a firewall / selinux running or just no SSH running.

I didn’t have too much time to play with it this morning but I was wondering how to get the tools running that I need.

-SSH
-Webmin
-FTP

Also I am sure I can find the locations of programs and logs but is there an easy summary of the differences?

Thanks much!

---

### Post by joeblow on 2006-12-07
Few notes...

FTP and SSH looks like its documented in the [server guide]("https://help.ubuntu.com/6.10/pdf/ubuntu/C/serverguide.pdf") so that helps.

I am running 6.06 dapper (not 6.01) ... I do have 2 opteron's in the production box.  Do I have to change anything to get it to run SMP?  My test box only has one CPU.

---

### Post by kebes on 2006-12-07
First off I think Ubuntu is a fine choice for a stable LAMP stack. As you said, 6.06 has "Long Time Support" so it's a good choice. (Fedora is also good, in my experience, but if you've been having a specific issue then I think Ubuntu is certainly worth a shot.)

> First thing I noticed was no root access.  Well that gets rid of a bad habit.

You can create a root account if you really want to... but I found that once I got used to it, I preferred "the ubuntu way" of not using root. You just have to do "sudo" whenever necessary. (You can also go "sudo -s" if you really want a root shell for a little while.)

> Second thing - I cant SSH in.  Not sure if there is a firewall / selinux running or just no SSH running.

As I recall, the SSH server (sshd) is not installed/running by default after an install (for security reasons). You can check with "pgrep sshd", but I believe you will have to go:
```

$ sudo aptitude install openssh-server
$ sudo /etc/init.d/ssh start

```


> I didn’t have too much time to play with it this morning but I was wondering how to get the tools running that I need.

It sounds like you're quite familiar with Linux and the commandline, so all you need to know is that Ubuntu uses "aptitude" as the package manager (instead of "yum" in Fedora). (Note: some people still use "apt-get" which is fine, but "aptitude" is a wrapper that calls apt-get but also stores more information which makes uninstalls more efficient).

So to install some things you want:
```

$ sudo aptitude install openssh-server
$ sudo aptitude install webmin
$ sudo aptitude install proftpd

```


> Also I am sure I can find the locations of programs and logs but is there an easy summary of the differences?

I don't know of a good summary (hopefully someone else has a good link?). I use both Ubuntu and Fedora right now... typically I'll just run a quick "which" or "locate" to remind myself where something is on each distro!

If you're looking for something specific, let us know...

---

### Post by joeblow on 2006-12-07
Good to all know.

I guess I am down to two questions.

-Is 6.06 running in SMP mode by default?
-How do I start/stop/restart services?
[will service httpd restart work?]

---

### Post by joeblow on 2006-12-07
wow - some of this stuff is pretty neat.

All the start/stop scripts in /etc/init.d ... not too hard to remember.

I downloaded the *deb of webmin but I cant really get aptitude to 'see' it tho.

Edit:
The following packages have unmet dependencies:
  webmin: Depends: libnet-ssleay-perl but it is not installable
          Depends: libauthen-pam-perl which is a virtual package.
          Depends: libio-pty-perl but it is not installable
          Depends: libmd5-perl which is a virtual package.


:(

---

### Post by po0f on 2006-12-07
joeblow,

For Dapper I believe you have to install the [686-smp](http://packages.ubuntu.com/dapper/base/linux-686-smp) kernel to utilize both of your Opties.

As for services, it should be as simple as:
```
[FONT="Courier New"]$ sudo /etc/init.d/<service-name> {start|restart|stop|force-reload}[/FONT]
```

[EDIT]

Looks like you already figured out the services part.  ;)

[EDIT2]

Have you tried double-clicking on the deb?  Or do you have just a server setup (no GUI)?

---

### Post by joeblow on 2006-12-08
> **po0f said:**
> joeblow,

For Dapper I believe you have to install the [686-smp](http://packages.ubuntu.com/dapper/base/linux-686-smp) kernel to utilize both of your Opties.



Thanks but that link is for a i386 kernel, not a AMD64 one.




> **po0f said:**
> 

[EDIT2]

Have you tried double-clicking on the deb?  Or do you have just a server setup (no GUI)?

Yep - server with no GUI.  The GUI usually saves a few min and then I just boot to a prompt after its all setup.  But if at all possible I'd like to be able to do all of this from the command line.

---

### Post by kebes on 2006-12-08
> I downloaded the *deb of webmin but I cant really get aptitude to 'see' it tho.

It's always best to install with "aptitude" instead of manually downloading the *.deb if at all possible. Thus you simply go "sudo aptitude install webmin" ... you may have to uncomment the 'universe' repository in "/etc/apt/sources.list".

If webmin is not available in any repository (it appears it is not), then you download the *.deb (which evidently you did), and use the "dpkg" command:

```

dpkg -i webmin_1.310_all.deb

```

If there are unmet dependencies, you'll have to install them manually, although in all likelihood a simple "aptitude" will get them all (because aptitude automatically resolves dependencies). So if you go "sudo aptitude install libmd5-perl" you might catch all the unmet packages.

---

### Post by joeblow on 2006-12-08
> **kebes said:**
> 

If there are unmet dependencies, you'll have to install them manually, although in all likelihood a simple "aptitude" will get them all (because aptitude automatically resolves dependencies). So if you go "sudo aptitude install libmd5-perl" you might catch all the unmet packages.

```
webmin: 
Depends: libauthen-pam-perl which is a virtual package.
Depends: libmd5-perl which is a virtual package.

```

Well I anm down to these two - whatever a virtual package is I'm not able to pull it from aptitude.

---

