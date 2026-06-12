---
title: "Some Questions"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by chameleonkid on 2006-06-10
Hey. First time poster long time linux admirer. I just switch over to Ubuntu this weekend from xp, and I am digging what I am finding and learning. I have some questions though being a 'newb' to linux.

1. When trying to launch xmms from the terminal (which I love to do btw) I keep getting this message
 <b>libmikmod.so.2: cannot open shared object file: No such file or directory
Message: device: default
</b>
and then xmms starts but as soon as I exit the teminal it exits out of the graphical xmms. I still find that I can control xmms in the terminal though once started graphically.  I am def. confused by this little statement and am wondering why it occers/how to stop it. 

2. Being a huge bittorrent fan and coming from xp I was a little scared to be going back to the olden days with Bittorrent (I was used to the wonderful uTorrent, which hopefully can surface on linux soon!), and am afraid my fears were confirmed. While not a master of the torrents I know how to set up for maximum dl/ul. I was shocked and appalled when I could not dl more than one torrent at a time, because "the port is already being used." Is there a way to change this or am I stuck in this singlularity?

Thanks and keep up the good work Ubuntu.

---

### Post by Solver on 2006-06-10
Launching apps from the terminal is a bit special. If you launch xmms from the terminal, it has to stay open for xmms to continue running. Basically, once you close the terminal, you abort whichever command it is currently running - xmms in your case. You can always press Alt+F2 to get a window where you can type in your command, if you prefer launching applications that way.

As for torrents... I'm sure you know about Azureus. Perhaps you should consider installing that on Ubuntu? It's after all a full-featured client with many options.

---

### Post by zugu on 2006-06-10
```
sudo apt-get install libmikmod libmikmod-dev
``` should solve the XMMS issue you have.
Can't help you in the bit torrent issue though.

LATER EDIT: I just found out that uTorrent is Gold on the Wine application list. This means that you can install Wine by:```
sudo apt-get install wine
``` then download uTorrent for Windows on your desktop and run it with```
wine /home/yourname/Desktop/utorrent.exe
```However, you might experience some minor glitches and bugs, as the application is not Platinum (i.e. does not work flawlessly with Wine)

---

### Post by chameleonkid on 2006-06-10
I tried that Zugu and this is what happened:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmikmod

Kinda weird, I'm thinking.

And Azureus. Blah. I tried installing that and it worked like a bloated charm, id est not very well. If anything I'll stick with bit torrent and my one torrent dl's.

P.s. Is it normal to have cpu processes in the 50%s and higher up to 90% when running simple programs?

---

### Post by zugu on 2006-06-10
I'm so sorry, I forgot to type a "2". Try```
sudo apt-get install libmikmod2 libmikmod2-dev
```And let me know how uTorrent works under Wine, if you decide to give it a try.

---

