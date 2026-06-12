---
title: "[SOLVED] Kompozer - How can I edit / publish my wife's page"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by crjackson on 2008-01-05
Okay,

I made this web page using FrontPage.  I want to redo the site using kompozer but it won't let me do anything to the page.

Can someone point me in the right direction on this?
[URL="http://home.carolina.rr.com/crjackson/"]
Joy's Quilting Sensations[/URL]

---

### Post by Samhain13 on 2008-01-05
Are you trying to open the page that contains the frameset or one of the pages that the frameset loads?

I haven't used Kompozer and haven't seen FrontPage for a very long time. But I suspect that if you're opening the frameset page and for some reason, the involved pages cannot be found, then either program will give you an error.

---

### Post by crjackson on 2008-01-05
I'm trying to open the index.html which does contain frames.  I just booted to XP and it works fine in Front Page.  I can't seem to open the site AT ALL using Kompozer.

---

### Post by Samhain13 on 2008-01-05
I'll install Kompozer and see what there is to see there. I'll get back to you. :)

[edit]
It seems Kompozer doesn't like framesets. But you should be able to open and edit the framed pages by themselves.

...on second thought:
when opening [http://home.carolina.rr.com/crjackson/](http://home.carolina.rr.com/crjackson/) from Kompozer, I get an alert saying, "This page can't be edited for some unknown reason." But the page, frameset and all appears correctly.

And the alert is most probably because I do not have permissions to edit the contents of that website. So in this case, Kompozer merely functions as a browser rather than as an editor.

---

### Post by FreewheelinFrank on 2008-01-05
What Front Page is probably allowing you to do is edit the page on the website.

I don't know if you'll be able to do this in Kompozer: you may have to edit the HTML code on your computer in Kompozer, then upload the index.html file to your web host.

You may need to use a FTP program like FileZilla to do this: you'll need your host name (ftp.yourISP.com or similar), username and password to do this.

---

### Post by CanonKen on 2008-01-05
I've just tried it in Komposer and says "this file can't be edited for an unknown reason"
I tried one of the other pages and that works fine, [THIS]("http://home.carolina.rr.com/crjackson/quillows.htm") is the one that worked

---

### Post by CanonKen on 2008-01-05
The link you posted doesn't end in .html just jackson/

---

### Post by Samhain13 on 2008-01-05
[edit]
Follow up to the permissions post I made above:

Ok, here's what you can do:

1. on the "Site Manager" secton (left side), click on the Edit Sites icon (the thing at the left side showing two computers)
2. enter your login and FTP details (screenshot included), click OK when done
3. the site should then appear in the box at the left side
4. click on the + sign beside the site's name to expand the directory, this may take a while

The other screenshot shows my site and the expanded directory to the left.

Now you should not be getting the error any more, unless the application really doesn't want anything to do with framesets. Cheers! :)

---

### Post by crjackson on 2008-01-05
> **Samhain13 said:**
> I'll install Kompozer and see what there is to see there. I'll get back to you. :)

[edit]
It seems Kompozer doesn't like framesets. But you should be able to open and edit the framed pages by themselves.

