---
title: "GIMP will not rotate images"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by AlanD on 2007-05-27
Has anyone tried using GIMP to rotate an image? I had an image that i took with my camera, turning my camera sideways. As expected, the image came out rotated 90 degrees clockwise. I rotated it 90 degrees clockwise in GIMP and saved the image. The thumbnail is fine but when I open it in any app other than GIMP, it's rotated 180 degrees counter clockwise. What gives? D:

---

### Post by silkstone on 2007-05-27
There is an orientation sensor in the camera which can tag the image file to automatically rotate, provided the viewing software reads the tag. Some applications do and some don't - that's the problem. IMO it's better to turn off the auto-rotate function on the camera so there is no confusion - you can do a lossless rotation in gThumb and most viewers/editors.

It is usually possible to tell the editor/viewer to ignore the rotation tag if you look under image properties.

---

