---
title: "Configuring Kubunta"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by aussie.ian on 2006-06-12
I've just installed Kubunta and am having a few problems.
1. Kate (advanced text editor) opens in user mode instead of root, which makes it difficult to edit anything. Emacs doesn't seem to be available.
2. System settings. when I try to change something in system settings either using the root user (I added) or as Sudo the apply button won't lightup, also making it difficult to edit or configure anything. The couple of things I did try to configure now won't open in System settings, I get - This configuration section is already opened in KDE Control Module. I don't know what 'KDE control module' is or where to open or close it. (I would have thought that's what system settings was). When I click on the help button in system settings it tells me 'There is no documentation available for /index.html.
I can't access any repositories for updates or adding programs, as /etc/apt/sources.list needs editing. I have no available sources.
Can anyone help out with these couple of things please?

---

### Post by fireshell on 2006-06-12
If I'm correct your using Kubuntu?

Under the menu select run and type kate, then press the options button. Select run as - root, your password

will give you full access to any file if you open it from within kate

---

### Post by Patrick-Ruff on 2006-06-12
you can also toggle sudo

```

sudo -s

```

---

### Post by fireshell on 2006-06-12
Ah thankyou for that... been wondering how to do that for a while now

---

### Post by aussie.ian on 2006-06-12
Run command won't open Kate in user or root.
I tried it both as Sudo and as root  and each time it just hung for a few seconds then closed.

Sorry amend that, tried it again and it worked. 
Thanks.

---

### Post by ajgreeny on 2006-06-12
Don't forget, you can also right click on a file in konqueror, and then click edit as root for a file you wish to open and change as root.  It's the simple way I find to edit config files such as *menu.lst* or *sources.list* and a backup is made automatically;  very useful!

---

### Post by aussie.ian on 2006-06-12
Add remove programs won't accept root password, says 'Conversation with su failed'. Why would this happen?
Where can I find update repositories in au, I googled and got nothing.

---

### Post by xtacocorex on 2006-06-12
kate won't open under sudo, you need to use kdesu to open it as root.

---

### Post by vinodis on 2006-06-12
kubunta ~ kubuntu ! lol

---

### Post by aussie.ian on 2006-06-12
[QUOTE=xtacocorex]kate won't open under sudo, you need to use kdesu to open it as root.[/QUOTE]
I managed to get Kate open as root via 'run command as root', It's trying to get apt online thats the main problem. I've now edited /etc/apt/sources but all that happens when I check for updates is a time out. I need to add acouple of AU mirrors but am not sure which to add - does Kubuntu have its own repositories or are they shared with Ubuntu. The only ones I can find (so far) are here [http://mirror.isp.net.au/#ubuntu](http://mirror.isp.net.au/#ubuntu) 
I don't have the handbook for apt installed for some reason, when I click on Adept Manager Handbook, nothing opens. In help Adept is not available and the reference to Apt is for using apt-get from the command line. It seems the install disk I used only installs the Man pages as there is no Kubuntu/Ubuntu index available.
I'm used to Yast package management (Suse) and could really use some help getting some pointers.

---

### Post by aussie.ian on 2006-06-12
[QUOTE=aussie.ian]I managed to get Kate open as root via 'run command as root', It's trying to get apt online thats the main problem. I've now edited /etc/apt/sources but all that happens when I check for updates is a time out. I need to add a couple of AU mirrors but am not sure which to add - does Kubuntu have its own repositories or are they shared with Ubuntu. The only ones I can find (so far) are here [http://mirror.isp.net.au/#ubuntu](http://mirror.isp.net.au/#ubuntu) 
I don't have the handbook for apt installed for some reason, when I click on Adept Manager Handbook, nothing opens. In help Adept is not available and the reference to Apt is for using apt-get from the command line. It seems the install disk I used only installs the Man pages as there is no Kubuntu/Ubuntu index available.
I'm used to Yast package management (Suse) and could really use some help getting some pointers.[/QUOTE]
Is there noone can help with an Australian mirror for updating or aren't there any?
Where can I find the Adept Handbook?
Or is there another forum for specifically for Kubuntu?

---

### Post by fireshell on 2006-06-12
Sorry can't help you there, I use Kubuntu and have never found any Aussie mirrors for updates

---

### Post by barisurum on 2006-07-03
You can create a launcher for any app. to run as root by clicking the right mice button and selecting "create new launcher". write somethin' like this as command [COLOR="Red"]"kdesu kate"[/COLOR]. You may select an icon too.

---

