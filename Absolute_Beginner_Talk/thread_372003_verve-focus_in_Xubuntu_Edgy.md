---
title: "verve-focus in Xubuntu Edgy?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by El Jamo on 2007-02-27
Running xubuntu edgy on my IBM r51 laptop.  I would like to bind a key combination to automatically focus on the Verve Command Line in my panel.  The [verve-plugin page at xfce goodies]("http://goodies.xfce.org/projects/panel-plugins/verve-plugin") tells me that I should have a binary named verve-focus that I can use for this, but I don't.  I'm wondering if there's any way to do this.

thanks for any help.

---

### Post by x1a4 on 2007-02-28
Try reinstalling the plugin 

*sudo apt-get --reinstall install xfce4-verve-plugin*

*verve-focus* is in that package.  It will be installed in /usr/bin/

---

### Post by El Jamo on 2007-02-28
Thank you very much for your response.  Here's what I tried, and the output:

```
james@james:~$ sudo apt-get --reinstall install xfce4-verve-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0B/14.7kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 91265 files and directories currently installed.)
Preparing to replace xfce4-verve-plugin 0.2.0-0ubuntu3 (using .../xfce4-verve-plugin_0.2.0-0ubuntu3_i386.deb) ...
Unpacking replacement xfce4-verve-plugin ...
Setting up xfce4-verve-plugin (0.2.0-0ubuntu3) ...
```

So that seemed to go fine.  However, I can't find verve-focus in /usr/bin, and here's what happens when I enter it into the command line:

```
james@james:~$ verve-focus
bash: verve-focus: command not found
```

Should I tell it to look for some specific newer package?

Thanks for any help.

---

### Post by x1a4 on 2007-02-28
I just reinstalled the Verve plugin and everything worked fine.  I then purged it, then installed it.  Again no problems.  I suspect you have a problem with your repositories.  

Can you please post the contents of your */etc/apt/sources.list* file?  And while you're at it the output of *ls /usr/bin/*verve* /bin/*verve**

---

### Post by El Jamo on 2007-03-01
Here's my sources.list file:

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

## Picked this up from http://www.debianadmin.com/install-mplayer-ubuntu.html, in an
## attempt to install mplayer.  We'll see how it goes.
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse
```

And here's the output of *ls /usr/bin/*verve* /bin/*verve**

```
james@james:~$ ls /usr/bin/*verve* /bin/*verve*
ls: /usr/bin/*verve*: No such file or directory
ls: /bin/*verve*: No such file or directory
```

In a related question, if I purge xfce4-verve-plugin, it also wants to get rid of xubuntu-desktop.  Should I allow it to do this?

Thank you for your help.

---

### Post by x1a4 on 2007-03-02
Hi,

There are issues with the internationalized repositories, just download from the main server.  

In Synaptic: 

Settings -> Repositories -> 'Download from:' drop-down list change to 'Main server'

Or, as the super user open _/etc/apt/sources.list_ and delete **us.** from the URLs

For example 

deb [http://**us](http://**us).**archive.ubuntu.com/ubuntu/ edgy main restricted

would become

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

Once that is done, update package information.  In Synaptic just hit the 'Reload' button, 
or *sudo apt-get update* from a terminal or console.  

Now reinstall the plugin

*sudo apt-get --reinstall install xfce4-verve-plugin*
(you can reinstall from Synaptic too if you prefer)


As to your other question.

**Do not** remove *xubuntu-desktop*.  If you do you'll remove Xfce and all Xubuntu/Xfce related utilities, themes, etc.

---

### Post by El Jamo on 2007-03-02
I removed **us.** from the beginning of all sources in */etc/apt/sources.list* that had it.

I then entered *sudo aptitude update*.  I wasn't sure if I should also use apt-get, so I also did *sudo apt-get update*.

Then I did *sudo apt-get --reinstall install xfce4-verve-plugin*.  Here's the output:

```
james@james:~$ sudo apt-get --reinstall install xfce4-verve-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded.
Need to get 0B/14.7kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 91265 files and directories currently installed.)
Preparing to replace xfce4-verve-plugin 0.2.0-0ubuntu3 (using .../xfce4-verve-plugin_0.2.0-0ubuntu3_i386.deb) ...
Unpacking replacement xfce4-verve-plugin ...
Setting up xfce4-verve-plugin (0.2.0-0ubuntu3) ...
```

Then I tried *verve-focus*:

```
james@james:~$ verve-focus
bash: verve-focus: command not found
```

Then I tried *ls /usr/bin/*verve* /bin/*verve**:

```
james@james:~$ ls /usr/bin/*verve* /bin/*verve*
ls: /usr/bin/*verve*: No such file or directory
ls: /bin/*verve*: No such file or directory
```

I don't know what is going on.  It's really odd to me.  I really appreciate all of your suggestions thus far.

Thank you.

---

### Post by x1a4 on 2007-03-02
I know what the problem is.  The version of the Verve plugin you're installing is an earlier version which doesn't have the *verve-focus* script.  I have 0.3.5 and yours is 0.2.0

Add these repositories: 

deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0 main
deb-src [http://ubuntu.tolero.org](http://ubuntu.tolero.org) edgy main

Update Xfce and all related tools (including Verve) and things should work.  

Sorry for not catching this sooner.

EDIT: If you don't want to add 3rd party repositories download Verve directly from the [Xfce Goodies](http://goodies.xfce.org/projects/panel-plugins/verve-plugin) site.

---

### Post by El Jamo on 2007-03-02
SUCCESS!

Excellent, after adding those sources and *sudo apt-get update*, followed by *sudo apt-get --reinstall install xfce4-verve-plugin*, it worked (after a reboot).  Just for archival purposes, here's the output it gave me:

```
james@james:~$ sudo apt-get --reinstall install xfce4-verve-plugin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded.
Need to get 0B/30.0kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  xfce4-verve-plugin
Install these packages without verification [y/N]? y
(Reading database ... 91333 files and directories currently installed.)
Preparing to replace xfce4-verve-plugin 0.3.5-0ubuntu1 (using .../xfce4-verve-plugin_0.3.5-0ubuntu1_i386.deb) ...
Unpacking replacement xfce4-verve-plugin ...
Setting up xfce4-verve-plugin (0.3.5-0ubuntu1) ...
```

(technically it looked slightly different at first, I just re-did it for demonstration purposes, and to note that verification warning it gives).  Just for good measure, I removed the verve-plugin that I had in my panel, and after a reboot I added it again, in case it had to be updated also or something.

Thank you very much for your help, and for your persistence.  I really appreciate it.

---

### Post by x1a4 on 2007-03-02
You're welcome.  Happy I could be of assistance.  I just wish I had been more observant, and  seen the version number in your first reply.  Hould have saved us both time and headaches.  

Goes to show you to pay close attention to what the computer is saying.  Usually, error messages and other output tells us more then we know.  More than once did I waste ridiculous amounts of time fixing an issue I could have solved in minutes if I had only paid closer attention to the error messages.  

Oh well, live and learn.

BTW Be sure to edit your original post and check the 'issue is resolved' checkbox.

---

### Post by x1a4 on 2007-03-02
> **El Jamo said:**
> 
*<snip>*

(after a reboot).

*<snip>*


Typically you don't need to reboot.  Although if you've updated an application you're running at the time of update it's good to restart it.  In the case of Xfce just hit Ctrl+Alt+Backspace, or you can open the console by pressing Ctrl+Alt+F1, login and run *sudo /etc/init.d/gdm restart*

---

