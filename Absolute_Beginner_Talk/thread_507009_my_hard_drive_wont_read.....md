---
title: "my hard drive wont read.... ?/? ?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-07-22
i just installed the vmware player and i boot in windows using that but for some odd reason it wont read my E:/ that contains all the music and personal files that i have.. how would i make it so i can read it ? i can read it perfect with ubuntu, kind of pointless though because thats why i got vmware is to use cs3 with my psd's.   any ideas ?

---

### Post by JesterDev on 2007-07-22
It's been a long time since I used vmware, however I "believe" you have to include your e:\ drive as a networked drive in vmware in order to be able to access it. Then again I might be wrong. 

The virtual machine is not aware of hardware outside itself. You can think of it as a box with no access to the outside world. If it's not in the box, it does not know it exists, and does not care. Check the vmware docs to see how to make your VM aware of your e:\ drive.

---

### Post by Likenota on 2007-07-22
okay ill look but idk if ill be able to find it perhaps i will idk. if not do you mind helping me out? im sure its something not too complicated.. o and why is it i cant access my nvidia control panel inside vmware it gives me vmware controls or something.. i wanna try out command and conquer with vmware.

---

### Post by 56seeker on 2007-07-22
VMware player only runs ready made virtual machines. If your virtual XP machine doesn't have an E drive; then it won't see it!

Unless you're trying to share a Linux partition to the virtual machine as the E drive?

You won't see the Nvidea control panel in a virtual machine as the virtual machine will be using a virtual graphic card with drivers supplied by vmtools.

Virtual machines are good for anything except 3D gaming... the graphics system isn't up to it.

---

### Post by JesterDev on 2007-07-22
If you insterested in playing Windows games under Linux try wine, or codega. Sorry I'm leaving or I would post some links. Try [www.google.com/linux](www.google.com/linux)

---

### Post by Likenota on 2007-07-22
umm what?!!? why isnt my e:/ working thenn.... its not a linux partition its all windows.. isnt there some type of command or something i can use in the vmx or vmd file to make it read it "?? ,, oo and btw its a sata drive if that matters...

---

### Post by Likenota on 2007-07-23
anyone? its soo annoying i just wanna be able to read my drive. please help me out this isnt cool.

---

