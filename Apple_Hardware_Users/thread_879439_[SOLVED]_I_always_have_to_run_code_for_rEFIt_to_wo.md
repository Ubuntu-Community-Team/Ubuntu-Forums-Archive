---
title: "[SOLVED] I always have to run code for rEFIt to work: any workaround?"
date: 2008-08-04
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-08-04
Hi,
I'm not sure there's any workaround for this, but on my aluminum iMac, when I'm on the OS X side and I want to reboot to get to Ubuntu, I HAVE to run this code before I restart or else my rEFIt boot page that gives me the option to boot into Linux will NOT appear on the restart:

```
sudo /efi/refit/enable-always.sh
``` 

Of course this works, but one gets tired of having to do this code. You'd think the 'enable-always' would do what it says, but no deal. 

I HAVE tried re-installing rEFIt at least twice already and it does not seem to make any difference. And I installed rEFIt before I partitioned and everything, so I don't know what I could have done wrong.

If anyone has any ideas, I'd appreciate it.

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-08-04
Well all that really does is bless the refit.efi file so that it boots on startup. My guess is that something (for some reason) is automatically reblessing OSX. Have you installed updates recently? Did you install refit to a special location? 

Oftentimes when installing an update OSX will rebless itself to make sure that it will be booted again on startup. There were some system updates recently, so that may be the issue.

---

### Post by Brightbelt on 2008-08-04
Hi,
  Thanks for responding Cyber. I do install OS X updates regularly, but I am pretty certain that this pattern of OS X usurping the reboot over rEFIt has occurred consistently ever since I installed rEFIt. 

I used rEFIt's package installer to install rEFIt, so I do not think I installed it in an odd location.

I posted about this problem when it first started and it IS possible that someone suggested moving rEFIt to a difference location, but I'm not sure.

Please tell me where rEFIt belongs and I can at least check that for now. 

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-08-04
> **Brightbelt said:**
> Please tell me where rEFIt belongs and I can at least check that for now. 
Well, I am pretty sure you are OK. The refit files are in /efi/refit on your OSX partition. You might check in with the refit devs and see if you can find an answer there, and maybe file a bug or something...

---

