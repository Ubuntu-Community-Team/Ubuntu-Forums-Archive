---
title: "Downgrade xorg, Catalyst and Compiz?"
date: 2008-01-29
forum: Arch and derivatives
---

### Post by Ub1476 on 2008-01-29
Hello, I have an ATI X1400 with the Catalyst 8.01 drivers (from repos). I read on the forum that Catalyst and Compiz doesn't work with the xorg version Arch is using, but is it possible to downgrade it? I don't really want to use any previous drivers with XGL (rather stay with Metacity then). Should I let pacmn ignore xorg, if Catalyst will support Archs xorg (1.4 is it?) soon?

And just another quick question. I read hibernate should work 100% on Cat 8.01, but I just get a blank screen. Do I need to modify any files?

---

### Post by fwojciec on 2008-01-29
The problem with downgrading xorg is that xorg is not a single package but really a collection of packages used together, so in order to downgrade xorg you'd need to downgrade a whole bunch of them (at the very least "xorg-server", it's immediate dependencies, xf86-[driver] packages and so on).  

The method to downgrade would be the usual -- use the PKGBUILDs from the ABS tree, change the versions to what you want them to be, compile and install with pacman.  At this stage it would also be necessary to put the newly installed packages in IgnorePkg section of pacman.conf so they don't get updated on the next system update.

It's a major hassle, in other words, and given that xorg is such a central part of the system it's not going to be an easy procedure and it's likely to cause problems in the long run.  I'd much prefer not using Compiz than having to deal with this, for example, but then the decision is easy for me because I wouldn't use Compiz in the first place ;)

---

### Post by aeto on 2008-01-29
or use packages from your cache if you haven't whipped them. and you could try your luck on mirrors that are at least a day late on updates, like pacific. that way pacman -U ftp:/bla bla/bla.pkg.tar.gz

---

### Post by Ub1476 on 2008-01-30
Thanks, I think I'll stay with current xorg. Anyone know if ATI will update their xorg comparability soon? Is it really a huge difference between xorg 1.3 and 1.4?  

And if someone can answer my hibernate/sleep question that would be great:)

---

### Post by BOBSONATOR on 2008-01-30
echo -n mem > /sys/power/state 

Will suspend on 8.1,

Im in the same boat as you for compiz + arch + cat 8.1, its a no-go untill ati get their shiza straight

---

### Post by Ub1476 on 2008-01-30
Cool, that worked nice. Any way to do this automatically when I close the lid?

---

### Post by fwojciec on 2008-01-30
> **Ub1476 said:**
> Cool, that worked nice. Any way to do this automatically when I close the lid?

First - you need the acpid daemon installed and running for this...

Second - edit /etc/acpi/handler.sh file and look for the section that starts with "button/lid)".  On my system it looks like this:
> button/lid)
#echo "LID switched!">/dev/tty5
;;
Edit it so it looks like this:
> button/lid)
#echo "LID switched!">/dev/tty5
**echo -n mem > /sys/power/state**
;;

Now you just have to restart the acpid daemon (/etc/rc.d/acpid restart) and your computer should suspend when you close the lid.

---

### Post by aeto on 2008-01-30
GUIs like KLaptop make power management easy (no user input in any configuration file, just asking for root permission so the app itself can edit them). So you may want to get one of them.

---

### Post by tigrmesh on 2008-02-09
I followed fwojciec's instructions to edit /etc/acpi/handler.sh:
> **fwojciec said:**
> 
button/lid)
#echo "LID switched!">/dev/tty5
echo -n mem > /sys/power/state
;;


Now you just have to restart the acpid daemon (/etc/rc.d/acpid restart) and your computer should suspend when you close the

I did this.  Hibernation worked perfectly.  How do I get it to resume?  I tried [esc], ctrl+alt+backspace, and hitting the enter key.  The fan comes on, but nothing else happens.

---

### Post by fwojciec on 2008-02-09
> **tigrmesh said:**
> I followed fwojciec's instructions to edit /etc/acpi/handler.sh:


I did this.  Hibernation worked perfectly.  How do I get it to resume?  I tried [esc], ctrl+alt+backspace, and hitting the enter key...

I'm assuming that resume works correctly when you hibernate by typing the command from command line...
It depends on your laptop.  One of my laptops wakes up automatically when I open the lid; on another laptop I need to press the power button.

EDIT: Actually, the way you describe the problem it seems that the problem is with the configuration of hibernate/resume on your laptop in general, not with the particular method of triggering the hibernation routine I described above.

---

### Post by tigrmesh on 2008-02-09
> **fwojciec said:**
> I'm assuming that resume works correctly when you hibernate by typing the command from command line...

[snip]

EDIT: Actually, the way you describe the problem it seems that the problem is with the configuration of hibernate/resume on your laptop in general, not with the particular method of triggering the hibernation routine I described above.
I think you're right.  Typing pm-hibernate gives me the same result.

I had suspend/resume on my "whenever I get around to it" list.  Then I saw your post and it looked easy.  :)  I'll search further in the Arch forums.

Thanks for the help.

---

### Post by fwojciec on 2008-02-09
> **tigrmesh said:**
> I think you're right.  Typing pm-hibernate gives me the same result.

I had suspend/resume on my "whenever I get around to it" list.  Then I saw your post and it looked easy.  :)  I'll search further in the Arch forums.

Thanks for the help.

try the various "quirk" switches for the pm-suspend command (pm-suspend --help for more info -- I think...).  see which one makes your system wake up from suspend correctly.  if nothing works try playing with hibernate-script -- it has a wealth of configuration options so you might be able to find what works that way.  finally -- in my experience compositing (especially xcompmgr) tends to prevent my computers from waking up correctly (nvidia video cards), so you might try disabling any compositing if you're using it.

---

### Post by tigrmesh on 2008-02-09
Thanks, I'll try it tomorrow.  I'm done with rebooting for the day.

---

