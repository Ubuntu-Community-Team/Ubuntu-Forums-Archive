---
title: "[SOLVED] Xorg/resolution or what!!"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2008-01-05
This is the third time this has happened. I get Gutsy all setup and running nicely then I get stupid and try to change the resolution, then kaplooey, all is undone. On a reboot Grub loads , then the screen informs me that it is running Local Boot Scripts, then, instead of the desktop, all I get is a raster.

I give it the Three finger salute and it goes back to the Boot Scrips window with a blinking cursor. Is there a way to fix this with a command at this point. I really don't want to have to do a clean install again. Heck, two are enough already...

Also, I noticed when I do a clean install it doesn't ask/tell what resolution range is being used. Just starts at a res it randomly chooses. Has not been the same through all three installations.

Thanks for any and all help,

Jon

---

### Post by glennzo on 2008-01-05
Can't you just restore the xorg.conf backup file? There should be an xorg.conf~ file in /etc/X11. Alternatively manually edit xorg.conf.

---

### Post by warbread on 2008-01-05
This is difficult to help without knowing how you changed the resolution in the first place.  Also, what are the particulars of your comptuer?

---

### Post by erfahren on 2008-01-05
try this:
boot into recovery mode from the GRUB menu - it'll ask for the root password - enter your user password - you'll get the root prompt ( # )

type in (no need for "sudo" since you are logged in as root):
```

dpkg-reconfigure -phigh xserver-xorg

```
That will take you through the steps of reconfiguring the X Server (the /etc/X11/xorg.conf file)
(I've never ran that with the "-phigh" option, but it's supposed to make it set the defaults for most of the selections)

you probably shouldn't try to set the resolutions manually unless you absolutely have to. They should get configured automatically.

once you are done you can reboot from the command line with (shutdown reboot now):
```

shutdown -r now

```

that utilitity will automatically make a backup of you /etc/X11/xorg.conf

if you get it working and try to fine-tune your resolution again make a backup of that file
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back1

``` 
(I usually make a backup of that file immediately after a fresh install)

at the command line in recovery mode you can also list the files in /etc/X11 directory and see if there is a backup of xorg.conf already 
```

ls /etc/X11

```
I usually change directory (cd) into it first 

you *can* also use the command line text editor (nano) to work on that file (back it up first!) - while in the /etc/X11 diectory:
```

nano xorg.conf

```
after making changes hit Ctrl+X to exit and save changes (it'll prompt you).

---

### Post by erfahren on 2008-01-05
oh, here's a guide on using that dpkg-reconfigure xserver-xorg
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

here's a couple guides on resolution
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

note: I read somewher that it's not good to manually set the sync, refresh rates unless you know what they are. I can't seem to find that but it said it could actually damage the display.

---

### Post by Romin-1 on 2008-01-05
Thanks to all who replied, especially efrahren, whose code did the trick. All is joy now.

Just for the record, the machine is a home built, dual Intel with 3+ gigs of ram.

I tried to change the resolution through Preferences-Screen Resolution.

Guess I'll have to live with what Gutsy feels is best.

Once again, many thanks,

Jon

---

