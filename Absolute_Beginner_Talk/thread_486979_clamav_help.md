---
title: "clamav help"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by cranshinibon on 2007-06-28
i have it installed but i can't seem to find the command to 

1.) update it to the most recent version
2.) open up the gui for it
3.) make a clickable icon on the desktop for easy access

i really like the switch to ubuntu. it's just really hard after being with windows for so long.

---

### Post by moredhel on 2007-06-28
You don't really need anti virus, the only reason would be incase you pass on virus-ridden programs to other windows friends. But then that's their responsibility to scan, not yours ;)

---

### Post by milton1 on 2007-06-28
> **cranshinibon said:**
> i have it installed but i can't seem to find the command to 

1.) update it to the most recent version

sudo freshclam

> 2.) open up the gui for it

not sure there is one by default, though I think there are some front-ends available

> 3.) make a clickable icon on the desktop for easy access

probably easier to stick with the command line "clamscan" It will scan the current folder. To scan recursively, use (I think) the -r flag.

Clamav is a nice toy, but not generally necessary. I keep it around just to scan uploads for a moodle site.

---

### Post by oilchangeguy on 2007-06-28
> **moredhel said:**
> You don't really need anti virus, the only reason would be incase you pass on virus-ridden programs to other windows friends. But then that's their responsibility to scan, not yours ;)

i agree.

---

### Post by chandler on 2007-06-28
Yeah, clamav is not a problem.  To add a link to your desktop you may be able to drag it over.

---

### Post by starcraft.man on 2007-06-28
Install the Klam front end for clam.

```
sudo aptitude install klamav
```

That will fix the GUI issue.

I agree with the above though. An AV solution is holey unnecessary for Linux at this time and the short term foreseeable future. There simply aren't exploits in the wild. In the end, I'm pretty sure people will start hacking Apple's OSX before they target Linux, A) OSX is a larger market than any one distro of Linux (or even combined) and B) The subtle differences and changes between distributions make finding an exploit for them all difficult unless its an essential service and thats not that likely and C) The sudo and firewall security in place by default makes propagation of viruses difficult at best (even if they could theoretically wipe your home partition if you don't protect it).

Hey, if you wanna know something really crazy? I don't even run an AV on XP :p I scan once a month, and the rest of the time theres nothing on except my software firewall and hardware router.

---

### Post by cranshinibon on 2007-06-28
i dont know what the icon is bc all i have is the directory.

i need the clamav bc its for a project for school. its required to have it. i know bleh lol

---

### Post by RomeReactor on 2007-06-28
Hi. As **starcraft.man** said, **klamav** is a graphical frontend to clamav; another one would be **clamtk**. Look for either of those through **Add/Remove...** (Applications-->Add/Remove...) or Synaptic (System-->Administration-->Synaptic Package Manager). Once it's installed, you can drag it to your desktop or any of the panels.

---

