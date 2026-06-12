---
title: "Sleep on powerbook 550, hoary"
date: 2005-01-10
forum: Apple PPC Users
---

### Post by chele on 2005-01-10
> I have installed hoary on this powerbook, and it works well after adding a modeline to the xorg.conf file.

I would like it sleep when I close the lid. I used to have a iBook 500 running debian that did that, as far as I remember I was using a special BenH kernel do allow that. 

Does the Ubuntu kernel allow that, and if so, how does one configure it? If not, where does one get a current kernel that has sleep configured?Works without the airport modules loaded.

As this machine will be used in a place without wireless access, I just removed the airport card and edited the /etc/modules file to reflect that.

I suppose that if I were keeping the airport card, something to unload & reload the modules on sleep/wakeup would do the job.

---

### Post by tiiim on 2005-01-11
[here](http://ubuntuforums.org/showthread.php?t=5760&highlight=sleep)

---

### Post by chele on 2005-01-11
Where does one get this kernel patch from? I've looked around the net and did not come across it.

---

### Post by tiiim on 2005-01-11
[QUOTE=chele]Where does one get this kernel patch from? I've looked around the net and did not come across it.[/QUOTE]
 well that link was the kernel itself...

---

### Post by chele on 2005-01-11
I guess I would rather compile a kernel for this specific machine then download a random kernel for a slightly different machine. 

I had hoped that these patches were part of the main ppc kernel by now, and it was just a matter of picking the right kernel options. Maybe that is true, as I can't seem to find any new ppc patches.

I suspect that a large percentage of linux ppc users are running either iBooks or powerbooks. Sleep (suspend-to-ram) is pretty much a necesary function for those users. I never turn of my laptop. Just close the lid, throw it in my knapsack, and off I go. 

No harm in just trying and compiling myself a new kernel, I guess. See what happens. I guess I'll look around for a .config to work with.

thanks

---

### Post by chele on 2005-01-11
hmmm. the more I read the more confused I get. The patch seems to be here: [http://gate.crashing.org/~benh/](http://gate.crashing.org/~benh/) 

But as it is called albook-ibookg4-sleep-7.diff  I don't think it applies to my case, as I have neither an iBookG4 nor an Aluminum powerbook. This is an old titanium G4 powerbook.  :confused:

---

### Post by tiiim on 2005-01-11
[QUOTE=chele]hmmm. the more I read the more confused I get. The patch seems to be here: [http://gate.crashing.org/~benh/](http://gate.crashing.org/~benh/) 

But as it is called albook-ibookg4-sleep-7.diff  I don't think it applies to my case, as I have neither an iBookG4 nor an Aluminum powerbook. This is an old titanium G4 powerbook.  :confused:[/QUOTE]
 hmm well i think the kernel is still in testing at the moment they will official implenent it sometime in the near future. You could always try if not backdate.

---

### Post by chele on 2005-01-12
I don't know what happened, but it has started to half work now. 

Sleep worked if I push the power-button, then wakes when I press any key.

It also sleeps if I close the lid, but does not wake properly when I open the lid.

I have installed the powerprefs gui, which has configuration options for these things. There wa also an update to the pbbuttons package. Maybe that was what made this change.

I will have to keep looking to see what I need to confgure to have it working smoothly. At least I know that the default kernel has the capability, so I don't need to bother with that.

---

### Post by chele on 2005-01-27
[QUOTE=chele]

I will have to keep looking to see what I need to confgure to have it working smoothly. At least I know that the default kernel has the capability, so I don't need to bother with that.[/QUOTE] I have unloaded the airport wireless modules, and now it works as expected.

---

### Post by adamw on 2005-02-03
I have a powerbook 1.5ghz running warty, and I can only sleep after killing hald. (but at least now I CAN sleep! And without a special version of the kernel!)

---

### Post by adamw on 2005-02-03
Better yet, if I create a file at:
/etc/hal/fdi/nocdrompolling.fdi  (the filename doesn't matter btw, but be sure to sudo mkdir -p /etc/hal/fdi first)

which contains the following xml:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
        <device>
        <match key="block.device" string="/dev/hdb">
        <merge key="storage.media_check_enabled" type="bool">false</merge>
        </match>
        </device>
</deviceinfo>

I can sleep just fine now without doing anything.  Turns out HAL was polling my cdrom which was causing my powerbook to be unable to wake from sleep.

---

### Post by Pineault on 2005-02-07
Well I tried to activate sleep in warty on ibook g4, did the following
downloaded and configured powerprefs, activated sleep option for battery,
killed hal, closed cover with xmms running, music continued to play but screen was blank, upon opening screen is dark though visible... hurting my eyes trying to write this...

So I can blank my screen by colsing lid, pressing power button, but no sleep..., any suggestions ?

---

