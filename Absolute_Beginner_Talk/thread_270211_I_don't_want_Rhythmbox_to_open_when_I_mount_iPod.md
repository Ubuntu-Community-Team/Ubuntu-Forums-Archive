---
title: "I don't want Rhythmbox to open when I mount iPod"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-10-02
How can I stop Rhythmbox from opening when I mount my iPod. If worst comes to worst I will delete it. I looked through rhythbox's settings and couldn't find anything.

---

### Post by aysiu on 2006-10-02
Go to System > Preferences > Removable Drives and Media

---

### Post by tdrusk on 2006-10-02
ah thanks.

---

### Post by orengolan on 2008-04-19
i can't see an iPod option in this screen on 8.04 beta.

any idea?

---

### Post by enigmaniac23 on 2008-04-19
Open Nautilus
Go to Edit --> Preferences 
Choose the Media tab
You should see Music Player.  You can change it here.

---

### Post by farueulogy on 2008-04-19
It's helpful if you make this as solved (if you're happy) :)

---

### Post by gandazgul on 2008-05-08
You cannot change the application there... The options are, Open Rythmbox or Do Nothing :mad:... how can I tell him to open something else?

Thanks

---

### Post by phoqueyoo on 2008-05-12
Same problem here. Rhythmbox doesnt work with my shuffle and gtkpod does. How do I make that autoopen instead of rhythmbox? The option does show up. It's either Open Rythmbox or Do Nothing. I couldnt find anything in gconf to add gtkpod.

---

### Post by stingrayl on 2008-06-07
I am having the same problem... 
I can set the option to "Do Nothing" in Nautilus when i mount my Ipod but I Can't change the program I want to handle the Ipod on mount event...

is there a way ?

---

### Post by aysiu on 2008-06-07
I'm not sure if this'll work or not, but in *gconf-editor*, try desktop > volume_manager

Check autoipod and change the autoipod_command from *rhythmbox* to *gtkpod*

---

### Post by mamcgrath on 2008-06-16
> **gandazgul said:**
> You cannot change the application there... The options are, Open Rythmbox or Do Nothing :mad:... how can I tell him to open something else?

Thanks
Edit the file /etc/gnome/defaults.list. Change the line 'x-content/audio-player=rhythmbox.desktop' to 'x-content/audio-player=gtkpod.desktop'. After logging back in you should be able to select gtkpod from Nautilus "File Management Preferences".

---

### Post by Wobblybob on 2008-06-19
> **mamcgrath said:**
> Edit the file /etc/gnome/defaults.list. Change the line 'x-content/audio-player=rhythmbox.desktop' to 'x-content/audio-player=gtkpod.desktop'. After logging back in you should be able to select gtkpod from Nautilus "File Management Preferences".

I've tried this in Hardy to select amarok but with no luck, any more ideas?

---

### Post by mamcgrath on 2008-06-19
> **Wobblybob said:**
> I've tried this in Hardy to select amarok but with no luck, any more ideas?

Did you log out and back in again after making the change?

---

### Post by mamcgrath on 2008-06-19
> **Wobblybob said:**
> I've tried this in Hardy to select amarok but with no luck, any more ideas?

OK. I installed amarok and initially it didn't work for me either. The installation creates several launcher files - amarok.desktop - but doesn't create one in '/usr/share/applications'. After copying one of the existing files to this directory, it works fine.

sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/

---

### Post by Wobblybob on 2008-06-20
> **mamcgrath said:**
> OK. I installed amarok and initially it didn't work for me either. The installation creates several launcher files - amarok.desktop - but doesn't create one in '/usr/share/applications'. After copying one of the existing files to this directory, it works fine.

sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/

Your a star mate, that works a treat, thanks for your help.

---

