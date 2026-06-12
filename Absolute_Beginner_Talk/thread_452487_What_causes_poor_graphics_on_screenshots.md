---
title: "What causes poor graphics on screenshots"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-05-23
I have noticed on both my machines and also in screenshots which are attached to various post in these forums as "thumb nails", that when I open, display, & try to read these screenshots, the graphics rendition is extremely poor, i.e. the text on the screenshot have gaps and openings/uncompleted places in the text characters.

This poor quality is **NOT** observed by me on the display that was the subject of the screenshot, i.e. the characters on the subject screen are complete and well defined.  

What is the cause this poor quality in the rendition of these thumb nails in the forum posts ?

Thanks.

---

### Post by tocleora on 2007-05-23
that's odd, because text isn't imbedded into images, so what you see should be exactly what we see.  Can you give us an example?

---

### Post by wpshooter on 2007-05-23
> **tocleora said:**
> that's odd, because text isn't imbedded into images, so what you see should be exactly what we see.  Can you give us an example?

Give me a second and let me see if I can find the screen shot on the post I was looking at just a minute ago.

It is the attachment on the post on this forum (I believe currently located on page 2) entitled:  **What is State and Style in Sessions?**

---

### Post by siralphred on 2007-05-23
it could be because true type fonts are not installed in such images thats why they appear that way

---

### Post by srt4play on 2007-05-23
I looked at that "state and style" thread and the image looks normal to me once I click to enlarge it.  I think it's normal that the browser autosizes it to fit the window and that's when it looks like crap. When you click on the image to bring it to normal size it looks fine.

---

### Post by wpshooter on 2007-05-23
> **siralphred said:**
> it could be because true type fonts are not installed in such images thats why they appear that way

Can you please expound upon that a bit ?

Is this something that needs to be fixed on my machine or in the Ubuntu O/S in general.  I get this same poor display quality of these screenshot on both my Ubuntu machine at home which uses Firefox as browser and on the machine at work that I am composing this on which is an XP machine using IE.

I can take a screenshot/print screen on the XP machine at work and then paste that screen into wordpad and I do NOT get this poor display quality.

Thanks.

---

### Post by siralphred on 2007-05-23
true type fonts make fonts appear smoother than the default fonts on ubuntu you can check this thread [http://ubuntuforums.org/showthread.php?t=54843](http://ubuntuforums.org/showthread.php?t=54843)  and here is a screenshot of my desktop , i dont think the fonts look like what you were describing [http://farm1.static.flickr.com/213/510944464_9e65859948_o.png](http://farm1.static.flickr.com/213/510944464_9e65859948_o.png)

---

### Post by srt4play on 2007-05-23
I'm still failing to see the "poor graphics" in that screenshot.

---

### Post by wpshooter on 2007-05-23
> **srt4play said:**
> I'm still failing to see the "poor graphics" in that screenshot.

I just copied the screenshot from the post directly to a location on my hard drive and then when I open it from there it display perfectly.  Does that mean that there is something to do with font settings in my either Firefox or IE browser that needs to be changed to correct this problem and if so what needs to be changed.  I have NOT changed anything in that area of the browser parameters, so I don't exactly understand why this is working for you and not me.

Thanks.

---

### Post by siralphred on 2007-05-23
can we see a screenshot of the problem on your desktop, cos now i dont really understand your problem

---

### Post by srt4play on 2007-05-23
As I said earlier, you are probably seeing the "shrunk" version of the image that firefox displays when you click the thumbnail. This is where it looks like crap. Firefox shrinks it to fit the window, and when you hover your mouse over the image the mouse will turn into a plus sign.  Click the image and it will enlarge it to its normal size and it won't look like crap anymore.

---

### Post by wpshooter on 2007-05-23
> **srt4play said:**
> As I said earlier, you are probably seeing the "shrunk" version of the image that firefox displays when you click the thumbnail. This is where it looks like crap. Firefox shrinks it to fit the window, and when you hover your mouse over the image the mouse will turn into a plus sign.  Click the image and it will enlarge it to its normal size and it won't look like crap anymore.

I must be missing something, because when I leave/hover the mouse pointer on the screen image I do NOT see any plus sign !!!  Why am I not seeing this behavior ???

Thanks.

---

### Post by srt4play on 2007-05-23
> **wpshooter said:**
> I must be missing something, because when I leave/hover the mouse pointer on the screen image I do NOT see any plus sign !!!  Why am I not seeing this behavior ???

Thanks.

You might not be seeing it if you're running a high screen resolution. My laptop will only do 1024x768.  

I'll post a couple of screenshots showing the difference on my machine. The first is with firefox having shrunk the image to fit in the browser window, the second after I click the image to make it it's normal size.

---

### Post by wpshooter on 2007-05-23
I don't exactly understand.  You say your laptop will only do 1024 x 768 (which by the way, is the same settings being used on both my work XP computer and also my home Ubuntu computer) but yet when I pass the mouse cursor over the two images you attached, I am seeing what appears to be resolution setting of 1440 x 850, the first one saying 65% scaled and the second one not mentioning any scaling (whatever scaling might be).

Thanks.

---

### Post by srt4play on 2007-05-23
It says 1440x850 because that's what the resolution of the screenshot is in that "state and style" thread.  When you do a single window screenshot, it automatically makes the filename the same as what's in the titlebar.

I'll post a screencast when I get home from work that will hopefully better explain what you're seeing.

EDIT:  here's the [screencast]("http://www.box.net/shared/xha0u23as8")

---

### Post by tocleora on 2007-05-24
Yeah he's right, it hit me what he was trying to say a few minutes after reading his post.  Firefox shrinks to fit the image in your browser window, so if you're browser window is 1024 x 768 (just look at the numbers if you don't understand) and the image is 1280 x 1024 (larger than the size of your browser window), Firefox will shrink the image so you can see the whole image in your browser window.  What happens with this is that because the picture isn't officially resized, it's choppy looking.  if you click on the image a second time I believe it should make it it's actual size and you'll see a sharp picture.  to always see the actual image size:

> 
   1. Enter about:config in Firefox address bar.
   2. Enter browser.enable_automatic_image_resizing in Filter field.
   3. You will get a single result in the bottom pane. Double click it to change to value to false


---

