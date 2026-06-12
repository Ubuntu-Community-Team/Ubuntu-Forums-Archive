---
title: "PowerBook G4 running Ubuntu 10.10 has a blue tint after every suspend"
date: 2011-11-28
forum: Apple Hardware Users
---

### Post by tomburnes on 2011-11-28
Hello,

Sorry for making such a long post![INDENT]I have an aluminum Apple PowerBook G4 15" with an ATI Radeon 9600 card. I recently installed Ubuntu 10.10 after numerous (failed) attempts at installing 11.10. Thanks to these forums, I have managed to "fix" everything on my PowerBook, except for four things:


[LIST=1]
[*]Adobe Flash
[*]Screen brightness keyboard controls
[*]S-Video output
[*]After waking from suspend, the screen has a blue tint.
[/LIST]

When I tried to connect to my TV via my S-Video port to make a dual monitor setup, A window appeared and asked me if I wanted to increase my virtual screen size. I opted for that, and ever since, my laptop screen has a blue tint to it after waking from suspend. If I log out and log back in, it is no longer tinted blue. I checked my xorg.conf file in /etc/X11/ and it is different than it used to be, and it has a virtual size segment that wasn't there before. My TV is not recognizing a signal, although Ubuntu recognizes the TV as "unknown" and has a list of available resolutions. I tried setting it to all of them, but none were successful. 

Does anyone know of any commands I can use to get my S-Video port usable, and/or (more importantly) fix the blue screen upon awakening issue?

I am running the most recent version of Firefox for PowerPC (3.6.something) and I cannot figure out how to install Flash. Has anyone successfully installed Flash?

System>Preferences>Keyboard Shortcuts allowed me to set every shortcut I needed except for the brightness buttons. Does anyone know how to set the brightness keys to the monitor brightness?

Would you guys recommend trying to get 10.10 to work the way I want to or upgrading (to 11.04 or 11.10)? *and if so, what is the best way to upgrade? I prefer 11.10, but I know that community supported builds are buggier and slower (to release) than official builds.

[/INDENT]Any instructions/links/useful programs would be much appreciated!
 Thanks, tomburnes.



****UPDATE****
Deleting the "Virtual Size" section in my xorg.conf got rid of the blue tint problem.

---

### Post by tomburnes on 2011-11-29
Bump

---

