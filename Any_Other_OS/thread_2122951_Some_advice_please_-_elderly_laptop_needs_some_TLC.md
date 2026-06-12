---
title: "Some advice please - elderly laptop needs some TLC in the form of a suitable distro"
date: 2013-03-06
forum: Any Other OS
---

### Post by scrumpypaul on 2013-03-06
Hi,

Absolute beginner here.

I have a Gericom Ego MS1003 laptop from around a century ago.

It did run XP. Not any more.

It had a bit of a hissy fit a few weeks ago and I ended up putting Lubuntu on it, which worked great for a few hours but then something popped - I think it was the hard drive.

Been on fleabay and bought a 6.5gb drive which seems to work okay but I'm struggling to put a lightweight distro on it.

Tried Lubuntu - it just sort of froze halfway through.

Tried Cr-OS - no go.

Tried Puppy Linux - came up with some sort of kernel error (pae?)

Currently trying to put Mint on it but it doesn't seem to be doing anything. In fact - no - it comes up with "This kernel requires the following features not present on the CPU: pae - Unable to boot - please use a kernel appropriate for your CPU.

That might as well be Dutch to me.................. If someone could explain what it means and whether it is something that can be bypassed/fixed/ignored??

Going to try Crunchbang next.

Any suggestions please as to the best lightweight OS I can use?

The laptop will be used by my 12 year old daughter to surf and that's about it.


TIA,

Scrumpypaul

---

### Post by Cheesemill on 2013-03-06
Can you give us any specs of the machine like CPU, RAM, graphics etc.

Without them we are all just going to be guessing.

---

### Post by scrumpypaul on 2013-03-06
I couldn't tell you at the minute.

Crunchbang loads via the DVD so I will have a hack at that tomorrow - but if anyone can tell me how to enable pae that would be a big help I think....

---

### Post by Cheesemill on 2013-03-06
PAE isn't something you can enable. It's a feature that your CPU either has or doesn't.

A big +1 for #! if you can get it running though, it's my go to distro for old machines.

---

### Post by theDaveTheRave on 2013-03-06
Does the following look like it might be the same spec as your machine ?

