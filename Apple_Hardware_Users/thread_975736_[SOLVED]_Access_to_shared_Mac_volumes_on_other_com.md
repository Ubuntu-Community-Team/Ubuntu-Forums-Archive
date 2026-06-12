---
title: "[SOLVED] Access to shared Mac volumes on other computers"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by mfox on 2008-11-08
I have an MSI Wind netbook running Ubuntu 8.04.1 in an otherwise Mac household.  What I'd like to be able to do is get wireless access to shared volumes on the Macs in my house.   My wireless router is a Time Capsule, and I can presently access shared volumes from one Mac to another; all running Leopard.  Ideally, I'd like to be able to mount one as I can now do from Mac to Mac.

---

### Post by bryonak on 2008-11-08
How comfortable do you feel with the command line?
Right now Iv'e got Samba and SSHFS in mind.

The first one requires you to enable Samba sharing on the OSX shared volumes/folders, which is fairly simple... and add an entry to your Ubuntu file system table (/etc/fstab), which isn't that hard either but requires some knowledge.

The second one only requires a SSH daemon (no problem with OSX) on the target machines and gives you a state-of-the-art encrypted connection, but is a bit slower and cannot display the free space left on remote drives.
The setup is also fairly straightforward, but again specific knowledge is needed, especially if you want to dynamically mount the drives while on your home WLAN but not when in the public...

Then again, that's what these forums are for ;)

---

### Post by cyberdork33 on 2008-11-08
You can also access AppleTalk shares with netatalk.

---

### Post by mfox on 2008-11-09
Thanks, cyberdork.  Connecting with netatalk was incredibly easy. In fact, I connected without any passwords in spite of the fact that a password is required from another Macintosh.  Should I be worried about this?  Does it mean that anyone outside my network can connect to it?

I could also see my Time Capsule from my MSI Wind.  Does that mean that I could back up my Ubuntu onto the Time Capsule using Time Machine?

---

### Post by cyberdork33 on 2008-11-10
> **mfox said:**
> Thanks, cyberdork.  Connecting with netatalk was incredibly easy. In fact, I connected without any passwords in spite of the fact that a password is required from another Macintosh.  Should I be worried about this?  Does it mean that anyone outside my network can connect to it?
If it is supposed to be password protected, it very well may be a security concern. Although, if you use the same login and password on both machines, it may be automatically passing your login for authentication. Whether access from outside your local network is possible would be more dependent on your network / firewall arrangement. (Services don't normally just passthrough a firewall unless it is specifially allowed.)

> **mfox said:**
> I could also see my Time Capsule from my MSI Wind.  Does that mean that I could back up my Ubuntu onto the Time Capsule using Time Machine?
Yes. As far as I know the Time Capsule is just a Network Shared hard Drive, and thus you can access it just as any other shared volume (I can't verify this though since I do not have one). Be aware of permissions issues though. There is a project to create something similar to Time Machine for Linux:
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by mfox on 2008-11-10
> **cyberdork33 said:**
> If it is supposed to be password protected, it very well may be a security concern. Although, if you use the same login and password on both machines, it may be automatically passing your login for authentication.... 
Actually, I do use the same login and password on both machines, but I also do on the other Macs in the house and they still ask me for name and password.  I guess Ubuntu (Linux?) is different in that regard.

> **cyberdork33 said:**
> Yes. As far as I know the Time Capsule is just a Network Shared hard Drive, and thus you can access it just as any other shared volume (I can't verify this though since I do not have one). ...
Time Capsule is a network shared drive in a sense, but using it as a Time Machine backup is different.  I know there is software to allow Time Machine backups to work on a Windows volume, but I'm not sure the same is true in Linux.  It's academic at the moment, but if I started using Linux for all of my regular work, it would be nice to be able to back up a volume with the elegant Time Machine solution on my Time Capsule.

---

### Post by harry.bush on 2009-01-17
hi
i'd like to know how you managed to configure netatalk to let you mount your time capsule from ubuntu
thanks

---

### Post by mfox on 2009-01-17
I didn't have to do any configuring, as I recall.  I just installed Netatalk, and it allowed me to see any shared volumes in my home network that were not sleeping or turned off.  This included the Time Capsule but note that what it sees on TC were files I had copied there, not the Time Machine Backups.  I don't know how to backup a Ubuntu volume with Time Machine, as Apple hasn't provided the software to do anything other than a MacOS or Windows TM backup.

---

### Post by harry.bush on 2009-01-18
hi
thanks for the reply!
when you say "...I just installed Netatalk, and it allowed me to see any shared volumes in my home network..."; how exactly did it let you see these volumes?
do you mean to say they appeared in nautilus the second you installed Netatalk?
thanks again

---

### Post by mfox on 2009-01-18
Sorry, Harry; I wasn't very specific.  After you install Netatalk and enable shared volumes on your Mac, your Mac volumes will appear in Network, which, in turn, should show up as an option under Places in your Gnome menu or on the left side of your file browser.  Your query was timely; I had just installed Ubuntu 8.10 on my MSI Wind (I had 8.04 on there with Netatalk before), so I had to get Netatalk again.  I did it through apt and when I was finished, Netatalk was automatically turned on.

I found an article [here]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") which actually covers Time Machine, though I haven't tried that part of it.  I hope this is more helpful.

---

### Post by harry.bush on 2009-01-20
hi

thanks for the info!

i think my problem resides in the fact that there is only one computer (my ubuntu desktop) connected to my time capsule...there is no mac coputer that can share the time capsule so that my ubuntu (w/ netatalk) can pick it up...

thanks anyways for your help. in the mean time, i'll survive with afpfs-ng

---

