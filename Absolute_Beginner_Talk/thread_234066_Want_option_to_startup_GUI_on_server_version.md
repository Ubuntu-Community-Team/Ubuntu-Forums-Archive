---
title: "Want option to startup GUI on server version"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by tudedude on 2006-08-10
I have installed the server version of Ubuntu with the command line interface. I want to continue to always boot to command line but have the option of starting a GUI by running startx. 
How do I do that? 
I have not downloaded gnome or anything else yet. The only reason I want a GUI option is so I cna run automatic backups to disk of my home network with backuppc which apparently requires a gui and apache server. I have not installed either.
Thanks for everyone's help

---

### Post by VirtuAlex on 2006-08-10
Are you sure you need gui for backuppc? I think apache will provide you sort of gui through remote administration. If I'm wrong there are tons of options. Look at [http://www.linux-backup.net/]("http://www.linux-backup.net/").

---

### Post by bonjun on 2006-08-10
You have to install ubuntu-desktop or xubuntu-destop to run gui.

---

### Post by bonjun on 2006-08-10
> **VirtuAlex said:**
> Are you sure you need gui for backuppc? I think apache will provide you sort of gui through remote administration. If I'm wrong there are tons of options. Look at [http://www.linux-backup.net/]("http://www.linux-backup.net/").

i guess [this]("http://backuppc.sourceforge.net/") is what he is talking about

---

### Post by VirtuAlex on 2006-08-11
> **bonjun said:**
> i guess [this]("http://backuppc.sourceforge.net/") is what he is talking about
Yeah, I understand, but the screenshots are seem to be screenshots from the browser window, which explains why apache is needed - for remote administration. So there is no gui. All the gui is the browser on the client machine. Or I did get it wrong?

---

### Post by tudedude on 2006-08-11
There is a central administration screen that you go to within a browser window and it is on the server to manage backups of the server and remote systems.

---

### Post by VirtuAlex on 2006-08-11
> **tudedude said:**
> There is a central administration screen that you go to within a browser window and it is on the server to manage backups of the server and remote systems.
What prevents you to access that screen from any client machine? Isn't that apache supposed to do - serve the http requests?

---

