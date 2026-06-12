---
title: "Inquiry for Ubuntu?"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by livefordirty on 2006-05-29
I just installed Ubuntu 5.1,    
Can i install snort and other network utility like nmap,netcat...... into Ubuntu?

---

### Post by kingmonkey on 2006-05-29
```
sudo aptitude install nmap netcat 
```

---

### Post by catlett on 2006-05-29
I don't know about the apps you're asking for but you can browse the available selection. Go to the top of the screen and hit on "System" when the box drops down go to "Administration" scroll down to "Synaptic Package Manager". This has the listing of all the applications available for download and installation.
You can pick a category or just choose "All" to list all the packages and you can scroll through them, Each entry has brief description. There is also a search box where you can enter a keyword.
If you find sonething, right click on it and choose "mark for installation" from the options. Then hit "apply" at the top of the window and the application will be automatically installed.
Under my post in my signature are links to "how tos" about progeam installation.

---

### Post by livefordirty on 2006-05-30
What i meant is :  
 can you install application and softwares which are not listed in the "synaptic"?

---

### Post by Klaidas on 2006-05-30
Umm sure you can :)
But that way you'll need to compile them/use a .deb file.
Some of usefull applications can be found on Universe/Multiverse. Did you enable that?

---

### Post by Jussi Kukkonen on 2006-05-30
[QUOTE=livefordirty]What i meant is :  
 can you install application and softwares which are not listed in the "synaptic"?[/QUOTE]

Of course -- you rarely need to, though. Everything you mentioned is available in the repositories.

---

### Post by Jagot on 2006-05-30
[QUOTE=livefordirty]What i meant is :  
 can you install application and softwares which are not listed in the "synaptic"?[/QUOTE]

Check out this link for installing using various methods, including for stuff that is not in the repositories:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by gr0kzer0 on 2006-05-30
If you want an app that isn't listed in Synaptic, try to find a .deb file of it.  You can install .deb files just by using the dpkg -i command.

If there's no .deb version, there will be installation instructrions in the tarball, usually in a file called README.

If there's a .rpm version available, I think you can install it using "alien" command

---

