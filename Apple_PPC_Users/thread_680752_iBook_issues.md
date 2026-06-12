---
title: "iBook issues"
date: 2008-01-28
forum: Apple PPC Users
---

### Post by oakley on 2008-01-28
I'm trying to install Dapper Drake on an old second generation iBook, (the two-tone clamshell with a firewire port). The live CD boots just fine but the graphical desktop is a mess. It's difficult to describe, but here goes.

Draw an imaginary horizontal line on the display such that one third of the screen is above the line and two thirds below. Most of Gnome top-edge menu panel is displayed on the second row below the line, with the remainder displayed on the first row below. Most of the bottom-edge menu panel is displayed on the second row above the line, with the remainder displayed on the first row above. It looks kind of like this:
[FONT="Courier New"]
---------------------------------------------------------------- (bottom-edge panel)
-------------- (remainder of bottom-edge panel)
---------------------------------------------------------------- (imaginary horizontal line)
-------------- (remainder of top-edge panel)
---------------------------------------------------------------- (top-edge panel)
[/FONT]
The cursor cannot be moved above the line directly but wraps to the top third of the screen when moved off the edge of the screen below the bottom two-thirds.

I've tried several of the boot options included on the live CD but none of them configure the display properly. Any ideas? Thanks in advance for the help!

---

### Post by daladheri on 2008-01-28
I have had this happen with an Intel Linux install but not a PPC Install. I think it has to do with video drivers. Maybe Ubuntu doesnt support the video on the ibook. Hopefully someone else will reply with an answer.

---

### Post by stream303 on 2008-01-28
Personally I only use the "alternate" install iso, not the live-cd.  If you are determined to run Dapper, I'd make sure to start with the latest respin, 6.06.2

There are some handy hints in these two articles for older machines:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

and

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Let us know how it goes!

---

### Post by jtbrookreson on 2008-01-28
I totally suggest the alternate CD install, as well with using Dapper. I am having issues with 6.10, but that might be because I am an idiot.

But I also recomend that once you get 6.04 running, install Xubuntu as well (see my earlierthread on Ubuntu and Xubuntu for some links) [http://ubuntuforums.org/showthread.php?t=680221](http://ubuntuforums.org/showthread.php?t=680221) . It is a slimmed down user interface that doesn't make the old hardware sweat as much...

-JTB

---

### Post by oakley on 2008-02-04
Thanks to all for the assistance. Using the alternate CD I was able to install without encountering any additional issues. My old iBook can now dual-boot in either Mac OS or Ubuntu. Cool!

---

### Post by Rubix Hacker on 2008-03-05
I have 7.04 running on the "blueberry" clamshell with no problems. Although I did experience problems the first 100 times I tried. But heres what I did.
[LIST]
[*]Alternate install cd
[*]On the keyboard layout option select no
[*]select U.S. Macintosh on keyboard layout
[*]finally no on download language support
[/LIST]

Before I would successfully install it, but when I logged in Nautilus failed and half the applets.
But using this method I have successfully installed on two 3g ibook clamshells.

Hope this helps anybody

---

### Post by stream303 on 2008-03-05
That's an insanely great tip!

I do that out of habit, but wonder how many other installs were botched by trying to set up a non-us keyboard during install?

If you need a non-us keyboard, I wonder how setting it up initially with a us-keyboard, doing the updates, and then trying to change your locale / keyboard goes...

Thanks!

Update: On a related note, I wonder if this affects our Debian brothers/sisters?  Debian updates you right during install, and if you've got a non-us keyboard selected initially, I wonder if this problem would carry over...

---

