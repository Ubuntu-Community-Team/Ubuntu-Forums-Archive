---
title: "Firefox 3.5b4 PNG Rendering"
date: 2009-05-24
forum: Art &amp; Design
---

### Post by trench.me on 2009-05-24
Everything is fine when viewing a png at full-size, obviously, but if you drop the image size using a percentage in your stylesheet  (i.e, img {width: 25%; height: 25%}) the rendering is horrible. Anybody know why this is? 

Haven't tried this with jpg or gif, but I'm, guessing if it's happening at a png level it's definitely happening on the other image types. 

Png's should be safe from this behavior, I would think.

Edit: [Example page.]("http://www.trench.me/png_example/") I'm not sure if this is a browser issue, a CSS issue, a PNG issue, or (doubtful) a hardware issue.

I understand what's happening and why it's happening, but the question is ***should it be happening?***

---

### Post by trench.me on 2009-05-24
Bumping because of the edit.

---

### Post by trench.me on 2009-05-24
[The page]("http://www.trench.me/png_example/") now has screenshots. This is definitely a bug. And it seems to be Ubuntu's bug. 

It's really bad. And that's an understatement.

As a friend said... "it looks like IE 6".

Yes.  Yes it does.

---

### Post by hessiess on 2009-05-25
Its called nearest neighbour interpolation;) It is used as it is faster than bilinear filtering, basically don't scale images with CSS if you can avoid it. You would have better luck complaining to the Firefox developers, rather than on a Linux distro support forum;)

---

### Post by trench.me on 2009-05-25
Right. ;)

The intent wasn't to "complain" on a Linux distro support forum. Rather, the intent was to notify a group of people I thought would be interested in the issue. Or "said complaint". If no one in the art/design section of the Ubuntu support forum cares that CSS-scaled images render like IE 6 - on the Current and Beta Firefox releases within the Current Ubuntu environment, no less - then yeah, my bad. Totally. 

I've been running through Mozilla bug reports since yesterday in spare time to see if this is already reported, so I'm definitely trying to take care of it on that end as well. \\:D/

As for *"don't scale images in CSS if you can avoid it"*, that's ridiculous. If one plans on reusing a preloaded image (especially a PNG) several times and needs smaller versions of it throughout a page or series of pages, scaling is the logical way to go. And we're trying to stay logical about the use of our nearest neighbour interpolations, yes?

Honestly, your "It is used as it is faster than bilinear filtering, basically don't scale images with CSS if you can avoid it." quote reads like a teamDev-MSIE "What to Say if Asked" company memo.

But I'm cool with that.

If you are ;)

---

### Post by zgornel on 2009-05-26
> **hessiess said:**
> Its called nearest neighbour interpolation;) It is used as it is faster than bilinear filtering, basically don't scale images with CSS if you can avoid it. You would have better luck complaining to the Firefox developers, rather than on a Linux distro support forum;)

Technically, if you scale down an image no interpolation is involved (you interpolate between known pixels). The errors come from the fact that nu blurring is done before subsampling thus high frequency info is lost.

---

### Post by joshdudeha on 2009-05-27
its fine on my mac on firefox

---

### Post by mcduck on 2009-05-27
> **trench.me said:**
> 
As for *"don't scale images in CSS if you can avoid it"*, that's ridiculous. If one plans on reusing a preloaded image (especially a PNG) several times and needs smaller versions of it throughout a page or series of pages, scaling is the logical way to go. And we're trying to stay logical about the use of our nearest neighbour interpolations, yes?

No, it's not ridiculous. You shouldn't scale images using CSS, HTML or any other markup language. If you do that, you just have to accept that your web pages might load slowly, and look bad.

Always create versions of your images in every size you use. If you code with PHP you can use Imagemagick to automatically generate different image sizes. Or if you don't, you could still use Imagemagick to generate the images on your computer beforehands.

Using single image and scaling it with CSS/HTML is pure laziness.

---

### Post by trench.me on 2009-05-27
> **mcduck said:**
> Using single image and scaling it with CSS/HTML is pure laziness.

Wrong. It's called thinking about downloaded data to the Nth degree. Once an image is cached, it's cached. It can then be reused as many times as you wish without any extra, unneeded, images to cache or download. This is why image-caching is a **good thing**, both for the web-developer as well as the end-user.

If you create numerous re-sixed images of ***the same image*** the page viewer has to download, and cache, each of those versions. That, sir, is ridiculous. 

Test your own theory. 

Using a single image create 50 CSS-Scaled versions of it and place them on a single page. Now, do the same thing with your "50 different versions of the same image". Ask yourself: "Which page is heavier?", "Which page loads quicker?", and "Why?".

This scenario is obviously ridiculous in-and-of-itself, but sometimes to explain the ridiculous one has to do the ridiculous. 

