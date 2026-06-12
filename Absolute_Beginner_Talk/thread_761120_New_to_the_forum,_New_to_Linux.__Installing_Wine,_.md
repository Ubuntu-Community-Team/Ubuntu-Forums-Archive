---
title: "New to the forum, New to Linux.  Installing Wine, help please"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by joshkahn21 on 2008-04-20
Ok, folks, first post, new to linux, new to the forum.  trying to install wine on my new cloudbook, which runs ubuntu gOS.  not sure what's the difference between the two but willing to learn.

so i went to the synaptic package manager to find wine and install it. but it gives me an error message. first it says that binfmt-support had to be marked and it does that but then it tells me: [SIZE="4"]"Depends: libaudio2 but it is not installable." [/SIZE]

so then i'm hoping, ya know, maybe add/remove programs can do it for me.  so i open that up and find wine.  and it tells me: [SIZE="4"]"Cannot install 'wine'
This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.
Switch to the 'synaptic' package manager to resolve this conflict.[/SIZE]"  And now i say, "DOH!!!!"

any help here?  what is conflicting with the install?  btw, i want wine so i can run an amazon program and sling box.  they are corporate programs that don't have a linux version.  any help?  many thanks guys.  keep up the good work.

(admins: i posted this in a wine thread already, but want it to be seen for sure.  So if it proves unnecessary to post this second time, don't worry about deleting one of them.  it's cool with me as long as i get my answer somewhere.  thanks!)

---

### Post by szymon_g on 2008-04-20
type 

sudo aptitude install wine

and paste whatever error you get

btw, eeepc rulez ;p


//////////////
of course type it in gnome-terminal (if you use gnome) or in konsole (if you use kde)

---

### Post by joshkahn21 on 2008-04-20
thank you for replying but i don't really understand.  i'm not good with the terminal.  what will happen next?  and, this is going to sound really stupid, i don't even know what my sudo password is.  i'm just a linux newb.

---

### Post by joshkahn21 on 2008-04-20
ok, so i guessed my sudo password.  (duh) and i got this:

[SIZE="3"]Reading package lists... Done
Building dependency tree        
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  wine 
The following NEW packages will be automatically installed:
  binfmt-support 
The following NEW packages will be installed:
  binfmt-support 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.9MB of archives. After unpacking 106MB will be used.
The following packages have unmet dependencies:
  wine: Depends: libaudio2 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
wine [Not Installed]

Score is -9881

Accept this solution? [Y/n/q/?] n[/SIZE]

and then it tried to install it again and it doesn't seem like it worked.  any more ideas?  again, many thanks.

---

### Post by benjaminsjw on 2008-04-21
That sounds familiar. Seems like I'm in the same position. also a complete linux-newbie, with the same problems to install wine (and a couple of other things, i might add... aMSN being one of them). I hope it can be resolved.

---

### Post by joshkahn21 on 2008-04-27
I got it installed with the synaptic package manager!  just had to click on the right repositories in the options menu.  
settings -> repositories -> and then i can't remember which one it was, but it's not hard to guess.  i got it on my first try. i think it was the third party tab.  good luck!!

---

