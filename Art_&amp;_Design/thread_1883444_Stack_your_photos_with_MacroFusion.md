---
title: "Stack your photos with MacroFusion"
date: 2011-11-19
forum: Art &amp; Design
---

### Post by dhor on 2011-11-19
Hi, 

There's another new utility to combine your photos to get HDR or deeper DOF.

It's MacroFusion (version 0.7), a GUI for Enfuse/Hugin tools. Short video, how to use it: [http://vimeo.com/32088731](http://vimeo.com/32088731)

[IMG]http://freecode.com/screenshots/e5/44/e544136a8cd39bbc659de8d23ee86d44_medium.jpg[/IMG]

To install it, use my PPA (ppa:dhor/myway), or by hand download package from [http://sourceforge.net/projects/macrofusion](http://sourceforge.net/projects/macrofusion).

To make MacroFusion works, you need Enfuse version >=4.0. Lucid users can install that version from my PPA.

```

sudo add-apt-repository ppa:dhor/myway
sudo apt-get update
sudo apt-get install macrofusion
```

Any feedback, translations and tests are welcome!

---

### Post by jcolyn on 2011-11-20
Will this program work with KDE or just the Gnome desktop?

---

### Post by prokoudine on 2011-11-21
> **jcolyn said:**
> Will this program work with KDE or just the Gnome desktop?

Anywhere. You only need GTK+ and its Python bindings. And, of course, enblend/enfuse.

---

### Post by jcolyn on 2011-11-21
Thanks

I'll have to give it a try....

---

### Post by nilarimogard on 2011-11-23
Unfortunately it doesn't work... When I try to add some images, I get this:

```
Traceback (most recent call last):
  File "/usr/bin/macrofusion", line 405, in ajout
    FenOuv=Fenetre_Ouvrir(self.liststoreimport,1)
  File "/usr/bin/macrofusion", line 647, in __init__
    self.tags2+=(_("<b>Aperture:</b> F/") + str(float(float(self.tags['FNumber'][0])/float(self.tags['FNumber'][1]))) + "\n")
KeyError: 'FNumber'

```

---

### Post by dhor on 2011-11-23
> **nilarimogard said:**
> Unfortunately it doesn't work... When I try to add some images, I get this:

```
Traceback (most recent call last):
  File "/usr/bin/macrofusion", line 405, in ajout
    FenOuv=Fenetre_Ouvrir(self.liststoreimport,1)
  File "/usr/bin/macrofusion", line 647, in __init__
    self.tags2+=(_("<b>Aperture:</b> F/") + str(float(float(self.tags['FNumber'][0])/float(self.tags['FNumber'][1]))) + "\n")
KeyError: 'FNumber'

```

Hmm, exif stuff... Fix on the way :)

---

### Post by gpsvn on 2012-01-17
I installed MacroFusion and Enfuse. Trying to run MacroFusion but nothing happens. 

When i right click a picture, there is option to open it with MacroFusion but again nothing happens.

Restarted the PC, it does not fix the problem.

I am using Ubuntu 11.10.

Appreciate any comment.

---

### Post by gpsvn on 2012-01-18
Update: I tried running MacroFusion from the terminal. It say:

**gtk2, pygtk or libglade is missing.**

---

### Post by dhor on 2012-01-20
> **gpsvn said:**
> Update: I tried running MacroFusion from the terminal. It say:

**gtk2, pygtk or libglade is missing.**

My fault - please install **python-glade2** package. I will fix that in next version.

---

### Post by rojaasensei on 2012-01-20
It's a great app from an excellent PPA :D

---

### Post by gpsvn on 2012-01-21
Thank you dhor, it works now.

I used MacroFusion for stacking focus (deeper DOF) but the result is quite blurry, I am not too sure what parameters, what options and how to configure the software to get sharp result.

I did try ALE, same result, ALE just take much longer time.

---

### Post by rbslime on 2012-01-27
Hello,

I'm getting this when trying to load 16bit tiff's (which I use for Luminance):

Will use all the powers of your CPU!
Traceback (most recent call last):
  File "/usr/bin/macrofusion", line 406, in ajout
    FenOuv=Fenetre_Ouvrir(self.liststoreimport,1)
  File "/usr/bin/macrofusion", line 686, in __init__
    Gui.put_files_to_the_list(self.fichiers)
  File "/usr/bin/macrofusion", line 627, in put_files_to_the_list
    im = Image.open(fichier)
  File "/usr/lib/python2.7/dist-packages/PIL/Image.py", line 1980, in open
    raise IOError("cannot identify image file")
IOError: cannot identify image file


This may be a PIL problem? I'm new to Python errors, but googling doesn't return any clues.

That said, I'm still new to HDR's but I loaded some jpg's in to Macrofusion and the default output was by far better than what I could get out of Luminance! Excellent work!

---

