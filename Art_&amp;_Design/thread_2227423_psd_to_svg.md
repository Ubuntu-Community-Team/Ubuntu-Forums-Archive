---
title: "psd to svg"
date: 2014-06-01
forum: Art &amp; Design
---

### Post by TheVisitors on 2014-06-01
So I am looking for a way to convert an psd to an svg.  I can open both and even save both, but using different programs.  Gimp can open a psd, but not save in svg.  And Inkscape can open and save a svg, but not open psd.  

The source file is a psd.  Saving it in any other format(ie.. png, jpg, ect...) will naturally not keep the quality of the psd.

Solutions?

---

### Post by ofnuts on 2014-06-02
A PSD is mostly bitmap graphics, while a SVG is mostly vector graphics. As far as I know an SVG can include a bitmap but it the SVG is upscaled this won't be pretty (a pure SVG can be rescaled at will). So if you really need an SVG with a bitmap in it, just convert the PSD to some intermediate format (PNG) and include it in an SVG (using Inkscape or else).

If your PSD has significant vector graphics contents (not too likely, the author would have used Illustrator for this) try to export it to EPS and then load the EPS in Inkscape, this may preserve the vector part.

---

### Post by TheVisitors on 2014-06-02
> **ofnuts said:**
> A PSD is mostly bitmap graphics, while a SVG is mostly vector graphics. As far as I know an SVG can include a bitmap but it the SVG is upscaled this won't be pretty (a pure SVG can be rescaled at will). So if you really need an SVG with a bitmap in it, just convert the PSD to some intermediate format (PNG) and include it in an SVG (using Inkscape or else).

If your PSD has significant vector graphics contents (not too likely, the author would have used Illustrator for this) try to export it to EPS and then load the EPS in Inkscape, this may preserve the vector part.
Converting it to a pnd then to an svg is not idea. You lose the quality doing so.

I was hoping someone had another method or maybe a plugin I was unaware of.
[http://pernsteiner.org/inkscape/psd_import/](http://pernsteiner.org/inkscape/psd_import/)

^ This plugin for example does not work properly with the current version.

---

### Post by mcduck on 2014-06-03
PNG is a lossless format (and supports up to 16 bit per color modes, color profiles and everything else) so no, you won't loose any quality by converting to PNG. You will only loose any possible layers you have (which you'd loose in the process anyway).

Creating a plugin to do such job automatically wouldn't be possible, PSD primarily a bitmap image format with very limited vector support,  while SVG is a vector format, so direct conversion is not possible. You can vectorize a bitmap image but that depends on manually adjusting settings to get a decent approximation, and depending on source image you will loose details in the process (and more often than not will still need to do manual editing and tracing to get a good result).

So, your options are either to export to PNG and then import it as a bitmap into the SVG file and then eithe rleave it as btmap object which is only useful in some special cases) or try to vectorize it (which only works well for graphics with clear detail and limited colors).

Or if you really are talking about just getting the *paths* from a PSD file (ignoring all the other possible content) then you can export the paths as .ai and import that to Inkscape directly. (which is pretty much the same as what that plugin you linked to would have done). Or if you have access to Illustrator it can export the paths to SVG.

---

### Post by SeijiSensei on 2014-06-03
[Imagemagick]("http://www.imagemagick.org/") supports both PSD and SVG, so it *might* be possible to use the convert command-line tool for this task.  I've not really worked with SVG, so I can only suggest you give it a try and see what results.  The **imagemagick** package is in the repositories.

---

### Post by Sasha_Aderolop on 2014-08-27
Open your .psd file with Adobe Illustrator (tested with CS6) and then "Save as..." > SVG.

---

### Post by ofnuts on 2014-08-28
There is an AI version for Linux or is this an informal announcement?

---

