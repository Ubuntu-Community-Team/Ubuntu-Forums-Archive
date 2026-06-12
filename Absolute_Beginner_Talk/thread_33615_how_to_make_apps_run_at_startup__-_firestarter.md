---
title: "how to make apps run at startup ? - firestarter"
date: 2005-05-11
forum: Absolute Beginner Talk
---

### Post by glandula on 2005-05-11
hey

another question, most likely there will be many more

how do i make programs run at start up ? for example i want to run firestarter automaticly

thanks again

---

### Post by tdell on 2005-05-11
Go to Sytem>Preferences>Sessions click on Statup Programs.

Tom

---

### Post by lt_kije on 2005-05-11
There's lots of different ways to do things like this. The best in your situation, though, sounds like creating a startup script. For example, the file '/etc/init.d/ntpdate' causes Ubuntu to synchronize it's hardware clock with the ububtu.com timeserver (you might have noticed this during your OS's boot). The file itself is just a script written in the BASH shell scripting language. Creating a new script, saving it in /etc/init.d/ and creating a symlink to one of the runlevel directories (eg /etc/rc2.d/) would be the preferred way to solve your problem.

If you're not comfortable editing system scripts, you could use GNOME's session utility to make Firestarter start when GNOME loads. I don't have GNOME on this system, but I think you'd need to go to the System or Admin menus and choose "Session." Adding commands once you've found that menu is pretty straightforward.

Good luck!

lt_kije

---

### Post by glandula on 2005-05-11
you guys are great, quick and good answers all the time. thanks a lot :)

---

### Post by az on 2005-05-11
Look at this (this is the list of files in the firestarter package from packages.ubuntu.com):  

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=firestarter&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=firestarter&version=hoary&arch=i386)


See the line:

etc/init.d/firestarter


That means that it is already part of the package when you install it.  It runs at boot by default.  Most debian or ubuntu packages are well-made and do not need you to do anything but occasionaly reconfigure them.  You should be able to do that using synaptic.

---

### Post by glandula on 2005-05-11
hi again

yes it seems firestarter is running by default. but i dont see it in the tray...i need to start it manually..i want the graphical stuff to run at startup

---

### Post by dresnu on 2005-05-15
[QUOTE=glandula]hi again

yes it seems firestarter is running by default. but i dont see it in the tray...i need to start it manually..i want the graphical stuff to run at startup[/QUOTE]

same issue but in kde

---

### Post by az on 2005-05-15
[QUOTE=glandula]hi again

yes it seems firestarter is running by default. but i dont see it in the tray...i need to start it manually..i want the graphical stuff to run at startup[/QUOTE]

Go to Sytem>Preferences>Sessions click on Statup Programs.

There must be somthing similar in KDE...

---

