---
title: "Mac OS X to Ubuntu undertaking"
date: 2008-08-27
forum: Apple Hardware Users
---

### Post by edenuccio on 2008-08-27
Precursory rant about Apple and Mac OS X... why I am switching. =)

I paid for OS X (well I bought a MacBook) and after two years of using it every day, I am generally just disappointed. There are bugs that I cannot fix, annoyances I can't reconfigure, objectively bad UI from legacy Mac behavior, subjectively bad UI which Apple claims to be objectively better but because they fail to recognize that a tradeoff exists, they don't make the tradeoffs configurable (one of the side-effects of the company and its CEO's lack of humility).

"It Just Works" is ********. There's always gonna be *tradeoffs* that don't "just work" for some people. Namely those of us who use our compoopers for something more than just rudimentary tasks, and jacking off.

Both of my roommates, and a few other friends, happen to be Apple engineers. When I discuss these bugs and annoyances they find cop outs for everything. The most common one is that "I'm just used to the way Windows does it". They are my friends so I would not tell them this, but I am also disappointed in this dismissive attitude which seems to be a recurring theme in Apple. I won't ever work there.

So-- I am switching to a GNU/Linux system as my primary OS, on my MacBook (the hardware is good), from Mac OS X. In doing so I have been stumbling over a lot of issues that I am trying to identify and find permanent solutions to. 

Qualifier: I appologize if this comes off as a list of whiny complaints. I am actually volunteering to take time out of my weekends and nights to address these problems and release my fixes and plugins back to this awesome community. =)

```

1) Music
	1A) Write a python plugins for Rythmbox to organize music / remove duplicates?
		This means learning GTK+ and Glade. This is something like the seventeenth GUI framework I've had to use. =|
			-- Ok, found a few Glade Interface Designer bugs. Should probably fix those first.

	1B) Fix bugs in Rythmbox... doesn't seem to be anything better. Just a few annoyances.

	1C) Add "repeat" option to Rythmbox for current song. As of writing this it only repeats the playlist.
		Repeat button should switch between the three repeat options: none, playlist, and current-song. Like iTunes

	1D) Migrate iTunes data. Playlists and ratings. Maybe make a separate Rythmbox plugin.

2) Equalizer. Global or in media player. Preferably global. How does this get overlooked? Looks like Jack might be a solution.

3) Volume control, funky sheyat! Every seperate control gets out of sync and has to be "fiddled" into order.
	3A) Reproduce and define the bugs, as they are difficult to isolate. (assuming multiple... unlikely one root cause)

4) MacBook keyboard
	4A) Swap fn key for ctrl so I don't have to invert my hand into itself to undo a mistake.
	4B) Key commands for all of my common actions. Use Mac's commands when applicable to minimize redundant muscle-memory.

5) Alarm Clock missing option to maximize volume. Other than that it's a good applet. =)

6) Trackpad. Horizontal scrolling is reversed. Vertical scrolling steps 3 lines at a time. Weird thing about this is I know that my trackpad is sending lots of scancodes that are being ignored. So the behavior I get is something to the effect of, only the third of every event is acknowledged, which is handled by jumping 3 lines. I want to take advantage of the full resolution. It would also be nice to have momentum-scrolling (the flick) but can do without. At least I have it in Firefox via an add-on.

7) Wireless! Broadcom! GAH!... figure something out. =(

8) Something to replace Spotlight. That thing rocked. Cannot live without it now. I at least need some kind of keyword based application launcher.

9) Office (My Job, not the software)
	9A) VPN...?
	9B) Get my VMWare Fusion virtual machines working. Either convert them for VirtualBox or downgrade to VMWare Server so I can run them on anything. Wish I knew Fusion-generated VMs will only run with Fusion. Suck my sack VMWare.

10) Eclipse... PDT breaks it, yet the EasyEclipse bundle for PHP development seems to work on its own. But I don't want two separate Eclipse development environments for Java and PHP. At work I have to use both. One proper Eclipse setup is essential.

11) A fail proof backup system... Ubuntu is definitely not as stable as OS X. But a good backup system is sufficient so that when everything implodes I won't be out of commission for a day or two while trying to restore it. Triple redundancy, incremental backups on a seperate partition, and logarithmic backups on external HD, synced daily with a Media Temple grid hosting account. Comments? =)

12) Gmail's "inbox" button does nothing when I click it while viewing a message. Firefox bug? Gmail bug? Hmph

13) I find it just a little bit irritating that items I add to GNOME's panels are pixel-positioned. I run into situtaions where something gets bigger and then I have to manually move everything around to tidy it up. And what is with the notification sub-panel in the main (top) GNOME panel having a grippy, but nothing else having a grippy? Seems odd and inconsistent. I'd like if everything was just simply aligned to the sides.
```


