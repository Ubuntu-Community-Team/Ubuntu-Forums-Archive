---
title: "web design question????????"
date: 2007-06-02
forum: Art &amp; Design
---

### Post by ninjaprawn on 2007-06-02
hi,

ive just started using Nvu, to build my site! its brilliant so far! 1 problem tho, if i want to put an advert or hit counter or some other html code from another site, i cant!

it pastes in, but gives no effect! ive used insert | html and that puts the html code where i want it, but the ad doesnt display!

for example, i signed up for google adsense, and the ads work in normal html code, but trying to put them into Nvu does nothing to the page!!!!

thanks!

[http://ninjaprawn.myby.co.uk](http://ninjaprawn.myby.co.uk)

---

### Post by Znupi on 2007-06-02
Why oh why do you use Nvu? Wysiwyg editor are pure evil... really.

---

### Post by JordanII on 2007-06-02
Did you use the tags ""?

~Jordan

---

### Post by ninjaprawn on 2007-06-02
how do u mean, tags? i went insert | html and copied the code exactly as it was shown, pasted into the insert | html box, and pressed insert, then i went to view the source code, and it was there, but in normal view, there is no advert. for example, on my site there is an advert source code at the very top! but there is no advert! not matter where i put the code, it makes no difference!
the page is [http://ninjaprawn.myby.co.uk/code.html](http://ninjaprawn.myby.co.uk/code.html) pull up the source code in your browser and see, it looks right, but nothing is displayed!!!

thanks

---

### Post by Znupi on 2007-06-02
I really think that this:
```

<script type="text/javascript" [color=red]src="show_ads.js"[/color]>

```
is wrong. The show_ads.js file is on google's servers, not yours.

---

### Post by ninjaprawn on 2007-06-02
i changed that to waht it should be directly on the server, and all the formatintg went from the page entirely! and still the ad wont display!!!

---

### Post by PilotJLR on 2007-06-02
At the top of your html file, try replacing this:
```

  <script><endnote><head>
<script></script>

```

with just this:
```

<head>

```

The other tags are not closed properly and could trip up most browsers.

---

### Post by JordanII on 2007-06-02
> **ninjaprawn said:**
> how do u mean, tags? i went insert | html and copied the code exactly as it was shown, pasted into the insert | html box, and pressed insert, then i went to view the source code, and it was there, but in normal view, there is no advert. for example, on my site there is an advert source code at the very top! but there is no advert! not matter where i put the code, it makes no difference!
the page is [http://ninjaprawn.myby.co.uk/code.html](http://ninjaprawn.myby.co.uk/code.html) pull up the source code in your browser and see, it looks right, but nothing is displayed!!!

thanks

[HTML]your HTML code goes here[/HTML]

~Jordan

---

### Post by Znupi on 2007-06-02
Right now it seems you removed the script completely...

---

### Post by Psicolonia on 2007-06-03
this may sound wierd comming from an unubntu user. I write a lot of code manually, and even thoug Macromedia Dreamweaver is a wysiwyg (sometimes) i still think it's the best. It runs perfectly on wine. Search for how to install it in ubuntu. It's worth it. It costs less then $60. You'll never you NVU again, NVU has been dead for more then one year and a half...

---

### Post by Znupi on 2007-06-03
Dreamweaver has the option of wysiwyg editing. Just giving you this option is a bad thing (in my opinion). If you want to code yourself, I recommend gedit, or if you can't live with that, here's a much better one: [UltraEdit-32](http://ultraedit.com). That's what I use, and it runs well under wine (not perfect). In my opinion, it's the best you can get. Many people I know use it, for HTML, PHP, JS, CSS, etc...

---

### Post by JordanII on 2007-06-03
I was trying to post the tags, but it isn't working. It's reading the tags as HTML. :)

---

### Post by RJQ on 2007-06-03
Try to paste the code directly in the "code view" and save, if you really like this program I recomend the "composer" in SeaMonkey instead of NVU, screem is also little bit better, but if you are use to write any other code language then HTMLKit is for you, the best I have been used so far for HTML and CSS, and still free I guess,  (you need wine for this) now if you like wysiwyg editor why not use google page creator? they have quite a basic editor mostly visual for an average site.

---

### Post by ninjaprawn on 2007-06-07
thanks for all this advice, in the end, i gave up with the wizzy wig's, changed the site slightly, and added the ad's with gedit! im going to try something like bluefish or cssed. i did learn quite a bit from nvu, as i am completly new to html, and css, i just wanted something easy to start me off, nvu did that. thanks!

---

### Post by durand on 2007-06-08
I use bluefish, love it. :D

---

### Post by tturrisi on 2007-06-09
your google ads are there, scroll to the right!
The table you have is over 1200 pixels wide.  Bad form.  Design the layout so it will fit in majority of screen resolutions.  Change the tables to:
<table style="text-align: left; width: 100%;

---

### Post by ninjaprawn on 2007-06-10
im going to change the site completly when i get chance, im not going to upload, or change the site till i have it right this time tho!

thanks for everyone advise! i learned a bit from using the wissy wig, im just reading how to use css properly now, and trying both cssed and bluefish to see which i prefer!

i put the ads there using gedit!

---

### Post by durand on 2007-06-10
Um, bluefish can do css, you know

---

### Post by notwen on 2007-06-10
+1 bluefish, made my site entirely w/ bluefish.  fun stuff

---

### Post by ninjaprawn on 2007-06-10
i know that both bluefish and cssed are very similiar! im using both at the minute, just getting the feel of both of them till i figure out which 1 i prefer!

fun times!!!!! ive bin more interested in transfering files from my nokia 7610 over the last few days, but that sorted now with obex, so back to putting all my time to learning html, css, and im thinking of learning a language!!! looked at python, and it looks ok, but thinking c/c++ or java would be more my thing!

thanks!

---

### Post by durand on 2007-06-11
Um, what do you mean by cssed? Im totally confused. CSS is a language like html, used for layout design and styling your pages. I don't get what you mean by "cssed"

---

### Post by ninjaprawn on 2007-06-11
cssed is software similiar to bluefish! i installed it from add/remove in the applications menu! [http://cssed.sourceforge.net/](http://cssed.sourceforge.net/) this is the page where there is info on it! i like it, i only tried bluefish for a short while, but i now prefer cssed! my page has now been re-made with it! [http://ninjaprawn.myby.co.uk](http://ninjaprawn.myby.co.uk) is my site!  it has an external .css file, and after never typing any source for web pages, i learned how to use css from [http://www.w3schools.com/css/default.asp](http://www.w3schools.com/css/default.asp) ,  my site is very simple again, but a bit better technically!

---

### Post by airtonix on 2007-06-11
you guys know that GEDIT is now same as dreamweaver minus the wysiwyg and group edit control?

it has : 
+ filebrowser sidebar
+ project sidebar
+ API broswer sidebar
+ dynamic templates insert via keyword+TAB
+ plugin system
+ code colouring
+ auto indentation  ( & manual with TAB and SHIFT + TAB )
 + code insertion (alt+space when in code motions.)

dosent have : like (psPad)
 + format and cleanup html code(makes source code neat and tidy)
 + code folding decrease scrolling through large documents.(just like you do with insanly large folder trees)
  
Also remeber peoples a native gnome feature is that you can make a new documents by dragging bits of highlighted text and dropping the block onthe desktop, it will become a file waiting for you to rename it.
Or... quicker from inside gedit... you can : ctrl+n -> ctrl + v (this makes the doc save under current folder context of other opend files or last opened doc.

tips: keep your languages in seperate files (css, js, html) this makes for faster file processing, for there is nothing worse than : 
- waiting five minutes for the screen to update on a five billion coloumn file.(mootools anyone)
- having uncoloured javascript syntax nested inside coloured html syntax

also cssed is only for css files. if your only using this program for having the list of css commands listed their infront of you, i remind you that typing "font-f" then ALT+space will list all possible commnads that start with "font-f". ie "font-family"

ps.s. css is source too baby! all your sources are mine.

blah.

---

### Post by ninjaprawn on 2007-06-11
cssed does html aswell as css, and from trying bluefish, gedit and cssed, in my complete nOOb opinion, cssed makes me feel more comfortable using it! but thats me, im happy cool! just need to comit as much css and html to memory as possible! good fun tho!

---

