---
title: "Server install for Desktop-Users"
date: 2008-02-02
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-02
Can you load Ubuntu on a very low memory machine?  Is even Xubuntu too much of a tax on your resources?  Do you need to administer a server, and just need to bring up a xterm or two, do your administration, and then shutdown the x server?

Have you tried doing a server-install, and then adding very simple X components back in for a snappy little gui box anyway?  (looks pc-based but applies to PPC just as well)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

This was brought up in another thread, but thought I'd point this out here for better exposure for those that think their 64mb PPC boxes are worthless and don't want to upgrade the ram.

It can be a lot of fun to make the most of your limited-resource box and just might surprise you how nice doing it the "old school" way is.  I've done it a few times with Debian, but the next low-end ppc that comes my way is going Ubuntu-homebrew.  The docs above are pretty easy to follow.

---

### Post by stream303 on 2008-03-03
I thought I'd go into more detail about my minimal server install with just enough X to be a bit more pleasant.  I manually upgraded the server kernel to the Gutsy desktop kernel.  Here's how it went:

Downloaded the Feisty 7.04 server ppc here:

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

Since I'm running a G5, I opted for the "install-powerpc64" option after hitting tab at the boot: prompt.

Answered a few questions, and I declined to install the dns or lamp server packages - jut hit tab to continue to finish the install.

Update the packages:
```
sudo aptitude update
```

Upgrade the packages:
```
sudo aptitude upgrade
```

Install X:
```
sudo aptitude install xorg
```

Install the very minimalist window manager around:
```
sudo aptitude install twm
```

Create an **.xinitrc** file in my home directory ~/.xinitrc to bring up an xterm, color the background and start twm by adding these lines to the file:
```

xterm &
xsetroot -solid darkslateblue &
exec twm
```

Beef up security on ~/.xinitrc to make sure that only you (or root) can do anything with it:
```
chmod 700 ~/.xinitrc
```

To bring up X, just type
```
startx
```

If you envision using more graphical X programs and want to see the fonts and dialog boxes better, startx with a custom dpi:

```
startx -- -dpi 96
```

(If you haven't used twm before, click on the upper right corner of the window, and while holding it down, move it to the sides or the bottom right of the window to resize them.  I haven't gone too deeply into X, but this is a start.  Yes, you could use a better window manager like fluxbox, but sometimes it is just as easy to say get another xterminal by just typing:

```
xterm &
```

in the current terminal.  Unless you configure your program's font and geometry in .xinitrc, you can change the font size in xterm by just holding down CTRL, and then right-clicking the window.  I usually use the large or huge options.  How about running the desktop clock, xclock - just type this at the terminal:

```
xclock &
```

It could have just as easily been firefox & if you had that installed, and so on.)

Note: G3 owners are most likely going to have to edit **/etc/X11/xorg.conf** and change the horizontal freq to 58-62, and the vertical freq to 43-117.  In addition, you may have to disable DRI by #commenting it out if the system is unusably sluggish.  See [https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

I was feeling generous, so I thought I'd grab a text-based browser which doubles as a nifty simple file-manager too:  Either one is fine, although I like elinks

```
sudo aptitude install lynx
sudo aptitude install elinks
```

Using links or elinks is easy enough as a file browser; to just browse your current directory:

```
lynx .
```

This will limit you to just your files.  If you want to browse the whole machine, you'll have to specify a directory outside to start with such as:

```
lynx /usr/share/doc
```

I also have to have some way to look at my images from my cheap digital camera.  I like ImageMagick and how when you use lynx as a file browser, it is the default image program:

```
sudo aptitude install imagemagick
```

or just type *display* and it will bring up imagemagick all by itself.  *display my.jpg*  works just fine too!

Although performance is fine with the server kernel, I wanted to update to just the Gutsy kernel, and then back out since I'm not trying to reproduce gutsy.  I just want to use the latest kernel.  This is totally optional.

I tried doing an apt-get upgrade again, and saw that 3 kernel packages were held back.  No problem, since I didn't want to run the Feisty upgrade kernel, but the one from Gutsy.  Wrote down the held back kernel packages:

linux-image-powerpc64-smp
linux-powerpc64-smp
linux-restricted-modules-powerpc64-smp

Let's grab these from Gutsy:

Edit as root (ie sudo nano) **/etc/apt/sources.list** and add this line at the bottom:

**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  gutsy main restricted**
(note the space between /ubuntu/  and  gutsy)

Update the repository again:
```
sudo apt-get update
```

Grab the new gutsy kernel stuff by specifically telling it what I want.  I **don't** want a total upgrade at this point, just the kernel!)
```
sudo apt-get -y install linux-image-powerpc64-smp linux-powerpc64-smp linux-restricted-modules-powerpc64-smp
```

Once the kernels are downloaded and installed, let's put the original sources.list file back in shape and update it again so it forgets that we ever used the gutsy repo's:

In /etc/apt/sources.list, comment out that line we used earlier:
[B]
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  gutsy main restricted[/B]

And again do an update to remind it that there isn't any gutsy:
```
sudo apt-get update
```

reboot, and you should find yourself with a 2.6.22-14 kernel as of this writing.

I more or less stopped it here by just getting X going with an xterm, and adding a few cli-based utilities.  I did try adding in Firefox since I have the ram and cpu speed, but at that point, why build up an Ubuntu system that could more easily be done with a regular install.  Maybe this will help someone with 64mb or even less get something up and running, although you'll be using the commandline a lot.  If you have a printer, top it off with a cupsys install (see other printing posts) and you're all set.

Fonts don't have to look bad either - just say NO when it comes to using bitmapped fonts:

```
sudo dpkg-reconfigure fontconfig-config
```

---

