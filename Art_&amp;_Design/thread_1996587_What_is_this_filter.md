---
title: "What is this filter?"
date: 2012-06-04
forum: Art &amp; Design
---

### Post by halibaitor on 2012-06-04
Does anybody recognize the filter/program used to create this effect?  I really like it, whatever it is...

before:
[IMG]http://i75.photobucket.com/albums/i319/halibaitor/Snow-Leopard-258x180.jpg[/IMG]


after:
[IMG]http://i75.photobucket.com/albums/i319/halibaitor/digital-animals_97794b2b_tn.jpg[/IMG]

---

### Post by Zappra on 2012-06-04
+1 Never knew it was a filter.

---

### Post by Dry Lips on 2012-06-04
**Fractalius**
[http://www.redfieldplugins.com/filterFractalius.htm](http://www.redfieldplugins.com/filterFractalius.htm)

---

### Post by halibaitor on 2012-06-04
Thanks, Dry Lips...  :D

I'll try it today!

---

### Post by Dry Lips on 2012-06-04
> **halibaitor said:**
> Thanks, Dry Lips...  :D

I'll try it today!

No problem! Have fun ;) But note that the original filter is for Adobe!

If you want something similar for Gimp, you'd better check this out:

**Rodilius**
[http://libregraphicsworld.org/blog/entry/gmic-gets-a-fractalius-like-filter-david-tschumperle-answers-some-questions](http://libregraphicsworld.org/blog/entry/gmic-gets-a-fractalius-like-filter-david-tschumperle-answers-some-questions)

---

### Post by halibaitor on 2012-06-04
The Rodilius filter looks like it would be an interesting tool also.  The price seems even better, is it really free? (open source)

My only problem seems to be figuring out how to install the plug-in.  Do you use this yourself?  I really don't know what I'm doing there...  (not a big enough nerd, I guess)  ;)

EDIT:  I finally found the folder I'm supposed to move it to, but when I attempt the move, I get a "Permission Denied" error...  How do I get around that problem?  I did change my permissions to Read & Write, but that didn't help any...  Is there some way to move it besides "drag and drop?"

---

### Post by kurja on 2012-06-04
open console and run ```
gksudo nautilus
```, that will open a file manager window with sudo privileges. ctrlc the file and paste it in that window you opened as sudo, that should do the trick.

---

### Post by Dry Lips on 2012-06-04
> **halibaitor said:**
> The Rodilius filter looks like it would be an interesting tool also.  The price seems even better, is it really free? (open source)

My only problem seems to be figuring out how to install the plug-in.  Do you use this yourself?  I really don't know what I'm doing there...  (not a big enough nerd, I guess)  ;)

EDIT:  I finally found the folder I'm supposed to move it to, but when I attempt the move, I get a "Permission Denied" error...  How do I get around that problem?  I did change my permissions to Read & Write, but that didn't help any...  Is there some way to move it besides "drag and drop?"

You can do what kurja suggested if you want to make G'MIC available for all the users on your machine... (Give nautilus root access and go to usr/lib/gimp/2.0/plug-ins/). 

Or you can move the file to '$HOME/.gimp-2.6/plug-ins/ 

.gimp-2.6 (or 2.8 if you have the newest gimp installed) is a hidden directory in your home folder, which means that you'll have to press Ctrl-H in order to be able to view it. Then you just drag the file into the plug-in directory. You don't need root access in order to do this.

Let us know if you still have problems installing it.

---

### Post by halibaitor on 2012-06-04
Thanks kurja.  That did the trick.  :)  (I gotta remember this one.)

Now to try the plug-in in Gimp...

---

### Post by halibaitor on 2012-06-04
> **Dry Lips said:**
> You can do what kurja suggested if you want to make G'MIC available for all the users on your machine... (Give nautilus root access and go to usr/lib/gimp/2.0/plug-ins/). 

Or you can move the file to '$HOME/.gimp-2.6/plug-ins/ 

.gimp-2.6 (or 2.8 if you have the newest gimp installed) is a hidden directory in your home folder, which means that you'll have to press Ctrl-H in order to be able to view it. Then you just drag the file into the plug-in directory. You don't need root access in order to do this.

Let us know if you still have problems installing it.


Thanks...  This will give me a good excuse to upgrade to the latest GIMP.  :guitar:

---

### Post by Dry Lips on 2012-06-04
> **halibaitor said:**
> Thanks...  This will give me a good excuse to upgrade to the latest GIMP.  :guitar:
No problem... Here are instructions for installing the latest Gimp:

