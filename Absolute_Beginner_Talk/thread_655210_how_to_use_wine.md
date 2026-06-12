---
title: "how to use wine"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2008-01-01
sorry about the really n00by question, but I just installed wine and I actually have no idea how to get my games to work on it.

I have tried right clicking on the autorun files from the disk and opening them with wine, but wine doesn't appear on the list.
Thanks in advance for the help!:)

---

### Post by RomeReactor on 2008-01-01
Hi. You can run Wine from the terminal (Applications->Accessories->Terminal); let's say you have a **setup.exe** for a certain game. You open the terminal and enter:
```
wine /path/to/setup.exe
```
substitute /path/to/setup.exe for the actual path you would follow to reach the file.

Also, there's a dedicated section in these forums for [games running under Wine]("http://ubuntuforums.org/forumdisplay.php?f=313"), inside the main gaming section, [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93"). You can find tutorials and guides to setup many games there.

---

### Post by metalpancake on 2008-01-01
ok, thanks. will do.:)

---

### Post by metalpancake on 2008-01-01
ok, so I tried doing what you said and here's what I got.```
wine/media/cdrom0/autorun.exe: No such file or directory
```

---

### Post by metalpancake on 2008-01-01
Also, can you just run wine with a Gui (i'm no good at the command line)

---

### Post by ahaslam on 2008-01-01
> **metalpancake said:**
> ok, so I tried doing what you said and here's what I got.```
wine/media/cdrom0/autorun.exe: No such file or directory
```

you need a space after wine.
```
wine /media/cdrom0/autorun.exe
```

PS. If this is your 1st time with wine, you'll need to issue the following beforehand:
```
wineprefixcreate
```

---

### Post by RomeReactor on 2008-01-01
There should be a space between **wine** and **/media/cdrom0/autorun.exe**:
```
wine /media/cdrom0/autorun.exe
```

As for a GUI for Wine, I think [Wine-Doors]("http://www.wine-doors.org/wordpress/") is a graphical frontend to Wine, but I haven't used it.

---

### Post by metalpancake on 2008-01-01
Now it's brought up the setup window for the game. only one problem.... it's completely blank:(

---

### Post by BL00dFox on 2008-01-01
You need a space between the "wine" and the location, since wine is the function, not part of the path you want to use it on. Its really quite easy to use wine from the command line, it hardly gets simpler, so I suggest you use the terminal for that. But you can always try wine-doors, etc...

cheers

---

### Post by BL00dFox on 2008-01-01
> **metalpancake said:**
> Now it's brought up the setup window for the game. only one problem.... it's completely blank:(

May I ask what game it is? You might have to use OpenGL:

```
wine /media/cdrom0/autorun.exe -opengl
```

---

### Post by RomeReactor on 2008-01-01
> **metalpancake said:**
> Now it's brought up the setup window for the game. only one problem.... it's completely blank:(

If you have Compiz enabled, try disabling it.

---

### Post by metalpancake on 2008-01-01
sorry, my mistake... I directed it to the autorun.exe file instead of setup.exe. it's installing now.

And the gam btw is children of the nile, a city building game.:)

---

### Post by BL00dFox on 2008-01-01
> **metalpancake said:**
> sorry, my mistake... I directed it to the autorun.exe file instead of setup.exe. it's installing now.

And the gam btw is children of the nile, a city building game.:)

Have fun with it =] Holler if you have any more problems

---

### Post by metalpancake on 2008-01-01
The Game uses two insatll disks, so of course it was going to ask me for the second disk eventually. 

I didn't count on this happeining though....[IMG]http:///home/dylan/Desktop/Screenshot.png[/IMG]

---

### Post by metalpancake on 2008-01-01
it breaks the news to me as such...```
An application is preventing the volume 'CD1' from being ejected.
```

It also bring up:```
Unfortunately, the device system:/media/scd0 (/dev/scd0) named 'CD1' and currently mounted at /media/cdrom0 could not be unmounted. 
The following error was returned by umount command:
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
Moreover, programs still using the device have been detected. They are listed below. You have to close them or change their working directory before attempting to unmount the device again.
                     USER        PID ACCESS COMMAND
/media/cdrom0:       dylan      8478 f.... wineserver
```:confused:

---

### Post by Xavieran on 2008-01-01
Please tell me you have two cdrom drives?
This happened to me once when installing a game on a friends computer under wine but luckily he had two drives...
If anyone has a fix for this it would be greatly appreciated...I do not have two cdrom drives.xD

EDIT: Hello fellow Australian!

---

### Post by metalpancake on 2008-01-01
hmmmm... I am using a lapto which only has one drive.... Might have to google this one...!
(unless anyone knows a way around this problem)
And.... Happy New Year Btw:)

---

### Post by BL00dFox on 2008-01-01
> **metalpancake said:**
> hmmmm... I am using a lapto which only has one drive.... Might have to google this one...!
(unless anyone knows a way around this problem)
And.... Happy New Year Btw:)

I dont know, but maybe you can create a virtual CD drive or two... Is there a Daemon tools version for linux around? (Havent tried...)

---

### Post by metalpancake on 2008-01-01
I think I might just try another game for now that only uses one disk and wait for someone to come up with a solution! thanks for the help!:)

---

### Post by BL00dFox on 2008-01-01
> **metalpancake said:**
> I think I might just try another game for now that only uses one disk and wait for someone to come up with a solution! thanks for the help!:)

I find warcraft 3 works quite well, you can try that, if you have it

---

### Post by Xavieran on 2008-01-01
Good Idea BLOODFox ...

There is a tool called gmountiso available in the repositories that you can use to mount a .iso of the disc you wish to use...so you would just do this:
Right click on cd icon on desktop with the first disc in your drive and click make image of the disk ...
then eject it rn gmountiso pointing it to your .iso image...
then just unmount the .iso in gmountiso and pop the second disk in the drive...

---

### Post by metalpancake on 2008-01-01
> ood Idea BLOODFox ...

There is a tool called gmountiso available in the repositories that you can use to mount a .iso of the disc you wish to use...so you would just do this:
Right click on cd icon on desktop with the first disc in your drive and click make image of the disk ...
then eject it rn gmountiso pointing it to your .iso image...
then just unmount the .iso in gmountiso and pop the second disk in the drive...
__________________
Ok, I will try that.

---

### Post by BL00dFox on 2008-01-01
> **metalpancake said:**
> Ok, I will try that.

Read this:

[http://ubuntuforums.org/showthread.php?t=655147](http://ubuntuforums.org/showthread.php?t=655147)

---

### Post by metalpancake on 2008-01-01
I'm waiting for my disc to make an image right now....

---

