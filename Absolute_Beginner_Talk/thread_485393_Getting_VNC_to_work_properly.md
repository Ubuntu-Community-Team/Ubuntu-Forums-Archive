---
title: "Getting VNC to work properly"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by OneLinux on 2007-06-26
I have read and followed just abut everything online, I've even resorted to voodoo and scrifices but still I'm having some trouble with VNC. And VNC is the #1 thing I need to work for me to convert completely to Ubuntu.

I have setup remote desktop on my Ubuntu 7.04 and can connect locally (inside of my home LAN) to MachineName:0 with the password but it only pulls up a black screen with a mouse cursor. I've tried MachineName:1 but it does not even prompt me for a password. I need to connect to my computer from windows machines via the internet using RealVNC viewer.

I would truly appreciate a helping hand in getting over this last hurdle, and I can stop getting strange looks due to my altar in the front yard ;)

---

### Post by Smandola on 2007-06-26
I can't help you with the blank screen and the mouse cursor... you may need to resort to the Voodoo dolls for that one (very strange).  But I can help you with the access via internet using RealVNC.  I use Hamachi and then when I VNC back to my ubuntu server, I enter the ip from Hamachi (ie: 5.X.X.X with the :0) and then I VNC thru hamachi and to my ubuntu server.  Its slick... although I'm sure there are other methods, this one was one of the easier ones for me.  

Good luck with the blank screen, hopefully someone out here has experienced that before.

---

### Post by information_entropy on 2007-06-27
Try this:

System -> Administration -> Login Window -> General -> Default Session -> Gnome

Then reboot.

This worked for me on two machines that I connect to with VNC.

---

### Post by OneLinux on 2007-06-29
I hadn't restarted after I made the change to Gnome, so I followed your advice and now when I access MyMachine.dyndns.org:0 I do get my desktop from work... however that is all I get. I can move the pointer around but nothing responds to it when I click. I'm using RealVNC at work, could that be an issue? I'm almost there (the speed is much slower than connecting to my Windows box remotely via VNC with a noticeable delay, but I'll accept that if I can just have it respond to my clicks)

As always, any help is much appreciated.

---

### Post by OneLinux on 2007-06-29
OK, slight update:

I closed my VNC session and reopened it about an hour later and a window was up (my second hard drive wihch I had tried double clicking the first time). So it is responding, just glacially slow.

We're talking like 10-15 minutes for a window to appear. Can anyone offer any suggestions as far as settings on the Ubuntu side to set to increase the speed. I'm on a 100mbps connection at work and 864kbps down 160kbps up DSL connection at home.

Thanks!

---

### Post by eentonig on 2007-06-29
And what's your works connection to the internet?

Seriously, vnc over the internet is a pain. The only thin you can do, is limit as much option as possible.

Use 
- Colour level 'Very low (8 colours)
- Do not send your background image
- etc

---

### Post by OneLinux on 2007-06-29
Yes, you read it right... 100mbps. I run one of the larger university networks in the US and it is summer so the avg. load going through the internet from campus right now is about 10mbps... leaving me about 90mbps :) So, no it wasn't a typo.

I have it set to all of those on the VNC side, I'm trying to figure out the optimal settings for the Ubuntu side. I have no trouble VNC'ing to my windows box at home and it is very fast. I can orbcast music/video from my windows box to work with no problem, so it isn't VNC that is the issue here.

Thanks

---

### Post by OneLinux on 2007-06-29
I have followed anything and everything online pertaining to VNC and Ubuntu, and while I can connect the screen does not update for some reason. If I click something (say a link on a page in Firefox which is already open when I VNC in) nothing at all happens. If I close VNC, and then reconnect, the link is open in Firefox.

So it is connecting, and accepting my input, but not updating the session. I have tried to manually refresh from the VNC viewer menu but it does nothing. If I close VNC and reopen, the screen is updated.

Anyone have any idea?

---

### Post by lazyart on 2007-06-29
This is a byproduct of desktop effects/beryl and vino, the included VNC server.

First, disable desktop sharing.
Next, install x11vnc-- ```
sudo apt-get install x11vnc
```
Now, launch it-- ```
x11vnc -noxdamage -forever
```

Now try connecting, using computername:0
If that doesnt work, try computername:1 (this would be the case if you didnt do step one)

If you like what you see, go to System>Preferences>Sessions and add that command as a startup program and its good.

---

### Post by Alterax on 2007-06-29
Tried X11VNC.
All I can say is WOW!  The old remote desktop was very slow, and did a poor job of rendering windows (usually I had to stab in the dark literally because some windows wouldn't present anything but a black box.

I'm definitely using this on my servers at work--once I figure out how to use a password with it. (Will post when I do)

--Alterax

---

### Post by lazyart on 2007-06-29
ah, for a password, append```
-passwd *password*
``` to the command and you're golden.

---

### Post by OneLinux on 2007-06-30
**lazyart**

You, sir, are the man! Absolutely 100% perfect. Simple, quick, and I'm posting this via VNC on my laptop into Firefox on my Ubuntu box!

Now, instead of all of these half-working options posted all over these forums and the net, this should just be the defacto standard method of running a VNC server on an Ubuntu box.

Thank You!

---

### Post by ubuntujonez on 2007-06-30
I've upgraded to Feisty and now after 2 years, via vnc, the keyboard isn't working properly. I use vncserver on a few headless machines. I ssh to the machine, and start the vncserver:

```
jonez@umberto:~/.vnc$ vncserver -depth 24 -geometry 1024x768

New 'X' desktop is umberto:1

Starting applications specified in /etc/X11/Xsession
Log file is /home/jonez/.vnc/umberto:1.log

```

... for example.

I can connect with ultraVNC with no problem and start a shell with no problem but, when I type: 
  qwerty
it comes out: 
 c.gvn

All the keys are jumbled. I've checked out the selected keyboard, the ultra vnc settings, re-installed the ubuntu-desktop package and the vncserver package. Everything else behaves just fine I just can't type anything!

It's very weird and I have no idea what to try next. Any help would be greatly appreciated.

-jonez

---

### Post by HermanAB on 2007-06-30
How about just using SSH without the VNC schtuff?

$ ssh -X -c blowfish-cbc [email]johndoe@server.com[/email]

Then run whatever program you want directly, for example:
$ gedit

You could even run a taskbar and launch stuff from the menu, for example 'gnome-panel' or the KDE 'kicker'.

I find VNC to be more limiting than enabling.

Cheers,

H.

---

### Post by ubuntujonez on 2007-06-30
Hi Herman,

Thanks for the advice. It does work but I'm more interested in getting the keyboard via vnc to become sane again. I frequently start long running jobs and disconnect the remote desktop and come back later, etc, like how one would use screen, especially when I take the laptop to a meeting, etc. 

-jonez

---

### Post by expatCM on 2007-06-30
There is a podcast discussing this in detail.

Have a look on this site 
[http://www.linuxreality.com/](http://www.linuxreality.com/)
for episode #51

---

### Post by ubuntujonez on 2007-07-03
fyi,

After reinstalling from scratch (7.04 server) and installing the ubuntu-desktop package, same thing... can vnc in fine, but the keyboard does not work (works on the console and via ssh, but not vnc), so it wansn't a corrupted keyboard file or whatnot. Oh, and then after rebooting, the ascii console was gone and the GDM was completely hosed. 

So, I had to install from scratch AGAIN, this time I installed 7.04 desktop. It works now, after installing all the server packages manually and using x11vnc and stuck with a resolution that I'm not happy with. I've lost 2 days of work, maybe I'll reconfigure again when I have some time. 

-jonez

---

