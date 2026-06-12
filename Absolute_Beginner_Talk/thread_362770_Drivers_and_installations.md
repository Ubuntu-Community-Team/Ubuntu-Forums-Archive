---
title: "Drivers and installations"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by pilot550 on 2007-02-16
I Installed Ubuntu from the live distro CD. I have a Sony VAIO VGN-FS550 wide screen laptop. I am trying to set up my screen resolution to 1280X800. I am trying to follow the 915Resolution: Intel Video BIOS Hack Guide: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) But I am new to linux and having trouble.

I downloaded the latest drivers from Intel and extracted them. I'm not sure how to install them. There is a file called "install.sh" so I clicked on it and selected "Run in terminal". A black screen flashed up for a split second and went away before I could see anything. Maybe I'm just use to using Windows, but I don't see how anything could install that fast. Is there somewhere I can check which drivers are installed?

The next step was to install X server so I extracted the files. I'm looking at the files and folders and don't even know how to begin to install it. Can I get a little help on the stuff please? Or at least pointed in the right direction?

---

### Post by fjf314 on 2007-02-16
To install it from the terminal type:

```
sh install.sh
```

---

### Post by r4ik on 2007-02-16
Download 915resolution from the repositories, using the syanptic package manager.

In a console type in: sudo 915resolution -l

It will then give you a list of available resolutions.

If the desired resolution is in the list, but is way down, for some reson it won't recognise it.
Pick a MODE that you will never use. (MODE 30 is usually ideal)

If you desire widescreen on a laptop for instance 1280 X 800 @ 24 bits/pixel type in:

sudo 915resolution 30 1280 800 24

This will patch 1280 X 800 @ 24 bits/pixel to MODE 30

In a console type in: sudo gedit /etc/default/915resolution

Now edit this file to agree with the above. ie

MODE=30
XRESO=1280
YRESO=800
BIT=24

Save this and then re-start X

You should now be operating in the new mode and it should also be available as an option in the System>Preferences>Screen Resolution menu.

Hope it helps.

---

### Post by kolinab on 2007-02-16
You're probably on the right track already, but on my system I didn't have to do anything too goofy to make the 915resolution package work. I just did a plain old:

```

sudo aptitude install 915resolution

```

(in the terminal that is)

I think it required a reboot, then things were peachy.

---

### Post by pilot550 on 2007-02-16
Wow! I got it, thanks for the help. I was trying to do more than I needed to. The step by step was a huge help. Thanks a lot.

---

### Post by kolinab on 2007-02-16
I'm glad something worked for you. What were you doing wrong?

Good luck with your Linux adventures - keep posting your questions here!

---

### Post by pilot550 on 2007-02-20
I wasn't typing in sudo first and I was trying to download and install 915resolution without using the synaptic package manager.  Thanks again. I'm getting the hang of this now.

---

