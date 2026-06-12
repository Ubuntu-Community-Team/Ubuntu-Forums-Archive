---
title: "uneditable layers in Gimp xfc file"
date: 2013-11-09
forum: Art &amp; Design
---

### Post by Buntu Bunny on 2013-11-09
I know I may need to ask this at the Gimp forum, but that means I'd need to register (lazy, I know!). Hopefully someone here can help.

I have a Gimp (2.8) file in layers that I saved in the native xcf format so that I could later edit the layers. However, when I re-opened the file I discovered I could not edit some of those layers. 

Previously I saved-as the file under another name so I could export it as a flattened bitmap. It is those layers that I cannot edit in the original xcf file. What did I do wrong?

---

### Post by SeijiSensei on 2013-11-09
First things first.  If you open the image in GIMP and hit Ctrl-L do you see all the layers you expect to see?  Perhaps the problematic ones were merged into other layers?

If you can find the layer you want to edit, hit the up arrow in the Layers dialog to push the layer all the way to the top of the image.  Can you edit it now?

I use layers all the time to make [animated GIFs]("http://forums.animesuki.com/album.php?albumid=115").  GIMP usually preserves all the layers in formats that allow them like XCF or GIF.

---

### Post by Buntu Bunny on 2013-11-09
SeijiSensei, thank you so much for your reply.

> **SeijiSensei said:**
> First things first.  If you open the image in GIMP and hit Ctrl-L do you see all the layers you expect to see?  Perhaps the problematic ones were merged into other layers?

Yes, I can see all the layers in the layers box. I can select and highlight all the layers. Even then, I cannot do any editing of those layers.

> **SeijiSensei said:**
> If you can find the layer you want to edit, hit the up arrow in the Layers dialog to push the layer all the way to the top of the image.  Can you edit it now?

I thought about that too, but it didn't help. :(

---

### Post by ofnuts on 2013-11-09
While you have a "floating selection" you cannot edit the other layers.

If the layer at the top is a "Floating selection", you have to "anchor"  it (merge it into its target layer)("Layers/Anchor layer" or Ctrl-H), or  make it a  new standard layer ("Layer/To new layer", or Ctrl-Shift-N,  or just rename it).

---

### Post by Buntu Bunny on 2013-11-09
No floating layers, so I tried your suggestion of renaming. Then it occurred to me that once the layer is anchored, the image will not "select" i.e. have the dotted outline. So I tried to move the image and it moved the entire layer. That accomplished what I want! 

Ofnuts, thank you so much. Seems silly now, but I learn so much from my problems and mistakes. I sincerely appreciate others who are willing to help.

---

### Post by ofnuts on 2013-11-09
The "dotted outline" is the boundary of the selected layer. It's always there (unless you make it invisible disable it explicitly with "View/Show layer boundary") ...

---

### Post by Buntu Bunny on 2013-11-09
> **ofnuts said:**
> The "dotted outline" is the boundary of the selected layer. It's always there (unless you make it invisible disable it explicitly with "View/Show layer boundary") ...

I'm guessing the dotted line goes from the image itself to the layer once the image is anchored. It's a large file (5700 by 3900 pixels) which I'm working on at at 12.5 and 25% of the view. I never would have figured out where the dotted line was like that.

So much to learn! And all of it has been as I've tried to muddle my way through various projects. I couldn't do any of it without these forums.

---

