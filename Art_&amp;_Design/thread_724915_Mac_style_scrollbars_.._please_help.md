---
title: "Mac style scrollbars .. please help"
date: 2008-03-15
forum: Art &amp; Design
---

### Post by adityakavoor on 2008-03-15
I have these png files.

Where do I put these so that I can have mac style scrollbars for 

my human theme without affecting anything else.

I desperately want this. The default scrollbars for human and clearlooks suck :(

Please help ..

---

### Post by bekirserifoglu on 2008-03-16
I have attached the scrollbar and progressbar you need. you should put them into /home/YOURUSERNAME/.themes/THEMENAME. replace the folders with ones in the tar archive. Also you may need to change the options in your gtkrc file, which is in the same folder. Here is the scrollbar and the progress bar part of my gtkrc. 
hope it works.





```
################################################################################
# SCROLLBAR
################################################################################

style "scrollbar" = "default"
{
	# The values I set here have to do with the relative size of three graphic elements
    # I have used: the slider, the arrow box, and the trough. They all have the same width
    # of 15 pixels, but gtk wants to put in some spacing between them. It seems like it
    # places the sliders inside the trough with a default 1 pixel border on either side of the slider,
    # so that the trough has its width stretched by an additional two pixels(?). Setting the
    # trough border makes the arrow box sit on top of the trough squarely, by making sure that
    # the trough stays the same width as the arrowbox(?). I could be totally wrong here.
    GtkRange::trough_border = 0
    GtkRange::slider_width = 15

    # This sets the size of the steppers (arrow buttons on the end of the scrollbar). 
    # The image I am using is 15x15 pixels, and if I dont set this a one pixel line 
    # gets cut off of the top of the "up" stepper.
    GtkRange::stepper_size = 15

    # Set a minimum length for the slider. Since I set the border on the slider 
    # image to 15 pixels on either end of the slider I want the min length to be 
    # at least 30 pixels to avoid an ugly slider when gtk wants to make it smaller 
    # than 30 pixels.
    GtkScrollbar::min_slider_length = 30

	engine "pixmap" 
	{
		# Horizontal slider background
		image 
		{
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "Scrollbars/trough-scrollbar-horiz.png"
            border          = { 30, 30, 0, 0 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
	    
	    # Vertical slider background
	    image 
		{
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "Scrollbars/trough-scrollbar-vert.png"
            border          = { 0, 0, 30, 30 }
            stretch         = TRUE
            orientation     = VERTICAL
        }

		# Normal horizontal slider
	    image 
		{
	        function        = SLIDER
	        recolorable     = TRUE
	        state           = NORMAL
	        file            = "Scrollbars/slider-horiz.png"
	        border          = { 15, 15, 6, 6 }
	        stretch         = TRUE
	        orientation     = HORIZONTAL
	    }
		
		# Horizontal slider (active)
		image 
		{
	        function        = SLIDER
	        recolorable     = TRUE
	        state           = ACTIVE
	        file            = "Scrollbars/slider-horiz-prelight.png"
	        border          = { 15, 15, 6, 6 }
	        stretch         = TRUE
	        orientation     = HORIZONTAL
		}

		# Horizontal slider (mouse over)
	    image 
		{
	        function        = SLIDER 
	        recolorable     = TRUE
	        state           = PRELIGHT
	        file            = "Scrollbars/slider-horiz-prelight.png"
	        border          = { 15, 15, 6, 6 }
	        stretch         = TRUE
	        orientation     = HORIZONTAL
	    }
	    
	    # Horizontal slider (Insesitive)
		image 
		{
	        function        = SLIDER 
	        recolorable     = TRUE
	        state           = INSENSITIVE
	        file            = "Scrollbars/slider-horiz.png"
	        border          = { 15, 15, 6, 6 }
	        stretch         = TRUE
	        orientation     = HORIZONTAL
	    }

	    # Normal vertical slider
	    image 
		{
	        function        = SLIDER
	        recolorable     = TRUE
	        state           = NORMAL
	        file            = "Scrollbars/slider-vert.png"
	        border          = { 6, 6, 15, 15 }
	        stretch         = TRUE
	        orientation     = VERTICAL
		}
		
		# Vertical slider (Active)
		image 
		{
	        function        = SLIDER
	        recolorable     = TRUE
	        state           = ACTIVE
	        file            = "Scrollbars/slider-vert.png"
	        border          = { 6, 6, 15, 15 }
	        stretch         = TRUE
	        orientation     = VERTICAL
		}

		# Vertical slider (mouse over)
	    image 
		{
	        function        = SLIDER 
	        recolorable     = TRUE
	        state           = PRELIGHT
	        file            = "Scrollbars/slider-vert-prelight.png"
	        border          = { 6, 6, 15, 15 }
	        stretch         = TRUE
	        orientation     = VERTICAL
	    }
	    
	    # Vertical slider (Insesitive)
		image 
		{
	        function        = SLIDER 
	        recolorable     = TRUE
	        state           = INSENSITIVE
	        file            = "Scrollbars/slider-vert-prelight.png"
	        border          = { 6, 6, 15, 15 }
	        stretch         = TRUE
	        orientation     = VERTICAL
	    }

################################################################################
# SCROLLBAR STEPPERS
################################################################################

	# Up
    image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= NORMAL
      file				= "Scrollbars/stepper-up.png"
      #border			= { 12, 2, 2, 9 }
      stretch			= TRUE
      arrow_direction	= UP
    }
 	image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= PRELIGHT
      file				= "Scrollbars/stepper-up.png"
      #border			= { 12, 2, 2, 9 }
      stretch			= TRUE
      arrow_direction	= UP
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= ACTIVE
      file				= "Scrollbars/stepper-up.png"
      #border			= { 12, 2, 2, 9 }
      stretch			= TRUE
      arrow_direction	= UP
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= INSENSITIVE
      file				= "Scrollbars/stepper-up.png"
      #border			= { 12, 2, 2, 9 }
      stretch			= TRUE
      arrow_direction	= UP
    }

 ######### DOWN ############


    image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= NORMAL
      file				= "Scrollbars/stepper-down.png"
      #border			= { 12, 2, 10, 2 }
      stretch			= TRUE
      arrow_direction	= DOWN
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= PRELIGHT
      file				= "Scrollbars/stepper-down.png"
      #border			= { 12, 2, 10, 2 }
      stretch			= TRUE
      arrow_direction	= DOWN
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= ACTIVE
      file				= "Scrollbars/stepper-down.png"
      #border			= { 12, 2, 10, 2 }
      stretch			= TRUE
      arrow_direction	= DOWN
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= INSENSITIVE
      file				= "Scrollbars/stepper-down.png"
      #border			= { 12, 2, 10, 2 }
      stretch			= TRUE
      arrow_direction	= DOWN
    }

############ RIGHT ################

    image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= NORMAL
      file				= "Scrollbars/stepper-right.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= RIGHT
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= PRELIGHT
      file				= "Scrollbars/stepper-right.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= RIGHT
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= ACTIVE
      file				= "Scrollbars/stepper-right.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= RIGHT
    }
 image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= INSENSITIVE
      file				= "Scrollbars/stepper-right.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= RIGHT
    }

############### LEFT ###################


    image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= NORMAL
      file				= "Scrollbars/stepper-left.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= LEFT
    }
  image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= PRELIGHT
      file				= "Scrollbars/stepper-left.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= LEFT
    }
  image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= ACTIVE
      file				= "Scrollbars/stepper-left.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= LEFT
    }
  image 
    {
      function			= STEPPER
      recolorable		= TRUE
      state				= INSENSITIVE
      file				= "Scrollbars/stepper-left.png"
      #border			= { 2, 9, 2, 13 }
      stretch			= TRUE
      arrow_direction	= LEFT
    }
  	}
}

################################################################################
# PROGRESSBAR
################################################################################

style "progressbar"	= "default"
{
	GtkProgressBar::trough_border = 0
	
  	engine "pixmap" 
  	{
  		# Horizontal progressbar background
  		image 
		{
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "ProgressBar/trough-progressbar-horiz.png"
            border          = { 1, 1, 1, 1 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }

		# Horizontal progressbar
		image 
		{
            function        = BOX
            recolorable     = TRUE
            detail          = "bar"
            file            = "ProgressBar/progressbar-horiz.png"
            border          = { 1, 1, 1, 1}
            stretch         = TRUE
            orientation		= HORIZONTAL
        }

		# Vertical progressbar background
		image
		{
		    function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "ProgressBar/trough-progressbar-vert.png"
            border          = { 1, 1, 1, 1 }
            stretch         = TRUE
		    orientation		= VERTICAL
		}

		# Vertical progressbar
	    image
	    {
		    function        = BOX
            recolorable     = TRUE
            detail          = "bar"
            file            = "ProgressBar/progressbar-vert.png"
            border          = { 1, 1, 1, 1}
            stretch         = TRUE
		    orientation		= VERTICAL
	    } 
	}
}


```

---

### Post by adityakavoor on 2008-03-16
I did that but in vain.

I think it conflicted with my existing scrollbar

---

### Post by bekirserifoglu on 2008-03-16
why dont you just change your theme completely now that you want it to look like mac os x. 

here is my theme and specs: 
[http://ubuntuforums.org/showthread.php?p=4526160#post4526160](http://ubuntuforums.org/showthread.php?p=4526160#post4526160)

---

### Post by adityakavoor on 2008-03-17
> **bekirserifoglu said:**
> Details:
Background - mac os x tiger
Controls - Mac4Lin GTK Aqua v0.3
Windows border - Mac4Lin GTK v0.4
Icons - Mac4Lin Icons v0.4 ( I have changed them a little bit)
Pointer - DMZ Black
Compiz
Conky with Gmail mailcheck script and exaile playing file info.

Oh! its awesome.

Where did you get those fonts ?

How did you get that spacing between menu items ?

Can you link me to the emerald theme and icons ?

---

### Post by adityakavoor on 2008-03-17
> **emilyandrew said:**
> Hi!

     Mac Style Scrollbars!?

     Sorry! I don't know about it!

    Bye

There were many other better ways to get your first bean. :)

Anyways welcome to the ubuntu community

---

### Post by Poyntz on 2009-08-19
[COLOR="Red"]*Message deleted by author.*[/COLOR]

For anyone else who makes this, make sure you set **GtkRange::trough_border** = **0**.
If you don't the arrow and the slider trough don't fit together perfectly

---

### Post by Fzang on 2009-08-19
If you want a mac theme, check out my iGTK theme

[http://fzang.deviantart.com/art/iGTK-iLeopard-for-linux-133380895](http://fzang.deviantart.com/art/iGTK-iLeopard-for-linux-133380895)

---

### Post by warreno on 2009-08-20
It's also worth looking at [Mac4Lin]("http://sourceforge.net/projects/mac4lin/"). I installed it — basically it's just another theme with some hand-tweaks necessary — and it works, but on my netbook it was a bit of a resource hog so I went back to GNOME's Human theme.

I've been working with Mac for mumbledysomething years, and they are nice machines, but GNOME is not broken, and neither is KDE. Why not try them for a while first and see what their strengths are?

There's honestly no reason to make your slick, shiny Linux install look like a Mac.

---

### Post by Poyntz on 2009-08-24
is there anyway to fix up scroll so it doesn't pixelate when scrolling?

---

### Post by Poyntz on 2009-09-02
> **warreno said:**
> It's also worth looking at 
There's honestly no reason to make your slick, shiny Linux install look like a Mac.

I totally agree, save for three things: 
1) The satisfaction you get from clicking on dock icons (yeah, its heaps more exciting than clicking icons on the gnome panel)
2) The Ubuntu scroll bars are really ugly, the Mac ones are better
3) The compiz widget layer is a very handy addition to gnome - I can see what the stocks have done, make notes, etc. 
It's a pity that the screenlet apps it runs are so buggy...

- Additionally, it's worth considering that many people love the Mac interface, but hate Mac as an OS. 

Anyhow, back on track. There are a few pictures missing from your icon set. The inactive bars aren't there and when you scroll down, the Mac bars don't ripple. Additionally, is there anyway to make scrolling smooth so the scrollbars don't flicker when you scroll?

---

### Post by marako on 2009-09-03
Can you post a screenie w/ it?

---

### Post by Poyntz on 2009-09-27
look at the scrollbars in my attachment - same ones

---

