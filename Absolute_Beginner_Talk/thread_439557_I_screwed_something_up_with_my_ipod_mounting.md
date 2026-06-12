---
title: "I screwed something up with my ipod mounting"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by aleska on 2007-05-10
So, I just did something that I can't seem to undo, and need help.

I'm running Ubuntu Feisty 7.04, and when I used to attach my ipod to it, it autodetected and automounted to "/media/IPOD".  I was trying out GTKPod for the first time, and when I tried to "connect" the ipod, it said that it couldn't find "/media/ipod".  
I thought maybe it was a case sensitive thing "IPOD" vs "ipod".  So, I right clicked on the ipod icon on my desktop, and in the preferences was a section to label the mount point.  So, I believe I changed it to "/media/ipod".  I ejected (unmounted) then reconnected the ipod.  
Now, I get an error message when I reconnect the ipod.  
It says, 
> Cannot mount volume.  Unable to mount the volume 'IPOD'.  Details:  mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
Help!  Please!  :(  I've goofed, and I can't ungoof it.  Is there a config file somewhere I should be looking at?
TIA - aleska

---

### Post by diatribe on 2007-05-10
whereever you mount things (should be /media)  rename the directory ipod to IPOD and it should work.

this may have to be done from the terminal; 

sudo mv /media/ipod /media/IPOD

when you are done and if it works, open gtkpod and edit the preferences to set your mountpoint to /media/IPOD

---

### Post by aleska on 2007-05-10
Now there is no /media/IPOD or /media/ipod 
So there is nothing to move with the mv command.  When I attach my ipod, I get the error I mentioned in my post.  That's it.  Now the ipod doesn't get mounted at all.

---

### Post by diatribe on 2007-05-10
in your media folder, mkdir IPOD

---

### Post by aleska on 2007-05-10
diatribe: in case it makes a difference, /media/IPOD used to be created automatically when the ipod connected.  It wasn't something I created and then manually mounted to...it was all done automatically until I "broke" it.  
That said, are you saying that if I manually create the directory under media it should work again?

Sorry if I'm being dim...I just want to make sure I understand how it works.

---

### Post by Keith Hedger on 2007-05-11
Hi
Ive just had exactly the same problem I fixed it by rebooting with my ipod plugged in and then opened the "Computer" folder thats on the desktop (you can set nautilus to show this in gconf) the ipod then showed up as "apple media player" or some such I right clicked on it and in the volumes tab under mount point I reset the mount point to ipod from /media/ipod and that fixed the problem.
Hope this works for you:)

---

### Post by symera on 2007-05-12
I fell for exactly the same gaff 
When I plug in my iPod (shuffle) nothing happens at all :( 
No lights come on on the player
cat /proc/scsi/scsi doesn't mention apple at all
no directories are created in /media
restarting doesn't seem to breathe new life into it either.

The strange thing is I'm pretty sure I didn't change the mount point from /media/ipod, it was more like /mnt/robs_suffle or something to begin with.  

Does anyone know how to get it back?
-r

---

### Post by kordite on 2007-05-13
My problem happened when I upgraded from v6.06 to v7.04. When I had the earlier version, I'd plug it it, it would mount, all's well. After the upgrade, nothing at all.

---

### Post by kordite on 2007-06-02
Similar problem when I upgraded. I have made some slight progress, however.

When I would plug it in, nothing would happen. No icon on the desktop. Nothing in /media. The iPod would show "charging" but it wouldn't have the "Do not disconnect" message of it actually being connected. Based on another forum posting, I plugged in the external power supply to my USB hub and now I'm getting the "Do not disconnect" message and "Cannot mount volume. mount:mount point /mst/ipod does not exist"

Both ipod and Apple iPod Music Player appear in the Computer. Nothing appears in the /media.

---