[http://ubuntuforums.org/showpost.php?p=11912447&postcount=20](http://ubuntuforums.org/showpost.php?p=11912447&postcount=20)



Edit:
P.S. In order to find the Rodilius filter:     Filters>G'MIC>Artistic>Rodilius

---

### Post by halibaitor on 2012-06-04
> **Dry Lips said:**
> You can do what kurja suggested if you want to make G'MIC available for all the users on your machine... (Give nautilus root access and go to usr/lib/gimp/2.0/plug-ins/). 

Or you can move the file to '$HOME/.gimp-2.6/plug-ins/ 

.gimp-2.6 (or 2.8 if you have the newest gimp installed) is a hidden directory in your home folder, which means that you'll have to press Ctrl-H in order to be able to view it. Then you just drag the file into the plug-in directory. You don't need root access in order to do this.

Let us know if you still have problems installing it.


Well, this blows chunks...  :(

After going through the procedure to remove the old gimp and install 2.8, I now have version 2.6.8.  To make matters worse, after putting the plug-in into the correct folder as described above, I still can't find the filter...

I am using Ubuntu 10.04, does that make a difference?  Or do I just need a nice nap?


**EDIT:  Now I'm even more frustrated.  I also have a netbook with Win 7.  I installed Gimp 2.8 on that machine, and then installed the plug-in.  Both installs seemed to go well, but I can't find the filter in the Windows 7 machine either.  At least I do have Gimp 2.8 on the netbook...**

---

### Post by Paddy Landau on 2012-06-05
> **halibaitor said:**
> After going through the procedure to remove the old gimp...
The referred thread says to run the command:
```
 sudo apt-get purge Gimp*
```I believe that should be a lower-case g, as in:
```
 sudo apt-get purge gimp*
```Try again to remove the package and re-install.

---

### Post by Dry Lips on 2012-06-05
> **halibaitor said:**
> 

I am using Ubuntu 10.04, does that make a difference?  Or do I just need a nice nap?


Yes, that makes a difference! I'm sorry but that ppa is only intended for precise or oneiric. I didn't notice that you were running Lucid. 

Hopefully you didn't manage to install it at all from the PPA, since you still are running 2.6.8! That's good luck! Installing Gimp from the PPA would be a bad idea on your system. 

In any way you should check if the PPA are added to your repos, and remove it promptly. 

Open "Synaptic Package manager">settings>repositories>other software
Then remove these two:
[http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu)
[http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu)
then:
```
sudo apt-get update
```


...if you want the latest Gimp on 10.04, you'll have to compile it from source:
[ftp://ftp.gimp.org/pub/gimp/v2.8/](ftp://ftp.gimp.org/pub/gimp/v2.8/)

---

### Post by Dry Lips on 2012-06-05
**@halibaitor:**

When it comes to not being able to find the plug-in, you need to make sure that you download the correct package.

[http://sourceforge.net/projects/gmic/files/](http://sourceforge.net/projects/gmic/files/)

I used the beta package, which worked fine:

gmic_gimp_1.5.1.5_beta_linux64.zip *if you're running 64 bit ubuntu*
gmic_gimp_1.5.1.5_beta_linux32.zip *if you're running 32 bit ubuntu*

You'll also need to get the right package for your Win7 installation.

---

### Post by Paddy Landau on 2012-06-05
I successfully installed GIMP 2.8, but I'm struggling to install this G'MIC filter set.

I downloaded the 64-bit .deb file (I tried both the 1.5.1.4 stable and the 1.5.1.5 beta [from the website]("http://sourceforge.net/projects/gmic/files/")).

When trying to install, it says, "Error: Dependency is not satisfiable: libcv2.1". This is despite having libcv2.3 installed. There is no libcv2.1 in the repositories.

Any ideas? Have you managed to get it installed?

---

### Post by Dry Lips on 2012-06-05
> **Paddy Landau said:**
> I successfully installed GIMP 2.8, but I'm struggling to install this G'MIC filter set.

I downloaded the 64-bit .deb file (I tried both the 1.5.1.4 stable and the 1.5.1.5 beta [from the website]("http://sourceforge.net/projects/gmic/files/")).

When trying to install, it says, "Error: Dependency is not satisfiable: libcv2.1". This is despite having libcv2.3 installed. There is no libcv2.1 in the repositories.

Any ideas? Have you managed to get it installed?

Don't use the deb. Use one of these files instead. 
[I]
gmic_gimp_1.5.1.5_beta_linux32.zip[/I] 
*gmic_gimp_1.5.1.5_beta_linux64.zip*

Then you just extract the file, and move it to:

$HOME/.gimp-2.X/plug-ins/ 

or

usr/lib/gimp/2.0/plug-ins/

---

### Post by Paddy Landau on 2012-06-05
> **Dry Lips said:**
> Don't use the deb. Use one of these files instead.
Oh... that was easy! Thank you.

I moved it to [FONT=Courier New]/usr/lib/gimp/2.0/plug-ins[/FONT] to make it available to everyone.

---

### Post by halibaitor on 2012-06-05
> **Dry Lips said:**
> Don't use the deb. Use one of these files instead. 
[I]
gmic_gimp_1.5.1.5_beta_linux32.zip[/I] 
*gmic_gimp_1.5.1.5_beta_linux64.zip*

Then you just extract the file, and move it to:

$HOME/.gimp-2.X/plug-ins/ 

or

usr/lib/gimp/2.0/plug-ins/

Nice.  :)  I just downloaded that 32 bit version and now have the filter available in 2.6.8.  I'm not going to mess with it any more.  Now I just have to learn how to use the darn thing.  Looks like a fairly steep learning curve.  :cool:

Do you have any suggestions for online tutorials on usage?

---

### Post by Dry Lips on 2012-06-05
> **halibaitor said:**
> 
Do you have any suggestions for online tutorials on usage?

[https://secure.flickr.com/groups/gmic/discuss/72157625021897552/](https://secure.flickr.com/groups/gmic/discuss/72157625021897552/)

Not all of these are relevant, but I guess it is a start.

---

### Post by Paddy Landau on 2012-06-05
> **halibaitor said:**
> Do you have any suggestions for online tutorials on usage?
I went to the [plug-in page]("http://gmic.sourceforge.net/gimp.shtml"). If you scroll down, you'll see an example of each filter. Click on any example to see how that filter is done.

---

### Post by halibaitor on 2012-06-05
Very nice.  That will get me started.

Thanks for all your help guys.  :)

---

