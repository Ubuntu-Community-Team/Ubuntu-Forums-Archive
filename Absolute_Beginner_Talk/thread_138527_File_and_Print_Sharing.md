---
title: "File and Print Sharing"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by wizzkid on 2006-03-02
Hi! I want to set up file and print shring here at my home network. my setup are:

Server - Windows XP Pro 
Client - Kubuntu 5.10

Do I need samba on windows xp? if not, what should I setup and where could i browse the windows xp file and print from kubuntu? :)

Any help will be highly appreciated. thanks.

---

### Post by soonindallas on 2006-03-02
Hello.

Samba is a linux app that will allow you to share folders, files and printers both ways with Windows computers over a network.

I have my Ubuntu box networked with a WinXP box.  The XP box has a printer that is shared and I print from Ubuntu to this printer.

You need samba on your ubuntu box (look in synaptic, though I think it's in the default install).

Check in the file /etc/samba/smb.conf that samba is using the same windows workgroup name as your windows box (MSHOME by default).

whenever you change smb.conf you need to restart samba so the new config gets loaded: ```
sudo /etc/init.d/samba restart
```

On your windows box you need to enable sharing of your files and printers as necessary (in folder properties and printer properties) and check in the XP firewall exceptions that these services are allowed.

you can configure your shares on ubuntu using system>administration>shared folders and printers are installed with system>administration>printing and choose network printer, windows printer (smb).

search the forums a bit and you'll find tons of information about samba configuration.

---

### Post by wizzkid on 2006-03-02
I Already installed the samba... when I go to Control Center > Internet & Network > sharing > file sharing. it says that I have to logged in as administrator, but the window is cut. so I cant see the very buttom part of the window. I even had it full screen still the same. Image snapshot is attached to this thread. 

Also, when I click Local Network browsing , it says The module could not be found.
Deatils:
The diagnostics is:
The desktop file could not be found.

I am using 1280 x 800 

My System is:
DELL Inspirom 700m
Kubuntu 5.10 Breezy

Please help!

---

### Post by soonindallas on 2006-03-03
I am not familiar with KDE but there is a whole forum dedicated to it ;-)

[QUOTE=wizzkid]I Already installed the samba... when I go to Control Center > Internet & Network > sharing > file sharing. it says that I have to logged in as administrator, [/QUOTE]

look at this thread: [http://www.ubuntuforums.org/showthread.php?t=121425&highlight=file+sharing](http://www.ubuntuforums.org/showthread.php?t=121425&highlight=file+sharing)

and this one:

[http://www.ubuntuforums.org/showthread.php?t=122837&highlight=file+sharing](http://www.ubuntuforums.org/showthread.php?t=122837&highlight=file+sharing)

[QUOTE=wizzkid]but the window is cut. so I cant see the very buttom part of the window....
I am using 1280 x 800 
[/QUOTE]

should you be using 1280 (or 1200) x 768 ?

---

### Post by Haegin on 2006-06-06
Simple fix for the cut off window problem.
1. Move the window so the top bar rests against the top of the screen
2. Drag the bottom of the windows down to make the window taller
3. Keep dragging until you see buttons

:)

P.S - if it is all greyed out you need to install samba for sharing with windows and nfs-kernel-server for sharing with other linux machines :)
For both: ```
sudo apt-get install nfs-kernel-server samba
```

[quote=soonindallas]
should you be using 1280 (or 1200) x 768 ?
[/quote]
I would assume its a widescreen as (im pretty sure) the Dell Inspiron is a laptop so the 1280 x 800 would be fine.

---

