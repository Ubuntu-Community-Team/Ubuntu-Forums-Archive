---
title: "[SOLVED] adobe flash player"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-23
i tried to go to youtube and i needed the addon of flash and in the flash page told me to dowload something and this apperaed

XML Parsing Error: not well-formed
Location: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 7:Target(mimeSource, valueProperty, true);
------^

---

### Post by dips_xe on 2007-11-23
sudo apt-get install flashplugin-nonfree

should do the job.

---

### Post by taurus on 2007-11-23
Close firefox.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```
Now, fire up firefox and see if the flash plugin works with that youtube.

---

### Post by patchido on 2007-11-23
worked... im a newb .. can i get an explanation in what that code did????

---

### Post by dips_xe on 2007-11-23
"sudo" gave you superuser privileges,
"apt-get" is the package manager,
"upgrade" reloads all the package information from the servers,
"install" installs
"flashplugin-nonfree" is the proprietary flash plugin from adobe.

---

### Post by kleo skywalker on 2007-11-24
You've already done what you wanted, but this might be useful later. You could do the same thing by going to System-->Administration-->Synaptic Package Manager. Search for *flashplugin-nonfree* and install it.

---

### Post by ExBuM on 2007-11-24
I did this and it worked in Firefox 2 but no in Firefox 3. :/

Can someone explain to me how to get flash to work in FF3 :[

---

### Post by kleo skywalker on 2007-11-24
> **ExBuM said:**
> I did this and it worked in Firefox 2 but no in Firefox 3. :/

Can someone explain to me how to get flash to work in FF3 :[

Isn't Firefox 3 in beta or something? I remember reading somewhere that it is unstable and recommended for developers only.

---

### Post by ExBuM on 2007-11-24
It's pretty stable but I guess that could be why. I forgot about that >.>
I'm still gonna stick with it though because it's pretty sweet x]

---

### Post by Anshar007 on 2007-11-25
I tried installing abode in terminal and i got this message..Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

---

### Post by FoAlBo on 2007-11-26
I ran the commands successfully but web sites still don't recognize that it is installed.

sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by plantman on 2007-11-26
> **taurus said:**
> Close firefox.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```
Now, fire up firefox and see if the flash plugin works with that youtube.

I tried this but could not get sound from YouTube. I went to Synaptic Package Manager and I have the latest version installed (flashplugin-nonfree 9.0.48.0.2+reallyOub). What do I do now?:confused:

---

### Post by philinux on 2007-11-26
Some websites are demanding version 10 or above. So the repo version is behind the curve. An update is needed soon.

---

### Post by eldepeche on 2007-11-26
> **philinux said:**
> Some websites are demanding version 10 or above. So the repo version is behind the curve. An update is needed soon.

Version 10 only exists for Windows. It's not the repo, it's Adobe.

---

### Post by AR_Kozz on 2007-11-28
Anfar, you probably need to enable the multiverse repository. To do this open synaptic, find settings>repositories on the drop-down menu and check the box next to the line with the word "multiverse"

I have had the most up-to-date versions of adobe's linux player for about 2 years and never have heard a peep of audio from them, though they're installed properly.

---

### Post by plantman on 2007-11-29
I have found an answer to this: [http://www.arsgeek.com/?p=2966](http://www.arsgeek.com/?p=2966) . Installed the fix and now I have audio!!!!!!!!!!!!!!:)

---

