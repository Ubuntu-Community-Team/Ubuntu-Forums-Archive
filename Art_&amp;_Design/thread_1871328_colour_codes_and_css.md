---
title: "colour codes and css"
date: 2011-10-28
forum: Art &amp; Design
---

### Post by tpprynn on 2011-10-28
I want to try and get rid of the lighter orange in Ubuntu 11.10's default theme that appears on certain buttons. I'm fine with the thick orange on menus, it's cheerful, but this other orange is annoying and limp.

Colours seem different in css files, they seem to have three sets of numbers separated by commas instead of a hash and six digits. Is there a way to convert between the two or find out what this orange is? I tried typing the comma-separated numbers into Gimp's colour picker but it didn't understand.

Then I could trace and recognise the relevant lines in the css file in the Ambiance theme and make it the same colour as other buttons.

Thanks.

---

### Post by ofnuts on 2011-10-28
> **tpprynn said:**
> I want to try and get rid of the lighter orange in Ubuntu 11.10's default theme that appears on certain buttons. I'm fine with the thick orange on menus, it's cheerful, but this other orange is annoying and limp.

Colours seem different in css files, they seem to have three sets of numbers separated by commas instead of a hash and six digits. Is there a way to convert between the two or find out what this orange is? I tried typing the comma-separated numbers into Gimp's colour picker but it didn't understand.

Then I could trace and recognise the relevant lines in the css file in the Ambiance theme and make it the same colour as other buttons.

Thanks.The "hash" notation is hex (00->FF), with two hex digits for each of R, G; B. The other is the same values, in the same order, in decimal (0->255). The color selection dialog in Gimp shows the value for each RGB component in decimal in the spinners, and shows the "hash notation" below the sliders ("HTML notation").

---

### Post by tpprynn on 2011-10-28
Thanks! After a bit of playing around and tapping values in I've now been able to banish the mild orange.

---

