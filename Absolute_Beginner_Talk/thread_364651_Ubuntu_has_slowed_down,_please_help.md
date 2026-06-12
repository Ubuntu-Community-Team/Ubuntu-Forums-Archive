---
title: "Ubuntu has slowed down, please help"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Tahir on 2007-02-18
I installed Ubuntu and I have got everything to work.  Then it slowed down.

This is what I did before it slowed down:

What I did was first install  flashplugin-nonfree from Synaptic Package Manager and then I opened firefox to see if it worked.  I went on Google Video and it asked me to install a plugin to view the videos and I installed it from firefox.  

When I started the PC on a later date I logged in as usual but when I tried to click on things nothing would open.  I tried logging in three times and after logging in the whole GUI would freeze if I tried to do anything.   I then logged in using safe mode and then I I uninstalled flashplugin-nonfree and restarted the computer in normal mode. 

Now after I login I can open things but the problem is that the whole user interface takes much longer to load.  (After its loaded, the system behaves normally).

How do I get it back to how it was (same thing but quicker loading after login)?

Is there a file which contains all the programs to load at boot time? I would like to edit it.

Thanks for reading,
-Tahir

---

### Post by Maestro23 on 2007-02-18
What was the plugin?  I just visited google video for the fist time on my Ubunutu machine/Firefox and was not asked to install any kind of plugin.

---

### Post by Tahir on 2007-02-18
> **Maestro23 said:**
> What was the plugin?  I just visited google video for the fist time on my Ubunutu machine/Firefox and was not asked to install any kind of plugin.

I installed Ubuntu just two days ago, and if you click on one of the videos on google video then a message will appear and a green jigsaw telling you to install a plugin to view video files.

I installed Ubuntu 6.10 Edgy Eft Desktop, for 32 bit machines.

Hope this helps,
Tahir. 

p.s if you already have flash player installed then it would just play the video, not tell you to install anything.

---

### Post by Maestro23 on 2007-02-18
> **Tahir said:**
> I installed Ubuntu just two days ago, and if you click on one of the videos on google video then a message will appear and a green jigsaw telling you to install a plugin to view video files.

I installed Ubuntu 6.10 Edgy Eft Desktop, for 32 bit machines.

Hope this helps,
Tahir. 

p.s if you already have flash player installed then it would just play the video, not tell you to install anything.

I might have mis-read your original post. Did you have the flash-plugin installed before you tried to watch a google vid?

The plugin would not be causing a slow-down in your system though.  Hmmm...

---

### Post by Tahir on 2007-02-18
> **Maestro23 said:**
> I might have mis-read your original post. Did you have the flash-plugin installed before you tried to watch a google vid?

The plugin would not be causing a slow-down in your system though.  Hmmm...

Yes and it then asked me to install something else.  Anyway do you know of any places where I can view the startup programs, I would be interested in seeing whether anything else installed itself when I updated ubuntu.

Cheers,
-Tahir

---

### Post by Maestro23 on 2007-02-18
> **Tahir said:**
> Yes and it then asked me to install something else.  Anyway do you know of any places where I can view the startup programs, I would be interested in seeing whether anything else installed itself when I updated ubuntu.

Cheers,
-Tahir

Log files are kept in [COLOR="Red"]/var/log [/COLOR]

Not sure which one might contain what you are looking for though.

**Old Pink has the ticket. Don't know why I didn't think of that. LOL

---

### Post by Old Pink on 2007-02-18
Is it running slow now? Head to System > Administration > System Monitor.

Go into the "Processes" tab, and hit "Resident Memory" until the highest resident memory value is at the top of the list. Now hold Alt and hit Print Screen. 

Save the image to your desktop or /tmp directory and upload it in a reply when you can, that should help. :)

---

### Post by Tahir on 2007-02-18
> **Old Pink said:**
> Is it running slow now? Head to System > Administration > System Monitor.

Go into the "Processes" tab, and hit "Resident Memory" until the highest resident memory value is at the top of the list. Now hold Alt and hit Print Screen. 

Save the image to your desktop or /tmp directory and upload it in a reply when you can, that should help. :)

nothing seems sinister in the picture, but recalling the events on the day,  what I can now remember is that I updated Ubuntu (the computer downloaded about 220 MB of updates and this may have slowed the boot.  But in fact forget the whole thing (consider it resolved) because even Windows XP has a slow boot when you install loads of programs and I have to say that Ubuntu is WAY faster than XP for me.

BTW there is no "Resident Memory" its just called "memory" on mine.

Cheers,
-Tahir

heres the picture anyway:

[[IMG]http://img509.imageshack.us/img509/6552/screenshot1sh9.th.png[/IMG]](http://img509.imageshack.us/my.php?image=screenshot1sh9.png)

---

