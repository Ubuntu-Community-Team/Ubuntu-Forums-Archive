---
title: "Edubuntu Feisty ltsp/x11vnc help needed"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by stormchas3r on 2007-04-10
Hello all.

I am trying to get this edubuntu server up and running to show "the bob's" at my work.  I am having issues with x11vnc on the client side. I have successfully istalled X11vnc on the client side of the server. I have searched everywhere including irc for the answers but cannot find them.  So that's why I am here.  


I just want to be able to view the desktops from the Thin Client Manager.

Any help is greatly appreciated.

TY

---

### Post by ipguru99 on 2007-04-10
Same problem, but you just saved me the hassle of downloading ed instead of x ;-)

I really don't want to use edubuntu, but love the fact that xubuntu gives me the same option of installing an ltsp.  So I used Feisty Xubuntu last night in a test.  Everything worked great (sending messages, etc., etc.).  But the page that lets you view the users desktop didn't work and i got that error that says, "install x11vnc on the client".  I did (I think).  And I still get the same message.

At least to help me clarify, did you 'sudo chroot /opt/ltsp/i386', then 'apt-get install x11vnc' ?  That is what I think of when they say, ".. on the client".  I did it on the server as well.  Made sure to reboot the client.. then the server.  Still no change.

I went to look this error up before I downloaded ed tonight.. glad I did.

