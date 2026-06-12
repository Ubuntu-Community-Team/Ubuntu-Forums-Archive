---
title: "Change startup splashscreen before login-screen Kubuntu 12.04?"
date: 2013-08-02
forum: Art &amp; Design
---

### Post by silconsystem on 2013-08-02
Hi There,

After upgrading from Kubuntu 11.10 to Kubuntu 12.04 some time ago my splash screen that is shown at boot, after selecting Kubuntu in the grub menu has changed to an ugly gritty grey picture.
The old one I was okay with but I'd like to change this one.
I've done quite some customizing already, changed the icon, splash(show after login) login and desktop themes, and all this can be done from the system settings.

The first splash is not customizable from the settings though. I changed the same screen in my Xubuntu distro, which was pretty simple. I just changed the script to point at another background.
I've been trying to find the right folder on Kubuntu but I've had no luck finding it yet. Online I can only find only stuff using programs like boot-manager or unrelated things.
Does anyone know where Kubuntu puts this script and what it uses for all these settings instead of lightdm.
I just want to change the background image then I'm satisfied.


Cheers,


Rob

---

### Post by GwL3eNC on 2013-08-02
Hi Rob,

do you mean the first screen which shows the systems you installed. The bootmenu?
It's possible that you can change that simply using the grub-customizer

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

Hope i understand you right.

---

### Post by silconsystem on 2013-08-02
Hi thanks for ur reply,

No, the grub menu I customized already, after selecting the Kubuntu option there a splash screen, a grey background with the KDE gear and some white dots. I think its scaled up or something cuz its really pixeled/gritty looking.
If I can find the folder + script that handles this I just replace the pictures with something else. I just cant find the folder (yet).
Do u know what handles this on KDE?

---

### Post by silconsystem on 2013-08-02
I just solved the thread I think, its plymouth , residing in /lib/plymouth. It just popped in my head. all the time I was thinking about KDM and Lightdm.
After a quick look in the folder I found the pics too.

I'll customize and see if it all works like I want and then mark the thread as solved, maybe it'll help someone else.


Cheers,


Rob

---

### Post by silconsystem on 2013-08-02
Nope, nothing changed yet but I'm on the right track.
I guess the script calling the pictures is not called on startup. but the images are the same so I'm getting close.

Does anyone have some more info on what kde calls directly after startup. Or is this somethig called by grub?
if you disable the -quiet splash option from grub the splash is not displayed, but the console output is.

---

### Post by GwL3eNC on 2013-08-02
Sorry for my late answer. Think plymouth is right. On a german site i found for change the desing

You can choose this packages. You have to install at least one


[LIST]
[*]**plymouth-theme-ubuntu-logo** 
[*]**plymouth-theme-kubuntu-logo** 
[*]**plymouth-theme-ubuntustudio-logo** 
[*]**xubuntu-plymouth-theme** 
[*]**plymouth-theme-ubuntu-text** 
[/LIST]
 


[LIST]
[*]**plymouth-theme-sabily** 
[*]**plymouth-theme-solar** 
[*]**plymouth-theme-glow** 
[*]**plymouth-theme-spinfinity** 
[/LIST]
Then type

sudo update-alternatives --config default.plymouth 

and choose one out of the appearing list. Hope it works
There also is something about own design. Therefore a package is needed

sudo apt-get install plymouth-theme-script

An english link is given with a course [http://brej.org/blog/?p=158](http://brej.org/blog/?p=158)[URL="http://wiki.ubuntuusers.de/Plymouth"]

[http://wiki.ubuntuusers.de/Plymouth](http://wiki.ubuntuusers.de/Plymouth)

[/URL]

---

### Post by silconsystem on 2013-08-02
Oh man,

Great, thats just what I needed.
At the moment I have to leave the computer, but when I get back to it tommorrow i'll let u guys know what happened and how. Surely someone else can benefit aswell.

Thank a lot !


Rob

---

