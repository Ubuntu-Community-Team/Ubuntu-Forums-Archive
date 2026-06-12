---
title: "Run command everytime Ubunu boots?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Stal on 2007-06-11
Hi,

Im just trying the latest version of Ubuntu which I was so impressed with how far it had come since I last tried it Ive installed it on my machine. :-)

I had trouble with booting from the LiveCD and found the answers on the forum here, I had to add this to the startup options:
```
break=top
```

then run:

```
modprobe piix
exit
```

to enable it to continue to boot.  That worked fine and all installed beautifully.

Now, I appear to have to run this code everytime it boots up, so I have 2 small questions:

1: what does this command actually do?
2: Which file is it I need to edit to make this run automatically at boot so i dont have to type that each time?

Thanks in advance! :D

---

### Post by p_quarles on 2007-06-11
[COLOR=Black]Which stage of bootup requires you to enter this code? I.e., during BIOS startup, kernel loading, or the X session? 

Also, are you still using the LiveCD, or are you booting it from the hard drive now?
[/COLOR]

---

### Post by HotShotDJ on 2007-06-11
EDIT:  NEVERMIND... don't do what I just said.

---

### Post by Stal on 2007-06-11
Hi,


when running off live cd, it would get to the boot options (where i would press F6 for extra options) then it would stop straight after that with an error something like "cannot start tty" or something.

I found someone on these forums suggesting the above workaround which got me into the live cd, i now have it installed the hard drive fine, but when booting from the drive it stops straight after the grub boot loader with the same "cannot start tty" message, but continues to load and work fine if i type "modprobe piix" then "exit". I then get the Ubuntu loading screen and then login.

So Im guessing I have to make ubuntu run that command for me automatically everytime (whatever it does!) in order to boot straight into the login screen. Just not sure how! lol

---

### Post by p_quarles on 2007-06-11
One way is (assuming you're using the Gnome version) to load the Control Panel, go to Sessions, and add that script as a startup program. That way it will load with the desktop.

---

### Post by Stal on 2007-06-13
hi, thanks for your reply.

I put the command in the startup script but that didnt seem to work. I think it may need to be run earlier than that as it stops before i even get the ubuntu boot screen.
:-(

---

### Post by Stal on 2007-06-14
ok, ive also noticed that by simply typing "exit" when it stops during boot it conitnues to load fine as well ??

When it stops it is saying something about busybox and cannot start tty.  Is there anyway to try and stop this from trying to start during boot, as it appears to work fine without it?

---

