---
title: "Quirks w/ Ubuntu (Feisty)"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ~Maxx on 2008-01-08
I've just reloaded Ubuntu FF on my old Compaq (Deskpro EP series, Pent II, 400Mhz, 384 MB RAM).  I had made an attempt a couple of months ago to load it with Xubuntu, but ran into some as-yet unresolved issues, so I decided to start again with a distro that (while a bit sluggish) actually works on this machine.  

Anyway...  I've noticed a few minor things that have me stumped.  For one - I am required to press the "number lock" key each time I boot up in order for the number keypad to work.  There is a setting for this in BIOS, but no matter how I change it it behaves the same. 

I addition, when I choose "shutdown" in Ubuntu the PC does not power down completely.  The drives shut down, but the power supply and front LED remain on and the Ubuntu splash screen remains on the monitor.  I found a possible fix for this by searching for a message I noticed I was getting during boot up (after the "Grub loading" message appears I see a line which reads something to the effect of "BIOS age (1999) fails cutoff (2000) acpi=force is required to enable ACPI").  Unfortunately I'm not entirely sure how to implement it.  The thread is [here]("http://ubuntuforums.org/archive/index.php/t-433404.html") if someone wouldn't mind filling in the details for me.

Lastly there seems to be an oddity with my printer.  This machine is connected via a crossover cable to my main PC (a slightly newer Gateway w/ WinXP Home - if details are important let me know) with which the internet connection and (hopefully soon) the printer are shared.  Printer is a Lexmark 4300.  I noticed when setting up the network printer in Ubuntu that the 4300 was not listed, so I tried the two closest models, but both had the same effect.  When trying to print with Ubuntu the print progress screen comes up in XP on the Gateway, but the progress bar hangs at 0% and the document doesn't print.

Sorry for the long post and number of questions.  But I'm assuming that they're all simple things that I'm just not privy to yet.  Thanks in advance for any advice.

All the best!

~Maxx

---

### Post by sumguy231 on 2008-01-09
> I am required to press the "number lock" key each time I boot up in order for the number keypad to work. There is a setting for this in BIOS, but no matter how I change it it behaves the same.
You can change that somewhere in the settings, but I'm a Kubuntu guy so I don't know where that is specifically. In Kubuntu the option is 'NumLock on KDE startup (Turn on/Turn off/Leave Unchanged). Check the keyboard settings.

> I addition, when I choose "shutdown" in Ubuntu the PC does not power down completely. The drives shut down, but the power supply and front LED remain on and the Ubuntu splash screen remains on the monitor. I found a possible fix for this by searching for a message I noticed I was getting during boot up (after the "Grub loading" message appears I see a line which reads something to the effect of "BIOS age (1999) fails cutoff (2000) acpi=force is required to enable ACPI"). Unfortunately I'm not entirely sure how to implement it. The thread is here if someone wouldn't mind filling in the details for me.
I'm not sure if your computer even supports ACPI (what lets the operating system power off the computer) if it's old enough to have a Pentium II. Did it ever work in any other operating system on that computer? Still, if you want to try that you can test it this way:
1.) Run 'gksu gedit /boot/grub/menu.lst'.
2.) Find the line that looks like this:
```
# defoptions=quiet splash
```
3.) Add the text 'acpi=force' to the end. It should look like this:
```
# defoptions=quiet splash acpi=force
```
4.) Save the file, and reboot. Then see if it can power itself off.

---

### Post by ~Maxx on 2008-01-09
> You can change that somewhere in the settings, but I'm a Kubuntu guy so I don't know where that is specifically. In Kubuntu the option is 'NumLock on KDE startup (Turn on/Turn off/Leave Unchanged). Check the keyboard settings.
Good idea, but I've been all over the keyboard options already with no luck.  Thanks though!

> I'm not sure if your computer even supports ACPI...  Did it ever work in any other operating system on that computer?
Really!?  That could explain a lot!  When I got it it had Win95, but was password protected.  So I used my Gateways XP install disk just to get it usable for 30 days while I figured something else out for it.  That's when I came across Ubuntu.  Anyhow...  I honestly don't remember weather it worked properly with those or not.  I'll definitely research the matter now that I know what I'm looking for.  Not that it's that big a deal to have to manually push the button after the drives power down.  Just a quirk I noticed.

