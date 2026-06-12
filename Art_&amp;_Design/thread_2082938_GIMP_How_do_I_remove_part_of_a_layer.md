---
title: "GIMP How do I remove part of a layer"
date: 2012-11-11
forum: Art &amp; Design
---

### Post by Codeless on 2012-11-11
So I made a border and want the middle to be cut out of the layer. I see an option to change transparency for the entire layer but this is not want I want, I want to keep the outside solid and make the middle 100% transparent (or cut out).

How do I achieve this?

---

### Post by dgharmon on 2012-11-11
> **Codeless said:**
> So I made a border and want the middle to be cut out of the layer

[Use the Rectangle Select Tool]("http://docs.gimp.org/en/gimp-tool-rect-select.html")

---

### Post by deadflowr on 2012-11-11
Use the rectangle as stated in post no.2.

Then go to select > to path.

Then go to layer> mask > add layer mask.

Pick selection and mark inverted, otherwise the area you wish to give transparency will remain and the outer area will be transparent.
 The go back to add layer mask and click apply layer mask.

Then save/export your image.

If at any point, you feel it isn't working as you want it, click edit > undo.(as many times as needed to bring you back to a safe spot.

---

### Post by Codeless on 2012-11-11
Thanks for your help. You make it sound simple but it wouldn't behave the way I wanted to... like it would just turn everything transparent. In the end I just redrew the border on a transparent layer.

I'm not really into graphics (obviously) this is for a java game I'm making... I guess I need to know a bit about graphics if I want to make games

---

### Post by deadflowr on 2012-11-11
It isn't very simple, I've just had practice at doing this.

I did find this thread on the subject for you, 

[http://ubuntuforums.org/showthread.php?t=1700480]("http://ubuntuforums.org/showthread.php?t=1700480")

It seems much easier to understand.

The gist of it is to use the rectangle selection tool, pick your area and then hit the delete key on your keyboard. The area will be deleted.

---

### Post by prokoudine on 2012-11-12
> **deadflowr said:**
> Use the rectangle as stated in post no.2.

Then go to select > to path.

Then go to layer> mask > add layer mask.

Pick selection and mark inverted, otherwise the area you wish to give transparency will remain and the outer area will be transparent.
 The go back to add layer mask and click apply layer mask.

This is a wee bit too complicated.

1. Select the area you want to hide.
2. Layer > Mask > Add Layer Mask.
3. In the dialog for creating a new mask use "Initiate with: selection"

That's it.

---