### Post by pxwpxw on 2008-08-05
This might be related to the rEFItBlesser, ( folder &#8220;rEFItBlesser&#8221; inside &#8220;Library/StartupItems&#8221; ) and shut-down method.

[http://refit.sourceforge.net/doc/c4s4_safesleep.html](http://refit.sourceforge.net/doc/c4s4_safesleep.html)

and 

[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

I do not use rEFItBlesser,  and don't feel the need for it, maybe just try removing it from the startup items.

---

### Post by Brightbelt on 2008-08-05
Thanks to both of you for replying. Pxwpxw,  I may try your idea about the refit-blesser.
There is a certain safety net about it, though, I'll try to cut the file out to my desktop and keep it there in case I need it.

Again, Many Thanks to you both.
Frank B.

---

### Post by Brightbelt on 2008-08-06
Well, it never fails. When you think you've got a sure-fire solution, something comes up.

My iMac actually WON'T LET ME delete the rEFIt-blesser. It gives me an 'Error 43' and mentions vaguely that there are other files involved; therefore, it cannot complete the action. 

Oh well. Like I said earlier, there is a safety net factor to all this which isn't so bad. I'd be frantic if I lost my Mac OS X partition.

Thanks, Frank B.

---

### Post by pxwpxw on 2008-08-06
> **Brightbelt said:**
> Well, it never fails. When you think you've got a sure-fire solution, something comes up.

My iMac actually WON'T LET ME delete the rEFIt-blesser. It gives me an 'Error 43' and mentions vaguely that there are other files involved; therefore, it cannot complete the action. 


You would need to uninstall rEFIt first as in the reference and then you can remove rEFItBlesser, and then re-install rEFIt the manual way, without using the  rEFItBlesser. (i.e. just use the enable or enable-always method you have been using to fix it). 

> 
Removal when using rEFItBlesser

If you installed through the installer package, these instructions are for you.

While booted into Mac OS X, rename or remove the “efi” folder. For a 100% clean de-installation, also remove the folder “rEFItBlesser” inside “Library/StartupItems”.


The existence of the problem seems to indicate there is some issue with the shut down procedure, for example, a crash or a forced shutdown (power of) or using hibernate/sleep modes. The reference mentions this.

But by all means do what you are comfortable with.:)

---

### Post by Brightbelt on 2008-08-06
Pxw, what does this mean?
> This manual installation method has a drawback that you should be aware of. Since you’re not using rEFItBlesser, Mac OS X updates will disable rEFIt, and the rEFIt menu will show up even when waking from Safe Sleep.


Does that mean in coming out of sleep that the machine will automatically reboot to the rEFIt page?

How would the rEFIt menu "Show up" when OS X comes out of sleep? I don't quite get it.

Many Thanks, Frank B.

---

### Post by pxwpxw on 2008-08-06
> **Brightbelt said:**
> Pxw, what does this mean?


Does that mean in coming out of sleep that the machine will automatically reboot to the rEFIt page?

How would the rEFIt menu "Show up" when OS X comes out of sleep? I don't quite get it.

Many Thanks, Frank B.

I dont get it either - never understood what the problem was, I'm using  the manual method, never had a problem, apart from occasional re-run of the enable.sh (or actually I just use the macosx bless utility that enable runs, with a spare blessed copy of rEFIt on a hfsplus formatted usb stick for insurance).

---

### Post by Brightbelt on 2008-08-06
I'm having trouble with the manual install of rEFIt. It says to copy the efi folder to the root level on your Mac OS X volume.

So, I'm clicking 'Go' at the upper task bar, choosing 'Computer', and double-clicking on my Mac hard drive Icon. Then I'm pasting the efi folder there.

That should do it, but then I run this code like the instructions say:
```
cd /efi/refit./enable.sh
```

And I get returned "No file or directory". The instructions on the rEFIt site say that that return means I've got the efi folder in the wrong place.

I've tried other places to make sure and I always get the same return.

I appreciate any help on this,...

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-08-06
> **Brightbelt said:**
> Pxw, what does this mean?


Does that mean in coming out of sleep that the machine will automatically reboot to the rEFIt page?

How would the rEFIt menu "Show up" when OS X comes out of sleep? I don't quite get it.

Many Thanks, Frank B.
It is talking about safe sleep (read hibernate) as opposed to sleep (read suspend). The first writes session info to disk and turns off the machine, then second stores information in RAM, and turns off uneeded devices (but keeps RAM powered).  Hibernate is good if you need to move your iMac, suspend is good if you are just going to be away from the computer for awhile.

However, for hibernation to work, the startup sequence is mostly like a normal boot except that the kernel (the OSX kernel in this case) detect the saved session info and loads it up. The refitBlesser prevents the refit screen from displaying after hibernation so that it guarantees that OSX is chosen to boot up. What it is trying to say is that if you hibernate, then turn the machine on, then boot into something besides OS X, your saved data could be damaged... So not having refitblesser is OK as long as you remember to boot into OSX after safe sleep.

---

### Post by cyberdork33 on 2008-08-06
```
cd /efi/refit./enable.sh
```should be two commands:

```
cd /efi/refit
```changes to the refit directory...then```
./enable.sh
```actually runs the script

You could also just run the script from wherever you are like most people would:
```
/efi/refit/enable.sh
```

---

### Post by Brightbelt on 2008-08-06
Thanks for the clarity Cyber. Why I didn't realize that was 2 lines of code is beyond me. 

I guess the way they list it with the period starting the second line of code keeps it from looking aligned like 2 separate lines. Duh. 

I got it done and it works. One more question if I might though: 

Doesn't Hibernation oftentimes happen spontaneously while you're away and the computer shuts down on its own? (I may be thinking more of a PC scenario there)

If so, it'd be easy to boot up and forget that the computer might be in hibernation, but I could have this all wrong. 

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-08-06
> **Brightbelt said:**
> Doesn't Hibernation oftentimes happen spontaneously while you're away and the computer shuts down on its own? (I may be thinking more of a PC scenario there)

If so, it'd be easy to boot up and forget that the computer might be in hibernation, but I could have this all wrong.That is not at all impossible, but if it is functioning that way, you can rectify this behavior in your power settings (on both OS X and Ubuntu).

---

### Post by ps_ on 2010-10-30
Many thanks guys !

i removed rEFItblesser from /library/startupitems/refitblesser

did "/efi/refit/enable.sh" on the terminal and now it works :)

---

