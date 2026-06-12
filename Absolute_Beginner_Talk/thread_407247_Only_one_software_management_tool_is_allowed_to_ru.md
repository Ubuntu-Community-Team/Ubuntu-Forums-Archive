---
title: "Only one software management tool is allowed to run at the same time"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by rocka on 2007-04-11
Hi all,

I got a message pop up saying I had 192 updates to be installed, but when I clicked on the little icon at the top of the screen and then put in my password, it says:

"Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first."

How do I find out what is running already? [ie: what is the Ubuntu equivalent of XP's task manager?]

 - and then, how do I stop it?
thanks in advance for your guidance :)

---

### Post by ParkingBrake on 2007-04-11
System - Administration - System Monitor
Then just type sudo kill ID (# of app to kill) in a terminal window

---

### Post by jem7v on 2007-04-11
If you have Synaptic running, Add/Remove running, a .deb installer running, or dpkg, apt-get or aptitude running in a terminal, those would all be software managers (aka package managers). You can only use one at a time, really, because they all use the same tools.

---

### Post by rocka on 2007-04-11
thanks a lot for your quick resonse, ParkingBrake. :)

I don't see either of those two programs running in the list of processes...
Maybe it's some other program causing the problem?
Is there a way I can copy that list from the System Monitor to here?

Thanks, again

---

### Post by j002 on 2007-04-11
type 

dpkg --configure -a

to see what's happening, and CTRL-C to stop it.

---

### Post by rocka on 2007-04-11
Hi jem7v,
just spotted your reply after I posted...

I'm fairly sure I'm not running any of those things you mentioned. I don't see dpkg or apt-get in the list. I'm not running anything in a terminal - all I have open is Firefox.

---

### Post by rocka on 2007-04-11
> **j002 said:**
> type 

dpkg --configure -a

to see what's happening, and CTRL-C to stop it.

Hi j002 - thanks for your help...

I put that in a terminal window and it came back with:

dpkg: requested operation requires superuser privilege



now, I vaguely remember something about that from a long time ago when I was trying Redhat 6  - something to do with sudo, is it?

---

### Post by bobplano on 2007-04-11
yes

```
sudo dpkg --configure -a
```

and then type in your password when it prompts for it

---

### Post by rocka on 2007-04-11
Thanks Bob
- I was just reading through a few pages about sudo from Google...


so:
here is the output from that command pasted in:

> merlin@merlin-desktop:~$ sudo dpkg --configure -a
Password:
Setting up openoffice.org-math (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-draw (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-gtk (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-calc (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-common (2.0.2-2ubuntu12.2) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 477 strings at 20 - 279c
Wrote aliases at 279c - 2948
Wrote parents at 2948 - 32f8
Wrote literal globs at 32f8 - 3354
Wrote suffix globs at 3354 - 66ac
Wrote full globs at 66ac - 66d0
Wrote magic at 66d0 - bd74
Wrote namespace list at bd74 - bd84
***
Updating OpenOffice.org's dictionary list... done.

Setting up python-uno (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-gnome (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-java-common (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-impress (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-base (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-writer (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org (2.0.2-2ubuntu12.2) ...

Setting up openoffice.org-evolution (2.0.2-2ubuntu12.2) ...

merlin@merlin-desktop:~$


I still don't see anything about synaptic or aptitude in there though. . . 
Does this make sense to anyone out there???
LOL

---

### Post by jem7v on 2007-04-11
Well, it looks like it finished what it was doing... you could try installing your updates again, now, and see what happens this time, I suppose!

dpkg is another software/package manager, you see.  All the things I mentioned in that earlier post are variations of the package manager.

---

### Post by rocka on 2007-04-12
YES!

it's working now...

thanks a lot to all who helped.

---

### Post by sethjbaker on 2008-07-19
where do i type i know this is a stupid question but still i need help 

dpkg --configure -a

---

### Post by munkyeetr on 2008-07-19
> **sethjbaker said:**
> where do i type i know this is a stupid question but still i need help 

dpkg --configure -a

you type it in a terminal window (**Applications** -> **Accessories** -> **Terminal**)

---

### Post by Partyboi2 on 2008-07-23
> **sethjbaker said:**
> where do i type i know this is a stupid question but still i need help 

dpkg --configure -a
Remember to put sudo infront
```
sudo dpkg --configure -a 
```

---

