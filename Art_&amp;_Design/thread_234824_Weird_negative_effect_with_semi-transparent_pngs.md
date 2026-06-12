---
title: "Weird negative effect with semi-transparent pngs"
date: 2006-08-12
forum: Art &amp; Design
---

### Post by Tom Brokaw on 2006-08-12
I like the idea of a shiny yet semi-transparent panel.  If you select an image, say one with a simple gradient and  highlight, then you can't change the transparency.  

I am trying to get around this by creating semi-transparent .pngs in the gimp.  However, whenever I apply them to my panel, the colors are weird.  Not exactly negative, but off.  If I make a red image, it comes out green.  If I make an aqua image, it comes out pink.  If I make a black image, it comes out blue.

I'm pretty new to the gimp and to Ubuntu/Linux.  Can anyone pick what I'm doing wrong?

I create a new image, 24x24.  I select the gradient I want, and if no highlight is inherently present, I add one in a new layer, by selecting a rectangle along the lighter side of the gradient and filling with white.

I merge the two layers if necessary and set the layer opacity to whatever I fancy - 50, 35, whatever.  Then I save as .png.  It gives me a message saying I should export it first, with the option to export it.  I choose export, click OK, and then set the newly created image as the background image in Panel Properties.

I've messed around for a while trying to suss out what the final color will be, but screw that.  How do I get it to work the way I want to, or rather, what do I need to learn to get it to do what I want?

Thanks!

---

### Post by xmastree on 2006-08-12
That is bizarre.

It can be done, I used a similar principle for [this]("http://ubuntuforums.org/gallery/showphoto.php?photo=3093&cat=2&si=lappy&perpage=12") panel. I created a new image, and used a gradient from foreground colour to transparent so that it shows the menu titles but then fades to nothing about one third of the way across (for obvious reasons).

Mine is 24x800, the width of the desktop. That might be an issue with yours being square.

How about posting a screenshot, and the png itself so we can see what's happening?

---

### Post by Tom Brokaw on 2006-08-12
I'll try making the panels the full size instead of tiling the background image.

Here's what I have.  I used the default gradient in The Gimp called "brushed aluminum.  As you can see, it comes out fine until I apply it to the panel.  Then it turns blue.

---

### Post by xmastree on 2006-08-12
Strange. I downloaded your brushed_aluminium, made a panel and set that as the background. 
[ATTACH]14219[/ATTACH]
Looks fine.

Then I set the opacity to 40%, saved it 
[ATTACH]14221[/ATTACH]
and used that.

The panel became transparent.
[ATTACH]14220[/ATTACH]
There you can see the new file in the lower right, against part of the desktop which shows the transparency better.

---

### Post by Tom Brokaw on 2006-08-12
Hmmm.  Well, two things come to mind.  The first is the way my video card handles transparencies.  It's a Nvidia 5900, a little bit older but a good gaming and all-around card.  What is your graphics card?

The other thing is maybe it's something with Dapper?  I noticed you're using Breezy (at least that's what's in your profile) so maybe that's it, but it seems less likely.

I was messing around and set the transparency of the image to 0.  This gave me a transparent green stripe for the panel.  I ended up making new panels using the "crown molding" gradient and "burlwood" pattern fill, and I like them OK for now.

---

### Post by xmastree on 2006-08-13
> **Tom Brokaw said:**
> What is your graphics card?It's built in. xorg.conf is using the sis driver, and reckons it's an SiS 630/730.

> I noticed you're using BreezyYep, I couldn't get the dapper installation to work.

What happens if you set a solid colour, and make it partially transparent? If that works then a transparent png ought to.

---

### Post by bvc on 2006-08-13
it's either a dapper gnome-panel bug or it's a gnome-panel bug. It can't handle transparent images any more. It happened about half way through dapper development. Sad....very sad....I miss my trans panels :(

---

### Post by red_Marvin on 2006-08-14
I'm using dapper and have no problem... Are you sure you run at a hi-color mode? :p

---

### Post by Tom Brokaw on 2006-08-14
> **red_Marvin said:**
> I'm using dapper and have no problem... Are you sure you run at a hi-color mode? :p

I can't think why I wouldn't be, and it looks like millions of colors to me - how do I check?

Do you have a Nvidia card as well?

---

### Post by Tom Brokaw on 2006-08-14
> **xmastree said:**
> What happens if you set a solid colour, and make it partially transparent? If that works then a transparent png ought to.

That works fine, and setting it to white and making it transparent looks good.  My original idea was to just add a highlight to that to make it look glassy.

---

### Post by bvc on 2006-08-14
> **red_Marvin said:**
> I'm using dapper and have no problem... Are you sure you run at a hi-color mode? :pI also would like to know more about your setup because you are truly a first w/o this problem, that I've heard of.

---

### Post by red_Marvin on 2006-08-15
The hi-color thing was mostly meant as a joke (hence the :p) you probably would notice if you run in 256 colors. However you can check by opening GIMP and double click on the colour chooser andd check that it's a smooth gradient...

My setup is: 1024x768(32bpp I think) P4 2.66GHz 512Mb RAM, ATI RADEON 9200 128Mb.
I have installed ati's drivers to get better 3d (I'm not sure which howto I followed, I had to recompile the kernel though.)

I have attached a screenshot of my gnomepanel and the image I use as it's background.

---

### Post by mcduck on 2006-08-15
> **bvc said:**
> it's either a dapper gnome-panel bug or it's a gnome-panel bug. It can't handle transparent images any more. It happened about half way through dapper development. Sad....very sad....I miss my trans panels :(
It's a Gnome-Panel bug. And unlikely to get fixed any time soon. I miss my trasnparent panels too :(

---

### Post by Tom Brokaw on 2006-08-15
> **mcduck said:**
> And unlikely to get fixed any time soon.

Why not?

---

