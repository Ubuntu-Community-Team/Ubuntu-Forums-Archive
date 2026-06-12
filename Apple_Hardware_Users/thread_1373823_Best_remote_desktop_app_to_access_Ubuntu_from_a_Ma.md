---
title: "Best remote desktop app to access Ubuntu from a Mac"
date: 2010-01-06
forum: Apple Hardware Users
---

### Post by dreamspy on 2010-01-06
Hi

I'm currently using NX to remote my Ubuntu from my Mac. It's super fast but it has it's glitches. F.x. has stoped working for no apparent reason, slow to connect, and the alt key is not working.

Anyone care to recommend some other good remote desktop solutions for accessing Ubuntu from a Mac?

regards
Frímann

---

### Post by llamabr on 2010-01-06
in what way do you want to "access" your ubuntu from your mac?  I'm not familiar with NX, but you can use ssh to connect remotely, you can use nfs to mount remote directories, etc.

---

### Post by dreamspy on 2010-01-06
I wan't to access the desktop of the Ubuntu machine. Remote desktop to the Ubuntu machine.

---

### Post by TheMiz on 2010-02-26
[Chicken of the VNC]("http://sourceforge.net/projects/cotvnc/")

That's what I use.

---

### Post by llamabr on 2010-02-26
Nice one.  Though you know you replied to a post that's a month and a half old.  Thanks, though.  I'll give it a try, too.

---

### Post by DefStatic on 2010-02-26
Well, it does answer a question of mine, except that Chiken of the VNC connects but I cnat do anything. Well, I can do things, but it doesnt display right on my screen.

---

### Post by nmaster on 2010-02-26
why not just use ssh? use the X or Y options to use the gui.

---

### Post by DefStatic on 2010-02-26
> **neal.m.master said:**
> why not just use ssh? use the X or Y options to use the gui.

Well, I barely know about OS X or Ubuntu... Any ideas where to start?

---

### Post by nmaster on 2010-03-06
i've never used ssh to access a personal computer, only my school servers.  i'm sure if you google around you should find something though.

---

### Post by loboc on 2010-04-14
OSX has two built in options for running gui apps on a remote linux machine

X fowarding:

start the mac X11 server ( its a extra install from the DVD)

in the xterminal thats starts up connect to your remote computer with 

```
 ssh -X username@host 
```

run your programs using the & bash suffix to relequinish control of the terminal after starting up

```
 xeyes& 
```

Remote Desktop:

On the Ubuntu box start the vino-server using the system preferences menu -> screen sharing preferences panel. Set the security settings as you wish, its also a good idea to verify your firewall on your router blocks vnc from the WAN 

On the Mac start the VNC viewing client, its located in 
/System/Library/CoreServices/Screen Sharing

connect to your linux box using its IP adress

To simplify this if you follow the directions to install netatalk (bonjour) on your ubuntu box the remote screen will show up in the shared portion of your finder sidebar

---

### Post by dreamspy on 2010-04-16
Thanks for those tips.  This X11 trick is incredible!!!


> **loboc said:**
> OSX has two built in options for running gui apps on a remote linux machine

X fowarding:

start the mac X11 server ( its a extra install from the DVD)

in the xterminal thats starts up connect to your remote computer with 

```
 ssh -X username@host 
```

run your programs using the & bash suffix to relequinish control of the terminal after starting up

```
 xeyes& 
```

Remote Desktop:

On the Ubuntu box start the vino-server using the system preferences menu -> screen sharing preferences panel. Set the security settings as you wish, its also a good idea to verify your firewall on your router blocks vnc from the WAN 

On the Mac start the VNC viewing client, its located in 
/System/Library/CoreServices/Screen Sharing

connect to your linux box using its IP adress

To simplify this if you follow the directions to install netatalk (bonjour) on your ubuntu box the remote screen will show up in the shared portion of your finder sidebar

---

### Post by scotartt on 2010-05-01
I've got a problem now that I've upgraded to Lucid 10.4. Formerly I could easily access ubuntu Remote Desktop (i.e. vino) from my Mac via Bonjour and the Mac's built-in remote desktop client everything was nice. Both 9.04 and 9.10 all was good.

Now since I upgraded to Lucid when I access the Ubuntu machine with the Mac, I get what I can describe as only a frozen 'snapshot' of the screen as it was when I accessed it. If I turn on the Ubuntu machines monitor and look at it across the room I can see my mouse actions having an affect (eg menus being selected) but I don't see them in the Mac's remote view.

I've tried a combination of settings (encryption on/off, password on/off etc) at both ends nothing seems to make this problem go away.

I prefer this solution to VNC or X11 port-forwarding over ssh, so it would be nice to get it back.

Any ideas? Google doesn't bring anything terribly relevant (the problem is with the Ubuntu '10.4' version, as soon as you type 'something 10.4 something mac' I got tons of results about OSX 10.4 ;-( )

It's the only flaw I've found with Lucid so far, very impressive.

---

### Post by NeddyDownUnder on 2010-05-03
> **scotartt said:**
> I've got a problem now that I've upgraded to Lucid 10.4. Formerly I could easily access ubuntu Remote Desktop (i.e. vino) from my Mac via Bonjour and the Mac's built-in remote desktop client everything was nice. Both 9.04 and 9.10 all was good.

