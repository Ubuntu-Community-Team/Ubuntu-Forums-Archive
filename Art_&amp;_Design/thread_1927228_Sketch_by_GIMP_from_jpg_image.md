---
title: "Sketch by GIMP from jpg image"
date: 2012-02-17
forum: Art &amp; Design
---

### Post by SupaDupaNooB on 2012-02-17
Hello,

I'm trying to make a sketch from a jpg photo by Gimp using a tutorial.
My Gimp's version is **GIMP 2.6.7** and Ubuntu is 9.10 (yes,not latest but running smoothly).
The tools,buttons etc. seem to be at different places than mentioned at the tutorial.Very confusing to figure out. So,I'm stuck at 'Step 6' (L&C dialog for creating an edges mask).
Here's the tutorial's link: [http://www.gimp.org/tutorials/Photo_To_Sketch/](http://www.gimp.org/tutorials/Photo_To_Sketch/) 

Any help about making a sketch from those above I mentioned or, any better idea?

Also, I've installed **gimp-help-en** and **gimp-help-common** by Synaptic package manager.But if I try to open Help,Context,User Manual from the **Help** menu it switches to online helps. So,where are these helps actually installed and how to get those things in work?

And I'm not sure if I've posted this at correct forum, so excuse me if I'm wrong.

Thanks :)

---

### Post by BcRich on 2012-02-19
> **SupaDupaNooB said:**
> Hello,

I'm trying to make a sketch from a jpg photo by Gimp using a tutorial.
My Gimp's version is **GIMP 2.6.7** and Ubuntu is 9.10 (yes,not latest but running smoothly).
The tools,buttons etc. seem to be at different places than mentioned at the tutorial.Very confusing to figure out. So,I'm stuck at 'Step 6' (L&C dialog for creating an edges mask).
Here's the tutorial's link: [http://www.gimp.org/tutorials/Photo_To_Sketch/](http://www.gimp.org/tutorials/Photo_To_Sketch/) 

Any help about making a sketch from those above I mentioned or, any better idea?

Also, I've installed **gimp-help-en** and **gimp-help-common** by Synaptic package manager.But if I try to open Help,Context,User Manual from the **Help** menu it switches to online helps. So,where are these helps actually installed and how to get those things in work?

And I'm not sure if I've posted this at correct forum, so excuse me if I'm wrong.

Thanks :)
Hi SupaDupaNooB
Welcome to UbuntuForums :)
I'm currently using GIMP 2.6.10 (but from what I remember I think 2.6.7 has most of the features in pretty much the same place so I hope this helps?) with regards to step 6 "L&C dialog for creating an edges mask" The tutorial is basically saying that you need to create the outline effect that appears around the child and man in the example image (this adds to the illustrated look). 
So basically, you first need to make a copy of the layer you added the Sobel edge detect filter to. You can open the Layers Dialog by clicking Windows > Dockable Dialogs > Layers. 
Right-click on the layer you would like to make a copy of (in the layers dialog) and choose "Duplicate Layer". Then with the new layer selected (you'll know it's selected because it will appear as highlighted in the layers dialog) click 
Colors > Invert
Then select the layer that the high pass filter was applied to,
click Edit > Copy
This will store a copy of the currently selected layer in your computers memory, however your image should in no way look any different than it did prior to running this command.
Then reselect the layer that you made a copy of in the beginning of step 6 (i.e. the layer that is the duplicate of the sobel effect layer). With this layer selected in the layers dialog right click on the layer and choose "Add layer mask". You should see another dialog that pops up titled "Add Layer Mask" click the button that says "Black (Full Transparency)" and you should see a layer mask appear.

A layer mask is a greyscale image that is used to show or hide parts of the layer that it is attached to and subsequently effect what parts of the layers below it are revealed or are hidden. For example black parts of the layer mask will be fully transparent and white parts will be fully opaque. The grey areas will be partly transparent or partly opaque depending on how much black or white they consist of. A layer mask is represented in the layer dialog as a layer that is indented at the same level as the layer that it is effecting. So it ultimately looks like you have two images on the same layer in the layers dialog. The layer mask is the second image on that layer and will always be a greyscale image (not color). 

