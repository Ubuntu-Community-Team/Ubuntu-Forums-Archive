---
title: "Does halting your computer have any negative effects?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-11-10
Every method I've tried on the internet doesn't work, my computer won't shutdown fully when I tell it to. All it does is hang at the loading screen after the bar is empty. I hear the disks going off, but the power is not cut off at all, and I am forced to hold the on button on my PC until it does. I did notice that by typing "sudo halt now" the computer will fully tun off.

Reboot reboots my system ok, and Halt completely shuts it down. The only problem is that when my computer is told to powerdown it doesn't. I've had this problem in Feisty as well as gutsy.

---

### Post by jhenager on 2007-11-10
I would check your ACPI settings in the BIOS.
Hit Del when it starts up, (or F2 on Dell computers - your hot button might vary)
Make sure it is configured.
[http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.acpi.info%2F&ei=xdQ1R7nuMqCeebmysY8P&usg=AFQjCNExbQ5JEJHu67GEg3UKD05at7HcWg&sig2=e3biWxaX5gq7ZlFWE0rG_w]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.acpi.info%2F&ei=xdQ1R7nuMqCeebmysY8P&usg=AFQjCNExbQ5JEJHu67GEg3UKD05at7HcWg&sig2=e3biWxaX5gq7ZlFWE0rG_w")
for more information.

---

### Post by Bartender on 2007-11-10
How old is the PC?  Just a coupla weeks ago I had an interesting experience with an old Compaq Celeron 466MHz PC that someone gave me.  I installed Ubuntu 7.10.  It would do exactly as you described.  Ubuntu quit but the PC didn't finish turning off.  I checked on HP's website for the latest BIOS revision.  There was a newer version so I flashed the BIOS.  After that the PC shut down entirely.

---

### Post by dysphasi on 2007-11-30
Any chance someone could answer the original question here? I've got a similar problem, ie shutdown via the normal procedure doesn't shutdown, the system hangs. 

I've tried all the menu.lst options I could find, nothing works. I've updated my bios, no joy, there aren't any acpi options etc that I can manually alter in the bios, it seems a bit of a no-gamer and until an ubuntu fix comes out I've got few hopes of solving the problem.

If I initiate halt from the terminal it doesn't, it shuts down all the way. 

[LIST]
Are there any deleterious effects of using halt as opposed to a normal shutdown? 
[/LIST]
[LIST]
If not, is there a way to change the default action of the shutdown button in the gnome shutdown menu to halt?
[/LIST]

---

### Post by fatality_uk on 2007-11-30
> **dysphasi said:**
> Any chance someone could answer the original question here? I've got a similar problem, ie shutdown via the normal procedure doesn't shutdown, the system hangs. 

I've tried all the menu.lst options I could find, nothing works. I've updated my bios, no joy, there aren't any acpi options etc that I can manually alter in the bios, it seems a bit of a no-gamer and until an ubuntu fix comes out I've got few hopes of solving the problem.

If I initiate halt from the terminal it doesn't, it shuts down all the way. 

[LIST]
Are there any deleterious effects of using halt as opposed to a normal shutdown? 
[/LIST]
[LIST]
If not, is there a way to change the default action of the shutdown button in the gnome shutdown menu to halt?
[/LIST]


Check that your hard drive is no longer spinning. If the HD light on your server has stopped then just powering off your PC is only disconnecting the power to the MOBO. Not ideal but better than a hard reset with a spinning hard drive. Also check around Google for shutdown and startup scripts in Ubuntu.

You could even create a "shutdown -P now" script I guess

---

### Post by dysphasi on 2007-11-30
Do you mean that using halt is akin to switching off the mains power (without a battery in in my case as I use a laptop)? 

It's basically impossible for me to tell hard drive activity on my laptop. What exactly does halt do?

And do you know which script is called when one clicks the shutdown button in gnome?

---

