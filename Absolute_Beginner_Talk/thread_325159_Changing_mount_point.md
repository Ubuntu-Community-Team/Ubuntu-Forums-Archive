---
title: "Changing mount point"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by IamAcoconut on 2006-12-25
How do I change the mount point of a partition?
I know how it should be done, yet I'm new to ubuntu. 
I tried System->Administraion->Disks, changed the mount points, clicked ok, but nothing changed. My changes where discarded.[LIST][*]Why?[/LIST]
I can't edit fstab either as I don't have the permissions. So how can I achieve this [LIST]
[*]Without using console[/LIST]
As I am configuring this computer for a particular human being that will cease to use Linux if he has to use console.

---

### Post by xyz on 2006-12-25
> As I am configuring this computer for a particular human being that will cease to use Linux if he has to use console.
Then this "particular person" probably will cease....if absolutely no console's allowed.
To edit fstab:
```
sudo gedit /etc/fstab
```
Post the outputs of your fstab and:
```
sudo fdisk -lu
```
I guess it could be possible to install a right-click (Open as Root) script and do it this way.
To be verified!

---

### Post by xyz on 2006-12-25
Also to open files not using a console, create a launcher on the desktop (right-click on Desktop> Create launcher)....name it something like 'Drag and Drop Sudo' and where it says "Command", copy/paste this:
```
gnome-open %u
```
Leaving your launcher on your desktop, you can then drag and drop a root file (for instance /etc/fstab) onto the icone. This will open the file as root and you'll be able to edit it.

Also, copy/paste this into a terminal:
```
sudo gedit ~/.gnome2/nautilus-scripts/Open\ as\ root

```
Copy/paste and insert this in the window:
> #!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"
Save and Close it.
One last thing in a terminal: copy/paste the following:
```
chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root
```
You'll then be able to right-click on a file and Open\ as\ root

---

### Post by IamAcoconut on 2006-12-25
Hey, thanks a lot, that's what I needed :-)
Yet, I entered ```
sudo chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root
``` and still don't have such an option on right click.
I have edited fstab, yet I still wonder why my changes in 'disks' were discarded...

---

### Post by xyz on 2006-12-25
> **IamAcoconut said:**
> Hey, thanks a lot, that's what I needed :-)
Yet, I entered ```
sudo chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root
``` and still don't have such an option on right click.
I have edited fstab, yet I still wonder why my changes in 'disks' were discarded...
You may have to reboot!
Please do this:
```
 cd ~/.gnome2/nautilus-scripts

```
The 'cd' will direct you to where we want to be (i.e nautilus-scripts). There we want to see whether the 'Open\ as\ root' file was effectively put in there. Then run:
```
 ls -l

```
where 'ls' will simply give us a list of what scripts are in 'nautilus-scripts'.
You may want to post this output in case you can't sort it out.
In that list, spot this:
> -rwxr-xr-x 1 th th    79 2006-08-23 11:00 Open as root

where 'th' is my username. IF 'Open as root' is in there, post what it says about '-rwx...' as in my last quote.

---

### Post by IamAcoconut on 2006-12-25
Edit: rebooted, it;s fine! Thanks a lot, **xyz**!

Yet I still wonder, why the first way I tried to do it failed. Was it my mistake, or something wrong with that tool?

---

### Post by xyz on 2006-12-25
Please see my post #3 above...where it does not say **sudo** chmod but only 'chmod'...
Try it! We'll get there!

---

### Post by IamAcoconut on 2006-12-25
I meant this... [quote]I tried System->Administraion->Disks, changed the mount points, clicked ok, but nothing changed. My changes were discarded.
Why?[/code]

---

### Post by xyz on 2006-12-25
> **IamAcoconut said:**
> I meant this... [quote]I tried System->Administraion->Disks, changed the mount points, clicked ok, but nothing changed. My changes were discarded.
Why?[/code]
The first time around you ran this:
```
sudo chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root
```
instead of:
```
chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root
```
When you used "sudo chmod"...you gave sudo (root) the right to Open as Root. Which is useless!
When you ran simply "chmod..." you gave yourself, the non-root user, the right/permission to right-click on a file using "Scripts > Open As Root" .
You wanted a non-console way so that a simple user could right click on a file 
and open it as root...thus, for instance, edit the file.
Hope it's clearer.

---

### Post by IamAcoconut on 2006-12-25
It was 100% clear, when you said that! 
The issue I am asking about is my first attempt to change mount points from System->Administraion->Disks, not creating that script.

:-)

---

### Post by xyz on 2006-12-25
> **IamAcoconut said:**
> It was 100% clear, when you said that! 
The issue I am asking about is my first attempt to change mount points from System->Administraion->Disks, not creating that script.

:-)
 System->Administraion->Disks  didn't work probably because your access path  didn't correspond to where it was mounted; a bit like living in Paris and taking the plane to London to go home. And once there, wondering why you can no longer find the "path" to your home.

---

