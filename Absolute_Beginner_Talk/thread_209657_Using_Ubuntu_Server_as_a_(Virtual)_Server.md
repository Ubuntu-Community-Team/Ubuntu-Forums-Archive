---
title: "Using Ubuntu Server as a (Virtual) Server?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Viper7 on 2006-07-05
Ok, I will say up front that I may be pushing the envelope a little bit here, but maybe not.  I am (primarily) a Windows Server (2K3) hosting provider.  One of my clients has spec'd using a Linux Server with Plesk 8.0.  I have absolutely no Linux server experience.  A friend pointed me to ubuntu.  I like the concept of the LAMP server.  I have successfully installed ubuntu server on one of my Windows 2K3 Servers in MS's new Virtual Server environment.  The install went well but I am having trouble with setting the screen resolution.  Is there a way to set the screen resolution at ubuntu's command prompt?

Also, is there a guide somewhere on ways best to administer an ubuntu server since it has no GUI?  I need to get Plesk installed and perhaps some other software and will be learning as I go here.

Thanks in advance for any help!

---

### Post by scxtt on 2006-07-05
if you installed the "server", there is no GUI - that's the idea - therefore you can't change any "resolution" ... unless you're talking about the size of the terminal window, which might be possible (defaults to 80x24, i think?) ...

---

### Post by Viper7 on 2006-07-05
Yes, that is correct, since it has no GUI, you would think that it would display fine.  However, I have attached a screenshot of what the server looks like fully booted up from the Remote Control window.  As you can see, I cannot even see the command prompt as it is another 20 or so lines down.  If I hit "Enter" a bunch of times, it scrolls up no problem but it sure would be nice if I could fit the whole screen into the window.

On a side note, when I first loaded the ubuntu server .iso file in the virtual CD drive to boot from, I had to choose the F4 option to switch from VGA mode to a higher mode (1024 x 768) to fit everything into the screen.  Now that it has been successfully installed, it is back to the default VGA (640 x 400) resolution.  I have investigated just about all of my options where Virtual Server is concerned as well.  At this point, I am still trying to determine if this is a VS issue or an ubuntu issue.

Does anyone else have any ideas?

TIA!

---

### Post by Viper7 on 2006-07-05
It appears that the default boot screen resolution mode for ubuntu server is standard VGA (640 x 400).  I have used Knoppix distros in the past where I had to set the screen resolution before booting up with a command line "knoppix lang=us screen=1024x768".  Is there a command like this for ubuntu?

---

### Post by scxtt on 2006-07-05
since you've installed it, i'm thinking you can pass a grub option when you boot the VM ubuntu - something akin to the knoppix option, but i'm not sure what it is since i've never needed to do it ... maybe even "screen" will work ... i'd do some grub research to start ...

---