Now since I upgraded to Lucid when I access the Ubuntu machine with the Mac, I get what I can describe as only a frozen 'snapshot' of the screen as it was when I accessed it. If I turn on the Ubuntu machines monitor and look at it across the room I can see my mouse actions having an affect (eg menus being selected) but I don't see them in the Mac's remote view.

I've tried a combination of settings (encryption on/off, password on/off etc) at both ends nothing seems to make this problem go away.

I prefer this solution to VNC or X11 port-forwarding over ssh, so it would be nice to get it back.

Any ideas? Google doesn't bring anything terribly relevant (the problem is with the Ubuntu '10.4' version, as soon as you type 'something 10.4 something mac' I got tons of results about OSX 10.4 ;-( )

It's the only flaw I've found with Lucid so far, very impressive.

I'm not sure how much I'll be able to help but I just thought I would let you know that the problem is not across the board in Lucid. I currently access my Lucid machine through my Mac's (OS X 10.6.3) built in ScreenSharing app and it works perfectly. Did you upgrade Karmic to Lucid or is it a clean install? Maybe you can try reinstalling 'Vinagre' and see if that helps. Or try it with a clean Lucid install if you are not already doing so...

Also FYI RE:
> I prefer this solution to VNC or X11 port-forwarding over ssh, so it  would be nice to get it back.

Mac's built in ScreenSharing is VNC, just thought I would mention this to stem confusion. 

Next, when you boot the Lucid machine do you have the monitor connected and turned on? If not it can stop Lucid from properly detecting the display and then stop the X server from starting. I had this happen, I solved this by creating an 'xorg.conf' file with display settings in it. (this does not sound like your problem, but just thought I would mention it.)

Lastly do you have a Key Chain password set on the Lucid machine? You will need to unlock the Key Chain on the Lucid machine before you connect to it if you are using a password to access the Lucid Machine.

Don't know how much this info will help, but just wanted you to know that I have it working so don't give up... 

Good Luck

---

### Post by scotartt on 2010-05-03
> **NeddyDownUnder said:**
> I'm not sure how much I'll be able to help but I just thought I would let you know that the problem is not across the board in Lucid. I currently access my Lucid machine through my Mac's (OS X 10.6.3) built in ScreenSharing app and it works perfectly. Did you upgrade Karmic to Lucid or is it a clean install? Maybe you can try reinstalling 'Vinagre' and see if that helps. Or try it with a clean Lucid install if you are not already doing so...


OK thanks for that useful information. It's an upgrade - not possible to clean install on this particular machine, however at work I've got a machine that's a clean install from Friday, I will try it on that one.

I will also try an uninstall and reinstall of vinagre too.


> **NeddyDownUnder said:**
> 
Also FYI RE:


Mac's built in ScreenSharing is VNC, just thought I would mention this to stem confusion. 

Next, when you boot the Lucid machine do you have the monitor connected and turned on? If not it can stop Lucid from properly detecting the display and then stop the X server from starting. I had this happen, I solved this by creating an 'xorg.conf' file with display settings in it. (this does not sound like your problem, but just thought I would mention it.)

Lastly do you have a Key Chain password set on the Lucid machine? You will need to unlock the Key Chain on the Lucid machine before you connect to it if you are using a password to access the Lucid Machine.

Ahh yes the monitor is on, it's perfectly OK on the console and the key chain is unlocked too. Also I tried disabling the connection password and it didn't make one jot of difference.

Thanks for the tips though, will let you know how that goes.

regs
scot

---

### Post by scotartt on 2010-05-03
Reinstalling Vinagre didn't do make jot of difference. Still the same issues. On the Mac I see a static picture, if I look at the screen on the Ubuntu server I can see that actually my mouse clicks (at least) have an effect, just never reflected what I see on the Mac.

---

### Post by e-Gee on 2010-05-03
You also have TeamViewer it is cross platform, simple to use and free for personal use i use that to connect with other OS [http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

---

### Post by scotartt on 2010-05-03
I was just trying out JollysFASTVNC on the Mac, same result. Although it did let me unlock the screen saver password at one point, after than no response in the local view whereas the remote screen looked like it was getting my mouse movements and clicks just fine.

---

### Post by scotartt on 2010-05-03
> **e-Gee said:**
> You also have TeamViewer it is cross platform, simple to use and free for personal use i use that to connect with other OS [http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

Thanks, but I don't know why I would use a commercial product when the free solution has never failed me before. My budget for such items is zero.

---

### Post by scotartt on 2010-05-03
I just realised that vinagre is the client, not the server. Anyway I ssh'd to the ubuntu box with X-forwarding turned on, then ran Vinagre, and connected back to the ubuntu box (a very roundabout way to test it) and it too has the same problem that the Mac builtin client and JollysFastVNC had. So it must be the vino-server configuration. I can see it in a process list:

16969 ?        S      0:07 /usr/lib/vino/vino-server --sm-disable

Does anyone know what that option '--sm-disable' means?

thanks

---

### Post by scotartt on 2010-05-03
Same problem connecting to a brand-new fresh installation of lucid 10.4 at work.

---

### Post by mlai on 2010-05-09
I have this problem as well.

A workaround that works for me is to turn off all visual effects on the Ubuntu desktop (System->Preferences->Appearance).

This is a known bug. For more information take a look at [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126?comments=all)

---

### Post by scotartt on 2010-05-09
Thanks for this information. It worked! Visual effects way overrated, especially over a VNC connection anyway ;-)

---