The fix you suggested above is very similar to the thread I referenced via the link in my initial post...
> edit your /boot/grub/menu.lst (or /boot/grub/grub.cfg for Grub2)

Find this entry (your kernel and hard disk/partition specifications might be different and you may not have a UUID entry) and add the part in bold to yours.

"title Ubuntu, kernel 2.6.20-15-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=3015a7a1-6e5d-42d6-934d-193459bed89b acpi=force
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault"
I'm doing my best not to sound like a complete moron here, but the truth is I'm just not sure how to implement this.  I didn't actually get around to learning anything about the command line.  In other words...  When I open a terminal and see my user and computer names...  What then?  Sorry to be so dense on the matter.  I just haven't really had a chance to break the ice with this stuff yet, and a lot of things I've read still seem to be over my head.

Thanks so much for replying!

---

### Post by sumguy231 on 2008-01-09
> The fix you suggested above is very similar to the thread I referenced via the link in my initial post...
The difference is that the solution in the link you posted will get overwritten on some system updates.


> I'm doing my best not to sound like a complete moron here, but the truth is I'm just not sure how to implement this. I didn't actually get around to learning anything about the command line.
You don't actually need to use the command line to do this. I would be happy to clarify any part of the instructions you need help with, just tell me what. I'm sure someone else could recommend a good command line tutorial if you want to learn more about that.

If it is old enough to have shipped with Windows 95 though, I do doubt that this would work but I'm not exactly sure. I guess it's worth a try. What year is the computer from?

---