### Post by dresnu on 2005-05-17
found the solution here: [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by pavel_kbc on 2006-11-28
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

doesnt works for me :(

---

### Post by antidrugue on 2006-12-10
> **pavel_kbc said:**
> [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

doesnt works for me :(

Make sure the line in your **/etc/sudoers** file looks like that :
```

%admin ALL= NOPASSWD: /usr/sbin/firestarter

```

So **/usr/sbin/firestarter** not **/usr/bin/firestarter**.

---

### Post by candtalan on 2007-05-08
> **glandula said:**
> hi again

yes it seems firestarter is running by default. but i dont see it in the tray...i need to start it manually..i want the graphical stuff to run at startup

I thought firestarter began automatically at boot up by default, and the tray icon is configured within the options in firestarter itself (not absolutely sure)? 

To see if firestarter is running ther is a wayto check the status, but I cannot recall it just now.

hth

---

### Post by sayid01 on 2007-05-08
i added firestarter to the sessions thing and it starts up when i log into ubuntu. is there anyway to make it open minimized and not have to enter the root pwd all the time?

---

### Post by bw44 on 2007-12-11
> **antidrugue said:**
> Make sure the line in your **/etc/sudoers** file looks like that :
```

%admin ALL= NOPASSWD: /usr/sbin/firestarter

```

So **/usr/sbin/firestarter** not **/usr/bin/firestarter**.

Guess I'm resurrecting an old thread, but I still can't get firestarter to launch at system startup. When I launch it manually it appears on my desktop and allows me to interact and start it.  But it doesn't appear in the list of running processes in the System Monitor, and it doesn't appear in the system tray when minimized. (I have alltray installed if that makes a difference.)

I added firestarter to the Sessions with the command ```
sudo firestarter --start-hidden
```but I don't seem to have a /etc/sudoers file.  Do I need to create one and add the line you suggest?

I checked out the  [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon) page and it still seems to be saying what you've suggested (except %admin is username).

Can anyone help? :confused:

---

### Post by discoade on 2007-12-11
why run firestarter as startup? its not your firewall!

---

### Post by bw44 on 2007-12-11
> **discoade said:**
> why run firestarter as startup? its not your firewall!

Uh oh!  Time to reveal my ignorance:  what is my Ubuntu firewall and how do I talk to it?

Thanks.

---

### Post by bodhi.zazen on 2007-12-11
> **discoade said:**
> why run firestarter as startup? its not your firewall!

+1

Your firewall is iptables.

Firestarter is both a configuration tool and network monitor. The problem is that it runs as root and is a security risk.

So you should run firestarter to configure you firewall (iptables) and then close it. Your configuration will be active an active on re-boot even with firestarter closed.

As background for security, see here :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

There are some links to IP Tables. Otherwise :

[http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/security-guide/s1-fireall-ipt-act.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/security-guide/s1-fireall-ipt-act.html)

[https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html](https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html)

Those links are written for Red Hat, but the apply to most any distro. They are introductory but a good starting place.

---

### Post by bcom on 2007-12-11
Quote; Uh oh!  Time to reveal my ignorance:  what is my Ubuntu firewall and how do I talk to it?

As stated, the firewall in Ubuntu is based on iptables.  Firestarter is a graphical front-end you can use to configure the iptables.  

If you are concerned about security, here is a quote from the book Ubuntu Unleashed that might set your mind at ease

"Ubuntu is unique among distros in that as default it does not listen on any network ports.  This means that it is pretty much secure.  However, you may have a requirement to open up ports for access by other local computers."

If you have such a requirement, you can use Firestarter.

---

### Post by bw44 on 2007-12-11
> **bcom said:**
> Quote; Uh oh!  Time to reveal my ignorance:  what is my Ubuntu firewall and how do I talk to it?

As stated, the firewall in Ubuntu is based on iptables.  Firestarter is a graphical front-end you can use to configure the iptables.  

If you are concerned about security, here is a quote from the book Ubuntu Unleashed that might set your mind at ease

"Ubuntu is unique among distros in that as default it does not listen on any network ports.  This means that it is pretty much secure.  However, you may have a requirement to open up ports for access by other local computers."

If you have such a requirement, you can use Firestarter.

Great reply -- thanks!  I didn't know Ubuntu was set up this way (so by default I don't have to know what iptables are!).  Since I don't have any local computer port requirements, I'll just leave firestarter installed (but not try to start it at boot time) in case I need it.

Cheers.

---

### Post by bw44 on 2007-12-11
> **bodhi.zazen said:**
> +1

Your firewall is iptables.

Firestarter is both a configuration tool and network monitor. The problem is that it runs as root and is a security risk.

So you should run firestarter to configure you firewall (iptables) and then close it. Your configuration will be active an active on re-boot even with firestarter closed.

As background for security, see here :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

There are some links to IP Tables. Otherwise :

[http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/security-guide/s1-fireall-ipt-act.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/security-guide/s1-fireall-ipt-act.html)

[https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html](https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html)

Those links are written for Red Hat, but the apply to most any distro. They are introductory but a good starting place.

Thanks for the info -- and the link to your intro to Ubuntu security thread! I'll leave firestarter installed and use it as you suggest -- when it's required.

---

### Post by discoade on 2007-12-11
spot on!!

---

