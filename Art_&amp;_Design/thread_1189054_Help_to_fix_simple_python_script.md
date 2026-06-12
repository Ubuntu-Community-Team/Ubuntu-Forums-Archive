---
title: "Help to fix simple python script"
date: 2009-06-16
forum: Art &amp; Design
---

### Post by rtsnhatl on 2009-06-16
What am I missing in this Python script, I am trying to write a simple script to hide or unhide all of the layers in an image.  I can only seem to get the active layer to hide. Below is the function I am using, must be something I am missing?

Thanks,
Bob

def hide_layers( image, drawable, hide ):
    layers = image.layers #get image layers
    for layer in layers:
    	#gimp_drawable_is_layer(layer)
    	pdb.gimp_image_set_active_layer(image, layer)
    	pdb.gimp_drawable_set_visible(drawable, hide)

---

### Post by lukeiamyourfather on 2009-06-16
I'm not familiar with scripting in GIMP, but this looks wrong to me.

```
layers = image.layers #get image layers
```

Calling a function in a module usually requires the parentheses even if there are no arguments for it. Like this.

```
layers = image.layers()
```

Not sure if that'll work. Did you get any error messages with it? Cheers!

> **rtsnhatl said:**
> What am I missing in this Python script, I am trying to write a simple script to hide or unhide all of the layers in an image.  I can only seem to get the active layer to hide. Below is the function I am using, must be something I am missing?

Thanks,
Bob

def hide_layers( image, drawable, hide ):
    layers = image.layers #get image layers
    for layer in layers:
    	#gimp_drawable_is_layer(layer)
    	pdb.gimp_image_set_active_layer(image, layer)
    	pdb.gimp_drawable_set_visible(drawable, hide)

---

