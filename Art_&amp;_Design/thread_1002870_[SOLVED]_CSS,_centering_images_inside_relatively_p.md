---
title: "[SOLVED] CSS, centering images inside relatively positioned div"
date: 2008-12-05
forum: Art &amp; Design
---

### Post by Nevon on 2008-12-05
... Maybe that topic description was a little bit long.

Anyway, I'm currently working on a personal website. I'm trying to display the three newest photos from my flickr stream inside a div. Now, I'm not a picky guy. Either the div could dynamically expand in width so that the photos would fit inside it, or it could just completely fill its "mother div" and the images would just have to spread out evenly. Somehow I can't seem to achieve either of those options.

Right now the div has expanded horizontally so that it's the same width as its "mother div", but the images are all aligned to the left - leaving unused space on the right side.

Here's an excerpt of the html (I know the table is ugly, but the images wouldn't align themselves horizontally otherwise, not even with float:left):

[HTML]<div id="container">
    
    <div id="Photos">
      <div id="flickr_div">
			<table id="flickr_badge_uber_wrapper" cellpadding="0" cellspacing="10" border="0">
				<tr>
					<td>
						<table cellpadding="0" cellspacing="20" border="0" id="flickr_badge_wrapper">
							<tr>
								<td>								
									<script type="text/javascript" src="http://www.flickr.com/badge_code_v2.gne?count=3&amp;display=latest&amp;size=m&amp;layout=h&amp;source=user&amp;user=33066627%40N04">
									</script>						
								</td>							
							</tr>
						</table>
					</td>
				</tr>
			</table>
			<a href="http://flickr.com/photos/tommy_brunn"><img src="images/flickr_tv.jpg" alt="Follow Me on Flickr" class="bubble" /></a>
		</div>
    </div>
    
</div>[/HTML]

and here's the CSS:

```
#container {
	width:900px;
	padding:50px;
	padding-top:30px;
	background-image:url(images/background.jpg);
	background-repeat:no-repeat;
	background-position:top right;
}
#flickr_div {
	border:1px solid #222830;
	background-color:#101318;
	position:relative;
	min-height:40px;
	padding:10px;
	margin-top:15px;
	margin-bottom:30px;
	width: auto;
	}
#flickr_div .bubble {
	position:absolute;
	bottom:-22px;
	right:-14px;
}
.flickr_badge_image {
	text-align:center !important;
	}
.flickr_badge_image img {
	border: 1px solid black !important;
	}
```

Here's what it looks like:

[img]http://img216.imageshack.us/img216/2313/flickrproblempo1.jpg[/img]

Any ideas on how to fix this?

---

### Post by whiteraven on 2008-12-05
First off, you might want to ditch the table and rethink your use of div tags. You should be able to center the image(s) using this technique:

[[COLOR="Blue"]_CSS: Centering Things_[/COLOR]]("http://www.w3.org/Style/Examples/007/center")

To align the images in a row, use different float and margin styling for each image. You may need to introduce padding to compensate for IE's lack of adherance to CSS. Some of the horizontal alignment issue may be related to how Flicker is styled at it's source.

That's as much as I know to help you out.

---

### Post by jorgecs10 on 2008-12-05
What's the generated code after the flickr's script is executed?
I'm pretty sure you don't need 3 divs and a table, with one div should be enough.

---

### Post by Nevon on 2008-12-05
> **jorgecs10 said:**
> I'm pretty sure you don't need 3 divs and a table, with one div should be enough.> **whiteraven said:**
> First off, you might want to ditch the table and rethink your use of div tags.
I know, it's totally retarded. It's Flickrs code, not mine. 

> **jorgecs10 said:**
> What's the generated code after the flickr's script is executed?
That I don't know, since it's a Javascript. You can't see what code is generated, as it's inserted after the DOM has loaded.

> **whiteraven said:**
> To align the images in a row, use different float and margin styling for each image. You may need to introduce padding to compensate for IE's lack of adherance to CSS. Some of the horizontal alignment issue may be related to how Flicker is styled at it's source.
I've tried floating, but then the images appear on top of the div they're in, which means they go outside of the div = not good.

