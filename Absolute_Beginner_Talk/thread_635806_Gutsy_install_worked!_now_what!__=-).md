---
title: "Gutsy install worked! now what?!?  =-)"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by ubnutu_dillon on 2007-12-09
Hello ubuntu World!

I just built my own PC,  I spent all my money on my hardware, and I had no $ for an OS.  ubuntu saves the day!  I Downloaded the gutsy iso, and installed it first try, and I am up and running and on the internet.  

I do have a couple fairly big issues that I would love to have help with if you have some time to walk me through it.  I considered myself fairly tech savy, but I am re-thinking that as I am clearly a complete newb here.

First issue I have is that my sound card is not recognized at all, and the video card is only working with the "no visual effects" option.  I have a Sound Blaster Audigy and a Nvidia GeForce 6200 video card.  I did try to find some threads out there already that seemed to fit the bill, but they were a bit over my head. 

for the video card I read in one thread to use Envy : 
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

well I was able to download that, but then I have no idea how to run, open, install, or what to do with the package.  I did find the Synaptic Package Manager, but had no luck getting it to find the Envy package.  Clearly, I need a newbie board to save me.  Please let me know if there are good walk throughs that you guys know about on other threads.

Cheers,

ubuntu_dillon

---

### Post by Rhubarb on 2007-12-09
To get your video card working (with 3D effects):
System --> Administration --> Restricted Drivers Manager
Put a tick in the enabled box for the NVIDIA accelerated graphics driver.
Follow all the prompts.  Then restart your PC.

If this doesn't work, get "nvidia-glx" from the synaptic package manager then restart your PC.

I'm not familiar with the audigy sound cards in ubuntu, so I would try to compilie the latest ALSA drivers for your sound card.  Or search here through the ubuntu forums a bit more ;)

---

### Post by julian67 on 2007-12-09
Audigy is usually recognised ok, but if there is no sound that's a different matter. You can  click the volume icon in the tray to open the audio properties, look at the switches and you might need to check/uncheck the box for external amplifier to get sound working.

---

### Post by RobotoWorks on 2007-12-09
Sorry if this is too off topic, but Ubuntu_Dillon, we live in the same state :)

---

### Post by ubnutu_dillon on 2007-12-10
thanks guys for the quick reply, I hadn't had a chance to get back to troubleshooting the issues until today.

Here's a quick update.  The package manager was the bane of my existence for about an hour before I posted my original thread topic asking for help.  I would search for "nvidia-glx", as I knew I was looking for nvidia drivers, but when I would search, it wouldn't find squat.  The reason, the only repository I had selected was from the original installation CD.  **You guys didn't mention that I had to enable that program manager to look at other down loadable repositories.**[/B]  When I said I was a newb, I really meant it  :) .

Once I went into the Software Sources window (Settings -> Repositories from Menu bar), and selected the various options from "down loadable from the internet", I found the "nvidia-glx" drivers in the package manager.  Then, and ONLY THEN was I happy with this package manager program  :) .  having found what I was looking for in the video driver department, I went in search of "Audigy" drivers, and found something else to install that might help my sound issue.

Video works, sound still did not.  After another 20 minutes of tinkering around, and not really finding anything that might work, I realized that when the video card wasn't working quite right, it was complaining about the drivers.  My sound wasn't working, but it wasn't complaining about my sound card drivers, it just wasn't seeing that I had a sound card installed at all.  I swapped the sound card out of one PCI slot, and into another, Voila! I have sound now too.

I wrapped up by downloading all of these security and recommended updates that were now enabled, now that I had selected down loadable repositories.  Prior to doing this I had some stability issues booting ubuntu (lots of freezes).  So far I have rebooted 5 times after all of these updates and with the new drivers, and I have not frozen yet.

Are there any other updates/configurations/recommendations that you all have to get the OS working in tip top shape?

Cheers,

Dillon

---

### Post by ubnutu_dillon on 2007-12-10
Looking through some other forum topics I noticed the sticky for [Complete Guide to Installation in Ubuntu]("http://ubuntuforums.org/showthread.php?t=500020") by [Starcraft.man]("http://ubuntuforums.org/member.php?u=250927") which has some fantastic information about not only how to install from the GUI, but even tells you to enable the down loadable sources as pretty much the first step in the GUI install process.

Had I read his guide prior to posting, I wouldn't have needed to post my questions.  In my defense, I had already installed from the iso image what I thought was fairly successfully.  I was searching for specific questions about video and sound drivers rather than general installation questions.

Hope the thread helps anyone else that might have similar issues.

Cheers,

Dillon

---

### Post by sowelie on 2007-12-10
Dillon,

Did you get your desktop effects working? I noticed you mentioned using the package "nvidia-glx".  To get the most out of your card you should install "nvidia-glx-new", either through the restricted driver manager, or through apt on the command line.  I find that the command line is much quicker than using synaptic package manager.

---

### Post by ubnutu_dillon on 2007-12-10
Thanks Sowelie, 

I did get the enhanced visual effects working, but your are right I did miss that in my description of the solution, I searched for "nvidia-glx", but that also turned up the "nvidia-glx-new" driver in the result, and that is what I ended up installing based on its description.

I am sure you are correct in that the command line is more efficient, but I haven't used any Linux OS before, and the last time I used UNIX was back in college. (EEK, 12 years ago now, so I know I don't really remember anything.)

"ls -l" is about all that comes to mind, and some of the navigation commands that are the same as or similar to DOS.  I remember that "grep" is useful, but I have no idea what I would be grepping for at this point.

Cheers,

Dillon

---

