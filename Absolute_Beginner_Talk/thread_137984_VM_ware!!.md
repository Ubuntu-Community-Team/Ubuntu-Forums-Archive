---
title: "VM ware!!"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by ubugoda on 2006-03-01
hello people!!
 i've installed VM ware into my ubuntu machien,and in  a VM i've created Windows xp proffesional system and it works well.
my  problem is i can't handle files between the two systems,Is there any tool or something that allow me to exchange the files!!

---

### Post by andrewsawyer on 2006-03-01
I've found the best way to do it is through networking.  If you set up your (windows) desktop as shared, then you should be able to access it though Linux using SMB.

---

### Post by ubugoda on 2006-03-01
thnx for the help and care!!
But the problem is i'm new to linux and i dunno how to set up a LAN!!
i'm already connected to the internet through a LAN,WHAT EXCATLY SHOULD I DO TO SHARE FOLDERS BETWEEN THE HOST AND THE GUEST OPERATING SYSTEM???
THANK YOU

---

### Post by andrewsawyer on 2006-03-01
From memory (which isn't too good!), you should just be able to click 'Places' on the Gnome Panel, and then choose 'Network Servers' and fingers crossed Windows should show up.

Obviously you have to have the VMware Virtual Machine up and running at the time.

You may have to install Samba from Synaptic too.  Try first without, then if it doesn't work try downloading it and give it another go.

---

### Post by n3ldan on 2006-03-01
Ah, has been a while since I ran that old beast.  Yeah, there is another way, or atleast I think it's different...  It shows up as a network resource in Windows, but it's actually just a regular folder to linux.

I think it's this:
[http://www.vmware.com/support/ws4/doc/running_sharefold_ws.html](http://www.vmware.com/support/ws4/doc/running_sharefold_ws.html)

---

### Post by ubugoda on 2006-03-02
Thanks it worked and also without installing samba,,But i think that there is a tool could be setup in the guest OP that allows you to brows ur real machien content,,,Anyone knows anything about it?

---

### Post by andrewsawyer on 2006-03-02
Not heard about it no, however I would be insterested to find out.

On a side topic, I installed Dos 6.22 and Windows 3.11 the other day (into VMware).  It loads up in 5 seconds flat to fully workable.  Unfortunately I can't get any more than 640x480 out of it, and I can't get networking to work either :-( Took me back though!

---

