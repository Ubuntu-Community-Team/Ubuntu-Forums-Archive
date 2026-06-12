---
title: "VNC on display:0 without X?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by sambront on 2007-10-20
Hi

I'm using Ubuntu 7.10. I've disabled gdm, so I just login to a command line. If I want to start X, I just type "startx", and I'm in the full blown install, everything looks nice.

What I'd like to do is get that same screen remotely with vnc, without starting X. I've installed vnc4server, and start that. When I connect to that using vncviewer I get a grey screen with a terminal window. It doesn't look nice. I can start application from the command line, but they don't look right.

Is there a way to get to the "nice looking" desktop (display:0) without starting X?

Also, on a side note, is there any difference between vnc4server, tightvncserver, etc?

Thanks.

---

### Post by sambront on 2007-10-21
bump

---

### Post by lazyart on 2007-10-21
you want to use the terminal from another machine?  SSH?

---

### Post by sambront on 2007-10-21
What I want to do is start the ubuntu up on a machine, just in command line mode (I disabled gdm).

Then I want to be able to connect to that via VNC and have a desktop that looks like it would if I typed "startx".

As is stands when I connect via VNC (I'm running vnc4server), I get a grey screen.

Thanks.

---

### Post by lazyart on 2007-10-21
Maybe this [thread]("http://www.linuxquestions.org/questions/ubuntu-63/vnc4server-on-ubuntu-458240/") will help?

---

### Post by kvonb on 2007-10-21
sudo apt-get install vnc4server

and have a look at the man page that comes with it.

Sorry for brief, in a hurry! :)

---

### Post by sambront on 2007-10-22
Thanks for the responses.

I've installed vnc4server (and in the past, "tightvncserver", "vncserver", etc).

When I start ubuntu (in VMWare Player), since I've disabled gdm, it goes to a command line. I then type "vnc4server -geometry 800x600 -depth 16", and the vncserver starts fine. Then I go to another machine and connect, and that works.

But what I get is a grey screen with a terminal window, and a big black "X" as a cursor. I can start stuff like Firefox by typing "firefox" in the command window, but I can't resize or move applications. It doesn't look like the desktop that "startx" looks like.

When I type "startx" and start ubuntu, and then enable the remote desktop stuff (vino, I guess), I can connect to display:0 and everything looks fine. But then I have the full-fledged ubuntu running anyway, and I want to avoid that so I can run lean and mean.





> **kvonb said:**
> sudo apt-get install vnc4server

and have a look at the man page that comes with it.

Sorry for brief, in a hurry! :)

---

### Post by kvonb on 2007-10-23
ah, gotcha :)

you will have to install a desktop manager on your "server" system.


```
sudo apt-get install ubuntu-desktop
``` or kde-desktop or xfce-desktop

that will give you a full blown ubuntu system, but also installs all the bloat as well.

Have a look in the vnc4server config file, you can set it to serve the x:0 display (if that is what you want).  That will allow you to start progs and keep them running when you disconnect.

A better way to do it (if you are using a Linux client), is to use ssh instead of vnc (which is very slow and resource hungry).

Install open-ssh server on your server, then connect to your server with ssh from your client (ssh -X ip.of.your.server) and simply run any x command from there.  

It is really cool and fast, but all progs will stop when you disconnect.

Was there anything specific you were wanting to do?  That might help people suggest other suggestions :)

---

### Post by sambront on 2007-10-23
I've actually installed the full-blown Ubuntu 7.10 install, I just disabled gdm by doing "update-rc.d gdm remove" (or whatever the syntx is) so that now when I start the VM (I'm using VMware Player) it starts, and just sits at a command console that I can login to.

What I want to do is login via the command line...so it's just text, no GUI...but I want to be able to use VNC (or something like that) and get to a nice looking desktop (as if I had started X).

I've installed vnc4server, and when I connect (I'm using :1) I get a grey screen with a terminal window and a big black "X" as a cursor. Not pretty.

Also, I'm not quite clear on how to do this with SSH. I've installed OpenSSH, and I think I've configured it correctly, but when I ssh into the machine (from Windows), and type "firefox" (for example), it says "Cannot open display", or some  such thing.



> **kvonb said:**
> ah, gotcha :)

you will have to install a desktop manager on your "server" system.


```
sudo apt-get install ubuntu-desktop
``` or kde-desktop or xfce-desktop

that will give you a full blown ubuntu system, but also installs all the bloat as well.

Have a look in the vnc4server config file, you can set it to serve the x:0 display (if that is what you want).  That will allow you to start progs and keep them running when you disconnect.

A better way to do it (if you are using a Linux client), is to use ssh instead of vnc (which is very slow and resource hungry).

Install open-ssh server on your server, then connect to your server with ssh from your client (ssh -X ip.of.your.server) and simply run any x command from there.  

It is really cool and fast, but all progs will stop when you disconnect.

Was there anything specific you were wanting to do?  That might help people suggest other suggestions :)

---

### Post by kvonb on 2007-10-24
So you are running 7.10 as a VM on your Windows machine?  Or did I get that wrong?

The ssh method will not work from a Windows desktop because it needs all the Linux libraries in order to render a window, hence the "no display" message.

However, you can do it (as I do) by downloading and installing a neat piece of software called "Xmanager2" by Netsarang.

[www.netsarang.com](www.netsarang.com)

It is trialware, but works after the 30 days, you just have to ignore the registration thing.  The only downside is that you only get a 1 hour session (I believe), after that it disconnects and you have to start it again.

