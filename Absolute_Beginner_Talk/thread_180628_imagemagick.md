---
title: "imagemagick"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-05-22
Everytime i run the aimate command with Image magick i just get the following...why is this and how do i rectify it?



neelabhro@ubuntu:~/opt/movie/movie_1$ animate *.jpg
Version: ImageMagick 6.2.7 05/15/06 Q16 [http://www.imagemagick.org](http://www.imagemagick.org)
Copyright: Copyright (C) 1999-2006 ImageMagick Studio LLC

Usage: animate [options ...] file [ [options ...] file ...]

Where options include:
  -authenticate value  decrypt image with this password
  -backdrop            display image centered on a backdrop
  -channel type        apply option to select image channels
  -clone index         clone an image
  -coalesce            merge a sequence of images
  -colormap type       Shared or Private
  -colors value        preferred number of colors in the image
  -colorspace type     alternate image colorspace
  -crop geometry       preferred size and location of the cropped image
  -debug events        display copious debugging information
  -define format:option
                       define one or more image format options
  -delay value         display the next image after pausing
  -density geometry    horizontal and vertical density of the image
  -depth value         image depth
  -display server      display image to this X server
  -dither              apply Floyd/Steinberg error diffusion to image
  -dither              apply Floyd/Steinberg error diffusion to image
  -extract geometry    extract area from image
  -flatten             flatten a sequence of images
  -format "string"     output formatted image characteristics
  -gamma value         level of gamma correction
  -geometry geometry   preferred size and location of the Image window
  -help                print program options
  -identify            identify the format and characteristics of the image
  -interlace type      type of image interlacing scheme
  -limit type value    pixel cache resource limit
  -log format          format of debugging information
  -loop iterations     loop images then exit
  -matte               store matte channel if the image has one
  -map type            display image using this Standard Colormap
  -monitor             monitor progress
  -monochrome          transform image to black and white
  -pause               seconds to pause before reanimating
  -page geometry       size and location of an image canvas (setting)
  -remote command      execute a command in an remote display process
  -repage geometry     size and location of an image canvas (operator)
  -resize geometry     resize the image
  -rotate degrees      apply Paeth rotation to the image
  -sampling-factor geometry
                       horizontal and vertical sampling factor
  -scenes range        image scene range
  -set attribute value set an image attribute
  -size geometry       width and height of image
  -strip               strip image of all profiles and comments
  -support factor      resize support: > 1.0 is blurry, < 1.0 is sharp
  -treedepth value     color tree depth
  -trim                trim image edges
  -verbose             print detailed information about the image
  -version             print version information
  -visual type         display image using this visual type
  -virtual-pixel method
                       virtual pixel access method
  -window id           display image to background of this window

In addition to those listed above, you can specify these standard X
resources as command line options:  -background, -bordercolor,
-borderwidth, -font, -foreground, -iconGeometry, -iconic, -name,
-mattecolor, -shared-memory, or -title.

By default, the image format of `file' is determined by its magic
number.  To specify a particular image format, precede the filename
with an image format name and a colon (i.e. ps:image) or specify the
image type as the filename suffix (i.e. image.ps).  Specify 'file' as
'-' for standard input or output.

Buttons:
  Press any button to map or unmap the Comman

---

### Post by morgengenuss on 2006-06-19
actually I use the GIMP to capture the screen. seems quite easy to me.
File -> Acquire -> Screen Shot

---

### Post by aysiu on 2006-06-19
[The ImageMagick homepage](http://www.imagemagick.org/script/animate.php) would probably help you more than the *man* page.

Though, you appear to be using the command correctly: > Example Usage

We list a few examples of the animate command here to illustrate its usefulness and ease of use. To get started, lets animate an image sequence in the GIF format:

  animate movie.gif

To animate a directory of JPEG images, use:

**  animate *.jpg**
 What happens when you use that command?

**Edit**: I just tried that command out on a bunch of pictures of my cat, and it popped up a window with a super-fast slideshow of all the pictures (I would imagine at 24 frames per second).

---