...on second thought:
when opening [http://home.carolina.rr.com/crjackson/](http://home.carolina.rr.com/crjackson/) from Kompozer, I get an alert saying, "This page can't be edited for some unknown reason." But the page, frameset and all appears correctly.

And the alert is most probably because I do not have permissions to edit the contents of that website. So in this case, Kompozer merely functions as a browser rather than as an editor.

Well, I don't think it's a permissions issue.  It doesn't prompt for username/password.  I get the same thing, and I can provide credentials.

---

### Post by crjackson on 2008-01-05
> **FreewheelinFrank said:**
> What Front Page is probably allowing you to do is edit the page on the website.

I don't know if you'll be able to do this in Kompozer: you may have to edit the HTML code on your computer in Kompozer, then upload the index.html file to your web host.

You may need to use a FTP program like FileZilla to do this: you'll need your host name (ftp.yourISP.com or similar), username and password to do this.

No, it won't let me even publish a test page.  I already tried that.

---

### Post by crjackson on 2008-01-05
> **Samhain13 said:**
> [edit]
Follow up to the permissions post I made above:

Ok, here's what you can do:

1. on the "Site Manager" secton (left side), click on the Edit Sites icon (the thing at the left side showing two computers)
2. enter your login and FTP details (screenshot included), click OK when done
3. the site should then appear in the box at the left side
4. click on the + sign beside the site's name to expand the directory, this may take a while

The other screenshot shows my site and the expanded directory to the left.

Now you should not be getting the error any more, unless the application really doesn't want anything to do with framesets. Cheers! :)

Okay, trying now...

---

### Post by crjackson on 2008-01-05
It's been trying for an hour now with negative results.

---

### Post by crjackson on 2008-01-05
Still no luck, have a look.

---

### Post by crjackson on 2008-01-05
Alright, does anyone know of a tool that can get the job done for me?  I REALLY don't want to turn to windows for this task.

---

### Post by FreewheelinFrank on 2008-01-06
Your web host seems to be geared to FrontPage, and you may not be able to edit files directly using Kompozer. (I was interested to see that Kompozer does have this function as Samhain13 described above- I'm quite new to Kompozer.) FrontPage works with some special directories on the host and Kompozer is unlikely to be able to work with these directories in the same way.

[http://home-admin.rr.com/help/faqMS.php](http://home-admin.rr.com/help/faqMS.php)

However, your host does allow you to upload files by FTP- see the FTP link here:

[http://home-admin.rr.com/help/](http://home-admin.rr.com/help/)

Simply save the pages you want to work on in Firefox, edit in Kompozer and upload via FTP.

This way of editing pages is not tied to any HTML editing program, operating system or particular FTP program.

Pages created with FrontPage may depend on FrontPage support provided by the host server (and they're also designed to work in IE and often don't work so well in other browsers) so you might be better off starting the page from scratch in more standards-compliant code.

There are lots of free templates available, for example here:

[http://www.dynamicdrive.com/style/layouts/category/C9/](http://www.dynamicdrive.com/style/layouts/category/C9/)

---

### Post by Samhain13 on 2008-01-06
> **crjackson said:**
> It's been trying for an hour now with negative results.
Right. When I tried it last night, Kompozer also wasn't able to connect. I had to change the entry I supplied in the **Publishing Address** field. Originally, it was like this:

> ftp:// ftp.abcruz.com/

That _didn't_ connect. So I tried this:

> ftp.abcruz.com

That's when I was able to connect and do a test edit in one of my files. Note that I removed the leading **ftp://**, and that I have no "/myusername" folder because I have access to the top-level directory of the site.

If this still doesn't work, perhaps you should call your hosting service provider for more information on the proper settings as they may vary from hosting service to hosting service.

---

### Post by crjackson on 2008-01-06
> **Samhain13 said:**
> Right. When I tried it last night, Kompozer also wasn't able to connect. I had to change the entry I supplied in the **Publishing Address** field. Originally, it was like this:



That _didn't_ connect. So I tried this:



That's when I was able to connect and do a test edit in one of my files. Note that I removed the leading **ftp://**, and that I have no "/myusername" folder because I have access to the top-level directory of the site.

If this still doesn't work, perhaps you should call your hosting service provider for more information on the proper settings as they may vary from hosting service to hosting service.

Publish isn't working at all.  I'm having to edit the page locally and then use an ftp program to upload the page.  I can't edit the framed index.htm at all, so I'm building a new one with tables instead of frames.  

My next problem is my buttons.  I don't know how to make it load the alternate image when the mouse rolls over it (gives the effect of a black border around the box - looks animated).

---

### Post by Samhain13 on 2008-01-06
> Publish isn't working at all. I'm having to edit the page locally and then use an ftp program to upload the page.

This is actually the prefered method if you're someone who thinks that keeping backups is a good thing. :)

As to doing away with the frames, it's also a good thing. But substituting tables for it will not make it any better. If you like, I can make a simple template for you using no tables and formatted with only CSS. With CSS, we can also solve your roll-over problems.

Or I can just post code here as we go along?

---

### Post by crjackson on 2008-01-06
> **Samhain13 said:**
> This is actually the prefered method if you're someone who thinks that keeping backups is a good thing. :)

As to doing away with the frames, it's also a good thing. But substituting tables for it will not make it any better. If you like, I can make a simple template for you using no tables and formatted with only CSS. With CSS, we can also solve your roll-over problems.

Or I can just post code here as we go along?

It's really an exercise in learning for me.  I'm trying to learn HOW to do tings in Linux.  If you think I would learn better from a template then that would be great.  If code would be more educational than that would be great too.

CSS is something I know nothing about.

Thanks

btw, I actually did get kompozer to connect to the site trying various ftp lines.  It seems it CAN edit some pages directly but not all.  It's my practice to to create the site off-line and then publish it.  When using Front Page, simply uploading via ftp won't work due to Front Page Extension being enabled.  I want to achive the same effect without using Front Page and it's extension.  I do realize I probably won't be able to duplicate or approximate the hit counter, so I'll probably just do away with that, unless this too can be done using CSS

---

### Post by crjackson on 2008-01-06
> **FreewheelinFrank said:**
> Your web host seems to be geared to FrontPage, and you may not be able to edit files directly using Kompozer. (I was interested to see that Kompozer does have this function as Samhain13 described above- I'm quite new to Kompozer.) FrontPage works with some special directories on the host and Kompozer is unlikely to be able to work with these directories in the same way.

[http://home-admin.rr.com/help/faqMS.php](http://home-admin.rr.com/help/faqMS.php)

However, your host does allow you to upload files by FTP- see the FTP link here:

[http://home-admin.rr.com/help/](http://home-admin.rr.com/help/)

Simply save the pages you want to work on in Firefox, edit in Kompozer and upload via FTP.

This way of editing pages is not tied to any HTML editing program, operating system or particular FTP program.

Pages created with FrontPage may depend on FrontPage support provided by the host server (and they're also designed to work in IE and often don't work so well in other browsers) so you might be better off starting the page from scratch in more standards-compliant code.

There are lots of free templates available, for example here:

[http://www.dynamicdrive.com/style/layouts/category/C9/](http://www.dynamicdrive.com/style/layouts/category/C9/)

Using the last link.  I tried to cut/paste the CSS and HTML code for some replacement buttons.  I couldn't figure out exactly where to paste the CSS code.  I obviously need some guidance with regards to CSS.

---

### Post by Samhain13 on 2008-01-07
> It's really an exercise in learning for me. I'm trying to learn HOW to do tings in Linux. If you think I would learn better from a template then that would be great. If code would be more educational than that would be great too.

CSS is something I know nothing about.

I guess a good way of looking at it is: HTML, or your basic web page, is supposed to be platform-independent. It has to work regardless of what operating system or physical machine you're using for viewing or for making it. But from experience (not to mention this situation we have here), it's the tools with which HTML is made and with which the website is maintained that cause a bit of trouble so that I'm left with the impression that writing it "by hand", as they say, is the best way to go.

There are lots of tutorials available in the Web about how to write HTML code. And it's really a very intuitive language so that it's every easy to understand. But in hoping to point you to the right direction, let me just say that:

HTML is your web page, or your web pages. The language is simply for identifying the stuff/contents that are contained in those pages like headings, paragraphs, lists, and so on, so that browsers will know what they are and how to deal with them.

CSS, on the other hand, is the language we use to tell the browser how to present those contents; telling it what the prefered typeface is for paragraphs, for example; or what parts of the page goes to the left  and what goes to the right. There are three ways with which to use it with your HTML-- but let's not get into that here as that's probably one of the first things you'll learn anyway from the many tutorials available in the Web.

But before I bore you, here's a way with which we can make something like your page (without the background images). You can copy the code below, paste it in a text editor and save it as "test.html", and open the file in a browser.

[HTML]
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

  <head>

    <title>Joy's Quilting Sensations</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    
    <style type="text/css">
        body {
          font-family : sans-serif ;
          font-size : 62.5% ;
          margin : 0px ;
          padding : 0px ;
        }
        
        h1 {
          color : rgb(200,0,0) ;
          font-size : 3em ;
          margin : 50px 0px ;
          text-align : center ;
        }
        
        p {
          font-size : 1.2em ;
          margin-left : 50px ;
          margin-right : 50px ;
        }
        
        #myLinks {
          font-size : 1.2em ;
          float : left ;
          list-style-type : none ;
          margin : 20px 0px 0px 10px ;
          padding : 10px 0px ;
          text-align : center ;
          width : 150px ;
        }
        
        #myLinks li {
          display : inline ;
          margin : 0px ;
          padding : 0px ;
        }
        
        #myLinks a:link, #myLinks a:visited {
          background : rgb(150,200,250) ;
          border-bottom : 2px rgb(100,100,100) solid ;
          border-top : 2px rgb(100,100,100) solid ;
          color : rgb(0,0,0) ;
          display : block ;
          margin-bottom : 5px ;
          padding : 10px 5px ;
          text-decoration : none ;
        }
        
        #myLinks a:active, #myLinks a:focus, #myLinks a:hover {
          background : rgb(200,0,0) ;
          border : 2px rgb(0,0,0) solid ;
          color : rgb(255,255,255) ;
        }
        
        #right {
          margin-left : 170px ;
        }
    </style>
    
  </head>

  <body>
    
    <ul id="myLinks">
      <li><a href="#">Quillows</a></li>
      <li><a href="#">Quilts</a></li>
      <li><a href="#">Home</a></li>
    </ul>
    
    <div id="right">
      
      <h1>Joy's Quilting Sensations</h1>
      
      <p>Welcome to Joy Jackson's home of Quilting Sensations.  We are a new website so please check back often for new updates.  You will find many quillow products, and we are striving to add more each week.  Thank you for visiting, and please sign our guest book, or leave an email for Joy.</p>
      
    </div>
    
  </body>

</html>
[/HTML]

Note that the CSS is everything that appears between <style type="text/css"> and </style>. The code may look arcane at first but mangle it for a few days and do some casual browsing from, for example [http://www.htmldog.com/](http://www.htmldog.com/), and it's going to make a lot more sense.

Here are a few more sites that you can go to:
[http://www.w3schools.com/html/](http://www.w3schools.com/html/)
[http://www.html.net/tutorials/](http://www.html.net/tutorials/) (more basic stuff)
[http://www.csscreator.com](http://www.csscreator.com) (if you have questions about CSS)

Cheers and good luck. :)

---

### Post by FreewheelinFrank on 2008-01-07
I'd suggest you experiment with a two column layout like this one first. It has the same format as the existing page. You can just use links in the left hand column and get the site up and running.

[http://www.dynamicdrive.com/style/layouts/item/css-left-frame-layout/](http://www.dynamicdrive.com/style/layouts/item/css-left-frame-layout/)

Search for the example text in the source code and replace it with your text.

CSS Left Frame Layout

CSS Left Frame Layout

You can also use CSS to apply the background images you want.

With CSS, you can separate the CSS file from the page code, so you can apply it to any page. If you do this, writing the other pages for your site will be a lot easier.

There are many CSS tutorials available on the web. 

I don't know how Kompozer works, but Dreamweaver allows you to open and edit the CSS files for a page you are working on: Kompozer may well have the same function.

When you have the pages set up and the links working, the next step will be to create buttons for the link.

Again you can do this by substituting your text and hyperlinks in the template source code.

Example here:

[http://www.dynamicdrive.com/style/csslibrary/item/wire-frame-menu/](http://www.dynamicdrive.com/style/csslibrary/item/wire-frame-menu/)

If you have problems, we can help you out here.

---

### Post by crjackson on 2008-01-07
> **Samhain13 said:**
> I guess a good way of looking at it is: HTML, or your basic web page, is supposed to be platform-independent. It has to work regardless of what operating system or physical machine you're using for viewing or for making it. But from experience (not to mention this situation we have here), it's the tools with which HTML is made and with which the website is maintained that cause a bit of trouble so that I'm left with the impression that writing it "by hand", as they say, is the best way to go.

There are lots of tutorials available in the Web about how to write HTML code. And it's really a very intuitive language so that it's every easy to understand. But in hoping to point you to the right direction, let me just say that:

HTML is your web page, or your web pages. The language is simply for identifying the stuff/contents that are contained in those pages like headings, paragraphs, lists, and so on, so that browsers will know what they are and how to deal with them.

CSS, on the other hand, is the language we use to tell the browser how to present those contents; telling it what the prefered typeface is for paragraphs, for example; or what parts of the page goes to the left  and what goes to the right. There are three ways with which to use it with your HTML-- but let's not get into that here as that's probably one of the first things you'll learn anyway from the many tutorials available in the Web.

But before I bore you, here's a way with which we can make something like your page (without the background images). You can copy the code below, paste it in a text editor and save it as "test.html", and open the file in a browser.

Note that the CSS is everything that appears between <style type="text/css"> and </style>. The code may look arcane at first but mangle it for a few days and do some casual browsing from, for example [http://www.htmldog.com/](http://www.htmldog.com/), and it's going to make a lot more sense.

Here are a few more sites that you can go to:
[http://www.w3schools.com/html/](http://www.w3schools.com/html/)
[http://www.html.net/tutorials/](http://www.html.net/tutorials/) (more basic stuff)
[http://www.csscreator.com](http://www.csscreator.com) (if you have questions about CSS)

Cheers and good luck. :)

Thanks, that was pretty slick.  I'll chop this up and play around with it until I figure out what makes it tick, and how to make it tock for me.  BTW it doesn't display correctly in KompoZer but looks fine in a browser.

---

### Post by crjackson on 2008-01-07
> **FreewheelinFrank said:**
> I'd suggest you experiment with a two column layout like this one first. It has the same format as the existing page. You can just use links in the left hand column and get the site up and running.

[http://www.dynamicdrive.com/style/layouts/item/css-left-frame-layout/](http://www.dynamicdrive.com/style/layouts/item/css-left-frame-layout/)

Search for the example text in the source code and replace it with your text.

CSS Left Frame Layout

CSS Left Frame Layout

You can also use CSS to apply the background images you want.

With CSS, you can separate the CSS file from the page code, so you can apply it to any page. If you do this, writing the other pages for your site will be a lot easier.

There are many CSS tutorials available on the web. 

I don't know how Kompozer works, but Dreamweaver allows you to open and edit the CSS files for a page you are working on: Kompozer may well have the same function.

When you have the pages set up and the links working, the next step will be to create buttons for the link.

Again you can do this by substituting your text and hyperlinks in the template source code.

Example here:

[http://www.dynamicdrive.com/style/csslibrary/item/wire-frame-menu/](http://www.dynamicdrive.com/style/csslibrary/item/wire-frame-menu/)

If you have problems, we can help you out here.

Nice tool site.  I'd like to use some of the buttons there, but I've had no luck recreating them.

---

### Post by Samhain13 on 2008-01-08
> BTW it doesn't display correctly in KompoZer but looks fine in a browser.

That's always a possibility in any WYSIWYG application, that's why I don't use them. The important this is that it displays correctly in as many browsers as possible. :)

---

### Post by FreewheelinFrank on 2008-01-08
> **crjackson said:**
> Nice tool site.  I'd like to use some of the buttons there, but I've had no luck recreating them.

Worked for me. See the page I bodged together below.

Bear in mind that there are two parts to the menu.

The CSS code has to be added to the following section:

```
 
<style type="text/css">
.
.
.
</style>

```

The HTML code is added where you remove the example text in the left hand column:

> CSS Left Frame Layout
Sample text here

This menu also requires two .gif images which I put in the same directory as the HTML file:

```
background-image: url(glossyback2.gif);
```

So I changed the image location from that in the original template.

```
background-image: url(media/glossyback2.gif);
```

I also put in your background images to the CSS for #framecontent and #maincontent (the two columns) and added your wife's picture, as well as adding the text from your site.

(Note I deleted a Javascript which generates example text.)

If you open the page in Kompozer, you can click the CSS icon and edit background images etc. from there.

Here's the finished page:

[http://geocities.com/dontsurfinthenude/joysquiltingsensations.html](http://geocities.com/dontsurfinthenude/joysquiltingsensations.html)

Well, that's about the sum total of my web-design skills: my own site is just based on a slightly more complicated three-column layout I got from a template, with the addition of a few background images:

[http://geocities.com/dontsurfinthenude/blog.htm](http://geocities.com/dontsurfinthenude/blog.htm)

Hope this gives you some ideas.

---

