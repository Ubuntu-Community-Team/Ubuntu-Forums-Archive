---
title: "Madwifi"
date: 2008-12-14
forum: Apple Hardware Users
---

### Post by Rocket Sock on 2008-12-14
Im using a Santa Rosa Macbook Pro, and all the instructions say to get the madwifi driver. (Note: Santa Rosa. Last time I posted someone ignored that and asked for me to figure out which version MBP I had)

Problem is that every tutorial on the subject gives me the same error, that the directory doesnt exist that im trying to apt-get from. So, could anyone help me out with an up to date run through?


And while Im at it, how do I fix this touch pad and enable the lights/functions on my keyboard?

---

### Post by shadowdude1794 on 2008-12-14
We do need a version number, (like MacBookPro4,1) without it we can't help you.
This should show what version it is, type this into the Terminal (Darwin)
```

sudo dmidecode -s system-product-name

```

---

### Post by Rocket Sock on 2008-12-14
Well, the SR is version 3 I suppose. Im not sure what the second number is.

---

### Post by Rocket Sock on 2008-12-14
Ok, its MBP 3.1

---

### Post by shadowdude1794 on 2008-12-14
These two wiki pages should fix the touchpad and the wifi. I'm not sure about the keyboard backlight though, I'll get back to you on that.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://wiki.ubuntu.com/MacBook/SantaRosa](https://wiki.ubuntu.com/MacBook/SantaRosa)

---

### Post by Rocket Sock on 2008-12-14
Ive seen people talk about that Wifi driver several times. Problem is the only thing I see there are two nvidia graphics drivers. One recommended, the other not.

---

### Post by shadowdude1794 on 2008-12-14
Did you uncomment the restricted repositories?

---

### Post by Rocket Sock on 2008-12-14
you mean under software sources? No they're all checked.

---

### Post by shadowdude1794 on 2008-12-14
I mean in the sources list, edit it with 
```
sudo gedit /etc/apt/sources.list 
```
uncomment the one that says:
```
 deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted 
```
and
```
 deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted 
```

sorry, uncommenting means removing the '#'

---

### Post by Rocket Sock on 2008-12-14
Dont worry, I know what a comment is (Im an amature program, so Im not a total loss, although thanks for being as descriptive as possible.)

As for the lines....they weren' commented.

---

### Post by shadowdude1794 on 2008-12-14
Sorry, I assumed you were. Could you post the error message you are getting when you try to get madwifi?

---

### Post by Rocket Sock on 2008-12-14
It's different for each one, but it happens when I  apt-get "webaddress". Im assuming because the tutorial was written long ago and the website doesnt work anymore. Ill try to find a tutorial if you need it. 

Any idea why that one driver doesnt work? Seems like Im just going through a ton of problems.

---

### Post by shadowdude1794 on 2008-12-14
Oh, there is your problem
try (without perenthesis)
```
 
wget "web address" | sudo apt-key add -
sudo apt-get update
sudo apt-get install "application name"

```
Edit: forgot to add the key

---

### Post by Rocket Sock on 2008-12-14
still no luck. Im using this tutorial btw

[http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451)

---

### Post by bryonak on 2008-12-14
MadWifi is outdated, replaced by the new ath5k/ath9k drivers in Ubuntu 8.10.

Uninstall MadWifi, ndiswrapper and other drivers you may have installed and just load the new Atheros modules:
```

sudo modprobe ath9k

```

For you ath9k should be the right module, as it is for me and I've got a 3.1 too.

If it works, don't forget to add it to /etc/modules in order to load it at boot.


For the backlight, have you enabled the additional Mactel repository?
Do this by following [this guide]("https://wiki.ubuntu.com/MactelSupportTeam/PPA").

After that fire up Synaptic and install the packages hal-applesmc and mbp-nvidia-bl-dkms. Update the package gnome-power-manager to the Macbook version.
You can also install the package isight-firmware-tools for your webcam, but you should have a OSX install because it needs a specific binary (or you can google for the binary).

---

### Post by Rocket Sock on 2008-12-14
> **bryonak said:**
> MadWifi is outdated, replaced by the new ath5k/ath9k drivers in Ubuntu 8.10.

Uninstall MadWifi, ndiswrapper and other drivers you may have installed and just load the new Atheros modules:
```

sudo modprobe ath9k

```

For you ath9k should be the right module, as it is for me and I've got a 3.1 too.

If it works, don't forget to add it to /etc/modules in order to load it at boot.


For the backlight, have you enabled the additional Mactel repository?
Do this by following [this guide]("https://wiki.ubuntu.com/MactelSupportTeam/PPA").

After that fire up Synaptic and install the packages hal-applesmc and mbp-nvidia-bl-dkms. Update the package gnome-power-manager to the Macbook version.
You can also install the package isight-firmware-tools for your webcam, but you should have a OSX install because it needs a specific binary (or you can google for the binary).


Ok, I know Im not helpless with somethings...but this I am. How do I add it to modules, and do the other stuff?

As for the terminal command....I input that several times and nothing happened. Just gave me a new input line.

---

### Post by Rog-Mahal on 2008-12-14
The modprobe command just executes with no output unless there is an error of some kind. To check if the module loaded correctly run the "lsmod" command, look for ath9k. I'm sure there's a way to use grep to make this easier, but I don't remember the syntax. If you find ath9k listed somewhere, the driver is loaded and we can work from there.

---

### Post by Rocket Sock on 2008-12-14
Ok, I see em.

---

### Post by bryonak on 2008-12-15
The lsmod command will list all the modules you have currently running. You can filter the list by "piping" it into the grep command, which will search for a specific string:
```

lsmod | grep STRING

```
where STRING will be ath9k in your case. Or 9k, or ath, whatever you like.
There are lots of commands you can "pipe into grep", like dmesg or lspci.


As for modprobe, no output means no errors.

I'm not sure that when you load the ath9k module it will be used after rebooting. You could just reboot once and see if it's loaded with the lsmod command above. Or to be sure, you can add it to the list of manually booted modules. To do so, type this into a terminal:
```

sudo gedit /etc/modules
```
make a new line below the other modules and just write ath9k on it.

---

### Post by cyberdork33 on 2008-12-15
Please don't take any of the following the wrong way, but I want to give you some pointers on how to get help better in the forum. Your original post(s) are quite vague and do not tell much about your specific problem.

> **Rocket Sock said:**
> Im using a Santa Rosa Macbook Pro, and all the instructions say to get the madwifi driver. (Note: Santa Rosa. Last time I posted someone ignored that and asked for me to figure out which version MBP I had)
So, why not post the version number like was asked previously? 
If you asked this previously, you should not start a new thread on the same subject, but instead reply to your previous post.

> **Rocket Sock said:**
> Problem is that every tutorial on the subject gives me the same error, that the directory doesnt exist that im trying to apt-get from. So, could anyone help me out with an up to date run through?
If you have an error, this comment is a bit vague. It would be better to try and be specific. For example, _which_ guide have you tried? You say you have tried more than one, but you don't actually say what those guides were....
If you have an error, copy and paste the command output or take a screenshot and attach it to your post.

> **Rocket Sock said:**
> And while Im at it, how do I fix this touch pad and enable the lights/functions on my keyboard?What is it exactly that you are trying to "fix"? Is the touchpad not working at all? Again, have you read the documentation for you mac version and tried the steps suggested?

Please try to give as much specific information as possible when asking for support.

---

