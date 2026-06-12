---
title: "Problems with using browsers on Ubuntu for web design"
date: 2010-11-04
forum: Art &amp; Design
---

### Post by olivaw_daneel on 2010-11-04
I've recently begun using Ubuntu for some web design projects. My assumption has been that Firefox and Chrome would work in exactly the same way on Ubuntu as they do on Windows.

However, I've noticed that browsers on Ubuntu behave differently.

For example, you can see a recent site I've done at [www.sdeyservices.co.uk](www.sdeyservices.co.uk). Now on Windows this site looks fine in Chrome, FF, IE8 and IE7. Yet on Ubuntu FF and Chrome the right-hand column is longer than the left and the 'get creative...' text is merging into the number above it.

Of course these aren't huge differences but they do matter from a professional point of view.

This concerns me because if I can't rely on Ubuntu browsers to render things the same way as they do on Windows (obviously with the biggest market share) then what's the point in testing my sites on Ubuntu? 

Is there a browser or something that I can do which will render websites exactly how they are on Windows?

---

### Post by mcduck on 2010-11-04
Actually there's a lot of point in testing your site on *every possible* platform.

If your code is right, and you do your layouts well, the site will look more or less the same on every platform and browser. If you get different results on different browsers apart from ones like IE6, of course), then there's something wrong in the way you are putting the site together.

For example the issues you are having could be caused by relying on text taking a certain space, which isn't true as all platforms have different default fonts and render them a bit differently. Not to mention that every user can have set a different default font size in their browser...

If you only care about the site working for Windows users (as opposed to everyone) then your best option of course is to just develop it on Windows. You really can't get stuff like font rendering to work like it does on another platform.

---

### Post by jcolyn on 2010-11-04
Windows regardless of browser is somewhat forgiving where html
errors are made. With that in mind notice you have a "/div"
break but no "<div>" at the beginning of the text. Could this be 
your problem? It could also be the font size set in your CSS file.
You may need to create a "div" just for this text.

Edit: On second thought your problem could be the font size in the html..
The first line is h1, second line is h2 and the third line is h3. Try setting all 
three lines h2 and see what happens

</div>



<h1>bespoke floating shelves</h1>

<h2>tel: 020 8876 2762</h2>

<h3>get creative&hellip;</h3>
                
            

        <!--END #header-->
        </div>

---

### Post by kuckie on 2010-11-05
Mainly the fonts behave differently. Display of css formated stuff should look the same, however the font formating can also break the layout, if your divs are at dynamic size, meaning the font/content inside will define the size: different font sizes -> different div sizes. 

Did you install the mst-corefonts? This helps a little.

I cant agree with jcolyn on fault tolerance, there should be no difference between windows firefox and linux firefox. However, even though they use the same html rendering engine, they were coded for different platforms and there might be some glitches. But dont wanna argue about that.

IE6 is not the only browser displaying valid html/css completely incorrect, IE7 does it too at some points (display: inline-table e.g.) and can be a pain-in-the-a...

I also noticed the 1-pixel-of-pain-problem on ubuntu browsers mainly on margins, but it seems to be platform wide, occuring in all ubuntu browsers (may have to do with fonts too).

Conclusion?
1 year after switching from windows to linux there hasnt been another solution than installing XP in the virtualbox and adjusting css to the browsers there. :(

---

### Post by jcolyn on 2010-11-05
> **kuckie said:**
> 
I cant agree with jcolyn on fault tolerance, there should be no difference between windows firefox and linux firefox. However, even though they use the same html rendering engine, they were coded for different platforms and there might be some glitches. But dont wanna argue about that.

I write all of my html in Bluefish on Mint then test it across platforms and browsers. I have yet to see different rendering between any.

The OP wrote his html using xhtml strict which is less forgiving than plain html which can cause issues if he makes syntax errors..

> **kuckie said:**
> Conclusion?
1 year after switching from windows to linux there hasnt been another solution than installing XP in the virtualbox and adjusting css to the browsers there. :(

If you know proper syntax you shouldn't have to make adjustments. Many html editors allow for checking proper syntax before posting your file online..

---

### Post by mcduck on 2010-11-05
> **jcolyn said:**
> 
If you know proper syntax you shouldn't have to make adjustments. Many html editors allow for checking proper syntax before posting your file online..
+1 to this. And there's always [http://browsershots.org/]("http://browsershots.org/") if you want to check how your site looks in different browsers.

---

