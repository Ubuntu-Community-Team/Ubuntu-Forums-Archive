---
title: "[SOLVED] Cluless Needs Tutorial on Basic Web Design."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2008-01-31
Hello. I am writing an article, and need to put a lot of photos in with the text. I need the text to wrap around the photo, leaving enough room for a caption. Right now, I am using Kompozer, but when i go into image properties, select appearance, and then text wrap, selecting wrap to right or left only allows one line to wrap. Is there a way to squeeze the photo into a paragraph like a newspaper in Kompozer? If not, what program can I use to do this easily? it would be great if I could just drag the photo (maybe even the caption too) around, and have the text rearrange itself to wrap the photo. Sorry I don't know the terminology of what I'm looking for. I know nothing of web design, and can't really study it right now. i just need to do this one thing by today or tomorrow. Any help is greatly appreciated. 
Thank you

---

### Post by emarkd on 2008-01-31
You'll probably have to use CSS to get that type of layout.  [Here's]("http://www.tizag.com/cssT/float.php") a decent-looking tutorial I found by googling.

---

### Post by coldstatue on 2008-01-31
Thank you, that's exactly what I need, but it looks like you have to have a class loaded on a server, and then refer to it in the HTML - is that correct? Or does the CSS code just go somewhere in the html, like the header. Sorry I'm so clueless and just asking when I could read up on CSS. I'm starting to get a little rushed because this is turning out to be more complicated than I had hoped. Sorry, can you explain how I use this? I mean, just if I need to learn a bunch of stuff about CSS and other files on the server, or can I still just make a self-contained HTML file that I can email to the site?

Thank you

---

### Post by emarkd on 2008-01-31
There are no classes.  The simplest but messiest way to do this would be to code the CSS inline with the HTML.  [Here's]("http://www.tizag.com/cssT/inline.php") an inline CSS tutorial from the same site.

---

### Post by coldstatue on 2008-01-31
EDIT - ok thanks that is great. forget the text below. I was editing and stuff while you were posting. thanks a bunch. That will work perfect.



Also, what about captions? I seem to remember using a pirated version of Dreamweaver (or some other popular software) a while back that allowed me to write a caption for a photo, and the caption went with the pic wherever i dragged it, with the text auto-wrapping. Still, the css would be fine, I've just got to get started on some solution.

---

### Post by emarkd on 2008-01-31
I've never used Dreamweaver.  If by caption you're referring to the text that appears when you hover over with your mouse, you do that with the 'alt' tag.

---

### Post by coldstatue on 2008-01-31
I meant the photo credit that sits under the image - centered on the image, maybe a diff font than the article.

---

### Post by coldstatue on 2008-01-31
BTW - I am using that site, and it's working great. I'm using the html version to compose an email for the editor. The webmaster can deal with getting it right ion the site, I just need to submit it in a way that shows where the photos belong in the text.

Thanks for all your help. I was starting to panic about time there for a sec.

---

### Post by emarkd on 2008-01-31
Dreamweaver must have made that for you out of basic html elements.  If the CSS is too involved for you, you may be able to get decent results just using tables.  That's assuming that you don't have much text below each image.

---

### Post by coldstatue on 2008-01-31
I don't - just a photo credit

---

### Post by erfahren on 2008-01-31
there's a tutorial here that shows how to float an image with a caption step by step [Tutorial 2. Floating an image and caption](http://css.maxdesign.com.au/floatutorial/index.htm)
this page has all the CSS and HTML code of the tutorial laid out: [http://css.maxdesign.com.au/floatutorial/tutorial0211.htm](http://css.maxdesign.com.au/floatutorial/tutorial0211.htm)

note: not sure is it was mentioned - but you can put the CSS code in style tags in the head of the document (between the <head> tags) like this:
```

<head>
stuff here
stuff here
<style>
.floatright
{
float: right;
width: 103px;
margin: 0 0 10px 10px;
background-color: #fff;
padding: 10px;
border-top: 1px solid #999;
border-right: 2px solid #555;
border-bottom: 2px solid #555;
border-left: 1px solid #999;
}

div.floatright img
{
border-top: 2px solid #555;
border-right: 1px solid #999;
border-bottom: 1px solid #999;
border-left: 2px solid #555;
}

p { margin-top: 0; }
</style>
</head>

```

EDIT: oh, you marked it Solved now - I'll just leave that just in case - good luck!

---

### Post by emarkd on 2008-01-31
Well, if you just wanted to use tables, that would be pretty easy to do.  Something like:

```

<table>
    <tr>
        <td><img src="image1"></td>
        <td><img src="image2"></td>
        <td><img src="image3"></td>
    </tr>
    <tr>
        <td>Caption 1</td>
        <td>Caption 2</td>
        <td>Caption 3</td>
    </tr>
</table>

```

Of course, you'd have to go in and play with the spacing, alignment, etc.  [Here's]("http://www.tizag.com/htmlT/tables.php") some good info on that.

---

### Post by coldstatue on 2008-01-31
It's turning out well. Thanks a bunch - both of you. I'm playing around, trying to get it just how I want it. Trying both...

---

### Post by coldstatue on 2008-01-31
> **erfahren said:**
> there's a tutorial here that shows how to float an image with a caption step by step [Tutorial 2. Floating an image and caption](http://css.maxdesign.com.au/floatutorial/index.htm)
this page has all the CSS and HTML code of the tutorial laid out: [http://css.maxdesign.com.au/floatutorial/tutorial0211.htm](http://css.maxdesign.com.au/floatutorial/tutorial0211.htm)

note: not sure is it was mentioned - but you can put the CSS code in style tags in the head of the document (between the <head> tags) like this:
```

<head>
stuff here
stuff here
<style>
.floatright
{
float: right;
width: 103px;
margin: 0 0 10px 10px;
background-color: #fff;
padding: 10px;
border-top: 1px solid #999;
border-right: 2px solid #555;
border-bottom: 2px solid #555;
border-left: 1px solid #999;
}

div.floatright img
{
border-top: 2px solid #555;
border-right: 1px solid #999;
border-bottom: 1px solid #999;
border-left: 2px solid #555;
}

p { margin-top: 0; }
</style>
</head>

```

EDIT: oh, you marked it Solved now - I'll just leave that just in case - good luck!

Putting the css in the head tags clarifies it for me. I know a bit, but not much. Please leave it!!!! Guess I just did by quoting. You two are lifesavers

---

### Post by coldstatue on 2008-01-31
perfect.

Thank you!

---

