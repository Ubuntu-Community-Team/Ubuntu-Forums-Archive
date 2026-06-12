---
title: "the gimp: animating a gif with a continuous background layer"
date: 2012-04-09
forum: Art &amp; Design
---

### Post by Thorsen V on 2012-04-09
Hi

I have an animation I'm trying to make use the gimp, to be saved as a gif. 

So I know about appended the time delay to the title of each layer/frame (50ms), and this works, great, except that the first layer/frame is special. It is the background for all the other frames which are mostly transparent. 

Leaving the time off the frame doesn't seem to work (the backround briefly flashes then disappears each time the animation cycles).

I know I've done this before but just can't recall how it's done.

Would someone remind me please? Thanks in advance

Regards,

Thorsen

---

### Post by lovinglinux on 2012-04-09
Click "Filter >> Animation >> Optimize (Difference)"

---

### Post by Thorsen V on 2012-04-10
> **lovinglinux said:**
> Click "Filter >> Animation >> Optimize (Difference)"
TY 

This isn't quite it, but I now think I was misremembering my previous experience and what I was trying to do is in fact impossible.

---

### Post by lovinglinux on 2012-04-10
> **Thorsen V said:**
> TY 

This isn't quite it, but I now think I was misremembering my previous experience and what I was trying to do is in fact impossible.

I have tested it and it worked, with a background and two translucent layers.

---

### Post by Thorsen V on 2012-04-10
possibly you are misunderstanding the problem

Here's an example of the original problem:

[[IMG]http://i40.tinypic.com/vhde7o.jpg[/IMG]]("http://i40.tinypic.com/vhde7o.jpg")

Looks okay on a white backround but click through to see the issue. The flash of white is the background frame.

Here's what happens when I do "Filter >> Animation >> Optimize (Difference)":

[[IMG]http://i41.tinypic.com/2yuj8d4.gif[/IMG]]("http://i41.tinypic.com/2yuj8d4.gif")

I can bucket-fill the background colour to all the frames but then  the gif ends up too big.

---

### Post by lovinglinux on 2012-04-10
> **Thorsen V said:**
> possibly you are misunderstanding the problem

Here's an example of the original problem:

[[IMG]http://i40.tinypic.com/vhde7o.jpg[/IMG]]("http://i40.tinypic.com/vhde7o.jpg")

Looks okay on a white backround but click through to see the issue. The flash of white is the background frame.

Here's what happens when I do "Filter >> Animation >> Optimize (Difference)":

[[IMG]http://i41.tinypic.com/2yuj8d4.gif[/IMG]]("http://i41.tinypic.com/2yuj8d4.gif")

I can bucket-fill the background colour to all the frames but then  the gif ends up too big.


Oh, I see. When I did the test, the overlays were the same size all the time, so I didn't notice this issue. In this case, I would recommend make duplicates of the background layer and merging each overlay wiotha copy of the background.

---

### Post by SeijiSensei on 2012-04-11
The problem with your spinning image is that the white background is only in one frame.  I suspect you didn't do the differencing properly.  You need to stack the sequence of *opaque* images, then tell GIMP to save as a GIF.  The differencing engine should preserve the initial white background and make a sequence of differenced layers that are largely transparent.  

Here are a few examples that you can examine in GIMP using the Layers window:

[img]http://forums.animesuki.com/images/as.albums/t/33/5c803b1e7944bcb744dea64f88bea482_33644.gif?dl=1296412590[/img] [img]http://forums.animesuki.com/images/as.albums/t/1/f86d77b3980076161a5522bfe3fec7a7_1524.gif?dl=1226784691[/img] [img]http://www.takinganimeseriously.com/images/avatars/chiko-in-chains-bordered.gif[/img] [img]http://forums.animesuki.com/images/as.albums/t/27/0cef46f0382f811f9a2a858a16884bc3_27806.gif?dl=1257085747[/img]

In the first one, there's only one opaque background frame.  The rest of the sequence is differenced against that.  The second is more complex because each frame is substantially different from the preceding one.  The main thing that differentiates the "background" frame in this case is that it remains on-screen for a longer period of time.

The third example demonstrates how our minds create the illusion of continous motion.  We don't really notice the transition back to the beginning of the sequence so the image looks to be seamless.  The chains enhance this illusion.  If you only saw Chizuko's hair and the flames, you be more apt to notice that the animation repeats the same sequence of frames endlessly. In comparison, it's harder to ignore the repetition of the motion of Nodame's hair in the fourth animation.

I make these by stacking the opaque frames up as layers then saving as a GIF.  GIMP's differencing engine will then determine which pixels can be made transparent and which must change from frame to frame.  

I assume you know that you need to add an alpha channel (Layer > Transparency > Add Alpha Channel) to create transparency.

---

### Post by Thorsen V on 2012-04-11
> **lovinglinux said:**
> Oh, I see. When I did the test, the overlays were the same size all the time, so I didn't notice this issue. In this case, I would recommend make duplicates of the background layer and merging each overlay wiotha copy of the background.
:)
that's really where I came in: I did that and the image looks right but is too big (for a forum avatar that is)

---

### Post by Thorsen V on 2012-04-11
> **SeijiSensei said:**
> The problem with your spinning image is that the white background is only in one frame.  I suspect you didn't do the differencing properly.  You need to stack the sequence of *opaque* images, then tell GIMP to save as a GIF.  The differencing engine should preserve the initial white background and make a sequence of differenced layers that are largely transparent.  

Here are a few examples that you can examine in GIMP using the Layers window:

[IMG]http://forums.animesuki.com/images/as.albums/t/33/5c803b1e7944bcb744dea64f88bea482_33644.gif?dl=1296412590[/IMG] [IMG]http://forums.animesuki.com/images/as.albums/t/1/f86d77b3980076161a5522bfe3fec7a7_1524.gif?dl=1226784691[/IMG] [IMG]http://www.takinganimeseriously.com/images/avatars/chiko-in-chains-bordered.gif[/IMG] [IMG]http://forums.animesuki.com/images/as.albums/t/27/0cef46f0382f811f9a2a858a16884bc3_27806.gif?dl=1257085747[/IMG]

In the first one, there's only one opaque background frame.  The rest of the sequence is differenced against that.  The second is more complex because each frame is substantially different from the preceding one.  The main thing that differentiates the "background" frame in this case is that it remains on-screen for a longer period of time.

The third example demonstrates how our minds create the illusion of continous motion.  We don't really notice the transition back to the beginning of the sequence so the image looks to be seamless.  The chains enhance this illusion.  If you only saw Chizuko's hair and the flames, you be more apt to notice that the animation repeats the same sequence of frames endlessly. In comparison, it's harder to ignore the repetition of the motion of Nodame's hair in the fourth animation.

I make these by stacking the opaque frames up as layers then saving as a GIF.  GIMP's differencing engine will then determine which pixels can be made transparent and which must change from frame to frame.  

I assume you know that you need to add an alpha channel (Layer > Transparency > Add Alpha Channel) to create transparency.

as I wrote in             #[**3**]("http://ubuntuforums.org/showpost.php?p=11832693&postcount=3") and expand here: I had a misunderstanding of how it worked and thought that there was a way to use one frame as a background for all the other frames (each of which have transparent elements), this being done so because without this approach the gif is too big.

 I thought I'd done this before (a year or two ago) but must have misremembered the circumstance.

I'll probably try taking out some frames and see if I can get the size down that way.

---

### Post by Thorsen V on 2012-04-11
Thanks for your help guys.

I shall flag this as solved to stop anyone else wasting their time.

---

