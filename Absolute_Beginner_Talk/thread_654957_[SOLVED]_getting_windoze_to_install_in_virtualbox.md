---
title: "[SOLVED] getting windoze to install in virtualbox"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-12-31
sounds simple right?  yeah.  well here's the catch.  the only installer i have for windoze is embeded in my hard-drive for use if the install screws up.  how do i get an install working in virtualbox if i don't have an install cd for the os (it came pre-installed on my dell laptop...  i don't use the install anymore...)?

---

### Post by overdrank on 2007-12-31
> **Niklas Schröder said:**
> sounds simple right?  yeah.  well here's the catch.  the only installer i have for windoze is embeded in my hard-drive for use if the install screws up.  how do i get an install working in virtualbox if i don't have an install cd for the os (it came pre-installed on my dell laptop...  i don't use the install anymore...)?

Hi and I would say ( with my limited experience) you will need to install it then you can use the info here
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

### Post by forestpixie on 2007-12-31
or the other option, phone Dell and insist ona  real life cd - tell them you installed linux and need to get back to win


but seriously if you push you should get a cd :)

edit - and thanks overdrank - knew you could do it with vmware, but the vbox one is new to me

---

### Post by Niklas Schröder on 2007-12-31
the problem is that i *CAN'T* install it cause i don't have a disk.  and i don't have the time to wait for the disk...

---

### Post by popch on 2007-12-31
> the only installer i have for windoze is embeded in my hard-drive for use if the install screws up. how do i get an install working in virtualbox if i don't have an install cd for the os (it came pre-installed on my dell laptop... i don't use the install anymore...)

Please excuse, but I find the account of your predicament slightly confusing. You have an install in case the install screws up, but do not know how to get it working because you do not have an install which came pre-installed, only you do not use the install anymore?

Which is the what? And you have what? And you lack what?

---

### Post by forestpixie on 2007-12-31
well I don't really know then - always made sure I had a disc when I was in the position of needing one

but

if you've still got the partition could you not run  it and reinstall ubuntu afterwards, unless you had problems installing ubuntu - it's going to be 40mins on top of the windows install, because if it isn't installed anywhere it'll have to be installed either for vbox to recognise or in it's own right

perhaps though I'm wrong and am going to be told so shortly

---

### Post by forestpixie on 2007-12-31
> Which is the what? And you have what? And you lack what?

he has a restore partition, the new way of making sure that MS customers don't have physical goods (last version I used was 2k) I think that XP and vista are the same

-
 but he doesn't have it installed anymore is how I read it

---

### Post by popch on 2007-12-31
> **forestpixie said:**
> he has a restore partition, the new way of making sure that MS customers don't have physical goods

If that's so, then you have given good advice: to install the Windows from scratch using that restore partition, then install Ubuntu into a separate partition, then moving the installed Windows into a VM.

---

### Post by forestpixie on 2007-12-31
it's just a guess tbh - as I said long time since I had a new MS product- always tried to stay one step behind so everyone else did the final R&D - then refused XP when the rest of the world went vista mad and came here instead :D - much more satisfying state of affairs

---

### Post by kenboyles72 on 2007-12-31
If your laptop came with the os pre-installed, you might can burn recovery install cd's. I can't remember straight off about Dell systems, but there might be a utility for making recovery install cd's. If not, then you will have to contact Dell and get them to send you copies of the install cd's. There should be some information about this that came with your laptop.

---

### Post by Niklas Schröder on 2007-12-31
ok.  some of you understand my problem.  others don't.  :p  here's my predicament.

my dell laptop came with windoze installed.  the factory set aside a small portion of the hard drive with an installer for windoze somehow on it.  if my pre-installed windoze install fails, i can hold f11 (or something similar) during boot and bring up the re-installer.  because of this, i didn't get any install disks with my computer.

i want to install windoze on virtualbox but don't have install cd's.  is there any way i can install *without* the disk (i don't want to uninstall ubuntu.  it's taken me months to get it back to the way i like since my last re-install.)?

---

### Post by forestpixie on 2008-01-01
can you not make a small partition - you'd need to resize your ubuntu to make room
then use the re-installer to install win to the newly made partition 

you'd probably need the win at the front of the disc - and you'd need to have the information to reinstall grub 

then once you're back in ubuntu, install vbox and look at the page overdrank gave

then you don't need to use discs to install

---

### Post by Niklas Schröder on 2008-01-04
ok.  i actually found one of our old xp install disks.  :)  only problem is that it was for xp home.  my computer came with media center 2005.  so i'm stuck with the 30 day trial since i can't register...  urg...  i was so close!  i'd rather not call microsoft/dell, so are there any other options?

---

### Post by Niklas Schröder on 2008-01-04
and i looked at the link above...  and it looks like i have to install with a disk and then it'll bring my data over from the windoze install...

---

### Post by tbranham on 2008-01-04
> **kenboyles72 said:**
> If your laptop came with the os pre-installed, you might can burn recovery install cd's. I can't remember straight off about Dell systems, but there might be a utility for making recovery install cd's. If not, then you will have to contact Dell and get them to send you copies of the install cd's. There should be some information about this that came with your laptop.

You're right, most of the vendors provide a way to burn a physical disk (usually a DVD at this point) to reinstall Windows XX. The problem, however, is that these are not virgin copies of Windows -- they usually have vendor-specific code wrapped around them which is tied to the hardware. For instance, I tried installing XP MCE from a burned install disk in VMware, but it would crash saying that is was not original Sony hardware (it was "seeing" the virtual hardware provided by VMware instead).

The solution, then, seems to be as the other posters have suggested: reinstall XP MCE via the process provided by the MFG. Then install Linux on a separate partition and migrate it to VirtualBox. 

Or... get yourself a copy of the actual Win XP MCE disk.

Good luck!

---

### Post by Niklas Schröder on 2008-01-04
urg...  i had no idea this would be so difficult...  i guess that's what i get for poking around in the world of windoze again.  :p

---

### Post by forestpixie on 2008-01-04
could be worse - you might never have known enough to have been here in the first place :)

---

### Post by fiddledd on 2008-01-04
Not sure if this will help or not, I think VMWare does a free program that will make a vmware image of an existing XP installation. This will work with VirtualBox as it supports VMWare images. I forget what the program is called though, sorry. If you look on VMware website I'm sure you'll find it and I know I've seen howtos on actually using it.

---

### Post by skroops on 2008-01-04
Phone a friend that has an OEM windows that is the same version as you have a license for, and borrow it.

or: You should be able to find a torrent with legitimate windows cd images.  Just find out which version you have (look on the sticker under your laptop), and download that version.  Then install with your key.

These are your best options if you can't wait for a replacement from Dell.

---

### Post by Niklas Schröder on 2008-01-05
i opted to hack xp home.  succeeded.  that's all i can say.  :p

---

### Post by ashmew2 on 2008-01-05
I dont know whether i m diong the right thing...replying to a SOLVED thread , but i was wondering...If he owns a legal copy of Microsoft Windows...would it be unfair on his part (or illegal) , to use an illegal copy of the Microsoft Windows (for his own personal use ONLY)?

---

### Post by Niklas Schröder on 2008-01-05
in my opinion it wouldn't be illegal.  but i didn't download a bootleg copy.  i just hacked the copy i had to remove the need to register.  ;)

---

