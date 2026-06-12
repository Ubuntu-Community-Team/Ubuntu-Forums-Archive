---
title: "Bluetooth sync my Samsung Phone?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-06-07
Hi,
I've managed to set up some sort of connection between my samsung e250 and my PC over bluetooth. All I've managed to do so far is send files from the phone to the PC and vice versa.
How might I sync my contacts and calendar between evolution and my phone?
I've installed multisync, and the ximian evolution plugin. I've also installed the syncml plugin. I don't really know what syncml is, but my phone has it, and there is a plugin for it on multisync, so I thought it would be a good place to start!  I'm stuck with what to do next, though.

Also, is it possible to use bluetooth to browse my phone and copy files to specific locations?  Any file sent over bluetooth ends up in the phones main memory, but this is pretty small. I'd like to be able to copy larger files onto the phone's memory card. 

Thanks!

---

### Post by Fidelio on 2007-06-07
Still not much further with this. I can still send files to and fro, but I haven't been able to set up a pairing.
On my phone, I can select the device (linux pc) and enter a pin, but I don't get prompted to enter a pin on the pc and the connection fails. can I set up a pair from the PC? The gnome bluetooth app doesn't seem to have that option.

---

### Post by Coombabah on 2007-06-07
I also have a Samsung E250 and want to sync the calendar etc via bluetooth.

Last time I tried this transferring files back and forth was as far as I got :(

Now that the phone has been around for a while I'm hoping that more will be possible.

I'll post here if I have any success.

---

### Post by Fidelio on 2007-06-08
Well, I've paired my phone with my PC now, which was just a case of changing a line in the hcid.conf file from 'security user' to 'security auto'
It doesn't really seem to have got me anywhere though. I can still send files to and fro (which I could do even without pairing) but I can't sync or browse my phone
If I start multisync and set up a pair with ximian evolution as the first plugin and syncml as the second, nothing happens when I press the sync button. I've tried using the irmc mobile device plugin as the second plugin too, but with this, multisync crashes.

I feel it should be possible...

---

### Post by Fidelio on 2007-06-09
Bit further forward but still looking for help.
I tried adapting these instructions [http://ubuntuforums.org/showpost.php?p=1998822&postcount=62](http://ubuntuforums.org/showpost.php?p=1998822&postcount=62) for gnome and my phone, but I'm not sure I understood it all.
I've now got my phone paired, I've got the evo-sync2 and syncml-obex-client which I can see and configure in the multisync gui.
I've tried different bluetooth channels, as I can't work out which one I should use. Depending on which one I use, I either get 'error while connecting' or a  'slow syncing' message.
The phone does say it's connected sometimes though. I must be getting close to this! Anyone know what else I need to do!

---

### Post by Fidelio on 2007-06-11
Samsung are really not very helpful people!

I think this should work. I'm using opensync with the evo2-sync and syncml-obex-client plugins. I'm trying to configure them with multisync gui, but I'm getting nowhere.
I really need to know the settings samsung uses for syncml. I need to know what bluetooth channel to use, what the device id string is, and what the names of the databases are for contacts, calendar etc. I emailed their technical support, and despite the fact that I just asked for a bit of info, they just gave a reply which said they only support windows. 
Can anyone give me a pointer here? Ive used sdptool browse but i'm not sure how to interpret the results. 
I've set up the connnection and sync function on my XP machine and tested it. It works fine. Maybe there's some way I could dig around in my windows configuration files and find what I need there?

---

### Post by alek66 on 2007-06-13
I'm about to buy that phone, does it works??

---

### Post by Fidelio on 2007-06-13
Sending files over bluetooth between the pc and the phone was really easy to set up and works great. 
But I still haven't managed to sync evolution. Great little phone though.

---

### Post by alek66 on 2007-06-13
you can browse all the phone files? what program do you use?
I am under ubuntu and i still dont have a good program todo browse. Except the KDE ones, but they tend to load a lot a libraries because I use gnome

---

### Post by Fidelio on 2007-06-13
No, I haven't worked out to browse using native gnome apps either.

---

### Post by Inxsible on 2007-06-13
Have you tried using Wammu, to get access to your SMSes contacts calendars todos etc?

---

### Post by alek66 on 2007-06-17
I can now browse to the files in the phone. But I still dont know how to sync contacts.
boomer

---

### Post by Fidelio on 2007-06-18
I can't even get wammu to work.I'll have a twiddle. But still got to get something to do the evolution sync.

---

### Post by mjamesd on 2007-11-07
I have a Samsung a900m and I use the bluetooth-analyzer package to connect, pair, and bond to my phone.  On my machine, I can right-click on the icon in the system tray by the clock, click "Browse Device...", it searches and finds my phone, I click it and click "Connect", and it opens Nautilus browser and I can view the files in my phone's "Exchange Folder". I think you may have to have gnome-obex-server and gnome-vfs-obexftp packages installed to do this.

---