### Post by dhor on 2012-02-19
Thanks all for tests and opinions.

I've uploaded to PPA new version 0.7.3. Well, it's rather cosmetic changes, but it seems, that finally Macrofusion is able to open 8/16bit TIFF. I hope, it'll work :)

---

### Post by kurja on 2012-03-21
Coming back to an old thread here.

I've switched to 12.04 beta, and I'm wondering if anyone has experience with this combination. For focus stacking I'd need Hugin for alignment, Enfuse for stacking and then Macrofusion to get a gui, am I right? It seems I can get them all from Software center, without adding other repositories or anything. Will it work? Or should I just try and see? I'm asking beforehand, because I already ended up reinstalling once ;)

edit - apparently Macrofusion can do alignment, as well. What else did I get wrong?

---

### Post by anyusername on 2012-04-05
I'm using Ubuntu 12.04 and did all this:

```
sudo add-apt-repository ppa:dhor/myway
sudo apt-get update
sudo apt-get install macrofusion
```

and got this message:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package macrofusion

What did I do wrong?

**UPDATE: I found a .DEB file here, which works fine: [http://sourceforge.net/projects/macrofusion/files/macrofusion-0.7.3/]("http://sourceforge.net/projects/macrofusion/files/macrofusion-0.7.3/")**

---

### Post by gpsvn on 2012-05-25
Updated to Ubuntu 12.
Reinstalled MacroFusion,it works!!!!

Actually this is the first time is see it work.

Congratulations and thanks.

---

### Post by kurja on 2012-05-26
I have macrofusion installed in 12.04 and "it just works"

---

### Post by kurja on 2012-06-22
Yes "it just works" for hdr stacking, but now I'm trying to make a focus stack... I have ten pictures taken at about 4x magnification so depth of field is rather shallow, and the result is an evenly blurry picture that isn't remotely sharp at any point even as the individual pictures have good sharpness at the focus point. It's as if the pictures were fused entirely, and not using only the focused parts, which is the intended outcome.  Can you offer any advice on this?

---

### Post by kurja on 2012-06-23
Checking the force hard mask option seems to help with the blurryness (judging by the preview), but either the computation time goes up like crazy or it hangs, I'm not sure - but after 18+ hours it seemed to be still working which seems a bit excessive?

Anyone here uses this for focus stacks? What's your experience and what settings do you use?

---

### Post by dhor on 2012-06-25
> **kurja said:**
>  I'm not sure - but after 18+ hours it seemed to be still working which seems a bit excessive?

Anyone here uses this for focus stacks? What's your experience and what settings do you use?

18 hours is not right definitely. Your method is OK (hardmask, align, autocrop), but I've check what's wrong with hardmask.

---

### Post by kurja on 2012-06-25
Thanks. Let me know if I can provide any further info on this.

---

### Post by r_mano on 2013-04-13
Hi, I am trying to use MacroFusion but I am unable to make it work. It seems that the focus breathing correction is not working --- the preview seems aligned but the final foto does not work (It's a blurry mix of the original photos). 
The three fotos are macro of pencils, each one focused on the named color: 

[http://www.rgtti.com/focusstack/F1yellow.jpg](http://www.rgtti.com/focusstack/F1yellow.jpg)
[http://www.rgtti.com/focusstack/F2blue.jpg](http://www.rgtti.com/focusstack/F2blue.jpg)
[http://www.rgtti.com/focusstack/F3orange.jpg](http://www.rgtti.com/focusstack/F3orange.jpg)

I am using ubuntu 12.10, with the dhor/myway PPA enabled. The outout is completely messed up: 

[http://www.rgtti.com/focusstack/output.jpg](http://www.rgtti.com/focusstack/output.jpg)

Hoping that with these shot someone more expert than me can see what's happening...
Thanks anyway,
Romano

PS by the way, the generated jpg **could not be opened** by the gnome image viewer, it says "Error interpreting JPEG image file (Suspension not allowed here)". GIMP opens it well.

---

### Post by kurja on 2013-04-15
Hi,

I can't see your images (firewall issues) but do you have overlapping in-focus areas with just three images? Afaik they won't get properly aligned otherwise, have you tried with images where focus is altered only very slightly between each frame, so they overlap?

---

### Post by r_mano on 2013-04-15
> **kurja said:**
> Hi,

I can't see your images (firewall issues) but do you have overlapping in-focus areas with just three images? Afaik they won't get properly aligned otherwise, have you tried with images where focus is altered only very slightly between each frame, so they overlap?

I will try to make the image visible to all: try [http://www.rgtti.com/focusstack/imgs.html](http://www.rgtti.com/focusstack/imgs.html)

I think that the main problem is that there is a LOT of focus breathing, and the align_image_stack step got the alignement completely wrong. I will try with another set of images...

PS I tried CombineZP on windows, and although the result is not perfect (the orange pencil comes out a bit transparent), overall the image is much better. Maybe there is a way to trim parameters of align_image_stack to have a better alignement...

---

### Post by robert shearer on 2013-04-15
You need more intermediate images. Three, using those spacings is not enough.
Focus stacking needs overlap, it is not for taking several disparately focused images and expecting there to be massive interpolation between each image.
Many photographers will use 20-70 images to stack for something as simple as a fly so your three pencils Imho are way short of enough.

---

### Post by r_mano on 2013-04-15
> **robert shearer said:**
> You need more intermediate images. 

Yes, I supposed that. Will using more images cause a better behaviour of align_image_stack? I still think that yes, three are too few images, but the result of the alignement is still very wrong...

Thank you for the comment, anyway. I will try to repeat the test with mucho more shots, and then comment.

---

### Post by robert shearer on 2013-04-15
> I think that the main problem is that there is a LOT of focus breathing, 

Don't refocus for each shot. Leave the lens focused as for the first shot and move the whole camera.
You will need some sort of stage for this. 
Handheld will not work.

> and the align_image_stack step got the alignement completely wrong
No, it did the best it could with the images it was given.  Gigo. :-)

[http://www.pentaxforums.com/forums/photographic-technique/172959-macro-focus-stacking-large-numbers-frames.html](http://www.pentaxforums.com/forums/photographic-technique/172959-macro-focus-stacking-large-numbers-frames.html)
[http://www.pentaxforums.com/forums/pentax-camera-field-accessories/151043-macro-focus-rail-advice.html](http://www.pentaxforums.com/forums/pentax-camera-field-accessories/151043-macro-focus-rail-advice.html)
[http://www.ebay.com/itm/Linear-Stage-Positioning-Micrometer-/350434921214?pt=LH_DefaultDomain_0&hash=item51978c8afe&afsrc=1on-701M-Linear-Stage-w-Starrett-Micrometer-A4-/230634193538?pt=LH_DefaultDomain_0&hash=item35b2de8282&afsrc=1](http://www.ebay.com/itm/Linear-Stage-Positioning-Micrometer-/350434921214?pt=LH_DefaultDomain_0&hash=item51978c8afe&afsrc=1on-701M-Linear-Stage-w-Starrett-Micrometer-A4-/230634193538?pt=LH_DefaultDomain_0&hash=item35b2de8282&afsrc=1)

---

### Post by kurja on 2013-04-15
As said above, adjusting focus on the lens is usually too crude a method for this... preferrably you'd have your camera attached to a focus rail on a tripod, so you can move the camera back and forth in minute increments. Change of focus in each consecutive shot should be very small, so that the sharp areas have good overlap; otherwise, automatic alignment just won't work. If you want you can ofc align and merge such photos in gimp (or photoshop or whatever you use).

---

### Post by r_mano on 2013-04-15
Kurja, Robert: 

thanks a lot for the useful insights. I do have a rail --- I just thought (wrongly) that changing focus would led to less different FOV than moving the camera. I will try again in the right way!

---

### Post by bepr on 2013-12-08
Hi there,
Macrofusion seems to complete all tasks but the preview does not appear.  Any help or suggestions more then welcome to get it going.  Thanks, Bert

---

### Post by bepr on 2013-12-08
Forgot the attachment with a screenshot.
Thanks,
Bert

---

### Post by kurja on 2014-04-25
Hello,

I'm unable to install macrofusion on 14.04; I did 

```
  209  sudo add-apt-repository ppa:dhor/myway
  210  sudo apt-get update
  211  sudo apt-get install macrofusion
  212  sudo apt-get install hugin-tools
  213  sudo apt-get install macrofusion

```

and an attempt to install macrofusion returns 

```

sudo apt-get install macrofusion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 macrofusion : Depends: gir1.2-gexiv but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by leillo1975 on 2014-11-14
Hello everybody

I have the following problem when I try to execute macrofusion in a terminal:
```
An error occured. Python or one of its sub modules is absent...
It would be wise to check your python installation.
```

I'm installed the program via ppa in Lubuntu 14.04 32bits.

I'm trying to reinstall python, but the problem persists

I need your help quickly because I have to install it in 31 PC's on a classroom. I work in a Technical School of Image (Photography)

---

### Post by vektoroptika on 2015-01-11
> **leillo1975 said:**
> Hello everybody

I have the following problem when I try to execute macrofusion in a terminal:
```
An error occured. Python or one of its sub modules is absent...
It would be wise to check your python installation.
```

I'm installed the program via ppa in Lubuntu 14.04 32bits.

I'm trying to reinstall python, but the problem persists

I need your help quickly because I have to install it in 31 PC's on a classroom. I work in a Technical School of Image (Photography)

The same problem here. Every dependency is installed and the python packages, too, yet macrofusion does not start and writes out that message.

---

### Post by Bandit on 2015-01-17
I am going to have to try this App out.

---

