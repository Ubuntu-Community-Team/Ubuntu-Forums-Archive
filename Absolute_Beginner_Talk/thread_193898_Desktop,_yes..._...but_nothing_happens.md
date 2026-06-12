---
title: "Desktop, yes... ...but nothing happens"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by muhkayoh on 2006-06-10
Hi all,

I'm trying out the live CD and I can see the ubuntu desktop, but I can't get anything to happen.  For example, when I tried launching Firefox, I saw the briefest flicker of a suggestion of a window, then the wait icon... ...and then nothing.  Same thing when I tried launching the GIMP.  I use both the  GIMP and FF on my Windows XP set-up, so I thought I'd try those first, but no go.  I've booted the live CD up 3 times now, and it always ends the same way:  No applications ever start, and eventually the mouse becomes sporadically frozen (frozen for 10-15 seconds, then mobile for 5 -10 seconds).  Eventually, hovering over stuff no longer yields any tool tips (or whatever they're called) and no amount of clicking seems to do anything.  All 3 times I've had to unplug the computer to get it to shut down.  Right now, I'm back in old XP mode so I could visit the forum and ask for help.

Here's what I know about my box:

hp pavilion 533w with a celeron processor, 2 GHz, 256 MB RAM

Also, while I'm new to linux (at least on the desktop side), I'm not completely helpless with computers and programming.  I know php, mysql and that sort of thing.

Anyway, I'd love to really try this out and I want to move over to linux, especially since I mostly use Windows ports of linux software anyway.  But I have to figure out how to get the live cd working first.  Any help would be appreciated.

Thanks,

Matt Jordan

---

### Post by muhkayoh on 2006-06-10
Oh, one more thing:

I wrote down these two items that seemed to be possible negatives/problems during the boot process:

PCMCIA not present
mount: function not implemented

I don't know what either of those mean, but there thay are in case they matter.

Thanks again,

Matt Jordan

---

### Post by pdc303 on 2006-06-10
checking the system logs comes to mind.

Press Control+Alt+F1 to switch to a fresh console and log in.

```
cd /var/log
ls
```

I don't know Linux well enough to know exactly which log file is your best bet here but I expect you should look at dmesg, kern.log, the logs in /var/log/gdm/ and maybe even the xorg logs.

To do this:
```
nano kern.log
```

the freezing issue and vanishing tooltips would make me think it's some sort of X issue. I guess apps under gnome could fail due to a 'screen' problem.

I don't know what "mount: function not implemented" means.

These are my thoughts anyway.

---

### Post by aysiu on 2006-06-10
Terminal output may help you diagnose the problem, too.

Yes, Firefox dies out when you click on it.

What happens (or what error messages do you get) if you type ```
firefox
``` in the terminal?

---

### Post by muhkayoh on 2006-06-10
pdc303 and aysiu,

Thanks for the replies.

When I type in firefox, nothing happens.  For the heck of it, I also tried sudo firefox (keeping in mind that I have no idea what I'm doing).  I got this output:

(firefox-bin: 7339): Gtk-WARNING**: cannot open display:

Then it told me something about not being a good idea to try this without -H; the computer then proceeded to try it with -H on its own and the output was similar:

(firefox-bin: 7390): Gtk-WARNING**: cannot open display:

I was able to see GIMP open this time, so at least there's that.  But it would really speed things up to get firefox running so that I can a) see if I can access the internet and, b) if so, learn how to use ubuntu by referring to the wiki and so forth.

I'm curious about aysiu's statement, "Yes, Firefox dies out when you click on it."  Do most people have trouble starting firefox from the live CD?

Thanks again for the help.

Matt Jordan

---

### Post by aysiu on 2006-06-10
No, I was just summarizing what you saw.

Firefox doesn't die it for most people... not unless they don't have enough RAM to be running the live CD. 256 MB of RAM should be enough... not plenty, but enough.

---

### Post by muhkayoh on 2006-06-10
Some progress.

I clicked on firefox in the applications menu and just waited.

And waited.

Maybe as long as ten minutes, and then firefox actually appeared with the Ubuntu start page that resides on the disc.  So I clicked on the link to the ubuntu site and waited some more.

But this time, after another ten or so minutes, the disc stopped spinning in the drive and I could get no further response (mouse movement, etc.).  So, again, I had to unplug the computer and reboot XP.

I think I'm done for the night and it may be next weekend before I get time to play with ubuntu again.  Thanks for the assistance.  :D 

Matt Jordan

---

