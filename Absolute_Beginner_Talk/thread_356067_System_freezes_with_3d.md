---
title: "System freezes with 3d"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by gojetsgo on 2007-02-08
I've been using ubuntu for a couple days now and it seems to freeze up quite a bit.  When it does I have to do a hard reboot on my laptop.

It freezes up if I try to use 3ddesktop, or if I preview some of the included 3d screensavers.  My laptop has integrated Via S3 video.

Any ideas on how to keep Ubuntu from freezing up?

---

### Post by shareMenaPeace on 2007-02-08
HI check out this might be informative-.-

[http://ubuntuforums.org/showthread.php?t=342115](http://ubuntuforums.org/showthread.php?t=342115)

---

### Post by xpod on 2007-02-08
> I've been using ubuntu for a couple days now and it seems to freeze up quite a bit. When it does I have to do a hard reboot on my laptop.
It freezes up if I try to use 3ddesktop, or if I preview some of the included 3d screensavers. My laptop has integrated Via S3 video.

Your lucky you can run beryl at all me thinks as i had to get a proper nvidia card before i could get much use out of the onboard s3 savage thing on this pc.

I actually never even tried beryl till i got a half decent card mind you and the closest my s3 graphics ever got to fancy desktops was the basic 3ddesktop thing in synaptic.

---

### Post by jd65pl on 2007-02-08
Do you have hardware 3d rendering? to check this do the command below if it returns yes then you have. If not you should look in to getting the driver for your card.

```
glxinfo | grep direct
```

---

### Post by gojetsgo on 2007-02-08
I tried the 

glxinfo | grep direct

and it says I do have 3d rendering.  I read the [http://ubuntuforums.org/showthread.php?t=342115](http://ubuntuforums.org/showthread.php?t=342115) thread mentioned above.  I have the same video card setup (VIA/S3G UniChrome Pro IGP, K8M800).

I also ran glxgears and everything ran smooth with no problems.

It says there is a bug that isn't resolved for this card and 3d applications.  

However, all I really want to be able to do is use 3ddesktop.  

3ddesktop actually works when I only have one workspace active (basically just one workspace spinning around).  Once I have more than one workspace, 3ddesktop will lockup my computer.

Is there a way around this or am I out of luck?  

Have other people been able to use 3ddesktop with Via/S3 video?

---

### Post by %hMa@?b&lt;C on 2007-02-08
the new nvidia drivers do not allow anything to go fullscreen, :(

---

### Post by gojetsgo on 2007-02-08
Is there a work around for this problem?  At least to get 3ddesktop to work?

---

### Post by gojetsgo on 2007-02-09
Does anyone know if this problem goes away with Ubuntu Edgy or some other Ubuntu version?

---

### Post by Vox754 on 2007-02-13
I have K8M800 for desktop PC and I have also the mentioned bugs. I get the "libGL warning: 3D driver claims to not support visual 0x46" even when using "xawtv", but that really doesn't do anything.
I haven't really checked, since it crashes, but all I see are 3D screensavers, so I don't use them anymore, I just turn off the monitor.
Actually, most of my screensavers worked just after a clean install of Ubuntu 6.10, but after some automatic updates the screensavers, along with the hibernation feature, simply stopped working.

I'll try "3ddesktop" and let you know what happens.
-------------------------------------------------------------------------
I just tried "3ddesktop" and works okay. It is inefficient, I must say.
It takes time to write "3ddesk" and then wait for the workspaces to go 3D, rotate them and choose which you want.
You do in 10 seconds what could be done in one with a mouse click. Obviously you can use keybindings but that's not my interest right now.

Desktop users better get a separate AGP or PCIe Card; laptop users... rest in peace.
-------------------------------------------------------------------------
Woa! After rebooting I can only use "3ddesktop" with one workspace, instead of four.
Scary stuff; I'm removing it.
-------------------------------------------------------------------------
Wait! Seems you need to "acquire" the workspaces' picture every time.
```

3ddesk --acquire
3ddesk

```

And there are also lots of options you can readily set in the configuration file "/etc/3ddesktop/3ddesktop.conf".
I can't believe what I'm going to say, but... read... the... manual...
```
man 3ddesk
```

---

### Post by gojetsgo on 2007-02-18
3d desktop can become a whole lot more efficient if you control it with hotkeys - and then it's definitely worth it.  If only I could get it to work.

I have the same video card - k8m800

I also can use it no problem with one workspace (no crashing).  But with any more than one workspace it locks up my laptop.

I've most certainly read the manual.  I've even tried using different switching modes (linear, price is right, etc.) but every mode will lock up if there is more than one workspace.  The manual does not indicate how to prevent a lock-up.

[B]
I'd just like to know - has anyone with a VIA/S3G UniChrome Pro, or more specifically, a K8M800, been able to get 3ddesktop working?[/B]

I've been searching and searching.  If it can't be done, I'm just going to give up.

---

