---
title: "web design question."
date: 2008-08-22
forum: Art &amp; Design
---

### Post by hockey97 on 2008-08-22
Hi  I just created my website the buttons and logo ect.

I just notice on ie7 and firefox that it looks great Then I notice on ie6 that it would show where it's supposed to be apha like nothing I would see with.

I was woundering how can you get around that??? I used for the logo nothing but test and the rest around it is really nothing like it's no value not black or transparent but  it's like aplha transparent. It is done in a way where you supposed to just see the text. So when I saw it on ie6 I see white around all the text, then in ie7 I see the area transparent and dosen't show only shows text and where the white was for ie6 I can see in ie7 that it would show the website background no white.

---

### Post by AJB2K3 on 2008-08-22
Test it in Firefox/opera/konquror (sp?) to see if it ok.
IE is know for not following the rules for webdesign.
If you can get in correct in ff/O/KO then its correct, then you can move onto workingout what exactly IE is not doing to the site.
Come here [http://www.design.ersblock.com/forum/]("http://www.design.ersblock.com/forum/")and ask as it a dedicated web design site.

---

### Post by kostkon on 2008-08-22
> **hockey97 said:**
> Hi  I just created my website the buttons and logo ect.

I just notice on ie7 and firefox that it looks great Then I notice on ie6 that it would show where it's supposed to be apha like nothing I would see with.

I was woundering how can you get around that??? I used for the logo nothing but test and the rest around it is really nothing like it's no value not black or transparent but  it's like aplha transparent. It is done in a way where you supposed to just see the text. So when I saw it on ie6 I see white around all the text, then in ie7 I see the area transparent and dosen't show only shows text and where the white was for ie6 I can see in ie7 that it would show the website background no white.
IE6 does not support PNG alpha transparency.

---

### Post by lyceum on 2008-08-22
Check this out:

[http://www.pcmag.com/article2/0,2817,1645331,00.asp](http://www.pcmag.com/article2/0,2817,1645331,00.asp)

Let me know how it works out. I have no way currently to check sites with IE6.

---

### Post by hockey97 on 2008-08-22
Ok, yes when I tried it in firefox it works great and also ie7 it works great.

it's just ie6 that it would make the transparent areas white and looks very ulgy.

Well if I can't fix this problem, I am just going to make  a java script and  make a pop up window for ie6 users saying that you would need ie7 because Microsoft made a boo boo lol.

I will take a look at the links above thanks, I am really getting frustrated making my website I got this and also a display resolution problem.

I hope microsoft and other browsers make a plug-in or a new browser to be able to resize a website page to scale according to the clients resolution.

---

### Post by hockey97 on 2008-08-22
ok thanks it works now.


here is the code I have just in case anyone here gets into the same problem:

```
jQuery.fn.cssPNGFix = function(sizingMethod) {
  var sizingMethod = (sizingMethod) || 'scale';
  if($.browser.msie && parseInt($.browser.version) < 7) {
    $(this).each(function() {
      var css_bg_img = $(this).css('background-image');
      var bg_img = css_bg_img.substring(5, css_bg_img.length - 2);
      $(this).css({'background':'none', 'filter':'progid:DXImageTransform.Microsoft.AlphaImageLoader(src="' + bg_img + '", sizingMethod="' + sizingMethod + '")'});
    });
  };
  return $(this);
};

jQuery.fn.imgPNGFix = function(sizingMethod) {
  var sizingMethod = (sizingMethod) || 'scale';
  if($.browser.msie && parseInt($.browser.version) < 7) {
    $(this).each(function() {
      var spacer_src = Drupal.settings.spacer_src;
      var the_img = $(this);
      var src = $(this).attr('src');
      $(the_img).attr('src', spacer_src);
      $(the_img).css({
        'background':'none',
        'filter':'progid:DXImageTransform.Microsoft.AlphaImageLoader(src="' + src + '", sizingMethod="' + sizingMethod + '")'
      });
    });
  };
  return $(this);
};

$(function() {
  if($.browser.msie && parseInt($.browser.version) < 7) {
    $('.png_bg').each(function() {
      var css_bg_img = $(this).css('background-image');
      var bg_img = css_bg_img.substring(5, css_bg_img.length - 2);
      $(this).css({'background':'none', 'filter':'progid:DXImageTransform.Microsoft.AlphaImageLoader(src="' + bg_img + '", sizingMethod="image")'});
    });
    $('.png_img').imgPNGFix('image');
  };
});
```

---

### Post by AJB2K3 on 2008-08-22
What one off these?
> Best viewed in FF3.0 & IE7 because MS made a boo boo.

---

### Post by lyceum on 2008-08-23
> **hockey97 said:**
> Ok, yes when I tried it in firefox it works great and also ie7 it works great.

it's just ie6 that it would make the transparent areas white and looks very ulgy.

Well if I can't fix this problem, I am just going to make  a java script and  make a pop up window for ie6 users saying that you would need ie7 because Microsoft made a boo boo lol.

I will take a look at the links above thanks, I am really getting frustrated making my website I got this and also a display resolution problem.

I hope microsoft and other browsers make a plug-in or a new browser to be able to resize a website page to scale according to the clients resolution.

Did you look at the link I posted? It is a <div> that makes png's work in IE5.5 and IE6. If it works, you do not have to use JavaScript.

<DIV ID="oDiv" STYLE="position:absolute; left:140px; height:400; width:400;

filter:progid:DXImageTransform.

Microsoft.AlphaImageLoader (src='image.png', sizing

Method='scale');" >

</DIV>

-edit-

Well, I guess you will have to look at the article, as the forum makes some of the code smile lol

:D

---

### Post by Merk42 on 2008-08-23
In general it would be helpful if you had it uploaded so we could see what is going on, unless you have and I missed it. Perhaps you could use a gif instead of png?

> **hockey97 said:**
> 
Well if I can't fix this problem, I am just going to make  a java script and  make a pop up window for ie6 users saying that you would need ie7 because Microsoft made a boo boo

That will only make IE6 users just not go to your site at all.  A person would sooner close the window and not visit your site again rather than upgrade their browser.  What about those running Windows 2000 and earlier that can't upgrade to IE7?  Or the thousands of people in a business environment that don't have the administrative rights to upgrade to IE7?  Forcing someone to change their browser, as opposed to a graceful degradation of the site, doesn't make you seem professional, but I don't even know what your website is advertising anyway.

> **hockey97 said:**
> I hope microsoft and other browsers make a plug-in or a new browser to be able to resize a website page to scale according to the clients resolution.

That's called doing a liquid layout, which I've mentioned to you before and you *refused* to learn.

Even if something like javascript reads the client's resolution, it doesn't take into account the size of the actual browser window (for example if it isn't maximized)

---