Of course if you were the unscrupulous type (I'm sure you're not) you would find a way around the limits ;).

You simply create a new "launcher" and put the linux command you want, I use "nautilus --no-desktop" for file management, you might simply want "firefox".  You make a new "shortcut" for each Linux prog you want to run.  But just about everything should work, I've even burnt CDs that way by using k3b remotely :).

The problem with the grey screen might be because the default window manager was removed (well the line in the config file which I can't remember which one it is at the mo'!) when you removed gdm.

I would reinstall gdm, then if it works properly again, simply open a terminal and type this:

```
sudo mv /etc/init.d/gdm /root/

```
That will stop gdm starting without removing it or anything else.  You should then be able to simply type:

```
startx
```

to start X :).

Reverse that command if you ever want gdm back again.

---

### Post by sambront on 2007-10-24
That's correct, I am running 7.10 in VMWare Player on my XP laptop.

I'll try XManager2, thanks.

Also, I didn't remove gdm, I just used "update-rc.d" to stop it from loading. Now when I start the VM, I am dumped to a command line. If I type "startx", the desktop starts as expected.

Again, thanks for the help.





> **kvonb said:**
> So you are running 7.10 as a VM on your Windows machine?  Or did I get that wrong?

The ssh method will not work from a Windows desktop because it needs all the Linux libraries in order to render a window, hence the "no display" message.

However, you can do it (as I do) by downloading and installing a neat piece of software called "Xmanager2" by Netsarang.

[www.netsarang.com](www.netsarang.com)

It is trialware, but works after the 30 days, you just have to ignore the registration thing.  The only downside is that you only get a 1 hour session (I believe), after that it disconnects and you have to start it again.

Of course if you were the unscrupulous type (I'm sure you're not) you would find a way around the limits ;).

You simply create a new "launcher" and put the linux command you want, I use "nautilus --no-desktop" for file management, you might simply want "firefox".  You make a new "shortcut" for each Linux prog you want to run.  But just about everything should work, I've even burnt CDs that way by using k3b remotely :).

The problem with the grey screen might be because the default window manager was removed (well the line in the config file which I can't remember which one it is at the mo'!) when you removed gdm.

I would reinstall gdm, then if it works properly again, simply open a terminal and type this:

```
sudo mv /etc/init.d/gdm /root/

```
That will stop gdm starting without removing it or anything else.  You should then be able to simply type:

```
startx
```

to start X :).

Reverse that command if you ever want gdm back again.

---

### Post by sambront on 2007-10-27
So I figured out how to do this.

I looked at your advice concerning XManager, and downloaded it, but before I installed I decided to look for a free alternative. I found Cgywin/X. I've downloaded Cygwin before, but never used it. This time I did, and everything is working perfectly.

For future reference, this is what I did.

Assuming that a VM of Ubuntu is already running in something like VMPlayer.

1. Install OpenSSH in Ubuntu

2. Remove gdm from Ubuntu ("sudo update-rc.d gdm remove")

    Now Ubuntu will start at the command-line.

    You can still type "startx" to start the GUI. I used the GUI to install whatever programs I wanted.

3. Installed Cygwin.

    There is a section that is not installed by default that you need to install under the "X11" section
    that is called "xorg-x11-base". This is Cygwin/X. Install it.

4. Once that is done, run the file called "cygwin\usr\X11R6\bin\startwin.bat"

5. That opens a command window. You'll need to SSH to the machine. This is the command I use:

    SSH -Y -2 user@server

    You'll need to enter the password, and then you'll be in the server.

6. From there, type whatever application you want. I type "eclipse", and the eclipse editor starts.


Pretty cool.







> **kvonb said:**
> So you are running 7.10 as a VM on your Windows machine?  Or did I get that wrong?

The ssh method will not work from a Windows desktop because it needs all the Linux libraries in order to render a window, hence the "no display" message.

However, you can do it (as I do) by downloading and installing a neat piece of software called "Xmanager2" by Netsarang.

[www.netsarang.com](www.netsarang.com)

It is trialware, but works after the 30 days, you just have to ignore the registration thing.  The only downside is that you only get a 1 hour session (I believe), after that it disconnects and you have to start it again.

Of course if you were the unscrupulous type (I'm sure you're not) you would find a way around the limits ;).

You simply create a new "launcher" and put the linux command you want, I use "nautilus --no-desktop" for file management, you might simply want "firefox".  You make a new "shortcut" for each Linux prog you want to run.  But just about everything should work, I've even burnt CDs that way by using k3b remotely :).

The problem with the grey screen might be because the default window manager was removed (well the line in the config file which I can't remember which one it is at the mo'!) when you removed gdm.

I would reinstall gdm, then if it works properly again, simply open a terminal and type this:

```
sudo mv /etc/init.d/gdm /root/

```
That will stop gdm starting without removing it or anything else.  You should then be able to simply type:

```
startx
```

to start X :).

Reverse that command if you ever want gdm back again.

---

### Post by kvonb on 2007-10-27
Good to hear you got it working :).

I tried cygwinX, but couldn't figure it out so I went with Xmanager instead.  I rarely use it anyway, so no big deal for me.

---

### Post by sambront on 2007-10-28
Same with me, too confusing in the past.

This wasn't too bad, just because I'm using it for one thing.

> **kvonb said:**
> Good to hear you got it working :).

I tried cygwinX, but couldn't figure it out so I went with Xmanager instead.  I rarely use it anyway, so no big deal for me.

---

