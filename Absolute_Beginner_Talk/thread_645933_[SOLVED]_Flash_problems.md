---
title: "[SOLVED] Flash problems"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by backflip on 2007-12-20
I installed flash plugin-not free  (firefox) but when I view a flash site I get a box opening asking me which application I want to view the swf with, it suggest totem. I uninstalled and tried gnash and got the same problem, mainly because  I think flash plugin has left a residue of config files somewhere, even though I uninstalled it via synaptic. I uninstalled gnash, tried flash plugin-not free  again with the same result, a box opening asking if i want totem to run. Has anyone any ideas how I can correct this?
Thanks

---

### Post by benerivo on 2007-12-20
I would uninstall both flash and gnash, and then run firefox. When you go to a flash site it should bring up an option to install flash manually. Do it this way and it may solve your problem.

---

### Post by LaRoza on 2007-12-20
Do you get a message saying it is not installed? A MD5SUM mismatch? 

You probably do.

Uninstall it.

Now, go to System->Administration->Software Sources and choice Updates, check "Pre Release...." and run:

```

sudo apt-get update
sudo aptitude install flashplugin-nonfree

```

---

### Post by backflip on 2007-12-20
Thanks for the replies, but still no joy, I uninstalled  and updated as suggested but  the same problem persists. I'll try the uninstall and manual method next, although I;ve uninstalled a few times now and I can';t remember a 'manual' option. There must be a config file somewhere which remains even  after the plugin is uninstalled and which reappears when ever I reinstall.
I appreciate your help, thanks.

---

### Post by browning_man9 on 2007-12-20
I'm having the same problem. I was installing flash for the first time by clicking on the box that comes up on the webpage when it requires flash. I installed it and restarted firefox and the "missing plugins" box still appears. If I click on it again and try to install flash again, it says flash-nonfree is already installed. I tried removing it and reinstalling it through synaptic. Any suggestions?

---

### Post by LaRoza on 2007-12-20
> **browning_man9 said:**
> I'm having the same problem. I was installing flash for the first time by clicking on the box that comes up on the webpage when it requires flash. I installed it and restarted firefox and the "missing plugins" box still appears. If I click on it again and try to install flash again, it says flash-nonfree is already installed. I tried removing it and reinstalling it through synaptic. Any suggestions?

Follow the steps I laid out.

---

### Post by Sordelka on 2007-12-20
**To get flash working well go to adobe website [www.adobe.com](www.adobe.com) and download the tarball there. They explain exactly how to install it.** 

Do not install from terminal or firefox, it blows up. Last time my play button was on top of the screen :lolflag:

---

### Post by angel.ramirez.isea on 2007-12-20
Sordelka's right.

That's the solution, and how do we report that failed installation procedure as a bug?

---

### Post by backflip on 2007-12-20
I've uninstalled, updated as suggested, still not working, and when I completely uninstall via synaptic, log out and back in, run firefox and go to a site using flash I still get a box opening asking me if I want to run totem to view the swf file. There MUST be some config file leftover when flash is uninstalled. Any ideas how I can get this thing working? Thanks.

---

### Post by LaRoza on 2007-12-20
> **angel.ramirez.isea said:**
> Sordelka's right.

That's the solution, and how do we report that failed installation procedure as a bug?

It is already reported and will be fixed soon.

The instructions I gave are the pre release update, and worked perfectly for me (with Opera 9.5b no less)

---

### Post by browning_man9 on 2007-12-20
Thanks....This fix worked for me!

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by kelvin spratt on 2007-12-20
I downloaded the tarbul from their site and installed using the instructions working ok,

---

### Post by gigaferz on 2007-12-20
Before doing the instructions from adobe, be sure to remove the previous installation,

sudo apt-get remove flashplugin-nonfree

 remember install to  the firefox dir (if you use firefox)  and do it as sudo so other users can use it as well (system wide installation)

---

### Post by kelvin spratt on 2007-12-20
You are so right I forgot to mention that bit

---

### Post by backflip on 2007-12-20
> **Sordelka said:**
> **To get flash working well go to adobe website [www.adobe.com](www.adobe.com) and download the tarball there. They explain exactly how to install it.** 

Do not install from terminal or firefox, it blows up. Last time my play button was on top of the screen :lolflag:

SORTED...thanks, that worked, I appreciate your help.:)

---

### Post by bodycoach2 on 2007-12-21
This solution worked for me. My question is: When there is another upgrade to flash, will we be able to use it? Since we installed flash manually, will apt detect it?

---

### Post by gigaferz on 2007-12-21
oohh, now thats a good question,

probably not, but before we realize about a new flash version we'll be probably in ubuntu 9X already, lol

the ubuntu 2k, then ubuntu xp......

---

