---
title: "add/remove out of date?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by darweth on 2007-01-07
This happens every single time I open add/remove.  I update it and it reloads... close it.  OPen it and it comes up again.  What is the problem?

---

### Post by meng on 2007-01-07
Try running in the terminal:
sudo apt-get update

then run Add/Remove again (although I personally don't recommend using Add/Remove for installing/removing applications, either go for the command line or use Synaptic!)
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

---

### Post by pay on 2007-01-07
Try opening the terminal and typing ```
sudo aptitude update
```
EDIT: meng beat me to it

---

### Post by darweth on 2007-01-07
I will keep that in mind about not using add/remove.  But little problems that I know exist still nag away at me.  

I updated both apt-get and aptitude in terminal and the situation persists. :/

Any other ideas?

---

### Post by darweth on 2007-01-07
for the hell of it, i ran a sudo aptitude remove gnome-app-install....  i think this removes add/remove?   i was planning on re-installing it then.  anyway, i aborted because this came up:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  ubuntu-desktop 
The following packages will be REMOVED:
  gnome-app-install 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1036kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gnome-app-install but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Leave the following dependencies unresolved:
nautilus recommends gnome-app-install (>= 0.2.6~)
Score is -501

Accept this solution? [Y/n/q/?] q


ubuntu-desktop is broken?  That is what it says.  How do I fix that?  How do I fix this situation?  Ahhh!  hehe.  i tried to install ubuntu-desktop, but it said i had the latest.

---

### Post by Delkster on 2007-01-07
> **meng said:**
> I personally don't recommend using Add/Remove for installing/removing applications

I do, because it's still the easiest thing to use for someone who doesn't want to know much about the details of package management. It could use a better search, though.

---

### Post by Delkster on 2007-01-07
> **darweth said:**
> ubuntu-desktop is broken?  That is what it says.  How do I fix that?  How do I fix this situation?  Ahhh!  hehe.  i tried to install ubuntu-desktop, but it said i had the latest.

Aptitude means that it would be broken after the action it was ordered to take, namely the removal of gnome-app-install. ubuntu-desktop is a so-called meta-package that contains no software itself but is intentionally set to be dependent on all packages that belong to the standard Ubuntu desktop. Since the package management system automatically makes sure that all such dependencies are satisfied by having the required packages installed (usually because many applications actually do require other packages in order to funtion), having ubuntu-desktop installed ensures that you have everything that comes in the default ubuntu-desktop.

Thus, removing something that is part of the default setup also "breaks" the dependencies of ubuntu-desktop and causes it to be removed as a result. Since it contains no software itself, having it removed doesn't really cause any loss of functionality and it's, in principle, safe to remove. However, it's recommended that you have ubuntu-desktop installed when you upgrade to a newer release of Ubuntu, so if you remove it, make sure that you re-install it before you start a distribution upgrade in the future.

---

