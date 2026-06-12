---
title: "Banshee Audio player"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-15
Hey i really need an audio player and i like the look of banshee the most. I put the following into the terminal:

Sudo apt - get install banshee

and got this in return:

This is the error i get

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
banshee: Depends: libnjb5 but it is not installable
Depends: libmono-cairo2.0-cil (>= 1.0) but it is not installable
Depends: libmono1.0-cil (>= 1.2.4) but it is not installable
E: Broken packages

What do i do? Whats worng?

---

### Post by Inxsible on 2008-04-15
Go to System>>Administration>>Synaptic Package Manager. Click on the bottom buttons. I forget the name...but when you click on one of them, you will see 'Broken' as one of the options in the tree in the top left corner.

Click on Broken and then on the right pane, right click on each and mark for complete removal. Then hit Apply

---

### Post by AeThEr777 on 2008-04-15
Sry bottom buttons? I dont see them.

---

### Post by spiderbatdad on 2008-04-16
Maybe in the 'edit' menu of upper left hand corner in synaptic...select 'fix broken packages.'

---

### Post by Inxsible on 2008-04-16
> **AeThEr777 said:**
> Sry bottom buttons? I dont see them.Left hand bottom corner. There are 4-5 buttons like Origin, Status 2-3 others as well.

I remember now, the buttons called 'Custom Filters'

---

### Post by AeThEr777 on 2008-04-16
do i have to search for nashee before slecting edit and fixing the banshee broken packages

---

### Post by cchester on 2008-04-16
Once you click on the fix broken packages choose apply. Let synaptic do that first to be on the safe side. Then when it completes search for banshee with the search once it comes up click in the box and click apply and banshee should install.

On a side note when it tells you what it is going to fix look at the files it lists and see what got broken so you will know for next time.

---

### Post by AeThEr777 on 2008-04-16
Ok so Ive tried to istall it through the terminal and got the error msg i posted above now through the synaptic package manager i and the steps outlined i got this msg. 

banshee:
 Depends: libnjb5  but it is not installable
 Depends: libmono-cairo2.0-cil (>=1.0) but it is not installable
 Depends: libmono1.0-cil (>=1.2.4) but it is not installable

---

