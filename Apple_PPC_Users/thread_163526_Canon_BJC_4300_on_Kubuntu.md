---
title: "Canon BJC 4300 on Kubuntu"
date: 2006-04-21
forum: Apple PPC Users
---

### Post by richbarna on 2006-04-21
Hi everyone, 
I am new to this forum as a user, although I have been using this forum for the last 2-3 months to find solutions to my problems.
Just want to say thanks to everyone for helping me solve all of my software and hardware problems.

I am stumped with my printer, I have spent a week looking for solutions to no avail.
Here is the problem:-
I am Dual booting XP with kubuntu 5.10 that recognises my printer ( Canon BJC 4300 on parallel )
I have installed the drivers (Canon-BJC-4300-bjc600.ppd and the newer gutenprint-5.0.0-rc2.tar.bz2 via console; no errors )
I have installed The Gimp and all associated print files from repository.
I have installed GUI print managers, viewers, setups etc. (Both KDE and Gnome)
Everything says that my printer is fine.
When I try to print a test sheet, a message says that it has been sent to the printer successfully.
After this nothing. The printer icon on my toolbar shows a red exclamation mark and that's where it ends.

I am accustomed to print user settings, installing drivers, checking folders to make sure everything is in it's right place, setting user permissions for folders hardware etc., assigning ports to devices, searching for information.

None of these have helped me so far.

I would be truly grateful if someone could point me to a step by step guide that i could read (if it exists).

I am quite happy to delete drivers and programs and start a fresh if need be.

Ok, thanks for taking the time to read my post, and thanks fro such a great forum.

Rich S

---

### Post by 3rdalbum on 2006-04-21
I'm unfamiliar with KDE, but in GNOME when you click on the printer icon it brings up a PrintMonitor-kind-of window. Does this do anything, and if so does it give you a more specific error message?

---

### Post by richbarna on 2006-04-21
Hi 3rdalbum,
Yes i do get a box that appears.
It shows me the job that is waiting to be printed, and says printer paused.
If i click to restart job i just get a couple of seconds of nothing and then the red exclamation mark appears on the icon again.
I can also access the printer settings:-
Printer - BJC 4300
Location - /dev/lp0
Status - Paused: Unable to open parallel port device file "/dev/lp0": Permission denied

I have given all groups print priveladges, including root and myself. So I don't understand the access denied message.

---

### Post by richbarna on 2006-04-21
Hi again,
Ok, so now after checking drivers, cables printer etc, logged in as root, and installed new printer. Went through the usual motions, everything fine.
Print test page......... nothing.
Tets printer and i get this message > Paused: Unable to open parallel port device file "/dev/lp0": Permission denied
My question is, how the hell can this have permission denied if it was all setup from "ROOT" ?
During the setup, you are asked to add users, I included root !! so what's the problem with this "port device file" ?

Any solutions would be greatly appreciated,
Thanks for your time,
Richs

---

### Post by 3rdalbum on 2006-04-21
I've no idea, sorry. I had a similar kind of problem when I used Xubuntu, but I solved it by launching Abiword with sudo.

The only thing I can suggest is to go into /dev/lp0 and check that everyone has read/write priviledges for it?

---

### Post by richbarna on 2006-04-22
Hi, tried that, everybody with read write permissions, no go.
Thanks for the suggestion though.
Funny thing is, when I had Xandros installed, the printer was recognised and worked straight away. Xandros and Kubuntu were my last two choices of distro after trying various others, always seems to be a tough call deciding which stuff you really need, and which distro has more or less everything.
I will be sticking with kubuntu though, as I dual boot with xp for the sake of printing, dvd shrink and a couple of games I play every now and then.

---

