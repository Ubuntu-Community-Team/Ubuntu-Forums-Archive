---
title: "gimp transparency layer not working?"
date: 2012-08-15
forum: Art &amp; Design
---

### Post by LLCoolJeff on 2012-08-15
I have posted in the gimp forums, but they are pretty dead compared to here so I figured I would give this a shot...

I have been a longtime photoshop and paint.net user so I am familiar with the functions, its just a new program setup is a little confusing.

I want to make a front layer slightly transparent (check my website in sig for examples on the charts) but gimp is not allowing me to do this, everytime I slide the opacity slider in the layer window, nothing happens until I cross 50% and then the layer just disappears. I originally had a gif and I thought that was the problem, but I've also tried saving it as a .png and .xcf and still it won't work.

Anyone know the solution here? (I have attached an example file that will not go transparent for me. The layer on top of the chart with the writing and lines should be slightly transparent...)


Thanks.

EDIT: I actually got a response pretty quick over at gimpforums, I guess I spoke to soon.

---

### Post by Pinoy Tux on 2012-08-16
Looking at the image properties, I noticed the Color Space was set to Indexed Color (9 colors).  Changing it to RGB (Image menu > Mode > RGB) should fix it.

---

### Post by LLCoolJeff on 2012-08-16
> **Pinoy Tux said:**
> Looking at the image properties, I noticed the Color Space was set to Indexed Color (9 colors).  Changing it to RGB (Image menu > Mode > RGB) should fix it.

yes, that worked, thank you

---

