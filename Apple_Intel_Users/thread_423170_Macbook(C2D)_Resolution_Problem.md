---
title: "Macbook(C2D) Resolution Problem"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by vegeto626 on 2007-04-25
Hey guys I just triple booted OSX, Vista, and Feisty, but having a few problems with Feisty
First up is my resolution i cant seem to get past 1024x768 i think it is, but i want to use the native 1280x800(i think thats it). its the intel 945gm on board graphics so dont think ATI or nVidia drivers would be of any help
        -about this i tried to use dpkg and some more commands that made me manually configure my xorg.conf file (I believe) and it messed up and now i cant boot into linux i boot directly to command prompt, I'm going to just reinstall Feisty, but i will still be stuck with the resolution problem

Also about the xorg.conf file, the resolution that i want 1280x800 is all over the file. The file doesnt even give me lower resolution choices, so it didn't make sense to me that i could only choose 1024x768 and below.

The only other problem i have with feisty is that i hate tap to click! I'm guessing this could be fixed by synaptics drivers...maybe?


thank you all for your help in advance.

---

### Post by ronocdh on 2007-04-25
> **vegeto626 said:**
> Hey guys I just triple booted OSX, Vista, and Feisty, but having a few problems with Feisty
First up is my resolution i cant seem to get past 1024x768 i think it is, but i want to use the native 1280x800(i think thats it). its the intel 945gm on board graphics so dont think ATI or nVidia drivers would be of any help
        -about this i tried to use dpkg and some more commands that made me manually configure my xorg.conf file (I believe) and it messed up and now i cant boot into linux i boot directly to command prompt, I'm going to just reinstall Feisty, but i will still be stuck with the resolution problem

Also about the xorg.conf file, the resolution that i want 1280x800 is all over the file. The file doesnt even give me lower resolution choices, so it didn't make sense to me that i could only choose 1024x768 and below.

The only other problem i have with feisty is that i hate tap to click! I'm guessing this could be fixed by synaptics drivers...maybe?


thank you all for your help in advance.
I believe you're looking for the **915resolution** package. It is available in the repositories via Synaptic.

---

### Post by vegeto626 on 2007-04-25
Thanks for the quick reply but i believe I have tried that too, sorry forgot to mention that, i did it through the console with "sudo apt-get install 915resolution" but I'll give it another try when I reinstall i guess.

Any other suggestion much appreciated =)

---

### Post by ronocdh on 2007-04-25
> **vegeto626 said:**
> Thanks for the quick reply but i believe I have tried that too, sorry forgot to mention that, i did it through the console with "sudo apt-get install 915resolution" but I'll give it another try when I reinstall i guess.

Any other suggestion much appreciated =)
Only other thing that comes to mind is running ```
sudo dpkg-reconfigure xserver-xorg
``` and setting your resolutions manually.

---

### Post by vegeto626 on 2007-04-25
Haha, yea thats the one that messed up my first install, but i might have done it wrong. Guess ill let you know when I reinstall later on today. THanks alot man!

---

### Post by ronocdh on 2007-04-25
> **vegeto626 said:**
> Haha, yea thats the one that messed up my first install, but i might have done it wrong. Guess ill let you know when I reinstall later on today. THanks alot man!
Anytime. Good luck, and please post back with results! Helps everyone here.

---

### Post by vegeto626 on 2007-04-25
Alright sweet 915 resolution worked, and so did gsynaptics, just need to make sure to reboot!

Ive got a new problem now though, I cant seem to get my wifi to work, I need WPA so i used ndiswrapper, but im stuck at the 

sudo modprobe ndiswrapper

step. it gives me a fatal message "Could not open '/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko': No such file or directory"

I checked with "ndiswrapper -l" and my net5416 is said to be installed correctly, but no usable card has shown up and iwconfig scan tells me nothing is capable of scanning. No idea where to go from here. help please ^_^. thanks a bunch!

---

### Post by vegeto626 on 2007-04-25
Nevermind, installed successful, but wifi isnt actually working, i shows up in network manager, but doesnt detect anything.. tried madwifi stuff, not showing their though

---

### Post by ronocdh on 2007-04-25
> **vegeto626 said:**
> Nevermind, installed successful, but wifi isnt actually working, i shows up in network manager, but doesnt detect anything.. tried madwifi stuff, not showing their though
I've been stuck at this same stage. Are you by chance using 64-bit? I am, and I'm going to reinstall with i386 tonight, because wireless works there. The moment I here that Madwifi has testable drivers for 64-bit I'll wipe and reinstall to file bugreports, but right now I'm spending too much damn time in OS X, because I can only be in Ubuntu with an ethernet cable!

And if you're running i386 already... I have no idea how to help! =D Can you point us to the specific guide you followed?

---