When working with the layer in question you must either select the image or the layer mask. You already know that clicking on the image icon will select the image on that layer, the layer mask is similar in that clicking on it's icon will select it for editing. 
Click the layer mask icon to make sure it is what you are editing, then click Edit > Paste. You should see the image you copied earlier appear as a floating selection above your currently selected layer (in the layers dialog). Right click on the floating selection layer (in the layers dialog) and choose "Anchor Layer". Your selection should now be merged into the layer mask which was previously in the layer below it.
Hope that makes sense? Good Luck.

Edit: I almost forgot to mention that you will still need the Help Browser (that comes with Ubuntu) to read the GIMP help documents but you do not need to be online to read this documentation. Clicking Help > Help should open the GIMP help documents from which you can navigate to other areas within the documentation which may have shortcuts in the GIMP help menu such as all the subsections under Help > User Manual >...  Hitting F1 on your keyboard should also bring up the GIMP help documents

---

### Post by 23dornot23d on 2012-02-19
If you have not got GMIC

you might like it ..... [http://registry.gimp.org/node/13469](http://registry.gimp.org/node/13469)

its also in the Ubuntu repos ... 

also some other scripts made .... for sketching ... etc ....  

as there are quite a few - I put some in a zip file here .... even setting layers and lots
of other things too .... ( I collected a few over quite a long time )

[https://sites.google.com/site/photoshoppping/home/stephens-3d-files/GimpMainScrips.zip?attredirects=0](https://sites.google.com/site/photoshoppping/home/stephens-3d-files/GimpMainScrips.zip?attredirects=0)

Once you unzip them .... its just a case of adding the folders in Gimp

Edit - Preferences - Folders - scripts .... 

after adding each of the 4 folders in the zip file go out of gimp and go back in again.

Hope this helps ... there are many scripts that do all sorts of jobs ... if you want to be selective you could go into the folders and pick only the ones you think you need.

Best of luck with them ....

---

### Post by SupaDupaNooB on 2012-02-20
> **BcRich said:**
> Hi SupaDupaNooB
Welcome to UbuntuForums :)
I'm currently using GIMP 2.6.10 (but from what I remember I think 2.6.7 has most of the features in pretty much the same place so I hope this helps?) with regards to step 6....
.........
................
Hope that makes sense? Good Luck.

Edit: I almost forgot to mention .....Clicking Help > Help .....

Hello, 
Thanks a lot for the welcome and all those illustrative helps. :) 


> **23dornot23d said:**
> If you have not got GMIC

you might like it ..... [http://registry.gimp.org/node/13469](http://registry.gimp.org/node/13469)

its also in the Ubuntu repos ............
............

Best of luck with them ....

There's lot to explore in those. I'll try those too. Thanks. :)

---

### Post by 23dornot23d on 2012-02-20
Your Welcome


The quick way to do a sketch - load in GMIC .... type this in a terminal , example of
what it does will appear below .... as I will do a screen shot shortly

**sudo apt-get install gmic**

> 
keith@keith-Aspire-7730ZG:~$ sudo apt-get install gmic
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gmic-doc
The following NEW packages will be installed:
  gmic
0 upgraded, 1 newly installed, 0 to remove and 449 not upgraded.
Need to get 3,263 kB of archives.
After this operation, 11.6 MB of additional disk space will be used.
Get:1 [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) precise/universe gmic i386 1.5.0.8+dfsg-1 [3,263 kB]
Fetched 3,263 kB in 11s (277 kB/s)                                               
Selecting previously unselected package gmic.
(Reading database ... 227430 files and directories currently installed.)
Unpacking gmic (from .../gmic_1.5.0.8+dfsg-1_i386.deb) ...
Processing triggers for man-db ...
Setting up gmic (1.5.0.8+dfsg-1) ...
keith@keith-Aspire-7730ZG:~$ 

Lots of ways of adjusting the thickness opacity ... etc ... to get it as you want with the sliders on the GMIC utilty

The Utility GMIC is found under the menu item FILTERS and is at the very bottom of the list ....


[IMG]http://img849.imageshack.us/img849/4963/waylando33.jpg[/IMG]

---

### Post by EmmaSystem76chick on 2012-02-22
Thank you for this helpful play-by-play on how to get the extra filters! Installing the plugin straight from the software center totally didn't work and I was wondering what I did wrong! I followed your instructions and used your links instead and it worked perfectly. I have tons of exploring to do! Thank you!

---

### Post by 23dornot23d on 2012-02-22
You are welcome :D and I hope more people pick it up and get to use it ......

---

