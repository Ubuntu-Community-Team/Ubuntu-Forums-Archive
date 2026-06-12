---
title: "KDE screen resolution"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by cub682 on 2007-12-01
There is no option to change screen resolution in kcontrol. How do I make changes?

---

### Post by aun on 2007-12-01
On the menu go to:

System Settings> Computer Administration> Monitor and Display

---

### Post by cub682 on 2007-12-01
> **aun said:**
> On the menu go to:

System Settings> Computer Administration> Monitor and Display

That option is not there.

---

### Post by aun on 2007-12-01
Oops, I think I need to clarify.  Your main KDE menu, not the kcontrol menu.

---

### Post by skyjacker on 2007-12-01
> **cub682 said:**
> That option is not there."System Settings/Monitor & Display/Size, Orientation & Positioning". Pick one.

---

### Post by cub682 on 2007-12-01
None of these options are there.:confused:

---

### Post by cub682 on 2007-12-01
Anyone else have any ideas?

---

### Post by SunnyRabbiera on 2007-12-01
are you using Kubuntu or ubuntu with KDE installed in it?

---

### Post by cub682 on 2007-12-01
ubuntu

---

### Post by XVII on 2007-12-01
It should be there then.

---

### Post by SunnyRabbiera on 2007-12-01
ahh, yes this is a problem...
no worries I have a fix:
go to synaptic and search for kde hal device manager,
use that and kcontrol and see if you can play around with the monitor settings
it should work as thats how i got the screen resolution and settings working on my computer
just install it and restart KDE and all should be cool after you go into the control center

---

### Post by cub682 on 2007-12-01
Downloaded the hal device manager but my monitor is not listed.
Still no options for display in k menu.:confused:

---

### Post by SunnyRabbiera on 2007-12-01
hmm, well you might be able to use a generic monitor in your selection of monitors to choose from.
I know I use a monitor that is not listed in the list of monitors given by the system but I do use the generic one and it works okay.
for the kmenu entries, ehh forget it if you know how to get to your control center.

---

### Post by cub682 on 2007-12-01
I should have said there are no monitors listed and no options in control center.

---

### Post by SunnyRabbiera on 2007-12-01
oh, I see... well i have so many things installed on here so there is probably something I missed...
kde powersave is most likely, either that its kde guidance powermanager...
like i said I have lots of apps on here so its possible I am missing something... other then my brain :p

---

### Post by cub682 on 2007-12-01
Thank you very much! I downloaded both and now have the options that I need.:KS

---

### Post by monte48lowes on 2007-12-01
Here is something I really like regarding kcontrol... the search box at the top. I typed in monitor and the menu selection I needed was displayed. Remember that for the future ;)

Mike

---

### Post by cub682 on 2007-12-01
> **monte48lowes said:**
> Here is something I really like regarding kcontrol... the search box at the top. I typed in monitor and the menu selection I needed was displayed. Remember that for the future ;)

Mike

I tried that but it wasn't there until I installed the other programs.

---

### Post by dwblas on 2007-12-01
I've seen the same problem, but only with Gutsy.  With Feitsy Fluxbuntu you can change the xorg.conf as usual, which I've been doing since 1995, but in Gutsy it appears that there is a change-perhaps to compiz?  Another thread suggested installing fglrx-control and then using fireglcontrol to change resolution, but I haven't tried it yet.  I'm going to install Feisty Kubuntu tomorrow and see what happens.

---

