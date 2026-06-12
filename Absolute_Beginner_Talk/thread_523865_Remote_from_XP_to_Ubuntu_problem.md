---
title: "Remote from XP to Ubuntu problem"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by kofac on 2007-08-12
Hi there I am a total newbie to Ubuntu its only been installed on a spare PC for about a day or so...finding it a bit hard to get my head around its not Windows but will get there :)

I am having a problem that I hope will be simple to fix. Searched as much as I can but cant seem to resolve it. Basically I am using 2 PCs next to each other on the same network and wanted to VNC them. 

After checking the web found out how to activate VNC on Ubuntu and activated the relevant boxs to allow this set up a password etc. 

This allowed me to connect to the Ubuntu box via my XP box using TightVNC on the XP box and the built in Ubuntu one on the Linux box.

It allows me to connect from XP to Ubuntu using the IP addy and the correct password. I can at that point see my Ubuntu desktop on my XP monitor so far so good. But now the problem starts....

If I move my mouse around on the XP monitor I see it moving the mouse on the Ubuntu screen. But when I click on anything in the Ubuntu screen from my XP VNC set up. The XP screen does not update so for example if I click on Firefox inside the VNC of XP to my Ubuntu connection. I see on the Ubuntu monitor it opens Firefox. But on the XP screen running VNC of Ubuntu it does nothing. The only way I can see that Firefox has opened is to close the VNC session and open a new one. But then I am still no further forward as its the same result.

Strange thing is doing it other way around so going from Unbuntu to XP. I can get it to work perfectly. That is with TightVNC Server installed on the XP Box.

Does the built in Ubuntu VNC have its own Server or do I need to install some from of VNC Server to get Ubuntu to work with XP. Sorry if this has been asked before I did search but could not find this specific problem.

Thanks for any help anyone can give me :)

---

### Post by talby on 2007-08-12
yes ubuntu uses "vino-server" (same as vncserver) just go to System -> Preferences -> Remote Desktop to configure and use a vnc client (like vncviewer) on windows to access it.

Personally, if you have the systems directly next to each other I prefer to use "synergy" which allows you to access the other systems keyboard/mouse, kind of like a virtual kvm.

Check out this for synergy details:
[http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/]("http://www.mattcutts.com/blog/how-to-configure-synergy-in-six-steps/")

---

### Post by kofac on 2007-08-12
Hmm yeah I have it set up the way you suggest with Remote Desktop. Then use a VNC Viewer via Windows. But have the problem it does not update the screen.

As for Synergy thanks for that suggestion. Maybe I should have made the post a bit clearer. 

The PCs are by each other. But I want to use 1 monitor to share the 2 PCs. At the moment the Ubuntu Box is using my monitor I use for Vista. Synergy is a great prog. I use a very similar one called Multiplicity have done for a long time. To go between Vista & XP machines.

I guess I may end up buying a cheap KVM Switch to do the job but was hoping to do it via software if possible.

---

