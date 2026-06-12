---
title: "ctrl alt del equivalent?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Thundercat on 2006-06-23
Hi all,
Just booted Kubuntu from the Live CD a couple of times, thats how new I am ;)

One of the times I had the system freeze on me, If it were windows I'd have pressed ctrl-alt-del to get the task manager up and see if I could recover it. Is there a similar "emergency key combo" in linux (ubuntu specifically)?

For more info, I'm using the AMD64 build of the latest release and when it froze I could move the mouse but not click anything or get any response from the keyboard... 

I, of course, rebooted and got running again but just wondered if there was anything else I could have tried?

---

### Post by SkyNet2029 on 2006-06-23
you could always use 
CTRL+ALT+BACKSPACE
to forcefully restart the x-server.
It will send you back to the login prompt after it nukes all of your running apps.

---

### Post by hotbrainz on 2006-06-23
Well, there is the "System Monitor" 
System -> Administartion -> System Monitor

which is something similar to the task manager in windows. I put a shortcut of this on the desktop and use it to bail me out of trouble. But what i would like to know as Thundercat is that can we use some nice key combination instead.

---

### Post by SkyNet2029 on 2006-06-23
This post (scroll down, it' s the one from Aysiu that is relevant)
[http://www.ubuntuforums.org/showthread.php?t=200873]("http://www.ubuntuforums.org/showthread.php?t=200873")
for the key-bindings needed for the equivalent.

---

### Post by Thundercat on 2006-06-23
I couldn't get the system menu, or indeed any of the menus to pop up, so I was literally stuck without a magic key combination. 
It is altogether possible that the state I was in was unrecoverable regardless, but it'd be nice to know if there is some way to access system monitor or even a command prompt in the event of a lockup?

If it happens again I'll try the ctrl-alt-backspace combo, but a less drastic option would be appreciated. Some way to enable me to kill just one process rather than nuking all apps?

PS many thanks for the replies

---

### Post by RRS on 2006-06-23
[QUOTE=Thundercat]I couldn't get the system menu, or indeed any of the menus to pop up, so I was literally stuck without a magic key combination. 
It is altogether possible that the state I was in was unrecoverable regardless, but it'd be nice to know if there is some way to access system monitor or even a command prompt in the event of a lockup?

If it happens again I'll try the ctrl-alt-backspace combo, but a less drastic option would be appreciated. Some way to enable me to kill just one process rather than nuking all apps?

PS many thanks for the replies[/QUOTE]

You can also use Ctrl-Alt-F1 to switch to a terminal. Enter; ```
ps auxww
```
This will list the currently running proccesses with their ID#'s. Then; ```
kill (process ID)
```
I've used this method when XMMS occasionally misbehaves when streamtuner fails to connect to a server.
Prevents having to reboot.

---

### Post by MaximB on 2006-06-23
guys...trust thundercat - it happend to me to a few times
and I couldn't do nothing - just move my mouse across the screen
no key combo worked
I couldn't click on anything

but I've found the source of the problem
it was 3dgraphics
after I've installed my ati graphic card - all worked fine (except the slowww graphics) but nothing stucked.

so thundercat - install your 3dcard , that should solve it.

---

### Post by hotbrainz on 2006-06-23
This one just works... 

> This post (scroll down, it' s the one from Aysiu that is relevant)
[http://www.ubuntuforums.org/showthread.php?t=200873](http://www.ubuntuforums.org/showthread.php?t=200873)
for the key-bindings needed for the equivalent.

thanks for the link Skynet2029 and all you guys for the help

---

### Post by Thundercat on 2006-06-23
Aha I have an ATI Radeon X800 in there. I'm only booting from the Live CD at the moment so hadn't got round to running through the instructions for the ATI driver install so I guess thats it. 

Having said that, these key combos will undoubtablty come in handy over my time in ubuntu ;)

---

### Post by rattyrat on 2006-07-11
I found these posts through Google and thought you might like to know how I got round a similar lockup on my system.

Assuming you have a second PC networked to the Linux box, install VNC, then you can log in a second time as Root and use the System Monitor to look for the locked task, and kill it.

If you cannot log in via VNC it probably indicates your system is totally locked and you need to re-boot.

Hope this helps.

RR

---

### Post by 3rdalbum on 2006-07-11
Right-click on a Gnome panel, click "Add To Panel...", then choose the "Force Quit" applet and hit Ok. Now, whenever you want to kill a program, you just click on that icon and then click a window of the hung program.

Alternatively, press Control-Alt-F1, log into the terminal, and then type:

```
pkill appName
```

where appName is the name of the hung program.

---

### Post by UbuntuniX on 2006-07-11
Keep in mind there IS a difference between ubuntu and kubuntu ;)

And if you use VNC be very careful,
there's exploits circling the web that allow people to access ANY computer running VNC.

Hope you like ubuntu :)

---

