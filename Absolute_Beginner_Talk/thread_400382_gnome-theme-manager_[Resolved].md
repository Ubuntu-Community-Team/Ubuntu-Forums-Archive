---
title: "gnome-theme-manager [Resolved]"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by zenic on 2007-04-03
[B]Hello. I  installed ubuntu (6.10) a couple of days ago. It's the first time I'm using linux and loving it. Unfortunately,  I have a problem with the gnome theme manager. When I run the command (gnome-theme-manager) I get the following error:

[COLOR="Red"]gnome-theme-manager: error while loading shared libraries:    /usr/lib/libmetacity-private.so.0: invalid ELF header[/COLOR]

I searched but was unable to find a solution and need some help. Thanks.[/B]

---

### Post by aysiu on 2007-04-03
I'm not sure if this'll help, but can you try pasting this command into the terminal? ```
sudo apt-get update && sudo apt-get install libmetacity0
``` If that doesn't work, post the output of that and the output of ```
gnome-theme-manager
```

---

### Post by zenic on 2007-04-04
Thanks for the reply. It didn't work. Here's the output:

[COLOR="Red"]Get:1 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/restricted Translation-en_US   
Get:2 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]        
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy Release                        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates Release                
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/main Packages                       
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/restricted Packages                 
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/main Sources  
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/restricted Sources
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release    
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/main Packages             
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/restricted Packages       
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [77.5kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [5678B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [15.8kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [937B]
Fetched 151kB in 4s (36.0kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmetacity0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.[/COLOR]

The gnome-theme-manager output is the same as before:
[COLOR="Red"]
gnome-theme-manager: error while loading shared libraries: /usr/lib/libmetacity-private.so.0: invalid ELF header[/COLOR]

---

### Post by seshomaru samma on 2007-04-04
can you change themes graphically?

---

### Post by zenic on 2007-04-04
You mean System-Preferences-Theme? No I can't. I see a Starting Theme (on the taskbar) for a few seconds and then it stops. It doesn't load anything. I also installed Beryl with AIGLX and Emerald Theme manager which seems to work but, I don't know how to apply the themes from it.

---

### Post by zenic on 2007-04-04
You mean System-Preferences-Theme? No I can't. I see a Starting Theme (on the taskbar) for a few seconds and then it stops. It doesn't load anything. I also installed Beryl with AIGLX and Emerald Theme manager which seems to work but, I don't know how to apply the themes from it.

---

### Post by 3rdalbum on 2007-04-04
> **zenic said:**
> You mean System-Preferences-Theme? No I can't. I see a Starting Theme (on the taskbar) for a few seconds and then it stops. It doesn't load anything. I also installed Beryl with AIGLX and Emerald Theme manager which seems to work but, I don't know how to apply the themes from it.

I think you've just told us the key - Beryl does trample on Gnome's settings manager a bit, and it's possible that the repository you've added has changed Metacity.

Try getting rid of the lines about "http://ubuntu.beryl-project.org" from your sources.list and doing the following:

Go into Synaptic package manager
Press the "Reload" button
Go to Edit > Search
Select "name" from the drop-down menu and type "libmetacity0" (without the quotes)
Hit the Enter key. When the search finishes, right-click on the libmetacity0 entry and do "Mark for reinstallation".
Press Apply.

When that's done, log out and then log back in, and hopefully that has helped.

By the way, I was very impressed with the way you asked for help, and how you searched Google before asking. You'll go far in the Linux world, my friend!

---

### Post by zenic on 2007-04-04
Thanks. Your solution worked perfectly. Theme manager is up and works great. Kept beryl though (really nice it is). :). Next in line those dull looking bars and tv-out (NVIDIA) which, will definitely be adventurous.

---

