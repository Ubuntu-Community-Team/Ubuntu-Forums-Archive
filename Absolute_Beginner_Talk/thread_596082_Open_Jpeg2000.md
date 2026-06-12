---
title: "Open Jpeg2000?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-10-29
I received a file in .jp2 format. Wikipedia tells me it is a jpeg2000 file. Does anyone know how to open it?

---

### Post by Clickbg on 2007-10-29
Try this [http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml) it is little old but :)

---

### Post by intense.ego on 2007-10-29
i downloaded the package, but how do you install?

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> i downloaded the package, but how do you install?

Did you d/l the Tarball (.tgz)?  Read the following Section: Installing from Source:

[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

---

### Post by intense.ego on 2007-10-29
I tried following the guide and i did the first part of the second half (tar -xvzf XnView-1.70-x86-unknown-linux2.x-static-fc4.tgz) and it gave me a list of what was in the folder. When i typed in the second part (cd XnView-1.70-x86-unknown-linux2.x-static-fc4) it says the directory is not found? It is in my home folder.

the one i downloaded (Sources mirror 1) is a .tgz, not a tar.gz. Could that be an issue? Should i try the rpm file?

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> I tried following the guide and i did the first part of the second half (tar -xvzf XnView-1.70-x86-unknown-linux2.x-static-fc4.tgz) and it gave me a list of what was in the folder. When i typed in the second part (cd XnView-1.70-x86-unknown-linux2.x-static-fc4) it says the directory is not found? It is in my home folder.

the one i downloaded (Sources mirror 1) is a .tgz, not a tar.gz. Could that be an issue? Should i try the rpm file?

If you have never installed anything from source before, you might try the .rpm.  You will need to use the **alien** command to convert it 1st.  That is also described on the link I provided you.

You were in your /home folder when you tried the 2nd part right?

---

### Post by intense.ego on 2007-10-29
I have installed tar.gz from source before, but never a .tar I think I will try the rpm.

---

### Post by intense.ego on 2007-10-29
also, what does the article mean by saying "no dependencies will be resolved"?

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> also, what does the article mean by saying "no dependencies will be resolved"?

When you install from source, you might run into packages that the program requires that you don't have installed.  These dependencies must be resolved before you can install/run the program.  The required programs can be search for/installed thru Synaptic.

---

### Post by intense.ego on 2007-10-29
I now have it as a .deb file but it is locked. How do i install it?

---

### Post by disturbedite on 2007-10-29
jpeg2000 is supported by default with kde...
there is a package in the ubuntu repos called libopenjpeg that supports jpeg2000 as well.

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> I now have it as a .deb file but it is locked. How do i install it?

Did you try: sudo dpkg -i packagname

*Also explained on the link I gave you.

---

### Post by Maestro23 on 2007-10-29
> **disturbedite said:**
> jpeg2000 is supported by default with kde...
there is a package in the ubuntu repos called libopenjpeg that supports jpeg2000 as well.

Thanks for that heads up distrub.  Never had call for anything jpeg2000 myself.  Just trying to help ths person out. :)

---

### Post by intense.ego on 2007-10-29
what would the package name be if it is on my desktop. I tried XnView-1.70-x86-unknown-linux2.x-static-fc4.deb and it did not work.

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> what would the package name be if it is on my desktop. I tried XnView-1.70-x86-unknown-linux2.x-static-fc4.deb and it did not work.

It would be the only .deb file on your Desktop if that is where it's at.  Did you not watch what was going on in the terminal when the alien command was converting the .rpm?

---

### Post by intense.ego on 2007-10-29
> **disturbedite said:**
> jpeg2000 is supported by default with kde...
there is a package in the ubuntu repos called libopenjpeg that supports jpeg2000 as well.

I couldn't find it in synaptic. Do you know how I can get it?

---

### Post by disturbedite on 2007-10-29
> **intense.ego said:**
> I couldn't find it in synaptic. Do you know how I can get it?
oops, sorry, my mistake, its not in the official ubuntu repos its in this repo:
deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) feisty 3v1n0
(no gutsy or hardy repo yet).

---

### Post by chrysler on 2008-05-08
> **Clickbg said:**
> Try this [http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml) it is little old but :)

The xnview for windows supports jpeg 2000 format.
However,
The xnview for linux can't support jpeg 2000.

How can we browse jpeg 2000 pictures.  I have the same problem. Somebody give me a hand please.

---

### Post by Cubytus on 2008-05-12
Well, after trying, unsuccessfully, to convert a RPM package to get working on Ubuntu, having tried the best freeware viewer for Windows in Wine (irfanview) and looked for a GIMP plugin (impractical), I finally tried XnView for Windows through Wine.

Not particularly lightning fast, but at least it works.

You can always try to convert through ImageMagick.

[rant]
JPEG 2000 is a STANDARD, why Ubuntu still doesn't support it?? Free software talibans are always there when it comes to criticizing Micro_oft, where are they when it comes to properly implement standards, whaterver their user base??
[/rant]

---