(Also note that Firefox, by default, automatically resizes images larger than the visible window (for example: [http://trench.me/ew/1.png](http://trench.me/ew/1.png) ). The way it's done, and the reason it's done, is out of logic - not laziness.)

---

### Post by trench.me on 2009-05-27
> **joshdudeha said:**
> its fine on my mac on firefox

Thanks for testing.

At this point I'm quite certain it's linux-specific. 

I'm convinced the issue lies within the Firefox-linux development team and has just gone unnoticed. Which is sad because this problem adds to the *"Linux just doesn't **look** good"* excuse that often comes from Win/Mac devotees. And it's why we in the Linux community need to take these issues seriously instead of shrugging them off.

---

### Post by mcduck on 2009-05-27
> **trench.me said:**
> Wrong. It's called thinking about downloaded data to the Nth degree. Once an image is cached, it's cached. It can then be reused as many times as you wish without any extra, unneeded, images to cache or download. This is why image-caching is a **good thing**, both for the web-developer as well as the end-user.

If you create numerous re-sixed images of ***the same image*** the page viewer has to download, and cache, each of those versions. That, sir, is ridiculous. 

Test your own theory. 

Using a single image create 50 CSS-Scaled versions of it and place them on a single page. Now, do the same thing with your "50 different versions of the same image". Ask yourself: "Which page is heavier?", "Which page loads quicker?", and "Why?".

This scenario is obviously ridiculous in-and-of-itself, but sometimes to explain the ridiculous one has to do the ridiculous. 

(Also note that Firefox, by default, automatically resizes images larger than the visible window (for example: [http://trench.me/ew/1.png](http://trench.me/ew/1.png) ). The way it's done, and the reason it's done, is out of logic - not laziness.)
How often would you really use 50 different sized versions of the same image on the same page? Or even 5? Honestly?

If you need, lets say 3, different sizes of the otherwise same image on the same page the file size is in most cases still neglible, but using separate images will look better as you can scale the images properly instead of having to rely on what ever scaling method the user's browser might use.

It's not theory, it's simply considering real-life situations in any normal page design. If you don't agree, please give me a link to even single page that has 50 versions of the same image each in different size. (and that isn't some kind of Frankenstein's monster of web design) :D

---

### Post by trench.me on 2009-05-27
Re: 50 images - You obviously missed the part of my comment where I said [I]**"This scenario is obviously ridiculous in-and-of-itself, but sometimes to explain the ridiculous one has to do the ridiculous"**

[/I]Now, if you need an example I'll gladly offer one up. 

Let's say you're using a bulletin board system of your own,  like vBulletin (which UbuntuForums is running on). You decide to add avatars for your users. They show up best in the forums, at the max, 150px x 150px. However, you decide that you'd like to offer themes for your user's profiles. Each user, you decide, could choose one of ten available profile themes. Wow, pretty cool, eh? In each of these differently designed profile themes the avatar is used differently. In one, it's the main focal point and works as an offset-header (e.g., it's large)... in another it's simply the regular forum size. It's at this point you realize you don't want users to be forced to create multiple copies of their own avatar, so you say to yourself - "Ah, I'll just let PHP do the work for them." And then it hits you. You have 20,000 active users. Potentially that's 20,000 new images at two to three times the current size of the already existing 20,000 avatars. "Damn," you would hopefully say, "that's a lot of unnecessary bandwidth that I'm going to have to pay for." And that's when (hopefully) logic hits you. "Wait," you shout, "**it's just a single image!**" And this is when you realize that image-caching is a blessing. You then decide to create your newly designed user profile themes with this in mind. Using a bit of math and a well-written style sheet, you are then able to allow your users to have larger images on their profiles (scaling them down when necessary, like for avatars in the forums) without slowing down your site or adding to your bandwidth costs. 

Awesome-dawson.

There are tons of other examples, but this is one I thought might be uniquely understandable given we are having this discussion on a bulletin board. :D

And, I believe we are missing the ultimate point: [B]In 2009, on Firefox, PNG's should not be pixelated upon size-reduction. 

Period.[/B]

;D

---

### Post by klange on 2009-05-27
The bug is a combination of X and Cairo far more than it is a bug in Firefox. While a workaround could (and probably should) be used, that isn't the case, and either way, Cairo and X are still at fault. I'll also note that it's the same bug that makes general zooming look horrible.

---

### Post by unc0nn3ct3d on 2010-09-21
Glad I'm not the only one that is annoyed by this.. However more so than a linux bug this appears to be a firefox bug as the same PNG looks perfect in Opera.  Re-enforcing my opinion that Opera is by far the best browser out there if it wasn't for the damn compatability issues and lack of plugins because it isn't open sourced.

---

### Post by DudeAlfred on 2011-04-14
I know it's an old thread, but I wanted to let you know that in Firefox 4.0, on Ubuntu 11.04beta the problem still exists. It's really a freaking pain, especially since it works fine in chromium on the same dist. And I'm really not gonna change all my design for one browser on one OS....But this should really be fixed, it looks like IE6 :-p

---