Looking over this list makes me sad. But I am just happy that I CAN fix them if I choose to, without having to wait on a company to do it for me (or dismiss it with some ******** reasoning). Any suggestions & comments are appreciated. I'll start by going through these one by one, looking for existing threads on these forums, existing bugs filed, corresponding existing fixes, and writing my own if nothing already exists. The learning experience is good. I don't consider it a waste of time. I'll update this page every step of the way.

Thanks peeps!

---

### Post by flaggh on 2008-08-27
I think pommed will let you swap the Fn and Ctrl key.

I use rsnapshot for backups.  Very configurable and seems to be reliable.  [http://rsnapshot.org/]("http://rsnapshot.org/")

---

### Post by joe_bling on 2008-08-27
Broadcom "just works" post-Ubuntu install if you run the Hardware Drivers util. Of all the GNU/Linux distros, Ubuntu is easily the best at getting Broadcom wireless chipsets and NetworkManager working well.

Stability? I have an old Intel Centrino laptop and this Powerbook G4 and the only time I ever reboot is for kernel updates. You need to probe why your Ubuntu install is not "stable", specifics are needed.

Keyboard mapping is available out of the box.

---

### Post by cyberdork33 on 2008-08-27
> **edenuccio said:**
> 1) Music
    1A) Write a python plugins for Rythmbox to organize music / remove duplicates?
        This means learning GTK+ and Glade. This is something like the seventeenth GUI framework I've had to use. =|
            -- Ok, found a few Glade Interface Designer bugs. Should probably fix those first.

    1B) Fix bugs in Rythmbox... doesn't seem to be anything better. Just a few annoyances.

    1C) Add "repeat" option to Rythmbox for current song. As of writing this it only repeats the playlist.
        Repeat button should switch between the three repeat options: none, playlist, and current-song. Like iTunes

    1D) Migrate iTunes data. Playlists and ratings. Maybe make a separate Rythmbox plugin.
If you want to contribute to Rhythmbox, this is not the place to do it.
[http://www.gnome.org/projects/rhythmbox/development.html](http://www.gnome.org/projects/rhythmbox/development.html)
[FONT=monospace]
[/FONT]> **edenuccio said:**
> 2) Equalizer. Global or in media player. Preferably global. How does this get overlooked? Looks like Jack might be a solution.This is really a preference thing and has probably been left out of Ubuntu on purpose by default (simplicity). Ubuntu Studio, which is targeted to the creative types has Jack installed by default.

> **edenuccio said:**
> 3) Volume control, funky sheyat! Every seperate control gets out of sync and has to be "fiddled" into order.
    3A) Reproduce and define the bugs, as they are difficult to isolate. (assuming multiple... unlikely one root cause)This really is an issue on several Macs right now. This would need help with ALSA. You do have to understand that this software is made to work well with much more hardware than just Macs. Mactels seem to be a little different than the same hardware on PCs and thus the driver acts strangely.

> **edenuccio said:**
> 4) MacBook keyboard
    4A) Swap fn key for ctrl so I don't have to invert my hand into itself to undo a mistake.
    4B) Key commands for all of my common actions. Use Mac's commands when applicable to minimize redundant muscle-memory.before you work too much on fixing the keyboard, there are A LOT of changes that are making their way into the kernel associated with Apple keyboards. The Fn key in one that is a bit weird. (Another is the the F1, F2, etc keys work only with the Fn key depressed, otherwise they do whatoever other action they normally do in OSX which is contrary to the way it should work IMO.

