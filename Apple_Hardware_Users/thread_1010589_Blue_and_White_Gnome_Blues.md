---
title: "Blue and White Gnome Blues"
date: 2008-12-13
forum: Apple Hardware Users
---

### Post by BeyondThePale on 2008-12-13
Hi folks. I am a beginner but am enjoying the challenge of learning and experimenting with ubuntu installations on older macs.

I have a Blue and White G3 tower that I wish to make a LAMP server out of. I have gotten 8.10 installed several times. I can SSH in to the server, everything seems cool.

My problem is I am a visual guy. I work with GUI's better than command lines. I install gnome on the G3 and when I reboot, the video just dies. The monitor is getting no signal at all. This has happened after 3 tries. I would try xubuntu, but IIRC it does not come with the remote client installed.

I want to put this network storage and utility machine in a corner and access it remotely. What's the best way to get the GUI on this box? Thanks.

---

### Post by stream303 on 2008-12-14
Nice!  I'm assuming you are installing the "server" version, which leaves you at just the commandline.  This is actually good, since you'll be running the server-tuned kernel, but you want to put some X on it.  The "server" images make setting up a LAMP environment easy with a simple checkbox during install.

You may have picked them up from here:

[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

Some might suggest falling back to 8.04 for the possibility of longer updates with the LTS version (although with ppc, there are no guarantees anyway)

Although these docs target low-memory users on Intel, they are GREAT docs for doing exactly what you want to do with your server for ppc:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

In your case, you are already running the server so you are half-way home.  All you need to do now is add the X components, and a window manager.  Everyone has their favorite, and mine lately is IceWM.  For server use, I see no need for a login manager such as xdm or gdm, but you can add those if you want to.  They are all just an apt-get away.

However, you may still be facing some common /etc/X11/xorg.conf issues, which you'll have to manually edit.

For the B&W, you'll need to know what your external monitors vertical and horizontal frequencies are, and it's native resolution if using an lcd.  Here is a recent response to another b&w user that might help:

[http://ubuntuforums.org/showthread.php?t=1010570](http://ubuntuforums.org/showthread.php?t=1010570)

and be sure to see the wikis since you'll probably have to edit in your video driver as well:

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

Hope this helps.  If things get too frustrating, I can also recommend Debian 4.0r5 as a server with a gui if it comes to that.  Grab the XFCE4 Cd-1 for powerpc and during install you'll also see the options for a server.  Doing what you want to do is very easy with Debian, and any reconfiguring of the X server for your monitor is also easy since it uses the older classical X server configurations.

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

Wow, sorry if this was info-overload. :)

---

### Post by BeyondThePale on 2008-12-14
This sounds great in principle, but does the xorg file get created or used before the install of gnome? If I lose video access immediately after install of gnome, I don't know how I would get to the file to edit it.

---

### Post by stream303 on 2008-12-14
There are a few ways to get to the file.

Try going to a virtual terminal with ctrl-alt-f2.  Then login, and do

```
sudo nano /etc/X11/xorg.conf
```

ctrl-o to write, ctrl-x to exit.  In some cases, the screen is so locked up this might not work.

Although you can't get to a gui now, some can at a funky resolution temorarily - they can

```
gksudo gedit /etc/X11/xorg.conf
```

assuming they are running ubuntu.

The other way is to edit the file with vi after going in with "rescue" mode, aka "Linux single", which you start at the second-stage boot: prompt.

---

### Post by BeyondThePale on 2009-01-04
Thanks for the assist. I finally got a GUI working by searching the links you provided. It was low-res, but enough for me to see there was really no purpose for it in my usage.

---

