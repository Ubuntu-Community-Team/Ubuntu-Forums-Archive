---
title: "Gimp &amp; PSD"
date: 2011-06-19
forum: Art &amp; Design
---

### Post by Fatman82 on 2011-06-19
I do some development work for my brother-in-law for his web design business. Until now I have used Adobe CS3 to open the mock PSD's and develop them in dreamweaver. 

I wondered if I could open the PSD in GIMP which I found out that I could, but some of the backgrounds were different colors, and even borders in different places. This really wont help me because the customer mocks have to be 100% what they send us. 

Is there a way to open a PSD more accurately? Is there some settings I have been missing?

Another issue may be that the PSD when open in photoshop has the layers all grouped nice and neat, but gimp does not have layer grouping. Could this difference in the layer structure be causing the problem?

Thanks,
Fatman

---

### Post by ChipOManiac on 2011-06-19
A thread somewhere talks about CMYK and RGB problems... If this is the case... you have to change in photoshop the image mode to RGB...

---

### Post by ChipOManiac on 2011-06-19
Read in a post somewhere... GIMP is RGB mode... if the mockups are in CMYK you have to convert them to RGB before importing...

---

### Post by CreativeReach on 2011-06-19
I use PSD's In gimp all the time, never had a problem.

---

### Post by prokoudine on 2011-06-20
> **Fatman82 said:**
> Is there a way to open a PSD more accurately?

Yes. Install trial version of Photoshop on WINE and use it.

Support for PSD will never be perfect. This is a low-level file format that Adobe doesn't even want 3rd party developers to ever touch. And since GIMP doesn't have a number of Photoshop's features (such as layer styles), it won't open many complex PSD files correctly.

Layer groups are supported in GIMP natively since v2.7.1, and most recent unstable code was patched to open PSD files with layer groups. But you won't get layers styles support or adjustment layers support in GIMP natively any time soon unless a bunch of new committed developers join the project.

It is possible that Krita will be able to open a lot of PSD files soon, they have a Google Summer of Code student working on it. But you will still have to wait till autumn at the very least, and even then there's no knowing what features exactly will be supported.

---

### Post by BcRich on 2011-06-20
Fatman82
Currently you are best off using Photoshop if your client supplies you images in PSD format. Although there are many Photoshop 7 (and below) features implemented in the GIMP 2.6.x, that implementation may never be 100% the same as Photoshop's. This is not fallibility on the part of the GIMP but a design decision that developers make when application feature migrations are necessary for compatibility between different environments or other issues.

---

### Post by Fatman82 on 2011-06-20
Thank you very much for all of the info!

I am just going to have to keep the Windows handcuff alongside my Xubuntu until further notice. I do use the Gimp quite often, but I just cant give up on Photoshop's abilities just yet.

---

### Post by PayPaul on 2011-09-15
> **Fatman82 said:**
> Thank you very much for all of the info!

I am just going to have to keep the Windows handcuff alongside my Xubuntu until further notice. I do use the Gimp quite often, but I just cant give up on Photoshop's abilities just yet.
How true is that. And it sucks. My Windoze installation of Win7 is buggy as all get out and so for the past few days I've discovered Ubuntu and so far it's stable. Not quite stable as a rock but it works and even with an occasional boot error that is soooo easily fixed with the EXIT command unlike windoze and it's non response to user needs at boot. Yet I have tons of PSD files that can't be worked with any further in the same kind of creativity in GIMP as in photoshop. I'm resigned to starting out fresh with gimp, processing new images with it. I didn't even know it did not allow layer styles or adjustment layers as such. That could be a problem. It means many more layers to be created with various image adjustments included in them to compensate for the lack of dedicated image adjustment layers. Adjustment layers are such a basic and common sense tool that facilitate flexible control over image changes that I wonder why the developers haven't found a way to incorporate them into the GIMP.  Maybe they're just another one of those Adobe proprietary elements? That would figure considering Adobe greed.

---

### Post by Deevad on 2011-09-17
> **ChipOManiac said:**
> Read in a post somewhere... GIMP is RGB mode... if the mockups are in CMYK you have to convert them to RGB before importing...
If they were in CMYK, Gimp would not even be able to open it ; so that's not and couldn't be the problem of Fatman82... 

[QUOTE=CreativeReach]I use PSD's In gimp all the time, never had a problem.[/QUOTE]
Because you don't use layer effect, or other pro features. Common bug are related to this : [https://bugzilla.gnome.org/show_bug.cgi?id=162395](https://bugzilla.gnome.org/show_bug.cgi?id=162395) 
- blending mode "overlay" don't exist in Gimp ( it's a miss labelled softlight , so 2 softlights )
- blending mode 'color' in Gimp is not based on HSY as in Photoshop ; but on HSL I think ( or HSV ? ) 

**@prokoudine :** +1 ; Photoshop in wine is the best PSD support now ; and Krita is the future hope for a better one in FLOSS. 

**@Fatman82 :** 
If you want to convert them and open them in Gimp ; you got to prepare your PSD in Photoshop first :

- no overlay or color blending modes
- Flatten the *Fx* layer effect ( create a blank layer under , then merge down 'Ctrl+Maj+e' them )
- pixelise/rasterise the vector data layers
- Use a RGB workflow ; and adjust your color management to be the same on both softwares. 
... and I certainly forgot other little adjustement, but you got the 'big lines' :)

---