---

### Post by badmedic on 2008-12-06
Hard to say without seeing exactly what the JavaScript renders. Have you tried selecting the area on the rendered page in Firefox, right clicking and selecting "view selection source"? This might show you the HTML output of the script.

As far as CSS suggestions, I would lose the table and then try adding some right/left margin to any img tag that appears inside of the div. You can also add centering to the container div.

Something like:

```


#flickr_div {
text-align: center;
}
#flickr_div img {
margin: 0 40px;
}

```

You should be able to tweak the value of the right/left argins until it looks pretty good.

---

### Post by Nevon on 2008-12-06
> **badmedic said:**
> Hard to say without seeing exactly what the JavaScript renders. Have you tried selecting the area on the rendered page in Firefox, right clicking and selecting "view selection source"? This might show you the HTML output of the script.

As far as CSS suggestions, I would lose the table and then try adding some right/left margin to any img tag that appears inside of the div. You can also add centering to the container div.

Something like:

```


#flickr_div {
text-align: center;
}
#flickr_div img {
margin: 0 40px;
}

```

You should be able to tweak the value of the right/left argins until it looks pretty good.

"View selection source" worked. Here's the output:
[HTML]<div id="Photos">
      <div id="flickr_div">
			<table id="flickr_badge_uber_wrapper" border="0" cellpadding="0" cellspacing="10">
				<tbody><tr>

					<td>
						<span style="position: absolute; left: -999em; top: -999em; visibility: hidden;" class="flickr_badge_beacon"><img src="http://geo.yahoo.com/p?s=792600102&amp;t=888392c48f65e97ae783987e16628f4d&amp;r=http%3A%2F%2Fblastfromthepast.se%2F&amp;fl_ev=0&amp;lang=en&amp;intl=us" alt="" width="0" height="0"></span>						
								<table id="flickr_badge_wrapper" border="0" cellpadding="0" cellspacing="20">
							<tbody><tr>
								<td>								
									<script type="text/javascript" src="http://www.flickr.com/badge_code_v2.gne?count=3&amp;display=latest&amp;size=m&amp;layout=h&amp;source=user&amp;user=33066627%40N04">
									</script></td><td style="padding: 0pt;" class="flickr_badge_image" id="flickr_badge_image1" valign="center" align="center"><a href="http://www.flickr.com/photos/tommy_brunn/3086575705/"><img src="http://farm4.static.flickr.com/3132/3086575705_91d6049020_m.jpg" alt="A photo on Flickr" title="Sexy Santa" width="160" height="240"></a></td><td style="padding: 0pt;" class="flickr_badge_image" id="flickr_badge_image2" valign="center" align="center"><a href="http://www.flickr.com/photos/tommy_brunn/3084070277/"><img src="http://farm4.static.flickr.com/3263/3084070277_a0b567cdb8_m.jpg" alt="A photo on Flickr" title="Me looking evil." width="160" height="240"></a></td><td style="padding: 0pt;" class="flickr_badge_image" id="flickr_badge_image3" valign="center" align="center"><a href="http://www.flickr.com/photos/tommy_brunn/3084031211/"><img src="http://farm4.static.flickr.com/3190/3084031211_4f59a28486_m.jpg" alt="A photo on Flickr" title="screen_full" width="192" height="240"></a></td>							
							</tr>
						</tbody></table>
					</td>
				</tr>

			</tbody></table>
[/HTML]

As for manually changing margin values, that would work fine if I was statically showing three images. But this stream shows the last three images from my flickr page, so the images can be of different sizes, which would mean that the spacing between them will be off.

EDIT: Duh, I'm stupid! Doing as you said worked out beautifully. Since there's a max width for the images there's no risk that they'll end up outside of the container, no matter how wide the original image is - without any effect on the spacing. It looks like this now:

[img]http://img381.imageshack.us/img381/984/blastfromthepastsetommyhn0.png[/img]

Thanks a lot. It's funny how sometimes the easiest solutions are the hardest to see. [www.blastfromthepast.se](www.blastfromthepast.se) is the URL, if you want to see it. The code is a lot prettier now that I don't have a huge table in there.

---

