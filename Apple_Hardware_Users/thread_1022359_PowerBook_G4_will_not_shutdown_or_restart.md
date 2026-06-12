---
title: "PowerBook G4 will not shutdown or restart"
date: 2008-12-26
forum: Apple Hardware Users
---

### Post by Sturgis on 2008-12-26
I have a PowerBook G4 Titanium 1GHz with an ATI "card".

Using the information I have gleaned off this forum, I was able to install the PPC alternate version of Ubuntu 8.10 and get it to boot up reliably with video and sound.

However it will not do a shutdown or restart from either the user desktop or from the login screen.

The display goes to a spreading white screen and all disk activity ceases until I press and hold the power button.

I have conducted several searches of the forum and internet in general looking for possible solutions but I have not stumbled across any method.

Failure to reliably shutdown or restart is kind of a deal breaker.

Anyone have any suggestions that I may have overlooked?

Thanks

---

### Post by stream303 on 2008-12-27
Wow - that's a new one for me.  I'm interested to see how this turns out.

In the meantime, can you safely shut it down from the command line?  Try this by pulling up a terminal:

```
sudo shutdown -h now
```

You can also try this from a virtual terminal, ie use ctrl-alt-f2 and login.  Then issue that same command to shut the machine down.

If you just want to reboot it, change the parameter to -r

```
sudo shutdown -r now
```

It sounds like there is a problem when it dumps the graphics upon shutdown, so perhaps by going into a virtual terminal and then shutting it down from there might be the best way to go.

Maybe this will help while the hunt is on to track down that shutdown bug.

---

### Post by Sturgis on 2008-12-28
Yeah, either one of those methods work.

The screen still goes to that sickly white with dark blotch image as soon as either command is issued but the machine will carry out the task of shutdown or reboot.

Upon startup now in verbose mode it no longer whines about having to repair the file system so that's a good thing.

While this is a good work around, we still can not deploy this to the users. Most of them are lucky to find the power button and keyboard.

I don't know if the issue is related to video or ACPI. Still looking.

Thanks

---

