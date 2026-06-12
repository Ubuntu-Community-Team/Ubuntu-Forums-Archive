---
title: "Battery died ubuntu wont start up"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by USFMD82 on 2008-03-04
So I had my computer running Ubuntu and put it in Suspend mode (to conserve energy) and I wasnt able ot make it back to it to shut it down or replug it in. the result was that the battery ended up dying. And when I have gone ot restart Ubuntu it comes up with a prompt to "Press any key"

Then a menu comes up telling me to choosed different options all of them end in a .lstexcept for the option to reboot, command line, and edit I think.. if you want me to handwrite these options down I will.

Whenever I pick the .lst options it goes to anotehr screen then right bakc ot the options screen I was just at (the .lst, reboot...)

Command line takes me to a DOS like interface and I can type stuff in btu have no idea what to type in reboot simply reboots the computer again and takes me right back to the original problem screen.

one other option just caused the screen to go black and then flushed it with a crapload of commands..


Anyone know how to get back to my ubuntu desktop and get it restarted?

---

### Post by wednesday allfather on 2008-03-04
geez, that sounds crazy.  I'm no guru, but I would try to see if you can get your desktop running from the command line. 
 ```
your@computer:~$ gnome-desktop
```

I think that is the command to start gnome.  If you are a XFCE user (Xubuntu) then it will be a different command.  I happen to use Gnome.

---

### Post by wormser on 2008-03-04
I had the same thing happen to me a month ago.  This is what worked for me.  Remove your battery and boot off of AC.  It booted fine for me after doing this.  Then shutdown and put the battery back in and boot back up.  It took me an hour or 2 to figure it out.  I thought I fried my computer.  Hopefully this works for you.

---

### Post by USFMD82 on 2008-03-12
Sorry about this I had forgotten I had posted it. Wromser it seems everytime my desktop deosnt want to boot up leaving it alone for a few hours seems to do the trick.. then it will reup.. last time however I had to actually run a dischk in microsoft and then oddly it worked.. but who knows.. ill tahnk both of you for the input though.. and will give your solutions a try should it happe nagain..

---

### Post by Golem XIV on 2008-03-12
You can always turn off the system by keeping the power button pressed for 5-10 seconds.  No need to wait until the battery runs out.  the other way of killing a non-responsive system is, of course, to take the battery out.

There is a correct way of rebooting a system that apparently doesn't accept keyboard input and it will gracefully reboot (gracefully as in it won't corrupt files, you will still lose unsaved work) - it's a series of keystrokes: Alt+SysRq+k - Alt+SysRq+r - Alt+SysRq+e - Alt+SysRq+i - Alt+SysRq+s - Alt+SysRq+o - Alt+SysRq+b

However, I lost the list and I'm typing it from memory.  I don't really remember what each set of keystrokes does, but generally it enables raw keyboard input, kills running processes, resyncs the disks and mounts them as read-only and finally reboots.  If you want to use this method, you may want to do a search to confirm it first.

---