> **edenuccio said:**
> 5) Alarm Clock missing option to maximize volume. Other than that it's a good applet. =)That's another software / preference specific thing.

> **edenuccio said:**
> 6) Trackpad. Horizontal scrolling is reversed. Vertical scrolling steps 3 lines at a time. Weird thing about this is I know that my trackpad is sending lots of scancodes that are being ignored. So the behavior I get is something to the effect of, only the third of every event is acknowledged, which is handled by jumping 3 lines. I want to take advantage of the full resolution. It would also be nice to have momentum-scrolling (the flick) but can do without. At least I have it in Firefox via an add-on.
The horizontal scrolling seems to be in reverse on all trackpads right now (even on non-macs). I have no idea why. For the cool muti-touch type of things, you might want to check out the new driver for the multitouch touchpads on the MacBook Pro/Air.
[http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040)


> **edenuccio said:**
> 7) Wireless! Broadcom! GAH!... figure something out. =(Good luck with that one.

> **edenuccio said:**
> 8) Something to replace Spotlight. That thing rocked. Cannot live without it now. I at least need some kind of keyword based application launcher. there are some spotlight-like and quicksilver-like applications out there. Just look.



> **edenuccio said:**
> 9B) Get my VMWare Fusion virtual machines working. Either convert them for VirtualBox or downgrade to VMWare Server so I can run them on anything. Wish I knew Fusion-generated VMs will only run with Fusion. Suck my sack VMWare. I am pretty sure that the Fusion disk images with mount in Virtualbox just fine.


> **edenuccio said:**
> 10) Eclipse... PDT breaks it, yet the EasyEclipse bundle for PHP development seems to work on its own. But I don't want two separate Eclipse development environments for Java and PHP. At work I have to use both. One proper Eclipse setup is essential.Outside the scopre of this forum. Try the development forum.


> **edenuccio said:**
> 11) A fail proof backup system... Ubuntu is definitely not as stable as OS X. But a good backup system is sufficient so that when everything implodes I won't be out of commission for a day or two while trying to restore it. Triple redundancy, incremental backups on a seperate partition, and logarithmic backups on external HD, synced daily with a Media Temple grid hosting account. Comments? =) Flyback is new software made to work similar to Time Machine if you liked that.


> **edenuccio said:**
> 12) Gmail's "inbox" button does nothing when I click it while viewing a message. Firefox bug? Gmail bug? HmphNo idea what you are talking about there.

---

### Post by kosumi68 on 2008-08-28
A note on Rythmbox: Amarok is apparently the most popular music player on linux right now, but it is KDE-based. Gnome and KDE are just about equally popular, so the incompatibility issues are not likely to go away. If you dont mind mixing Gnome and KDE applications, Amarok is worth a try.

---

### Post by blueyelabs on 2008-08-28
Not that I want to turn this into a sort of flame war (whatever that IS) but what kind of OSX bugs? I have both an Ubuntu install on my family computer and my MacBook Pro and I have to say that I find my mac much more usable, friendly and powerful. For me everything "just works" and I actually use my mac for doing video editing, other graphics and web development (which is more than typing and watching porn). Although I do really like Ubuntu I find it has way more problems (mostly in the way that the filesytem is configured, and the way some software has to be installed). Maybe something was just wrong with your mac?

---

### Post by cyberdork33 on 2008-08-28
> **blueyelabs said:**
> Not that I want to turn this into a sort of flame war (whatever that IS) but what kind of OSX bugs? I have both an Ubuntu install on my family computer and my MacBook Pro and I have to say that I find my mac much more usable, friendly and powerful. For me everything "just works" and I actually use my mac for doing video editing, other graphics and web development (which is more than typing and watching porn). Although I do really like Ubuntu I find it has way more problems (mostly in the way that the filesytem is configured, and the way some software has to be installed). Maybe something was just wrong with your mac?

I know that the OP started off with this type of information, but this is a support forum, and I would ask that OS X discussions (problems or no problems, bad or good) be taken to the OS X forum:
[http://ubuntuforums.org/forumdisplay.php?f=165](http://ubuntuforums.org/forumdisplay.php?f=165)

---

