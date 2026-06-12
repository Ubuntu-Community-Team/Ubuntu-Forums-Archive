---
title: "Uninstalling Evolution"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by metjoo on 2006-04-30
Hello!

I want to uninstall evolution which was installed with the Ubuntu package during the installation.

When trying to delete it with Synaptic, the system tells me its going to delete as well some desktop and gnome files.

Is that right? Should I continue with the uninstallation?

Thank you!

---

### Post by Rinzwind on 2006-04-30
Yes, go ahead. I did it too :)


It'll only delete files that are not used by other programs.

---

### Post by CompShrink on 2006-04-30
It's ok, but note that removing evolution data-server also removes ekiga, which is just a VOIP internet phone and ms netmeeting program, so you probably don't care.

---

### Post by metjoo on 2006-04-30
I have accept the deletions.

Some gnome-session, and stuff where deleted.

Now when I run Ubuntu I enter my username and password, everything freezes and the system crashes..

What can I do??

---

### Post by Biltong (Dee) on 2006-04-30
Oh dear.
I uninstalled Evolution a week ago today and had the same thing happen to me. Finally, in frustration I reinstalled Ubuntu from scratch. Now Evolution stays on the compuer and I pet it occasionally...

---

### Post by daschl on 2006-04-30
oh that sounds rather strange. there are loads of ways to recover your system, but the fastest for you would be to install it from scratch again.

if you want to, you can boot a live-cd, chroot in the environment and reinstall evolution again (via apt-get). another solution would be to boot not in the graphical mode and reinstall it again (well i dont know when your system crashes)

---

### Post by metjoo on 2006-04-30
Well, thank you all.

I'm back again on Linux. I had to reinstall it from scratch...

:-k But I'm still wondering.. How do I remove evolution from my system without messing around the gnome configuration...?

When trying to remove the **Evolution-data-server** package the followed are advised to be removed as well:

[LIST]
[*]evolution
[*]evolution-exchange
[*]evolution-plugins
[/LIST]

Nice until here, but also...

[LIST]
[*]gnome-applets
[*]gnome-applets-data
[*]gnome-control-center
[*]gnome-panel
[*]gnome-session
[*]gnome-terminal

[*]nautilus
[*]ubuntu-desktop
[/LIST]

The fact is that somehow (or maybe I don't really understand what's happening) they are removed!, and when restarting, obviously, the system crashes.

Any idea?

---

### Post by daschl on 2006-04-30
do you choose "removal" or "complete removal" ?

---

### Post by metjoo on 2006-04-30
Complete removal, but if I choose only "removal" the alert shows as well.

---

### Post by daschl on 2006-04-30
the altert, that stuff gets removed pops up everytime if you delete something.

try "removal" and look whats happening ;). if it only disturbs you in the app-menu, use the "alacarte menu editor" to make it invisible :)

---

### Post by Rinzwind on 2006-04-30
Weird.

I deleted it from my install without a problem.

---

### Post by cvmostert on 2006-05-23
i removed evolution but not the data-server... after reading this thread, i think i will just leave it there safe and sound... i dont have evolution anymore... just the data-server....

---

### Post by jdmcbr on 2008-06-19
This is a couple of years late, but...

I just ran in to the same problem. I was not particularly interested in reinstalling, so I messed around in terminal mode for a bit. It seems that ubuntu-desktop was somehow installed, so I just did sudo apt-get install ubuntu-desktop and then rebooted, and that seems to have done the trick.

---

### Post by johngml on 2008-06-22
> **jdmcbr said:**
> This is a couple of years late, but...

I just ran in to the same problem. I was not particularly interested in reinstalling, so I messed around in terminal mode for a bit. It seems that ubuntu-desktop was somehow installed, so I just did sudo apt-get install ubuntu-desktop and then rebooted, and that seems to have done the trick.

I have had a problem that I uninstalled Evolution and updated later on and then next time I rebooted I had no desktop. I followed your instructions and it now works. Interestingly was the fact that it reinstalled Evolution so I have to assume that Evolution is tied to Ubuntu and cannot be removed easily without screwing up your computer. 

Thanks for this.

---

