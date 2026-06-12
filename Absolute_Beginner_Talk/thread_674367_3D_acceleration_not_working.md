---
title: "3D acceleration not working"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Samip on 2008-01-21
I used envy, like suggested in a topic i was looking at. it seemed to have worked. I rebooted the system and then i typed in: glxinfo | grep rendering
this is what it said i should have gotten: direct rendering: Yes

I received this instead:  
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

how do I fix this? I really want to get this working!

thanks in advance to anyone who helps me.

---

### Post by r4ik on 2008-01-21
In the terminal,

sudo envy --uninstall-all

Then look for the restricted drivers manager

system=>administration

Good luck !

---

### Post by Samip on 2008-01-21
What am i supposed to do in restricted drives manager?

and i typed in glxinfo | grep rendering after i ran sudo envy --uninstall-all and it came up with the same thing.

---

### Post by r4ik on 2008-01-21
Activate the driver ?

---

### Post by Samip on 2008-01-21
the driver is not listed

---

### Post by r4ik on 2008-01-21
My bad it is a ATI card please try,

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#ATI_users_and_Compiz)

Good luck !

---

### Post by smurphy_it on 2008-01-21
Have you been able to follow along what the other individual(s) have been recommending ?

You need to go into a terminal, It's located under applications, accessories, terminal.

Then type sudo envy --uninstall-all

I would probably reboot to clear everything out just in case and then when you get back into X-windows goto System, Administration, Restricted drivers manager and enable the video driver.

If you can't enable anything there, you should jump back into a terminal and type lspci and post the results here (might be sudo lspci if the first command fails).

---

### Post by Samip on 2008-01-21
oh, sorry i didnt tell you before, my graphics card is a GeForce 7300 GS

---

### Post by r4ik on 2008-01-21
I have the same card just activate the driver and reboot when asked.

---

### Post by Samip on 2008-01-21
@smurphy_it

I tried that, the driver did not show up, when i typed what u said to in terminal, it said command not found.

@r4ik

the driver does not even show up

---

### Post by r4ik on 2008-01-21
Copy and paste the command and you should be oke i just checked it.
The Restricted Drivers are for  a lot of Nvidia cards just run it.

I have to go now when you are done go to,

System=>Preferensces=>Appearence=>Visual Effects

Good luck !

---

### Post by Samip on 2008-01-21
@smurphy_it

nvm this is what it shows up:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware Inc Unknown device 0790 (rev 02)
02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:02.0 USB Controller: VMware Inc Unknown device 0770

---

### Post by Samip on 2008-01-21
@r4ik

no drivers show up there in the first place. the only things listed in there are things for VMware.

---

### Post by r4ik on 2008-01-21
Running virtual, than i guess it is a no go  sorry.
EDIT: Cant help you with VMware.

---

### Post by Samip on 2008-01-21
so i gotta actually have it booting for it to work?

---

### Post by smurphy_it on 2008-01-22
From the looks of the output of lspci which you sent me it appears as if you are trying all of this in a VMWare session.  I don't think you are going to get the results you want in a virtual session as it doesn't sense the video information properly.

I haven't done this myself, but a friend of mine tried setting up his video in a vmware session and it wouldn't take right.  He eventually installed it to his computer and was able to get the driver to work properly then.

---

### Post by Shazaam on 2008-01-22
WMware uses a hardcoded SVGA video controller (virtual video card) that you CANNOT change so 3d acceleration will be slim to none for a virtual session. VMware is working on an update to this but it probably won't be released for a while. You are wasting your time trying to install drivers.
As far as other virtual software (VirtualBox, etc) you will run into the same problem with 3d apps.

---

### Post by Samip on 2008-01-22
thanks
I would if installed it without vmware, but my mouse always freezing after a minute or so.

I just found this in this forum: [http://ubuntuforums.org/showthread.php?t=84344](http://ubuntuforums.org/showthread.php?t=84344)

would that fix it?

---

