---
title: "jollyFastVNC doesn't refresh the screen. [remote desktop]"
date: 2009-08-30
forum: Apple Hardware Users
---

### Post by chenjin824 on 2009-08-30
Hi All,

I had this problem for a while and did some research but no luck...

Here is the thing: I want to remotely control my desktop (Ubuntu 9.04) with my MBP running a JollyFastVNC client. X11VNC is running on the Ubuntu machine. I followed the method from here:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

> Setting up x11vnc

   1. Install x11vnc: sudo apt-get install x11vnc
   2. Set the password: vncpasswd ~/.vnc/passwd (vncpasswd is included with vnc-common, which is installed by default)
   3. Make it auto-start when the user logs in and show which port we're running on (useful if you run multiple vnc servers) the port will be put in ~/.vnc/port.txt:
         1. sudo gedit /usr/local/bin/sharex11vnc Paste in the following:
            Code:

            #!/bin/sh

            x11vnc -nap -bg -many -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}"|grep -Eo "[0-9]{4}">~/.vnc/port.txt

            # comment out the following if you don't want a popup telling you which port you're using.
            zenity --info --text="Your VNC port is `cat ~/.vnc/port.txt`"

         2. sudo chmod 755 /usr/local/bin/sharex11vnc
         3. System->Preferences->Sessions->Startup Programs then click Add and type in sharex11vnc

The problem is that when I connect to the Ubuntu desktop using JollyFastVNC, I was able to see the whole GNOME desktop and the color seems fine. But what ever I did after that, I can't see the screen refreshing on my vnc client. However, I saw all the mouse moving and key stroking on my Ubuntu machine's screen. 

This means I've connected to the Ubuntu machine and my vnc client didn't refresh. I also tried chicken of VNC, no luck.

I tried vnc4server/tightvncserver/ instead of x11vnc from Synaptic Manager, still no luck.

Anybody could help? Thanks a lot!

-Jin

---

### Post by krunge on 2009-08-30
> **chenjin824 said:**
> 
The problem is that when I connect to the Ubuntu desktop using JollyFastVNC, I was able to see the whole GNOME desktop and the color seems fine. But what ever I did after that, I can't see the screen refreshing on my vnc client. However, I saw all the mouse moving and key stroking on my Ubuntu machine's screen. 

Did you try any other VNC Viewers besides JFVNC?

My guess is the same issue would happen with any VNC Viewer and you are seeing is the XDAMAGE bug problem:

[INDENT][http://ubuntuforums.org/showthread.php?t=1097683](http://ubuntuforums.org/showthread.php?t=1097683)[/INDENT]

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-beryl](http://www.karlrunge.com/x11vnc/faq.html#faq-beryl)[/INDENT]

The workaround is to use the x11vnc "-noxdamage" option to avoid the Xorg/compiz XDAMAGE bug:```
x11vnc -noxdamage ...
```or to disable compiz.


BTW, JFVNC may still have a bug where it 'sprays' x11vnc with too many requests per second. If things still seem sluggish when connecting with JFVNC, try adding one of these to x11vnc's command line:
```
-defer 5 -wait 5 -nonap
```
OR
```
-allinput
``` If you see this latter problem, please report how the above workarounds do.

---

### Post by chenjin824 on 2009-08-30
Hi Krunge,

Thanks for ur quick reply!

I actually tried Chicken of VNC also, but no luck on that.

I just tried your workaround to add -noxdamage into the script file "sharex11vnc" and logged out and logged in. The problem is the same--no screen "refreshing" after I connected to the remote desktop. The same things as using Chicken of VNC.

What could be the reasons? Thank you!

---

### Post by krunge on 2009-08-31
> **chenjin824 said:**
> 
I just tried your workaround to add -noxdamage into the script file "sharex11vnc" and logged out and logged in. The problem is the same--no screen "refreshing" after I connected to the remote desktop. The same things as using Chicken of VNC.

Did you verify that you restarted the x11vnc process? Changing the line in the script might not be enough. You can use "ps wwwwwwaux | grep x11vnc" to see it running and to look if it has "-noxdamage" on its command line.

Completely exiting your X desktop session should be enough, but it is not clear that is what you mean by "logged out" (maybe you meant the VNC session.)  Rebooting the linux machine would definitely make sure the x11vnc process is restarted.

---

### Post by chenjin824 on 2009-08-31
Wonderful! It works now after reboot the machine! 
Thanks to Krunge!

The only thing is that it's still kind of sluggish, so I will make the changes as you suggested to see if it improves. 

Will post the results in no time! BTW, how to setup x11vnc so that I could have larger screen display on my vnc client? 

Thanks!

---

### Post by krunge on 2009-08-31
> **chenjin824 said:**
> 
The only thing is that it's still kind of sluggish, so I will make the changes as you suggested to see if it improves. 

Thanks, let me know how that goes for you (it has been a long time since I used JFVNC.)  Instead of '5' for the -defer and -wait you can use smaller values too, e.g. 1. The JFVNC guy, predictably, said he uses 0.  I assume that will peg the CPU usage by x11vnc at 100%...
> BTW, how to setup x11vnc so that I could have larger screen display on my vnc client? Maybe the -scale option:
[INDENT][http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-scale](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-scale)[/INDENT]

---

### Post by chenjin824 on 2009-08-31
Hi Krunge,

I've tried JFVNC at home and I didn't observe any speed improvement by modifying the -defer and -wait options. The overall time lag is still big enough to be annoying, is there anything I could do to get more responsive connection?

I'm a mac user and hope to get a solution for remote Ubuntu desktop. I know it's another story...:)

Thanks once again!

---

### Post by v_2ryann on 2010-07-30
> **chenjin824 said:**
> Hi All,

I had this problem for a while and did some research but no luck...

Here is the thing: I want to remotely control my desktop (Ubuntu 9.04) with my MBP running a JollyFastVNC client. X11VNC is running on the Ubuntu machine. I followed the method from here:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)



The problem is that when I connect to the Ubuntu desktop using JollyFastVNC, I was able to see the whole GNOME desktop and the color seems fine. But what ever I did after that, I can't see the screen refreshing on my vnc client. However, I saw all the mouse moving and key stroking on my Ubuntu machine's screen. 

This means I've connected to the Ubuntu machine and my vnc client didn't refresh. I also tried chicken of VNC, no luck.

I tried vnc4server/tightvncserver/ instead of x11vnc from Synaptic Manager, still no luck.

Anybody could help? Thanks a lot!

-Jin

Here is the answer to the refresh problem, on how to do it without changing the effects:

1) Open a terminal o press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I found it found here:
[http://swiss.ubuntuforums.org/showthread.php?t=1496368](http://swiss.ubuntuforums.org/showthread.php?t=1496368)

---

### Post by worm91 on 2011-05-31
> **v_2ryann said:**
> Here is the answer to the refresh problem, on how to do it without changing the effects:

1) Open a terminal o press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I found it found here:
[http://swiss.ubuntuforums.org/showthread.php?t=1496368](http://swiss.ubuntuforums.org/showthread.php?t=1496368)

Thanks for that it works perfect for me with thightvnc

---

### Post by arnab_das on 2011-12-16
this helped me out today! thanks a ton

---