[http://download.gericom.com/NOTEBOOK/Ego-Serie/MS1003/DATASHEET/MS1003.pdf](http://download.gericom.com/NOTEBOOK/Ego-Serie/MS1003/DATASHEET/MS1003.pdf)

If so you may be able to run a copy of linux from a USB key (or put it on your new HDD and run that from the USB in the first instance)

Quick note:

I had a laptop die on me about a year ago, I pulled out the HDD, pluged it into another pc (via USB) and everything worked beautifully!
Make sure that you have definately got a 32 and not 64 Bit version.
If you can get linux on a USB to work, open a terminal, type the following

ls hw

and post the outupt back to here.

That is of course if you can't get crunchBang to work.

David

---

### Post by mips on 2013-03-06
> **theDaveTheRave said:**
> Does the following look like it might be the same spec as your machine ?

[http://download.gericom.com/NOTEBOOK/Ego-Serie/MS1003/DATASHEET/MS1003.pdf](http://download.gericom.com/NOTEBOOK/Ego-Serie/MS1003/DATASHEET/MS1003.pdf)

That's actually not that 'old'. With enough ram it will run XFCE just fine.

---

### Post by aromo on 2013-03-06
All modern distros require the processor to PAE (some kind of power management capability AFAIK).

My wife's Thinkpad R50 couldn't take Lubuntu 12.10 because of that so it is stuck with Lubuntu 12.04.

---

### Post by Cheesemill on 2013-03-06
> **aromo said:**
> All modern distros require the processor to PAE (some kind of power management capability AFAIK).

PAE (Physical Address Extension) is actually a feature that enables addressing of more than 4GB of RAM when running a 32-bit OS.

---

### Post by sanderj on 2013-03-06
> **scrumpypaul said:**
> 

That might as well be Dutch to me.................. 

... hey, I can help with Dutch! Dat is geen enkel probleem. ;-)

But seriously: how much RAM has it got? 1GB RAM could be OK for Ubuntu.

If RAM is 256 MB or even lower, IMHO any current Linux **with** a current webbrowser will be very slow.

---

### Post by black veils on 2013-03-06
the mini.iso from ubuntu will allow non-pae, here is a guide if you need it [http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

---

### Post by sanderj on 2013-03-06
And ... bingo. The typical ubuntu forums run away thread: the original poster posts a question, and then a loooot of replies, possibly overwhelming the OP.

---

### Post by patriot56 on 2013-03-06
> **scrumpypaul said:**
> Hi,

.......Tried Puppy Linux - came up with some sort of kernel error (pae?)

Currently trying to put Mint on it but it doesn't seem to be doing anything. In fact - no - it comes up with "This kernel requires the following features not present on the CPU: pae - Unable to boot - please use a kernel appropriate for your CPU.

That might as well be Dutch to me.................. If someone could explain what it means and whether it is something that can be bypassed/fixed/ignored??


Scrumpypaul
It looks to me like your CPU does not  support PAE.
If you can get to a Terminal on this machine, and type the following:
```
cat /proc/cpuinfo ; cat /proc/meminfo
``` then post the output here.
This will provide more information about your CPU and Memory configuration.

*[COLOR=#0000ff]**Linux Lite**[/COLOR] is a very good option, but your CPU must support PAE for Linux Lite to run on it.*

---

### Post by mips on 2013-03-07
> **scrumpypaul said:**
> 
Going to try Crunchbang next.

Crunchbang Waldorf will work, Manjaro Openbox will also work. I tried both of those just two days ago on my laptop with non-PAE CPU.
[http://crunchbang.org/download/waldorf](http://crunchbang.org/download/waldorf) Select 32-bit

From either of those you can add a Desktop Environment of your choice if Openbox is not your cup of tea.

---

### Post by scrumpypaul on 2013-03-07
Hello kind folks........

Thank you for all the advice and help.

It transpires that Crashbang is working on the laptop and I've set it up so my wee offspring can use it.

One minor question - how can I put a folder on the desktop? Say "videos"..........

I've tried various right/left click scenarios but to no avail.

TIA


SP

---

### Post by dodo3773 on 2013-03-08
> **scrumpypaul said:**
> Hello kind folks........

Thank you for all the advice and help.

It transpires that Crashbang is working on the laptop and I've set it up so my wee offspring can use it.

One minor question - how can I put a folder on the desktop? Say "videos"..........

I've tried various right/left click scenarios but to no avail.

TIA


SP

You cannot dump files/folders onto the desktop aka root window in openbox (the window manager that comes with crunchbang). That's why you couldn't figure it out. Unless you either overlay something on the desktop like a dock or a panel or similar you will not get this functionality while openbox is drawing the window.

---

### Post by mips on 2013-03-08
> **scrumpypaul said:**
> Hello kind folks........

Thank you for all the advice and help.

It transpires that Crashbang is working on the laptop and I've set it up so my wee offspring can use it.

One minor question - how can I put a folder on the desktop? Say "videos"..........

I've tried various right/left click scenarios but to no avail.

TIA


SP

[http://crunchbanglinux.org/wiki/howto/add_desktop_icons](http://crunchbanglinux.org/wiki/howto/add_desktop_icons)

For some odd reason I though Thunar could do this?

---

### Post by dodo3773 on 2013-03-08
> **mips said:**
> [http://crunchbanglinux.org/wiki/howto/add_desktop_icons](http://crunchbanglinux.org/wiki/howto/add_desktop_icons)

For some odd reason I though Thunar could do this?

Thunar can't I don't think. Some file managers can if you have them redraw the root window but then you will lose your openbox pipemenu. The only real work around would be rox filer.

---

### Post by Markup 001 on 2013-03-10
Sorry, after reading your post properly I realised that I hadjumped in to offer advice that would have been out of date. Excuse me?
Mark

---

### Post by iamkuriouspurpleoranj on 2013-03-11
scratch that :-) it had already been given (link deleted)

---

