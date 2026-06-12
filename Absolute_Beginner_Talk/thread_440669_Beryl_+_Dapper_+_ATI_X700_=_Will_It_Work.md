---
title: "Beryl + Dapper + ATI X700 = Will It Work?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-11
Hey there. I was looking to see if anyone had a step by step or a how to that would allow me to load this nice little program up as I'd love to use it but I want to make sure I do this right the first time. I've never used it or loaded it up before so I don't want to screw things up and have to reload it. I've got things how I like em and wish to keep it that way. I greatly help and respect anyone who can accomidate this request! Thanks!! :)

---

### Post by starcraft.man on 2007-05-11
> **Tumpster said:**
> Hey there. I was looking to see if anyone had a step by step or a how to that would allow me to load this nice little program up as I'd love to use it but I want to make sure I do this right the first time. I've never used it or loaded it up before so I don't want to screw things up and have to reload it. I've got things how I like em and wish to keep it that way. I greatly help and respect anyone who can accomidate this request! Thanks!! :)

Have you already got your ATI drivers installed? If so it would seem you've already done most of the work (most people get messed up with install of ubuntu and the drivers when dealing with ATI). I think you want to follow the [Edgy]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29") guide, I believe that the repos for it include a dapper version.

I'm an nvidia guy though so I haven't done it on a X700 card.

If you haven't installed your drivers, use the Envy script on this [site.]("http://www.albertomilone.com/nvidia_scripts1.html") Steps are listed at top of the page, just download install run envy and select automatically install ATI drivers. (Its listed under applications > System tools > envy when installed).

---

### Post by spacegypsy on 2007-05-11
I tried to do that in dapper without any positive result.:( 

Maybe it's because I'm not an expert.

So I switched to Feisty

With positive result.:)

---

### Post by Tumpster on 2007-05-11
Can I run that script either way as it sounds it would just reinstall the drivers??

---

### Post by starcraft.man on 2007-05-11
> **Tumpster said:**
> Can I run that script either way as it sounds it would just reinstall the drivers??

Well, did you already install your ATI drivers? If they work fine there isn't any reason to reinstalling them using envy. If you never did install your ATI drivers (you would have had to do so after booting into ubuntu and updating) then yes, you do want to run the script. Without drivers beryl won't work...

hope that helps you decide what to do with Envy :)

---

### Post by Tumpster on 2007-05-11
Thanks man! I'm going to try and see what I can do and see how things go!

---

### Post by starcraft.man on 2007-05-11
> **Tumpster said:**
> Thanks man! I'm going to try and see what I can do and see how things go!

No problem, and good luck. Post back if any problems pop up.

---

### Post by Tumpster on 2007-05-12
Only got so far.....

Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: libberylsettings0 but it is not going to be installed
         Depends: libberyldecoration0 but it is not going to be installed
  beryl-core: Depends: libberylsettings0 but it is not going to be installed
              Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed              Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
  beryl-manager: Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
                 Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
                 Depends: libcairo2 (>= 1.2.4) but 1.0.4-0ubuntu1 is to be installed
                 Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
                 Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
                 Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be installed
  beryl-plugins: Depends: libberyldecoration0 but it is not going to be installed
                 Depends: libberylsettings0 but it is not going to be installed
                 Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
                 Depends: libcairo2 (>= 1.2.4) but 1.0.4-0ubuntu1 is to be installed
                 Depends: libdbus-1-3 but it is not installable
                 Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
                 Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
                 Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be installed
                 Depends: libberyldecoration0 but it is not going to be installed
  beryl-settings: Depends: beryl-settings-bindings but it is not going to be installed
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libberyldecoration0 but it is not going to be installed
  xserver-xgl: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
E: Broken packages

---

### Post by Tumpster on 2007-05-12
Any help?

---

