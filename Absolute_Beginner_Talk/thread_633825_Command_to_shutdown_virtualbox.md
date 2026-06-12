---
title: "Command to shutdown virtualbox"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-12-07
Ok I no the command to start my virtual windows xp,but does anybody no the command to properly shutdown windows xp in virtualbox?

---

### Post by FoxOne on 2007-12-07
you should be able to just go to the start menu and go to shutdown. VB will pick up the signal and close the window when the shutdown process is finished

---

### Post by jonward690 on 2007-12-07
I already no how to do that.I have seemlesly intergrated windows into kubuntu and I am trying make it to where kubuntu automaticaly shutsdown windows on logout.I found the command it is this.
VBoxManage controlvm "Windows XP" acpipowerbutton

But do you no how to run that command on logout of kubuntu?

---

### Post by PJSingh5000 on 2008-01-28
jonward690,

Are you looking for a command-line solution or a UI solution?

I have a an instance of Windows XP running in Kubuntu using VirtualBox.  Ubuntu is probably similar:  I am able to select K | Logout | Turn Off, and  Virtual Box presents me with a "Close Virtual Machine" dialog.  I accept the default option, "Send the shutdown signal," and Windows is shut-down as if I had initiated the shutdown process manually through Windows, by clicking Start | Shutdown.  After Windows shuts down, however, there is a small glitch: VirtualBox cancels the Kubuntu (KDE) shut down prcess.  This looks like it is a design feature of KDE (and I'm sure there is a way to disable it).  At that point I have to select K | Logout | Turn Off again.

Note that I did have ACPI enabled in VirtualBox when I created the Windows XP virtuial machine.  I had installed VirtualBox using the official VirtualBox repository (deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free) so the version of VirtualBox I am using is 1.5.4.  The repositories for different distros are listed at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), if you did not already know.

---

