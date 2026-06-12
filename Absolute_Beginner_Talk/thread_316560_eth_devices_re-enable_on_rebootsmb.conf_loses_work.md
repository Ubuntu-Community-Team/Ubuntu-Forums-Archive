---
title: "eth devices re-enable on reboot/smb.conf loses workgroup"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by urbancontra on 2006-12-10
I installed Kubuntu 6.10 a couple days ago and got pretty much everything I need working on my own, but I have a few questions I can't figure out on my own.  I haven't found anything with Google or the search here (maybe my search isn't good enough!)

I have Samba running on this box to share out folders to my Xbox.  I edit /etc/samba/smb.conf with my workgroup name and everything is awesome.  After I reboot, though, I can't reach my shares with my xbox.  I open up smb.conf again, and the "workgroup =" and "server string =" lines are gone.  The rest of the stuff I added manually is there.  What gives? I followed these directions originally to get it working: [http://www.xboxmediacenter.com/wiki/index.php?title=Linux_File_Sharing_%28using_samba%29](http://www.xboxmediacenter.com/wiki/index.php?title=Linux_File_Sharing_%28using_samba%29)

Also, every time I reboot, I have to disable ath0 (a wireless card in my box I only use in case of emergencies) and eth1 (my motherboard has 2 NICs and I dont use the other one).  I do this through the "network settings" area in "system settings" from the K menu.  I'm obviously a long-time WIndows user and I don't know what the terminal commands are for a lot of things, including this.  Is there a better way to tell linux to disable these devices permanently?

One more general question: I have weird problems, like certain programs (Synaptic, usually) failing to start for no reason, then starting the next time I try to use it.  Should I blame Edgy?  Would 6.06 be better for someone who doesn't want to deal with random problems?

[Edit: Read stickies like a good boy.  Should I go to 6.06 or another release for a stable install?  Is Kubuntu 6.06 as stable as Ubuntu 6.06?  I kinda like KDE better.]

---

### Post by urbancontra on 2006-12-11
Too hard for the beginner's forum? :P

---

