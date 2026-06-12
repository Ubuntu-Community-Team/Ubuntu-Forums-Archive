---
title: "[SOLVED] python-fu and script-fu issues with GIMP"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Kiwilad on 2008-01-03
Ok, I downloaded some .scm sript-fu files for GIMP to my desktop (bwcontrast.scm, Eg-BlackandWhite.scm, and tonemapping.scm). Can someone please explain how I actually install these into GIMP?? I'll need some detailed instructions sorry, cos I'm really not sure about how this all works yet.

Also, my python-fu has disappeared off the menu bar. Any idea how to get it back?

Thanks heaps

Stu

---

### Post by jan quark on 2008-01-04
open the terinal and copy the scripts files to the script folder

you need the sudo permsission to copy into that folder so:

try this

```
sudo cp whateveryouwant /usr/share/gimp/2.0/scripts
```

---

### Post by Kiwilad on 2008-01-05
Thank you,

So the "whateveryouwant" section should contain the following text which I see when I open the .scm file?

(define (script-fu-bwcontrast aimg drawable dodge softlight)

  ; Start an undo group. Everything between the start and the end will
  ; be carried out if an undo command is issued.
  (gimp-undo-push-group-start aimg)

  (let ((img (car (gimp-drawable-get-image drawable)))
	(soft-layer (car (gimp-layer-copy drawable 1)))
	(dodge-layer (car (gimp-layer-copy drawable 1))))
    (gimp-image-add-layer img soft-layer -1)
    (gimp-image-add-layer img dodge-layer -1)
    (gimp-layer-set-name soft-layer "Soft Light")
    (gimp-layer-set-mode soft-layer 19)
    (gimp-layer-set-name dodge-layer "Dodge")
    (gimp-layer-set-mode dodge-layer 16)
    (gimp-layer-set-opacity soft-layer softlight)
    (gimp-layer-set-opacity dodge-layer dodge))
    
    ;; Complete the undo group
    (gimp-undo-push-group-end aimg)
    
    ;; Flush output
    (gimp-displays-flush))

(script-fu-register "script-fu-bwcontrast"
              "<Image>/Script-Fu/Photography/High-Contrast BW"
              "Simulates high-contrast BW prints. Apply on black and white images."
              "Eugene Zaikonnikov <viking@funcall.org>"
              "Eugene Zaikonnikov"
              "2004-08-11"
              "RGB*, GRAY*"
              SF-IMAGE "Input Image" 0
              SF-DRAWABLE "Input Drawable" 0
	      SF-ADJUSTMENT "Dodge Amount" '(18 0 100 1 10 0 1)
	      SF-ADJUSTMENT "Softlight Amount" '(31 0 100 1 10 0 1))

Thanks again

Stu

---

### Post by Kiwilad on 2008-01-09
Ok, so without any further clarification I tried the following, bearing in mind that I downloaded the files to my desktop. In this instance I was trying to upload the bwcontrast.scm script to gimp.

opened terminal
sudo cp bwcontrast /usr/share/gimp/2.0/scripts

and I get this
cp: cannot stat 'bwcontrast': No such file or directory 

Any ideas?

Thanks

Stu

---

### Post by Krusty Ruffle on 2008-01-11
Try

```
sudo cp Desktop/bwcontrast.scm /usr/share/gimp/2.0/scripts
```

---

### Post by Kiwilad on 2008-01-12
Thanks Krusty Ruffle, much appreciated

That worked a treat,

Stu

---

