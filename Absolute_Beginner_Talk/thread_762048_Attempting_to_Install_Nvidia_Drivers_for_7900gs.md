---
title: "Attempting to Install Nvidia Drivers for 7900gs"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Ballping on 2008-04-21
Hi all,

I'm attempting to install the drivers for my Nvidia 7900gs, i go into Restricted Drivers Manager and there "Nvidia accelerated graphics driver" is listed. It says that it is not enabled. I click on the check box to enable it and a window pops up with the reasons why this should be enabled. I click on the button to "enable driver" and the pop up window closes, the "Nvidia accelerated graphics driver" greys out for a minute and then turns solid again. The "enabled" check box never gets checked off. What is going wrong and how can i fix this? Or is there a manual way of installing the drivers via the terminal? Sorry to have to post this but i'm trying to get my head wrapped around Linux still and i haven't been too lucky attempting to search for an answer here on the forums. Any help would be appreciated. Thanks. :-)

---

### Post by ru7hl3ss on 2008-04-21
I only use the manual way...

Ctrl+Alt+F1 to open console
Login
sudo /etc/init.d/gdm stop
cd <to_directory_of_downloaded_drivers_from_nvidia_website>
sudo sh NVIDIA-Linux-(whatever, just press tab to complete the name)

Hit enter through the install...

Then just reboot (what I do) or start gdm.
to reboot: sudo shutdown -r now
start gdm: sudo /etc/init.d/gdm start 

Hope this helps some...

---

### Post by Ballping on 2008-04-21
Thanks, i'll give this a try. Its hard cause i don't have an internet connection through ubuntu so i have to reboot through windows to look up anything heh. I'll let ya know if this works or not. 

> **ru7hl3ss said:**
> I only use the manual way...

Ctrl+Alt+F1 to open console
Login
sudo /etc/init.d/gdm stop
cd <to_directory_of_downloaded_drivers_from_nvidia_website>
sudo sh NVIDIA-Linux-(whatever, just press tab to complete the name)

Hit enter through the install...

Then just reboot (what I do) or start gdm.
to reboot: sudo shutdown -r now
start gdm: sudo /etc/init.d/gdm start 

Hope this helps some...

---

### Post by skymera on 2008-04-21
i had the 7900GS.

Envy worked a charm, didn't have any problems.

---

### Post by stchman on 2008-04-21
> **Ballping said:**
> Hi all,

I'm attempting to install the drivers for my Nvidia 7900gs, i go into Restricted Drivers Manager and there "Nvidia accelerated graphics driver" is listed. It says that it is not enabled. I click on the check box to enable it and a window pops up with the reasons why this should be enabled. I click on the button to "enable driver" and the pop up window closes, the "Nvidia accelerated graphics driver" greys out for a minute and then turns solid again. The "enabled" check box never gets checked off. What is going wrong and how can i fix this? Or is there a manual way of installing the drivers via the terminal? Sorry to have to post this but i'm trying to get my head wrapped around Linux still and i haven't been too lucky attempting to search for an answer here on the forums. Any help would be appreciated. Thanks. :-)

Download Envy Legacy 0.9.10 (I am assuming you are running Gutsy or earlier) or EnvyNG(Hardy).

Fire up envy and select uninstall the nvidia driver if you have tried to install one.

After that select install driver manually and select install nvidia driver manually.  There will be a 169.12, selct that and let it go.  Let Envy mod the xorg.conf and reboot.  It worked like a charm on my 8800GT under Feisty.

---

### Post by Ballping on 2008-04-21
Well i followed Ruthless's instructions and that got me into the driver install program, but the install said that my distro had "No libc header files" and told me to "Install the Distrobutions libc dev package." 

I have version 7.04. From what i've read i'm guessing thats called feisty??

Anyways i'll try Envy and see if that works for me but i'm not sure, i may need to figure out where to get this libc dev package.

I appreciate the quick responses. I'll let yall know how envy works out for me. Thanks.

---

### Post by Ballping on 2008-04-21
Well Envy didn't work either. It came back with "Error- dependancy not satisfiable: build-essential" so i guess its still needing those libc header files it mentioned.

I attempted to do a search under the packages but all i could find that was similar was libc6 and several other library packages that started with libc6 prefix.

So if anyone knows what i'm missing i'd appreciate the help.

Thanks.

---

### Post by ru7hl3ss on 2008-04-21
Heh, sorry about that... try typing into a terminal:

sudo apt-get install build-essential
sudo apt-get install libc6 libc6-dev

---

### Post by Ballping on 2008-04-29
hey guys,

 sorry for taking so long to write back about this. Unfortunately my motherboard took a dive and i ended up having to rebuild my entire system so my issue has completely changed. I now have a new vid card which i think might be part of the problem i'm having now but i'll go ahead mark this thread as resolved as i think ruthless's solution would have worked.(it seems i can't mark it as resolved, the option isn't showing up heh) Thanks guys.

---

