---
title: "What exactly is CMYK?"
date: 2008-09-17
forum: Art &amp; Design
---

### Post by nkri on 2008-09-17
Hey guys,

As the title implies, what's CMYK?  I always see people saying how much they hate that The GIMP doesn't have CMYK support, but why is it so important?  I understand that it has something to do with printing...

I do a lot of photography and use both Photoshop and GIMP, but I wanted to start printing some of my pics (which I've only done on rare occasions up to this point, and only in Mac OS X) and want them to be the best quality possible.

Thanks!
-nkri

---

### Post by mrtomservo on 2008-09-17
[http://en.wikipedia.org/wiki/CMYK]("http://en.wikipedia.org/wiki/CMYK")

:)

---

### Post by lesergi on 2008-09-17
[http://en.wikipedia.org/wiki/CMYK](http://en.wikipedia.org/wiki/CMYK)

---

### Post by Half-Left on 2008-09-17
It's only important if you want the most accurate colour from screen to print, most people wouldn't know if you used RGB or CMYK. This IS one of the most overrated issues with GIMP.

---

### Post by Merk42 on 2008-09-17
As already mentioned CMYK is used for print because it's a subtractive color model versus the additive color model of RGB used for websites.  Depending on the image you **will** see a color difference.  Sometimes colors aren't as vibrant in RGB. For "Joe User" this usually isn't a big deal, true, but for professional photographers it can be.

---

### Post by nkri on 2008-09-18
Ah, ok.  Thanks, everyone, for clearing that up:)
-nkri

---

### Post by AJB2K3 on 2008-09-18
Everytime I see a post going on about lack of cmyk support in gimp it makes me screme all you have to do is tell gimp where the profile (*.icc) file is and you get that support, simple.
CMYK - Cyan, Magenta, Yellow, blacK is a system for measuring ink.
When CMY is mixed 1:1:1 the finial colour is black however 
RGB - Red, Green, Blue is a system used for lighting.
When RGB light is mixed 1:1:1 you end up with white and this is where the problem with screen print calabration shows its head on linux.
Apparently there are tools to solve it ( the spider is supposed to work) however By the simple black art of reading I found that using the correct input and output profiles in gimp (CMYK Print/import) make a difference.

---

### Post by nkri on 2008-09-19
> **AJB2K3 said:**
> Everytime I see a post going on about lack of cmyk support in gimp it makes me screme all you have to do is tell gimp where the profile (*.icc) file is and you get that support, simple.

Sounds good, but where might I find such a profile?

Thanks!
-nkri

---

### Post by mike1234 on 2008-09-19
> **nkri said:**
> Sounds good, but where might I find such a profile?

Thanks!
-nkri

 Copy it from Windows XP. If you have dual boot. ICC profile is based on your hardware. My Dell ICC profile might not be a good match for your LG monitor as an example.

[http://www.color.org/creatingprofiles.xalter](http://www.color.org/creatingprofiles.xalter)


M.

---

### Post by DirtDawg on 2008-09-19
> **Half-Left said:**
> It's only important if you want the most accurate colour from screen to print, most people wouldn't know if you used RGB or CMYK. This IS one of the most overrated issues with GIMP.

This is one of *the biggest* problems with GIMP as a *professional* tool(actually, the lack of an anti-aliased fill tool is breathtakingly lame as well, IMO).

When designing for print, it's common practice to leave your screen in RGB mode, as the visual will more closely resemble what the actual print color would be. But a CMYK mode is important to professionals because many professional printers require you to give them CMYK seperated files, so they need to be converted before you turn them in.

But even if using a printer that does accept RGB files, it's a risky to give a printer RGB files because there is a very good chance some of your carefully chosen RGB colors will be out of the gamut of CMYK. In other words, a brilliant RGB yellow might turn out a putrid mustard color when printed because it's too bright for CMYK inks to reproduce. If a client asks you to design a brochure and they print 5,000 of them and that yellow they saw on the proof turns out to be a putrid mustard color, and now they have 5,000 copies of a brochure that looks terrible, well that client is not going to be happy.

It's true that most people will never miss CMYK seperation, but in the world of professional design, Gimp's lack of CMYK color is a killer. That said, I prefer Gimp over Photoshop any day. It's overall design, IMO, is much friendlier and better for streamlining work. That's right I said it, I *prefer* the Gimp's GUI to Photoshop's! :D

---

### Post by DirtDawg on 2008-09-19
> **AJB2K3 said:**
> Everytime I see a post going on about lack of cmyk support in gimp it makes me screme all you have to do is tell gimp where the profile (*.icc) file is and you get that support, simple.
CMYK - Cyan, Magenta, Yellow, blacK is a system for measuring ink.
When CMY is mixed 1:1:1 the finial colour is black however 
RGB - Red, Green, Blue is a system used for lighting.
When RGB light is mixed 1:1:1 you end up with white and this is where the problem with screen print calabration shows its head on linux.
Apparently there are tools to solve it ( the spider is supposed to work) however By the simple black art of reading I found that using the correct input and output profiles in gimp (CMYK Print/import) make a difference.

I haven't heard of this before. Is this method reliable? If it's so easy, why not enable this feature by default?

EDIT: Okay I see, saw this post too late:
> **mike1234 said:**
> Copy it from Windows XP. If you have dual boot. ICC profile is based on your hardware. My Dell ICC profile might not be a good match for your LG monitor as an example.[/URL]
If the ICC profile is based on hardware, that seems to me like a not very reliable alternative. I suppose it could be with enough tweaking and a couple 'leaps of faith.'

---

### Post by BLTicklemonster on 2008-09-19
... sounds like a limitation in the printing world to me.

---

### Post by DirtDawg on 2008-09-20
> **BLTicklemonster said:**
> ... sounds like a limitation in the printing world to me.

That's just the nature of the inks. Press printing is what it is. An entirely different beast than desktop publishing.

---

### Post by AJB2K3 on 2008-09-20
In windows the icc profile is stored in the spoiler folder for printers.

> The best way to hide something is in plain view.

The options to use icc's are under the preferences panels

Fair shout that gimp can't export CYMK, I'd defiantly not want 5000 mustered yellow brouchers when they shout be sunburst yellow :lolflag:

---

### Post by BLTicklemonster on 2008-09-20
> **DirtDawg said:**
> That's just the nature of the inks. Press printing is what it is. An entirely different beast than desktop publishing.

I know, I just like putting it off on the printers instead. :)

---

