---
title: "How do I make sure I have the NVidia drivers enabled?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-27
I enabled Restricted drivers, but then foud a thread (whihc I can't find now) on enabling Nvidia in FF.  Well, halfway through that, it failed, so I tried the two step method listed in this thread:

[http://ubuntuforums.org/showthread.php?t=424741&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=424741&highlight=nvidia)

Anyway to check?

---

### Post by Kobalt on 2007-04-27
You can check that in your xorg.conf file. I understand you installed the nvidia-glx package using Synaptic then...
Open you xorg.conf file with 
```
gksu gedit /etc/X11/xorg.conf
```
Look for the section "Device". Below your Graphic card name should be a "Driver" line. Make sure in front of this you have "nvidia" and then you're sure you're using the drivers. If it says "nv" then modify it to stand "nvidia" and reboot.
You should see a nVidia screen appear before the login screen by the way...

---

### Post by Schalken on 2007-04-27
To enable nvidia drivers, either use the restricted drivers manager, or install nvidia-glx-new, nvidia-glx or nvidia-glx-legacy (depending on your card) and run " sudo nvidia-glx-config enable" from the terminal. Don't try any other methods unless those don't work. Other methods such as downloading the file from nvidia's website or using envy, will cause problems during upgrades.

To test, run "glxgears", give it a few seconds and if it reports numbders in the thousands you have drivers correctly installed. play with screensavers to test further.

---

### Post by gohanssjn on 2007-04-27
Hmmm, well I know I never saw an Nvidia splash screen, so something must be up.  I may just reinstall Ubuntu anyways to make sure I do it all right this time and only run the short fix, lord knows what I did last time....

---

### Post by Kobalt on 2007-04-27
You shouldn't need to reinstall Ubuntu all the way, it's really not a big problem I guess...can you please copy/paste the output of this : ```
cat /etc/X11/xorg.conf
```
> run " sudo nvidia-glx-config enable"
*sudo nvidia-xconfig* will suffice...

---

### Post by gohanssjn on 2007-04-27
I can on Sunday when I get back into town, sure.

I wish I could find the instructions I was using to see if there was any harm done.

---

### Post by gohanssjn on 2007-04-27
Ok, found the instructions I had used:
**-----------------------------------------------------------------------------**
[I]restricted drivers manager has made things a mess for a lot of people with newer and older nVidia cards.The restricted modules are getting load priority over the nvidia-installed module.

If you want to fix this follow this procedure

sudo apt-get install build-essential

sudo apt-get install xserver-xorg-dev

sudo vi /etc/default/linux-restricted-modules*

**Change the DISABLED_MODULES=&#8221;" to DISABLED_MODULES=&#8221;nv&#8221;**

Save the file and exit.Now you need to reboot your machine.

After reboot, download the proper driver package from the nVidia website and save it somewhere where you can easily access it.

Now you need to press Ctrl-Alt-F2 to open up a console and login

Use the following command to shutdown Xorg

sudo /etc/init.d/gdm stop

Now run the following command from the location where you saved the nV file.

sudo sh NV*

Run through the installer and tell it to update your xorg.conf for you.

Reboot once again (just type reboot at the console) and you should have full nVidia acceleration.[/I]
**-----------------------------------------------------------------------------**
Where it is bolded is what I could not get to work, so I stopped there.  Did anything I do before that mess anything up?  IE, what did these three entries do exactly?

sudo apt-get install build-essential

sudo apt-get install xserver-xorg-dev

sudo vi /etc/default/linux-restricted-modules*

---

### Post by freakavoid on 2007-04-27
If i understood you correctly you can just type "glxinfo | grep direct" and see if the output comes as "direct rendering: yes". As far as the nvidia splash screen goes the default xorg.conf in feisty comes with the option "NoLogo"   "True". So it's alright if you don't see it with this option.

---

### Post by gohanssjn on 2007-04-27
Just a quick bump to see if anyone knows what...

[I]sudo apt-get install build-essential

sudo apt-get install xserver-xorg-dev

sudo vi /etc/default/linux-restricted-modules*[/I]

...actually did.  if not, see you all on Sunday!

---