### Post by ~Maxx on 2008-01-09
PC was actually manufactured in `99.  It belonged to a school though, which (I'm assuming) was running Win95 for their network at the time.  So I doubt it shipped with Win95.  That's just what they were using.

Anyhow...  I did a bit of reading, and it seems that if the machine were ACPI capable there would be an option for it under the power management settings in BIOS.  No such settings exist, so I'll assume that the machine does not support ACPI.  Not a big deal really.  I just have to hit the button to turn it off.  Actually if I leave it on the network card will restart the PC when my main machine turns on.  So it may be a convenience in disguise.

The numlock issue, however is a tad annoying.  And I'm still not sure what to do about the printer.  It acts as if it should work, but just won't go the last step and actually print the document.  I did read on a recent post that Lexmarks are not well supported.  So maybe I'm just out of luck in that regard.

Thank you so much for your replies.  Any suggestions anyone might have regarding the printer or numlock key would be much appreciated.  I'll keep digging on my end and post my findings.

---

### Post by sumguy231 on 2008-01-09
> I did read on a recent post that Lexmarks are not well supported.
This is true, I've had a couple Lexmarks that were simply not supported, I'm not sure about your model. If you're ever looking for a new printer, I recommend HP printers - they're the most supported in Linux(as far as I know all Deskjets work)  and are also pretty good printers for regular-type stuff.

---

### Post by ~Maxx on 2008-01-10
HP printers, huh?  I'll definately keep that in mind.  Unfortunately we just bought this one about 6 months ago, so I'm stuck with it for now.  It looks like this is all stuff I'm just going to have to deal with.  Fairly minor all in all, so I can't say that I'm terribly discouraged.

Again - thanks so much for your help!

---

### Post by stchman on 2008-01-10
> **~Maxx said:**
> I've just reloaded Ubuntu FF on my old Compaq (Deskpro EP series, Pent II, 400Mhz, 384 MB RAM).  I had made an attempt a couple of months ago to load it with Xubuntu, but ran into some as-yet unresolved issues, so I decided to start again with a distro that (while a bit sluggish) actually works on this machine.  

Anyway...  I've noticed a few minor things that have me stumped.  For one - I am required to press the "number lock" key each time I boot up in order for the number keypad to work.  There is a setting for this in BIOS, but no matter how I change it it behaves the same. 

I addition, when I choose "shutdown" in Ubuntu the PC does not power down completely.  The drives shut down, but the power supply and front LED remain on and the Ubuntu splash screen remains on the monitor.  I found a possible fix for this by searching for a message I noticed I was getting during boot up (after the "Grub loading" message appears I see a line which reads something to the effect of "BIOS age (1999) fails cutoff (2000) acpi=force is required to enable ACPI").  Unfortunately I'm not entirely sure how to implement it.  The thread is [here]("http://ubuntuforums.org/archive/index.php/t-433404.html") if someone wouldn't mind filling in the details for me.

Lastly there seems to be an oddity with my printer.  This machine is connected via a crossover cable to my main PC (a slightly newer Gateway w/ WinXP Home - if details are important let me know) with which the internet connection and (hopefully soon) the printer are shared.  Printer is a Lexmark 4300.  I noticed when setting up the network printer in Ubuntu that the 4300 was not listed, so I tried the two closest models, but both had the same effect.  When trying to print with Ubuntu the print progress screen comes up in XP on the Gateway, but the progress bar hangs at 0% and the document doesn't print.

Sorry for the long post and number of questions.  But I'm assuming that they're all simple things that I'm just not privy to yet.  Thanks in advance for any advice.

All the best!

~Maxx

As far as the numlock I believe there is a numlockx package.  My PC does this and I find it VERY minor.

Your PC not shutting down completely is a BIOS thing.  I had an older PC and it required me to flash the BIOS and then it worked fine.

You said you have the PCs hooked up via a crossover cable?  In that case you are not going to get an IP assigned.  Do you have internet access.  If yes cable/DSL routers are very cheap and easy to use.

As far as networking the printer I recommend you hook the printer up to the Ubuntu box as I have found it WAY easier to share printer with Ubuntu to XP than the other way around.  I have a tutorial to help you with this.
[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

 Be warned Lexmark printers are not very good with Linux as Lexmark has decided not to support Linux very well.  I could not find the 4300 at openprinting.org.  HP is far better with Linux.

---

### Post by ~Maxx on 2008-01-11
> As far as the numlock I believe there is a numlockx package.Good to hear!  What's a numlockx package?

> Your PC not shutting down completely is a BIOS thing.  I had an older PC and it required me to flash the BIOS and then it worked fine.I've never flashed my bios before, but have read a bit about it.  I may give that a try at some point.  As I mentioned above, though, I may just leave it as is.

> You said you have the PCs hooked up via a crossover cable?  In that case you are not going to get an IP assigned.  Do you have internet access.  If yes cable/DSL routers are very cheap and easy to use.I do have internet access shared between the two machines.  Initially I didn't see the need for a router when networking only two PCs.  But it does seem that having one would open up more possibilities.  I'll definately look inti it.

> As far as networking the printer I recommend you hook the printer up to the Ubuntu box as I have found it WAY easier to share printer with Ubuntu to XP than the other way around.  I have a tutorial to help you with this.
[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)I'll give it a try!

>  Be warned Lexmark printers are not very good with Linux as Lexmark has decided not to support Linux very well.  I could not find the 4300 at openprinting.org.  HP is far better with Linux.I remember reading that very thing somewhere!  what a shame...

By the way...  Your website is an absolute wealth of information.  I've bookmarked it and will be spending a good deal of time there.

Thank you!

---

### Post by stchman on 2008-01-11
> **~Maxx said:**
> Good to hear!  What's a numlockx package?

I've never flashed my bios before, but have read a bit about it.  I may give that a try at some point.  As I mentioned above, though, I may just leave it as is.

I do have internet access shared between the two machines.  Initially I didn't see the need for a router when networking only two PCs.  But it does seem that having one would open up more possibilities.  I'll definately look inti it.

I'll give it a try!

I remember reading that very thing somewhere!  what a shame...

By the way...  Your website is an absolute wealth of information.  I've bookmarked it and will be spending a good deal of time there.

Thank you!

The numlockx package is for doing the very thing you want to do.  Google it and you will find lots of info.

Flashing the BIOS on a mainboard is very easy.  You will have to see if the mainboard maker has an updates BIOS for your particular board.

The problem with ICS is that you have to leave one PC on all the time as it acts as a router.  This is a big waste of electricity.  I have found wired routers at PC swap meets for under $10.  yes a a router does open up many more possibilities.

---

### Post by sumguy231 on 2008-01-11
> Good to hear! What's a numlockx package?
A software package in the Ubuntu repositories which is supposed to help you manage numlock key behavior. Never used it myself.

---

### Post by ~Maxx on 2008-01-13
Numlockx did the trick!  Initially I noticed that it only worked *after* log-in.  But I searched for some more info in the forums here (assuming that others had run into the same issue), and found [this]("http://ubuntuforums.org/showthread.php?t=578749&highlight=numlockx") post which advised how to correct the issue.

Thanks a bunch!

---