I hope this is just a 'beta' issue, or that I am doing it wrong, because with this and [ http://www.cendio.com/seamlessrdp/]("http://www.cendio.com/seamlessrdp/"), I can say goodbye to citrix!! 

I will subscribe to this thread, but if you get this working, send a shout out to my email, please.

---

### Post by stormchas3r on 2007-04-11
Yes I installed it the same way as you described.  I hope its a beta issue too.  I will definitely let you know if I get it working.  I hope you will do the same.

---

### Post by obiyoda on 2007-04-12
I am also trying to figure this out. Some how from what I have understood from reading the documentation the x11vnc client needs to be started at boot time in the chroot environment. I just don't know how to get the service to start. Seems like [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/) has some good information. I just haven't had time to look at it and figure it out.

---

### Post by stormchas3r on 2007-04-13
I was told by the developers that there will be a "How-To" create for the users after release.  Only 6 more days...........

Thanks for all the replies.

Rob

---

### Post by stormchas3r on 2007-04-17
Here it is boys, [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients)

Let me know if you have any issues.

---

### Post by ipguru99 on 2007-04-17
Thanks stormchas3r!

It is getting better!  I am able to actually see clients in the student-control-panel under 'Screen Viewer'.  

Issues I have (and I haven't updated Xubuntu yet.. so it could be anything)....

When I click on 'Share Screen' at the top, nothing happens.  

I am able to see that 'ltsp-client :6' is listening on port 5900, and from the server, if I try (for the hell of it) to 'vncviewer 192.168.0.70', it actually rolls through the setup of a screen, then it just dies.  Error is something about End of Stream... I didn't think that would work, but oh well.

If I log out of my terminal and log back in, 'Screen Viewer' shows that x11vnc isn't installed.  Reboot and everything works again.

And.. while typing this.. my 'student-control-panel' has crashed twice??  Just sitting there, it died.  It says "The program 'student-control-panel' received an XWindow System error.  This probably reflects a bug in the program.
The error was 'BadGC (invalid GC parameter)'
 (Details: serial 111794 error_code 13 request_code 60 minor_code 0)

Weird... but anyway, I like where all of this is headed!!  Anyone else do any better?  Edubuntu??

thanks!

---

### Post by krunge on 2007-04-18
> I am able to see that 'ltsp-client :6' is listening on port 5900, and from the server, if I try (for the hell of it) to 'vncviewer 192.168.0.70', it actually rolls through the setup of a screen, then it just dies. Error is something about End of Stream... I didn't think that would work, but oh well.

If I log out of my terminal and log back in, 'Screen Viewer' shows that x11vnc isn't installed. Reboot and everything works again.

Perhaps this is the KillInitClients problem discussed here? [http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

You see, the display manager (kdm, gdm, or xdm) can be (and often is) configured to kill all initial X clients (x11vnc is one of them) after the user logs in. One could just restart x11vnc and reconnect with the vncviewer, but that is a pain.

If you don't want to attempt the display manager workaround discussed at the above link, I suppose the command in the LTSP/x11vnc  Howto could be changed to:

```
x11vnc -display :6 -forever -loop &
```

Note the "&" and that "-bg" cannot be used.  -loop simply has x11vnc restart itself after it exits.  Version 0.8.1 is probably required for the -loop option.  Let me know if that works.

---

### Post by krunge on 2007-04-19
```
x11vnc -display :6 -forever -loop &
```

I forgot to mention you will still have to run the vncviewer a 2nd time if x11vnc is killed at login.
All the -loop does is restart x11vnc a second or two later.

---

### Post by Katchina on 2007-04-20
Hello,

I have the same x11vnc problem, and I'm happy to have found this thread.

Unfortunately, following the instructions in the howto is troublesome...

My thin client now does not properly starts the x11 environment, and after many minutes of wait finally falls back to text-mode display :
> 
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)


Can anybody help ?  I suppose I screwed up with one of the steps in the howto but I don't quite know which one, and don't know how to find out either.

Any help is appreciated.

---

### Post by ipguru99 on 2007-04-20
with the rc.local file (in the chroot) being:
x11vnc -display :6 -forever -loop &

The logout/log back in issue is resolved!! Thanks Karl!  I not only logged out and back in several times, but I was able to use the student control panel to kick people out and they could get back in and I could see their screen... so that is all working great.

Otherwise, all of the issues with 'student-control-panel' still exist.  I can't share the desktop (like Shadowing if you are coming from a Citrix environment).  I can't blank the screen.  Actually, all I can do is see the screen with Karl's wonderful x11vnc!!

Even the 'lockdown' stuff (plugins) doesn't work ( I can log out when I have marked 'no logout')??  Does anyone know if I should start a new thread on the student control panel thing?  Or does anyone else have this thing doing anything more in Edubuntu?  I updated my Xubuntu and the chroot as well, and rebooted... so everything should be up to date.

thanks!

---

### Post by krunge on 2007-04-21
> Otherwise, all of the issues with 'student-control-panel' still exist. I can't share the desktop (like Shadowing if you are coming from a Citrix environment). I can't blank the screen

I have never used LTSP (although I've spoken with the developers and they are good folk), but
in general with x11vnc if you want to share the desktop you need to add the "-shared" option
to the x11vnc cmdline.  Then multiple VNC viewers can view it at the same time.  Not sure if that
is what you meant by "share the desktop", but it could be useful info in any event.

Blanking the physical screen while still viewing it remotely may be difficult on Linux/Xorg.  Not sure.

---

### Post by ipguru99 on 2007-04-22
-shared worked!!  In the 'Screen Viewer', it shows a very small version of the users screen.  I can't click on the 'Share Screen' box, but I can open up vncviewer and see the desktop!!  Thanks Karl!  I was able to go in and then close it.. go back in, close it.. Works great!  In case admins are reading.. You can use vncviewer without your users knowing!!  I was not able to detect a screen flicker or anything!  Hate to be that way, but some people require that kind of attention.

The blanking of the screen would be nice, but for me (not in a classroom) it isn't a big deal.

My biggest issue is now the lockdown of the thing.  I am going to try Edubuntu and see if any of this stuff works.  Nobody else tried it yet?

Thanks again Karl.  I have read through your page (nice detail and examples.. always a plus!) and I have decided that I will be spreading the x11vnc love from now on!

If anyone else finds out how to get plugins (lockdown specifically) to work, please let me know.

Thanks,

ipguru99

---

### Post by chrisblessing on 2007-04-23
Greetings - I followed these instructions but get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x11vnc

Thanks

---

### Post by ipguru99 on 2007-04-23
Just running through my checklist before I answer, but have you moved your /etc/apt/sources.list to the /opt/ltsp/i386/etc/apt/sources.list ?  Just the first thing that came to my mind that might let you start the install process of a package, then say that the package isn't there.

---

### Post by gnosys on 2007-05-15
Even I've read all the posts and tried all the solutions I've not been able to run x11vnc on the client..I'm not using ubunt DHCP3 service because I have a proxy on my network, so I've configured it to run the service..I can install x11vnc on the server, and on the client..but i can't run the service on the client..

---

### Post by ipguru99 on 2007-05-15
I just replicated this whole thing on Edubuntu (the features all work in Ed.. but not so much in X??).  The three things I now have written down are:

1.  Make sure you install x11vnc in the chroot (sudo chroot /opt/ltsp/i386; apt-get install x11vnc)

2.  Make sure your /etc/rc.local (in the chroot.. 'cat /opt/ltsp/i386/etc/rc.local') has this statement on the last line
 x11vnc -display :6 -forever -loop -shared &

3.  Make sure you move the K99rc.local to S99rc.local in /etc/rc2.d (in the chroot.. /opt/ltsp/i386/etc/rc2.d/).. this is the one I always forget.

After that, you should be able to reboot your thin client.  On the server, you should be able to 'netstat -nr| grep 5900'  This command will show you what ip is listening on the server at port 5900.

Can you verify all of those things?

---

### Post by w4wlr on 2007-05-23
Hello!  I am new at edubuntu. I have tried all the different ways to install X11vnc on the client with no avail!  I am able to see the desktop using the console command, but not using the thin client manager. I am unable to get past the second step found at [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients). It says it cannot find the package. 

I have tried to set it up manually in the default settings, but that did not work either.

I have worked with M$ servers and have been able to overcome problems, but this one escapes me. 

One other thing... If this is to succeed as an alternative to M$, there needs to be a resource where the step by step procedures are spelled out. Otherwise, it is too complex for the average teacher (spent 20+ years in the classroom).

Where am I going wrong with this?

Will

---

### Post by ipguru99 on 2007-05-23
Hey Will, hang in there.

Yeah, that wiki has one slip.. it doesn't say anything about making sure your /etc/apt/sources.list is copied over.  If you haven't, you won't be able to install software.

You want to 'sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/'

Then, 'sudo chroot /opt/ltsp/i386'

Then, 'apt-get update'

Then, 'apt-get install x11vnc'

If you copy and paste those commands and it still doesn't install, copy the message and what you typed down here (everything between the single quote.. not the quote itself... ).  Hang in there...

bk

---

### Post by w4wlr on 2007-05-24
**Success!**

Got it to work. It still occasionally will say that the x11vnc is not installed in the client, but restarting clears it up.

Thanks! 

Will

---

### Post by chrisblessing on 2007-05-25
Thanks for your help page. I, unfortunately, am still having difficulty with this. I copied the sources.list from /etc/apt  to /opt/ltsp/i386/etc/apt and then followed the instructions. This is what I get:

pyp@EdubuntuPYP:~$ sudo chroot /opt/ltsp/i386/
Password:
root@EdubuntuPYP:/# apt-get install x11vnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x11vnc

I'm open to suggestions. After finally getting Flash 9 sound to play on the clients, this is my last challenge.

Thanks again,

Chris

---

### Post by tr3s on 2007-07-06
hi,

i already copied the sources.list into the chroot but when i do a ```
apt-get update
``` in chroot, i always get "could not resolve archive.ubuntu.com" error.

am i missing something? 

tnx in advance

---

### Post by ipguru99 on 2007-07-06
To chrisblessing, make sure your universe repository is enabled.  x11vnc is in there.

To tr3's, can you ping anything when you are in the chroot?

---

### Post by tr3s on 2007-07-07
no, i cant ping anything outside the lan from the chroot but i can ping local computers. in normal user prompt i can ping outside like google.com, yahoo.com etc.

btw, im using edubuntu as ltsp server and it is just connecting to the internet through a proxy server.

---

### Post by ipguru99 on 2007-07-07
I don't have access to the box I usually use, but I think you should be able to ping outside the local network from the chroot??  If you just want to try the x11 stuff, you can do an```
apt-get -d install x11vnc
```

This will pull down the package, but not install it (do this outside of the chroot).  Then move the .dpkg file that you downloaded into the chroot.. install it from there with the dpkg command.

Way hackish... as you should probably figure out why your chroot isn't allowing you outside of your local network (I am assuming it doesn't know about the gateway.. which seems weird).

---

### Post by mikebyrne on 2007-08-03
Hi, I've run into the same problem and finally came across this thread.  No matter what I did I always got the same 'couldn't find x11vnc' error when I tried to install the package.  I also was unable to apt-get update from within the chroot - I would get 'unable to resolve' errors.

I finally saw that I was able to ping IP addresses but not resolve names from within the chroot.  After looking at network configuration and /etc/resolv.conf 20 times or so, I tried copying over my resolv.conf into the chroot (sudo cp /etc/resolv.conf /opt/ltsp/i386/etc/).  At that point I was able to ping google from within the chroot, apt-get update was working, and apt-get install x11vnc ran successfully.  Rebooted the thin client and now it works.

I'm not sure why this worked for me.  I guess the new folder at /etc/ltsp/i386 needs its own set of important files to work with?  Maybe someone with more knowledge can clear this up for me..

Either way, hopefully this helps someone else.  -mb

---

### Post by goldenzim on 2007-08-15
The "unable to find x11vnc" errors a couple of you are getting when you're inside your ltsp chroot could be due to the fact that your ltsp server is behind a proxy server. So, your server can access the internet and update/install packages but your chroot can't. 

The quick fix for this is to run this inside your ltsp chroot : 

export http_proxy=http://yourproxyaddress:yourproxyport
apt-get update
apt-get install x11vnc

Note : you will also need the universe repository enabled inside your chroot's /etc/apt/sources.list before you run the "apt-get update" command. If you are unsure how to do that. Just run this, again, inside the ltsp chroot :

echo "deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe multiverse" >> /etc/apt/sources.list

I hope this helps.

---

### Post by joshuaalviar on 2007-10-03
Got it working

---

### Post by rcslex on 2008-05-14
After pulling my hair out on this with Gutsy (and Hardy) I came across this thread:
[https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients)

Seems after installing x11vnc in the chroot you have to exit and rebuild the squashfs.

Ubuntu/Edubuntu 7.10 and onwards - Make sure that the ltsp image gets updated:

sudo ltsp-update-image

If you are using an i386 image on an AMD64 build the command is:

sudo ltsp-update-image --arch i386

Reboot your thin clients and you should be able to connect to them via vnc now.

---

### Post by nroussi on 2008-05-20
I tried as well with this post [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients) and everything went well. I even added that line in the rc.local on the server. I tried everything that this thread has and still nothing. I am using 8.04 AMD64 with i386 client environment. Is there anything else I can try?

Oh, when I run ltsp-update-image --arch i386 this is the output:
> 
Warning: image defined with different port already in inetd.conf
Info: using already defined portnumber 2001
Info: updating PXE

Is that warning a problem?
Also when I run a netstat -an this is what comes out
> tcp6       0      0 ::1:5900                :::*                    LISTEN
Does that mean that port 5900 is already used?

---

