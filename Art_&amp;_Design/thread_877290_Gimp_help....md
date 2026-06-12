---
title: "Gimp help..."
date: 2008-08-01
forum: Art &amp; Design
---

### Post by hockey97 on 2008-08-01
Hi I am trying to export or at least save layers as seperate images.

How can I do this??

---

### Post by blueamcat on 2008-08-01
taken from Gimp's online documentation...

"To preserve all the components of your image when you save it — the layers, channels, etc. — use ".xcf" format, which is the GIMP's native format."

Hope that helps you!

---

### Post by hockey97 on 2008-08-01
I did. I am trying to right now save all layers as seperate images so I can use each image for my website.

any idea how to save each layer as it's own image file not combine all into one image.

---

### Post by blueamcat on 2008-08-01
Well, I'm not at home so I can try it myself right now. I'm just reading through this right now...
[http://docs.gimp.org/en/](http://docs.gimp.org/en/)

I'll post anything else I find though.

---

### Post by BLTicklemonster on 2008-08-01
In "layers" just leave the little eye showing on the layer you want, and save it as the file name you want for it. Move to the next layer, unchecking the little eye for the previous, and check the eye for the layer/image you want now, then save it, and move to the next one.

---

### Post by blueamcat on 2008-08-01
Ah there ya go. Thanks for the assistance!

---

### Post by hockey97 on 2008-08-01
Thanks it works lol. So there is no other way then that?? 

it would suck if you had to make a huge website and you designed it on gimp which would be a pain to save every singal layer.

---

### Post by atoc on 2008-08-01
Select and Drag a layer to the toolbox.
Voila. New image from layer.

Fun with gtk-recordMyDesktop and mencoder:
Video of the above.
[http://072570.com/linuxstuff/gimpnewlayerfromimage.avi](http://072570.com/linuxstuff/gimpnewlayerfromimage.avi)

---

### Post by BLTicklemonster on 2008-08-01
Bingo. I just came back from a concert and was thinking about that the whole evening and was eager to see if dragging the layers like that worked. Good job!

---

### Post by lyceum on 2008-08-02
> **atoc said:**
> Select and Drag a layer to the toolbox.
Voila. New image from layer.

Fun with gtk-recordMyDesktop and mencoder:
Video of the above.
[http://072570.com/linuxstuff/gimpnewlayerfromimage.avi](http://072570.com/linuxstuff/gimpnewlayerfromimage.avi)

cool info, thanks for the tip!

---

### Post by hockey97 on 2008-08-02
Ok got another problem. I am able to save each layer as an image.

I been looking at tutorials on how to make your website design in gimp. 

I still never figured out how to do it. 

I am trying to design my website. I made every layer the same height and width but each layer contains just one element of the website.

like tabs / lines ect ect.

Is they any good way to design a website using gimp??

I heard somthing about slicing images or something.

The reason I want to use gimp is that I can see the design once I agree with the design I can then just code in the webpage and then add the images where it was designed to be.

any suggestions??  

also how do you guys deal with display settings different display settings. Like my website would look differently in many differnet display settings.

I heard of fluid design. I just can't really grasp the concept.

---

### Post by Merk42 on 2008-08-02
The slicing of images goes back to when websites were done using <table> for layout.  You still can technically do it that way, but it is highly recommended to use <div> and the like for layout.

If I've just confused you with terminology, keep in mind a web **designer** and a web **developer** are usually not the same people.  One is the architect, making it look attractive, and the other is the engineer, creating it so it works.

Most websites used a fixed width for their site, so people with higher resolutions would just have white space.  You can make the site a % of the window instead of set number of pixels, but then you have to be care to see how the inner objects would move about on different resolutions.

If you're going to develop a site, get as many browsers and possible.  Especially IE6, it's awful, but still a vast majority of people use it and it may not display the same as it does in IE7, Firefox, Opera, Safari, etc

---

### Post by hockey97 on 2008-08-02
I understood what you said about web designer and a web developer.

I am good at web developer but not that great at web designer.

yep I tried using the % instead of px which I learned on a tutorial of liquid design layout.  I tried the % and when I tested it...it was fine with the default resolution of how I made the website but when the resolution got bigger or smaller some elements would overlap each other.

I am trying to make a professional website so having the % used on my website makes it look like some 5 year old coded it and would make my website look less professional. 

Well I thought that I could make a javascript or somthing that would adjust my website based on the persons web browser and resolution.

I am trying to make a browser friendly website. I have asked this many times in the programming section but I get replies saying why not use liquid design. I know for a fact when you start a video game it would adjust the game art ect in the game window and would adjust based on what resolution you have set up.

I was thinking is this a web design problem or a web development problem I thought it was a problem in the web development part,but in the programming section on this site I was told the only way to fix it is to make a design that is liquid , which I tried to learn but all tutorials were telling me to use % instead of px which this would make elements overlap each other at some point.

I notice professional websites like Ea games website it would not use % but notice that the design would work in any resolution.
I tried ie7,ie6 and firefox and all were exacly the same except in firefox the scrollbars were default in firefox I don't know if in firefox you can change the scroll bar colors ect.

---

### Post by lyceum on 2008-08-02
It looks like you are new at this. Let me give you 2 options for making an easy website. 

1. Use KompoZer. I do not like it, as it messes with my code, but it is a WYSIWYG (What You See Is What You Get). You can see what you are doing building your website. 

2. Use OpenOffice.org. Open a new Writer document and save it as an html file. Build your web pages there and link them together by hyperlinking the pages.

Once this is done you will have an easy, but poorly coded website. At this point, you will need to fix your code using a program like Bluefish or Aptana. You will most likely figure out that table are the best way to line things up. You will want to go back and replace the tables with divs and learn some cool CSS tricks. 

This is a good way to learn, build it working, but sloppy then fix everything as you learn how to code better. For what you are doing I would recommend going to a used book store and picking up a book on html and CSS, or if you want to get fancey dhtml (d for dynamic) and CSS. Just be sure if you get one book that it cover both topics. "Spring into HTML and CSS" is not bad. html and CSS are pretty easy to learn, so really any book is good, or you could google for some tutorial sites. Personally, I like books. I still find myself looking at the O'Reily pocket books on these 2 from time-to-time. 

Hope that helps :)

---

### Post by Merk42 on 2008-08-02
> **hockey97 said:**
> I tried the % and when I tested it...it was fine with the default resolution of how I made the website but when the resolution got bigger or smaller some elements would overlap each other.

You'd have to make all the elements % so they'd all scale accordingly.

> **hockey97 said:**
> 
Well I thought that I could make a javascript or somthing that would adjust my website based on the persons web browser and resolution.
I believe that is technically possible, but do you really want to make a sepaerate one for IE, Firefox, Opera, Mac, Windows, Linux, hi res low res widescreen?

> **hockey97 said:**
> 
I am trying to make a browser friendly website. I have asked this many times in the programming section but I get replies saying why not use liquid design. I know for a fact when you start a video game it would adjust the game art ect in the game window and would adjust based on what resolution you have set up.

Most gaming is polygons, so they can easily scale/crop to any size.  So it's not really a fair comparison

> **hockey97 said:**
> 
I notice professional websites like Ea games website it would not use % but notice that the design would work in any resolution.
If you look at the source code, and subsequently the css you can see they use a fixed with, which shows more whitespace on higher resolutions, which it what I was describing in my first post.

> **hockey97 said:**
> 
I tried ie7,ie6 and firefox and all were exacly the same except in firefox the scrollbars were default in firefox I don't know if in firefox you can change the scroll bar colors ect.

Changing the scrollbar colors is a non-standard, so you can ONLY do it in IE.

---

### Post by atoc on 2008-08-02
> **lyceum said:**
> cool info, thanks for the tip!
You're welcome.
I discovered it quite by accident a while back and am happy to share.
Apparently it is a documented feature, but I'm not one to RTFM unless I really, really have to :)

---

### Post by hockey97 on 2008-08-03
Well I am not really new to this. I did read many liquid design which would use % instead of px. I did try all elements % and then tried half and half. I use images as boards around an image and those boarders would appear on the image or too far out.

I need to use px else I can't get a perfect looking website.

Is their a way where I can just use javascript and like edit css so that I can  based it on the clients browser window I can rescale the website to fit the persons resoultion.

I was told to just use a table.

I can't fully get around this. I did try fluid design followed many tutorials but didn't work for me.

---

### Post by Merk42 on 2008-08-03
> **hockey97 said:**
> Well I am not really new to this. I did read many liquid design which would use % instead of px. I did try all elements % and then tried half and half. I use images as boards around an image and those boarders would appear on the image or too far out.

I need to use px else I can't get a perfect looking website.

Is their a way where I can just use javascript and like edit css so that I can  based it on the clients browser window I can rescale the website to fit the persons resoultion.

I was told to just use a table.

I can't fully get around this. I did try fluid design followed many tutorials but didn't work for me.

Yes you can just put 
```
if ((screen.width>=1024) && (screen.height>=768))
{
<link rel="stylesheet" type="text/css" ref="1024768.css" />
}
else if   ((screen.width>=1280) && (screen.height>=1024))
{
<link rel="stylesheet" type="text/css" ref="12801024.css" />
}

```

But then you'd have to make a separate style sheet for every possibly combination of browser and resolution wouldn't you?

That's really more work than it needs to be.  Either figure out the liquid thing, maybe by putting in some min-width / max-width properties. Or just do the fixed width like the EA site you mentioned earlier.

---

