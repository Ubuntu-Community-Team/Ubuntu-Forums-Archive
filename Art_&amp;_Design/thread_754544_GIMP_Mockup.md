---
title: "GIMP Mockup"
date: 2008-04-13
forum: Art &amp; Design
---

### Post by smartboyathome on 2008-04-13
I made a mockup of a possible GUI future for GIMP. It has been submitted to the [GIMP UI brainstorm site]("http://gimp-brainstorm.blogspot.com/"). Tell me what you think. :KS

---

### Post by k99goran on 2008-04-14
I assume yours is the node-based UI. I have a few thoughts.

1. Obviously this is a primitive sketch, so it will need some beautification. :)
2. I think the advanced material room in Poser is a good example of what this could look like. Each node has two icons, one that hides/shows the settings and controls, and one that hides/shows the preview of each node.
3. If multiple filters/effects are applied in sequence, the user should be able to merge the nodes of those effects. The new node would contain all the settings and controls of all the merged nodes but only have one preview.
4. I don't like the idea of having the layer palette floating like that. It is supposed to be the 'anchor' of the node system to which all nodes are ultimately tied. Unless you want the user to be able to create several layer palettes.
5. Hiding a layer should also hide all nodes that are exclusive to that layer.
6. It may be a good idea to use tabs in this interface, where any node can be opened up as a new tab. In this tab, the user would have access to a large preview of the image and the controls used for whatever tool he/she selected. An example:
- Click on the "edit" button on a "sharpen" node opens up a new tab with the settings associated with that effect.
- The user can choose between displaying the original image, the image as it looked prior to the sharpen effect, the image as it looked just after the sharpen effect and the final image.
7. If the node in question is a composite of several effects like mentioned in #3, the settings associated to all merged effects should be visible in the tab.
8. How are selections to be handled?

---

### Post by smartboyathome on 2008-04-14
> **k99goran said:**
> I assume yours is the node-based UI. I have a few thoughts.

1. Obviously this is a primitive sketch, so it will need some beautification. :)
2. I think the advanced material room in Poser is a good example of what this could look like. Each node has two icons, one that hides/shows the settings and controls, and one that hides/shows the preview of each node.
3. If multiple filters/effects are applied in sequence, the user should be able to merge the nodes of those effects. The new node would contain all the settings and controls of all the merged nodes but only have one preview.
4. I don't like the idea of having the layer palette floating like that. It is supposed to be the 'anchor' of the node system to which all nodes are ultimately tied. Unless you want the user to be able to create several layer palettes.
5. Hiding a layer should also hide all nodes that are exclusive to that layer.
6. It may be a good idea to use tabs in this interface, where any node can be opened up as a new tab. In this tab, the user would have access to a large preview of the image and the controls used for whatever tool he/she selected. An example:
- Click on the "edit" button on a "sharpen" node opens up a new tab with the settings associated with that effect.
- The user can choose between displaying the original image, the image as it looked prior to the sharpen effect, the image as it looked just after the sharpen effect and the final image.
7. If the node in question is a composite of several effects like mentioned in #3, the settings associated to all merged effects should be visible in the tab.
8. How are selections to be handled?

Actually, it isn't. I forgot to attach it, it is attached to the origional post now. Oops. :oops:

---

### Post by k99goran on 2008-04-14
Ok. :oops::grin:
I do find the idea of a node based UI to be interesting though. They must provide some method of utilizing the non-destructive editing supported by GEGL.
Wasn't something like your idea planned? I read somewhere that you would be able to dock the toolbox to provide a single window user interface.

---

### Post by smartboyathome on 2008-04-14
> **k99goran said:**
> Ok. :oops::grin:
I do find the idea of a node based UI to be interesting though. They must provide some method of utilizing the non-destructive editing supported by GEGL.
Wasn't something like your idea planned? I read somewhere that you would be able to dock the toolbox to provide a single window user interface.

Not that I know of. The closest GIMP came was making the toolbox window a "utility window", clearing up a space in the window list. Unfortunately, nothing close to what this mockup portrays has been planned. :(

---

### Post by k99goran on 2008-04-14
I just found where I read it. It's a bit old, so it may not be relevant anymore...
> The second main point being worked on is the user interface. One of the most annoying things for lots of users is the many windows you've to deal with when working with GIMP, it sometimes just interrupts the workflow. The developers are trying a solution where tools and other windows can 'dock' at the main image window.
[source]("http://www.gimpusers.com/news/2007-12-20/gimp-2-6-aims.html")

---

### Post by Crafty Kisses on 2008-04-14
> **smartboyathome said:**
> I made a mockup of a possible GUI future for GIMP. It has been submitted to the [GIMP UI brainstorm site]("http://gimp-brainstorm.blogspot.com/"). Tell me what you think. :KS

Looks pretty sweet, I'd think that'd be a better interface, good job man.

---

### Post by smartboyathome on 2008-04-14
> **Codename said:**
> Looks pretty sweet, I'd think that'd be a better interface, good job man.

Thanks, just working on experience from using GIMP, and seeing both sides of the discussion of the interface. This came as a happy medium. :KS

---

### Post by exploder on 2008-04-14
I like your idea, it makes sense..

---

### Post by st0n3cutt3r on 2008-04-15
Honestly, I hate using the Gimp. 
I love doing image editing, and even image creation, but I hate that once I click on a tool, or a layer, I have to move my mouse BACK to the image I am working on, and click on it before any commands from my keyboard will be heard... like zooming in, or using the arrow keys to move layers (instead they switch which layer I am looking at!) it drives me crazy!

I would love to have an all-in-one-window interface like this where my keystrokes would not go unheard (or worse, misunderstood) as they do now while using the gimp!
 
I hope it makes it to reality!

---

### Post by smartboyathome on 2008-04-15
> **st0n3cutt3r said:**
> Honestly, I hate using the Gimp. 
I love doing image editing, and even image creation, but I hate that once I click on a tool, or a layer, I have to move my mouse BACK to the image I am working on, and click on it before any commands from my keyboard will be heard... like zooming in, or using the arrow keys to move layers (instead they switch which layer I am looking at!) it drives me crazy!

I would love to have an all-in-one-window interface like this where my keystrokes would not go unheard (or worse, misunderstood) as they do now while using the gimp!
 
I hope it makes it to reality!

That is why I use E17 when image editing. Even if I click in the window, it doesn't go up unless I alt+click or click the window border. It does get focused, however. I wish there was a way to do this in GNOME, but there isn't. :(

---

### Post by Half-Left on 2008-04-15
They are doing a UI change in 2.5 branch, I usually just customize the layout on only use panels I need and close them when I dont need them.

Some features are really a pain I agree because you have to guess because of no preview. The great thing about Photoshop is it has layer effects which you can change at anytime and live filters. It's great for image editing since thats what it does best but for putting art together it's pretty weak. but good for a free.

---

### Post by dsiembab on 2008-04-18
still waiting for paint-mono

---

