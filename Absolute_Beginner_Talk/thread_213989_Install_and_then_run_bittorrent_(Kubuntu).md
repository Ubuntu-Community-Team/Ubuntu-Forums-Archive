---
title: "Install and then run bittorrent (Kubuntu)?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by candtalan on 2006-07-12
Kubuntu is newly installed, and I want to use bittorrent rather than ktorrent. Adept indicated bittorrent was not installed, so I installed it, now it is listed as installed.   :-)

Now I need hints please about how I can run it, preferably from an icon or an apps list although a command line would get me going.
(I am familiar with linux - suse).

tia

---

### Post by Kobalt on 2006-07-12
Is there no bittorent icon in your K menu ? Otherwise, you can easily start it by pressing Alt+F2, then entering your app name... Or you can create a launcher. To locate the launch file of bittorent type "whereis bittorent" in a console. Then create your launcher with a right click on you desktop and give it the path you have been given by "whereis..." Associate an icon of your choice, description, and you're done !

Cheers !

---

### Post by fluffington on 2006-07-12
Edit: Ignore this post; I'm an idiot.

---

### Post by candtalan on 2006-07-12
> **Kobalt said:**
> Is there no bittorent icon in your K menu ? Otherwise, you can easily start it by pressing Alt+F2, then entering your app name... Or you can create a launcher. To locate the launch file of bittorent type "whereis bittorent" in a console. Then create your launcher with a right click on you desktop and give it the path you have been given by "whereis..." Associate an icon of your choice, description, and you're done !

Cheers !

Thanks. whereis indicates /usr/share/bittorrent, and alt-F2 bittorrent results in 
Sorry K Desktop:
bittorrent
could not run the specified command.

looking at /usr/share/bittorrent, it is a directory, not a file, that I see,the properites show
owner root, group root
permissions:  drwxr-xr-x
contents of directory: 0 files

So it looks as if bittorrent is not actually installed??
adept indicates it is installed.

I subsequently went to the bittorrent site and downloaded a deb file of it to install and installed via (context menu) (adept?) - it looked as if it was going in ok. 
looking deeper, Adept seemed to indicate python was needed (for this version or similar) and I got adept to install python. it seems. 
Unfortunately I still get
bittorrent
could not run the specified command

If I were go back to square one, how should I install it (via adept hopefully), which function or icon should I click on please? It looks as if I am missing something.

tia

---

