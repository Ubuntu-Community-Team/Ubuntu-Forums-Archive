---
title: "[SOLVED] k3B only loads when run as sudo from terminal in Gnome"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by blumnday99 on 2008-01-26
I'm having a problem with k3B in Ubuntu 7.10.  I was able to get it running before but after a clean install it's not working perfectly.

I did a sudo apt-get install k3b to install the program.  It's listed in the applications menu, but when clicking on the k3b icon, nothing happens.  I've also made K3B the default application for isos, but nothing happens when double-clicking isos.

However, when I open a terminal and run sudo k3b and enter my pw, k3b runs just fine.  

How can I force k3b to run under SU with an icon and keep the terminal window from popping up?  Or can I just fix k3b so it'll run when I click the icon under the application windows?

I'm confused as to why k3b is even running this way.

Thanks for any help.

Mark

---

### Post by LaRoza on 2008-01-26
What messages do you get when you type "k3b"?

---

### Post by MasterAslan on 2008-01-26
were you logged in as root when you installed it?  

try removing it and installing it through the package manager

---

### Post by blumnday99 on 2008-01-26
> **MasterAslan said:**
> were you logged in as root when you installed it?  

try removing it and installing it through the package manager

Nope...logged on as me, not as root.  Already tried a Synaptic package install but it still doesn't work through the icon.  I don't think it's a problem with the install because the program still runs fine when I run it through the terminal.

---

### Post by blumnday99 on 2008-01-26
> **LaRoza said:**
> What messages do you get when you type "k3b"?

trying to create local folder /home/mark/.kde/share: Permission denied
trying to create local folder /home/mark/.kde/share: Permission denied
trying to create local folder /home/mark/.kde/share: Permission denied
trying to create local folder /home/mark/.kde/socket-dlna-gnome: Permission denied
trying to create local folder /home/mark/.kde/socket-dlna-gnome: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/mark/.kde/socket-dlna-gnome/kdeinit__1'
ERROR: KUniqueApplication: Can't setup DCOP communication.

---

### Post by blumnday99 on 2008-01-26
> **blumnday99 said:**
> trying to create local folder /home/mark/.kde/share: Permission denied
trying to create local folder /home/mark/.kde/share: Permission denied
trying to create local folder /home/mark/.kde/share: Permission denied
trying to create local folder /home/mark/.kde/socket-dlna-gnome: Permission denied
trying to create local folder /home/mark/.kde/socket-dlna-gnome: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/mark/.kde/socket-dlna-gnome/kdeinit__1'
ERROR: KUniqueApplication: Can't setup DCOP communication.

Used this thread to fix the problem

[http://ubuntuforums.org/showthread.php?t=511300&highlight=dcopserver&page=2](http://ubuntuforums.org/showthread.php?t=511300&highlight=dcopserver&page=2)

That DCOP error came up again when I tried to use Krusader.  I googled that DCOPserver thing and found out it's used by KDE programs to communicate with each other.  From info in the thread above, I found out that my /home/username/kde folder was owned by root.  I tried using chown to change the ownership to my user.  That gave my access but still didn't work.  So I deleted the KDE folder (the thread said that KDE would recreate all the files on the next login), uninstalled K3B and Krusader, and rebooted.  

On reboot, I reinstalled K3B and Krusader using Synaptic and they all worked!

Thanks for the replies everyone...this support forum has the quickest response time ever.

Mark

---

