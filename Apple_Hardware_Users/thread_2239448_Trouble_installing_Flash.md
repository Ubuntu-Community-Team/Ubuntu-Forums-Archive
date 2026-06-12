---
title: "Trouble installing Flash"
date: 2014-08-13
forum: Apple Hardware Users
---

### Post by jacatone on 2014-08-13
I ran the following command to install Flash on my Powerbook G4 running Lubuntu 12.04:

"sudo apt-get update && sudo apt-get install adobe-flashplugin -y"

Then it gave me this:

"Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate"

I'm kinda at a loss here.

---

### Post by slooksterpsv on 2014-08-13
flashplugin-installer - Adobe Flash Player plugin installer

So try: sudo apt-get install flashplugin-installer

It should be that one. I'd recommend using Chrome or Chromium and using Pepper it's a Flash like plugin builtin to chrome but it doesn't use Adobe Flash.

---

### Post by jacatone on 2014-08-14
I tried sudo apt-get install flashplugin-installer and got nothing. Is this installer in a repository I need to add? 

I never cared for Chrome. It just doesn't have all the great addons that Firefox has. Unfortuneately, Firefox doesn't have a flash addon and uses Adobe Flash. I was able to download a tar ball of the latest flash player. Just never had much luck compiling tar balls.

---

### Post by slooksterpsv on 2014-08-14
The tarball of flash is usually just the plugin that you have to move to the mozilla plugins directory. You can also try to install the meta-package lubuntu-restricted-extras as that should install it, as well as some fonts, gstreamer (for various video and music formats in apps (wma, mp4, etc.)), and more. It's a bigger package, but carries a lot of good stuff in it.

---

### Post by jacatone on 2014-08-15
Where would I find these "extras" and codecs?

---

### Post by deadflowr on 2014-08-15
> [COLOR=#000000]I tried sudo apt-get install flashplugin-installer and got nothing. Is this installer in a repository I need to add? [/COLOR]

Did you enable the multiverse repo?
That where that package is.
I would assume you do have it enabled, but maybe not...

Also Lubuntu 12.04 desktop has already reached end of life, FWIW.

---

### Post by jacatone on 2014-08-15
I can still update v. 12.04 without any issues. Just find it works a lot better without it. I'm not seeing this Multiverse repo anywhere in Synaptic. Where would I find it?

---

### Post by Tar_Ni on 2014-08-15
You should go for a clean install of Lubuntu 14.04.1 LTS. Why would you want to remain on an unsupported version of Lubuntu? The support has ended october 2013 so you just can't receive updates. The system requirement of 14.04.1 are as low as 12.04 and a lot of improvements have been made since then.

Then you just go to system tools --> Lubuntu Software Center and download adobe flash player.

---

### Post by deadflowr on 2014-08-15
> **jacatone said:**
> I can still update v. 12.04 without any issues. Just find it works a lot better without it. I'm not seeing this Multiverse repo anywhere in Synaptic. Where would I find it?

The lubuntu packages are unsupported. The underlining ubuntu packages are still supported, which is why you still get functional updates.
So in the end any flaw or bug within those lubuntu packages, like lxpanel, will never be fixed, leaving the system albeit slightly, vulnerable to exploits and such.

That said, in terms of enabling multiverse, you can see if multiverse is check from within synaptic.
I beleieve you can click on the menu item edit and select software sources.
There should be an entry for multiverse on the first page.
mark it, close the window and in synaptic press reload.
This should enable it and add the flashplugin-installer package.

---

### Post by jacatone on 2014-08-15
Yeah, multiverse was checked. When I've installed v14.04, I don't get a good user experience. Windows have this "genie" effect and I don't have sound. Where can I find a .deb of this chromium-browser?

---

