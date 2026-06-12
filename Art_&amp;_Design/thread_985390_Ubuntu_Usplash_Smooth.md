---
title: "Ubuntu Usplash Smooth"
date: 2008-11-17
forum: Art &amp; Design
---

### Post by volanin on 2008-11-17
This is the original Ubuntu Usplash for Intrepid Ibex with an exciting twist!

**Now the progress bar is time-based!**

What does it means?
Well...

The original Ubuntu Usplash progress bar didn't tell you much information.
It moves in small/huge increments, and sometimes stands still for a few seconds.

**This Ubuntu Usplash Smooth does it different!**

It remembers the time of your previous boot/shutdown, and will smoothly increase the bar according to this time. Since the boot/shutdown times change very little, you will get a very precise bar with a very smooth animation showing exactly how much time is left!

**Check it for yourself!**

Modesty aside(!), this is how the usplash progress bar should have been done from the beginning!

Easily packaged in a DEB file, you just have to install it, and boot your computer a couple times. The first boot/shutdown will be quite off the mark, of course, since the Usplash Ubuntu Smooth still don't know how much time it will take to complete. But from the second boot/shutdown onwards, you will simply fall in love!

If you hate it for any reason... just uninstall it, and your system will return to the original configuration.

**Enjoy!**

-----

Ok, marketing is over!
Let's talk seriously now.
:)

This is a personal project of mine to make the usplash progress bar time-based.
Besides making ubuntu boot look nicer, it also gives you accurate time of the boot process.
This kind of bar is already used in MacOSX, and I admit it was from there that I took the idea!

It was an ugly fight with usplash, because I didn't want to modify it in any way.
I wanted to do this using the technology already implemented in Ubuntu,
and achieve this using just a simple theme.

Anyway, check it out, and give your opinions below!
Thank you!
:)

**Direct Download:**
[Ubuntu Usplash Smooth]("http://gnome-look.org/content/show.php?content=93386") (Hosted at gnome-look.org)
[Ubuntu Usplash Smooth]("http://ubuntu-art.org/content/show.php/Ubuntu+Usplash+Smooth?content=93394") (Hosted at ubuntu-art.org)

**Ubuntu PPA:**
[https://launchpad.net/~usplash-smooth/+archive]("https://launchpad.net/~usplash-smooth/+archive")

**Ubuntu WIKI:**
[https://wiki.ubuntu.com/UsplashSmooth]("https://wiki.ubuntu.com/UsplashSmooth")

**Ubuntu Brainstorm:**
[http://brainstorm.ubuntu.com/idea/15741/]("http://brainstorm.ubuntu.com/idea/15741/")

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)

---

### Post by Vadi on 2008-11-17
The 64bit .deb worked great except I got 2 bars instead of 1.

(also, might want to put it on ubuntu-art.org instead. the gnome-look people weren't too happy about ubuntu being there last time I checked...)

---

### Post by volanin on 2008-11-17
Two bars? Wow!

I am also using the 64-bit version, with an Intel Card, and it does not happen here.
Is it possible for you to take a picture of the screen with a camera or cellphone?

Thank you a lot for the feedback!
:)

> also, might want to put it on ubuntu-art.org instead.
the gnome-look people weren't too happy about ubuntu being there last time I checked...

Done!
:)

---

### Post by MadsRH on 2008-11-17
I haven't tested it yet, but _great work_!

Have you purposed this for Jaunty? If no, you should.

**//MadsRH**
[AnotherUbuntu.blogspot.com]("anotherubuntu.blogspot.com")

---

### Post by Crafty Kisses on 2008-11-17
Thanks, they look excellent.

---

### Post by volanin on 2008-11-17
> The 64bit .deb worked great except I got 2 bars instead of 1.

New version is out!
Maybe it fixes this for you!

> I haven't tested it yet, but great work!
Have you purposed this for Jaunty? If no, you should.

> Thanks, they look excellent.

Thank you a lot!
I am just ironing out the remaining problems before proposing.
I am very proud of this version 0.2, so it should happen soon!
:)

---

### Post by Genius314 on 2008-11-17
Sounds really cool.
And clever. :)

---

### Post by ShirishAg75 on 2008-11-18
> **volanin said:**
> New version is out!
Maybe it fixes this for you!

Thank you a lot!
I am just ironing out the remaining problems before proposing.
I am very proud of this version 0.2, so it should happen soon!
:)

Volanin, I would suggest you make a PPA in launchpad. This would make it easier for people to do wider testing and you may generate greater feedback. 

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by Vadi on 2008-11-18
Looks like you messed up the upgrade from 0.1 to 0.2 a bit (see screenshot).

I'll try removing 0.1 manually.

---

### Post by Martje_001 on 2008-11-18
Hey,
I think I'm doing something wrong, because I have no splash screen at all, after installing. Does there need to be anything installed besides *usplash-smooth*? Because the description only says:
```
Usplash Smooth
Support for creation and use of usplash themes with a time-based progress bar
```
Nothing about 'themes included'...

Edit: aah, I see, I have to compile usplash-ubuntu again. Thank you, looks great!

---

### Post by Martje_001 on 2008-11-18
I think I'm just plain stupid :(. If I try to compile it, I get:
```
martijn@mekkie:~/usplash-theme-ubuntu-0.18$ make
make: Circular throbber_back.png <- throbber_back.png.c dependency dropped.
pngtousplash throbber_back.png > throbber_back.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o throbber_back.png.c.o -c throbber_back.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular throbber_back_16.png <- throbber_back_16.png.c dependency dropped.
pngtousplash throbber_back_16.png > throbber_back_16.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o throbber_back_16.png.c.o -c throbber_back_16.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular throbber_fore.png <- throbber_fore.png.c dependency dropped.
pngtousplash throbber_fore.png > throbber_fore.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o throbber_fore.png.c.o -c throbber_fore.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular throbber_fore_16.png <- throbber_fore_16.png.c dependency dropped.
pngtousplash throbber_fore_16.png > throbber_fore_16.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o throbber_fore_16.png.c.o -c throbber_fore_16.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular usplash_1024_768.png <- usplash_1024_768.png.c dependency dropped.
pngtousplash usplash_1024_768.png > usplash_1024_768.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o usplash_1024_768.png.c.o -c usplash_1024_768.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular usplash_1365_768_scaled.png <- usplash_1365_768_scaled.png.c dependency dropped.
pngtousplash usplash_1365_768_scaled.png > usplash_1365_768_scaled.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o usplash_1365_768_scaled.png.c.o -c usplash_1365_768_scaled.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular usplash_800_600.png <- usplash_800_600.png.c dependency dropped.
pngtousplash usplash_800_600.png > usplash_800_600.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o usplash_800_600.png.c.o -c usplash_800_600.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular usplash_640_400.png <- usplash_640_400.png.c dependency dropped.
pngtousplash usplash_640_400.png > usplash_640_400.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o usplash_640_400.png.c.o -c usplash_640_400.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
make: Circular usplash_640_480.png <- usplash_640_480.png.c dependency dropped.
pngtousplash usplash_640_480.png > usplash_640_480.png.c
gcc  -g -Wall -fPIC -l usplash-smooth -o usplash_640_480.png.c.o -c usplash_640_480.png.c
gcc: -lusplash-smooth: linker input file unused because linking not done
gcc  -g -Wall -fPIC -l usplash-smooth -o usplash-theme-ubuntu.c.o -c usplash-theme-ubuntu.c
gcc: -lusplash-smooth: linker input file unused because linking not done
gcc  -g -Wall -fPIC -l usplash-smooth -shared -o usplash-theme-ubuntu.so throbber_back.png.c.o throbber_back_16.png.c.o throbber_fore.png.c.o throbber_fore_16.png.c.o usplash_1024_768.png.c.o usplash_1365_768_scaled.png.c.o usplash_800_600.png.c.o usplash_640_400.png.c.o usplash_640_480.png.c.o usplash-theme-ubuntu.c.o
rm usplash_1024_768.png.c usplash_1365_768_scaled.png.c throbber_fore_16.png.c throbber_back.png.c usplash_640_480.png.c usplash_640_400.png.c throbber_back_16.png.c throbber_fore.png.c usplash_800_600.png.c

```

**usplash-theme-ubuntu.c:**
```
/* usplash
 *
 * eft-theme.c - definition of eft theme
 *
 * Copyright © 2006 Dennis Kaarsemaker <dennis@kaarsemaker.net>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301 USA
 */

#include <usplash-theme.h>
#include <usplash-smooth.h>
/* Needed for the custom drawing functions */
#include <usplash_backend.h>
extern struct usplash_pixmap pixmap_usplash_640_400, pixmap_usplash_640_480;
extern struct usplash_pixmap pixmap_usplash_800_600, pixmap_usplash_1024_768, pixmap_usplash_1365_768_scaled;
extern struct usplash_pixmap pixmap_throbber_back;
extern struct usplash_pixmap pixmap_throbber_back_16;
extern struct usplash_pixmap pixmap_throbber_fore;
extern struct usplash_pixmap pixmap_throbber_fore_16;

void t_init(struct usplash_theme* theme);
void t_clear_progressbar(struct usplash_theme* theme);
void t_clear_progressbar_16(struct usplash_theme* theme);
void t_draw_progressbar(struct usplash_theme* theme, int percentage);
void t_draw_progressbar_16(struct usplash_theme* theme, int percentage);
void t_animate_step(struct usplash_theme* theme, int pulsating);
void t_animate_step_16(struct usplash_theme* theme, int pulsating);

struct usplash_theme usplash_theme_640_480;
struct usplash_theme usplash_theme_800_600;
struct usplash_theme usplash_theme_1024_768;
struct usplash_theme usplash_theme_1365_768_scaled;

int global_percentage = 0;

/* Theme definition */
struct usplash_theme usplash_theme = {
	.version = THEME_VERSION, /* ALWAYS set this to THEME_VERSION, 
                                 it's a compatibility check */
    .next = &usplash_theme_640_480,
    .ratio = USPLASH_16_9,

	/* Background and font */
	.pixmap = &pixmap_usplash_640_400,

	/* Palette indexes */
	.background             = 0,
  	.progressbar_background = 32,
  	.progressbar_foreground = 131,
	.text_background        = 0,
	.text_foreground        = 117,
	.text_success           = 189,
	.text_failure           = 55,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 212,
  	.progressbar_y      = 196,
  	.progressbar_width  = 216,
  	.progressbar_height = 8,

	/* Text box position and size in pixels */
  	.text_x      = 96,
  	.text_y      = 246,
  	.text_width  = 360,
  	.text_height = 100,

	/* Text details */
  	.line_height  = 15,
  	.line_length  = 32,
  	.status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar_16,
    .draw_progressbar = t_draw_progressbar_16,
    .animate_step = t_animate_step_16,
};

struct usplash_theme usplash_theme_640_480 = {
	.version = THEME_VERSION, /* ALWAYS set this to THEME_VERSION, 
                                 it's a compatibility check */
    .next = &usplash_theme_800_600,
    .ratio = USPLASH_4_3,

	/* Background and font */
	.pixmap = &pixmap_usplash_640_480,

	/* Palette indexes */
	.background             = 0,
  	.progressbar_background = 32,
  	.progressbar_foreground = 131,
	.text_background        = 0,
	.text_foreground        = 117,
	.text_success           = 189,
	.text_failure           = 55,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 160,
  	.progressbar_y      = 251,
  	.progressbar_width  = 320,
  	.progressbar_height = 18,

	/* Text box position and size in pixels */
  	.text_x      = 120,
  	.text_y      = 307,
  	.text_width  = 360,
  	.text_height = 100,

	/* Text details */
  	.line_height  = 15,
  	.line_length  = 32,
  	.status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar,
    .draw_progressbar = t_draw_progressbar,
    .animate_step = t_animate_step,
};

struct usplash_theme usplash_theme_800_600 = {
	.version = THEME_VERSION, /* ALWAYS set this to THEME_VERSION, 
                                 it's a compatibility check */
    .next = &usplash_theme_1024_768,
    .ratio = USPLASH_4_3,

	/* Background and font */
	.pixmap = &pixmap_usplash_800_600,

	/* Palette indexes */
	.background             = 0,
  	.progressbar_background = 32,
  	.progressbar_foreground = 131,
	.text_background        = 0,
	.text_foreground        = 117,
	.text_success           = 189,
	.text_failure           = 55,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 240,
  	.progressbar_y      = 321,
  	.progressbar_width  = 320,
  	.progressbar_height = 18,

	/* Text box position and size in pixels */
  	.text_x      = 220,
  	.text_y      = 407,
  	.text_width  = 360,
  	.text_height = 150,

	/* Text details */
  	.line_height  = 15,
  	.line_length  = 32,
  	.status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar,
    .draw_progressbar = t_draw_progressbar,
    .animate_step = t_animate_step,
};

struct usplash_theme usplash_theme_1024_768 = {
	.version = THEME_VERSION,
    .next = &usplash_theme_1365_768_scaled,
    .ratio = USPLASH_4_3,

	/* Background and font */
	.pixmap = &pixmap_usplash_1024_768,

	/* Palette indexes */
	.background             = 0,
  	.progressbar_background = 32,
  	.progressbar_foreground = 131,
	.text_background        = 0,
	.text_foreground        = 117,
	.text_success           = 189,
	.text_failure           = 55,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 352,
  	.progressbar_y      = 400,
  	.progressbar_width  = 320,
  	.progressbar_height = 18,

	/* Text box position and size in pixels */
  	.text_x      = 322,
  	.text_y      = 475,
  	.text_width  = 380,
  	.text_height = 200,

	/* Text details */
  	.line_height  = 15,
  	.line_length  = 32,
  	.status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar,
    .draw_progressbar = t_draw_progressbar,
    .animate_step = t_animate_step,
};

struct usplash_theme usplash_theme_1365_768_scaled = {
	.version = THEME_VERSION,
    .next = NULL,
    .ratio = USPLASH_16_9,

	/* Background and font */
	.pixmap = &pixmap_usplash_1365_768_scaled,

	/* Palette indexes */
	.background             = 0,
  	.progressbar_background = 32,
  	.progressbar_foreground = 131,
	.text_background        = 0,
	.text_foreground        = 117,
	.text_success           = 189,
	.text_failure           = 55,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 352,
  	.progressbar_y      = 475,
  	.progressbar_width  = 320,
  	.progressbar_height = 18,

	/* Text box position and size in pixels */
  	.text_x      = 322,
  	.text_y      = 475,
  	.text_width  = 380,
  	.text_height = 200,

	/* Text details */
  	.line_height  = 15,
  	.line_length  = 32,
  	.status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar,
    .draw_progressbar = t_draw_progressbar,
    .animate_step = t_animate_step,
};

void t_init(struct usplash_theme *theme) {
    int x, y;
    usplash_getdimensions(&x, &y);
    theme->progressbar_x = (x - theme->pixmap->width)/2 + theme->progressbar_x;
    theme->progressbar_y = (y - theme->pixmap->height)/2 + theme->progressbar_y;
    usplash_smooth();
}

void t_clear_progressbar(struct usplash_theme *theme) {
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back);
}

void t_clear_progressbar_16(struct usplash_theme *theme) {
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_16);
}

void t_draw_progressbar(struct usplash_theme *theme, int percentage) {
    global_percentage = percentage;
}

void t_draw_progressbar_16(struct usplash_theme *theme, int percentage) {
    global_percentage = percentage;
}

void t_animate_step(struct usplash_theme* theme, int pulsating) {
    int w = (pixmap_throbber_back.width * time_percentage());
    if(global_percentage == 0)
        usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back);
    if(global_percentage < 0){/* Unloading */
        /* Draw background to left of foreground */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back.height, 
                         &pixmap_throbber_back, 0, 0);
        /* Draw foreground to right of background */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back.width - w,
                         pixmap_throbber_back.height, &pixmap_throbber_fore, w, 0);
    }
    if(global_percentage > 0){/* Loading */
        /* Draw foreground to left of background */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back.height, 
                         &pixmap_throbber_fore, 0, 0);
        /* Draw background ot right of foreground */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back.width - w, pixmap_throbber_back.height, 
                         &pixmap_throbber_back, w, 0);
    }
}

void t_animate_step_16(struct usplash_theme* theme, int pulsating) {
    int w = (pixmap_throbber_back_16.width * time_percentage());
    if (global_percentage == 0)
        usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_16);
    if (global_percentage < 0){ /* Unloading */
        /* Draw background to left of foreground */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_16.height, 
                         &pixmap_throbber_back_16, 0, 0);
        /* Draw foreground to right of background */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back_16.width - w,
                         pixmap_throbber_back_16.height, &pixmap_throbber_fore_16, w, 0);
    }
    if (global_percentage > 0){/* Loading */
        /* Draw foreground to left of background */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_16.height, 
                         &pixmap_throbber_fore_16, 0, 0);
        /* Draw background to right of foreground */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back_16.width - w, pixmap_throbber_back_16.height, 
                         &pixmap_throbber_back_16, w, 0);
    }
}
```

**Makefile:**
```
CC=gcc
CFLAGS=-g -Wall -fPIC
LDFLAGS=
INCLUDES=

COMPILE = $(CC) $(INCLUDES) $(CFLAGS) -l usplash-smooth
LINK = $(CC) $(CFLAGS) $(LDFLAGS)

INSTALL = /usr/bin/install -c
INSTALL_DATA = $(INSTALL) -m 644
INSTALL_PROGRAM = $(INSTALL) -m 755

usplash-theme-ubuntu.so: throbber_back.png.c.o throbber_back_16.png.c.o throbber_fore.png.c.o throbber_fore_16.png.c.o \
						 usplash_1024_768.png.c.o usplash_1365_768_scaled.png.c.o usplash_800_600.png.c.o \
						 usplash_640_400.png.c.o usplash_640_480.png.c.o usplash-theme-ubuntu.c.o
	$(COMPILE) -shared -o $@ $^

%.png.c: %.png
	pngtousplash $< > $@

%.bdf.c: %.bdf
	bdftousplash $< > $@

%.c.o: %.c
	$(COMPILE) -o $@ -c $<

install:
	$(INSTALL) -d $(DESTDIR)/usr/lib/usplash
	$(INSTALL_PROGRAM) usplash-theme-ubuntu.so $(DESTDIR)/usr/lib/usplash/usplash-theme-ubuntu.so
clean:
	rm -f *.png.c *.bdf.c *.c.o *.so
```

---

### Post by volanin on 2008-11-18
> Volanin, I would suggest you make a PPA in launchpad. This would make it easier for people to do wider testing and you may generate greater feedback.

Done!
You can get usplash-smooth via Ubuntu PPA here:
[https://launchpad.net/~usplash-smooth/+archive]("https://launchpad.net/~usplash-smooth/+archive")
:)

> Looks like you messed up the upgrade from 0.1 to 0.2 a bit (see screenshot).
I'll try removing 0.1 manually.

That was intentional.
Version 0.1 had only the theme.
Version 0.2 had the theme and a library for every other theme creator, so the name of the package changed!

Since the name changed, it would not autoremove the prevous one.
So I had to make it conflict. Just uninstall manually as you did!
:)

> Nothing about 'themes included'...
Edit: aah, I see, I have to compile usplash-ubuntu again. Thank you, looks great!

There is no need to compile nothing!
Just install the package and a new theme will be installed for you!
But you made a VERY GOOD observation about the description!
So I updated it, thank you!
:)

By the way.
This idea is in Ubuntu Brainstorm! Please vote for it!
[http://brainstorm.ubuntu.com/idea/15741]("http://brainstorm.ubuntu.com/idea/15741")
:)

---

### Post by gnrathon on 2008-11-18
Would this work w/ lilo ?

Sadly my SATA drive is unable to use grub :(

---

### Post by volanin on 2008-11-18
> **gnrathon said:**
> Would this work w/ lilo ?
Sadly my SATA drive is unable to use grub :(

The boot loader makes no difference.
If usplash already works for you, then this will also work!
:)

---

### Post by gnrathon on 2008-11-18
usplash doesnt show for me

any pointers on how to enable it

i have no clue

---

### Post by volanin on 2008-11-18
Check your lilo configuration.
There are two things that must be present:

1. The initrd image.
2. The "splash" kernel parameter.

An example configuration would be:

```
image=/boot/vmlinuz-2.6.27-8-generic
	label=linux
	root=/dev/sda1
	initrd=/boot/initrd-2.6.27-8-generic
	append="quiet splash"
	read-only

```

---

### Post by gnrathon on 2008-11-18
i dont under stand

would "quite splash" disable the splash?


here is my lilo.conf file for reference:
```
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/sda

# Specifies the device that should be mounted as root. (`/')
#
#root=/dev/sda1

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=20

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#	prompt
#	delay=100
#	timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1
	append="root=/dev/sda1  "
	initrd=/initrd.img
	
image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
#	restricted
#	alias=2
	append="root=/dev/sda1  "
	initrd=/initrd.img.old
	



# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3

```

---

### Post by volanin on 2008-11-18
Here!
Just change the first "append=" instance of the configuration file:

```
# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
```

to this:
*(uncomment the line and add the options)*

```
# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
append="quiet splash"
```

And don't forget to run lilo after saving the file:
$ sudo lilo


> would "quite splash" disable the splash?

These are two different kernel options:

**quiet:** Be silent and do not display lots of text.
**splash:** Enable usplash progressbar.
:)

---

### Post by gnrathon on 2008-11-18
I did exactly as you said and no success 

i installed lilo through the ubuntu alternet CD if it helps

---

### Post by volanin on 2008-11-18
Oh, my bad.
I wrote:

**append="quiet usplash"**

But the correct option is:

**append="quiet _splash_"**

I already fixed it in the above post.
But fix it in your lilo.conf, and then rerun lilo!
Also, you might want to reinstall usplash, like this:

**$ sudo aptitude reinstall usplash**
**$ sudo lilo**

-----

If it still does not work, edit your /etc/usplash.conf and type this:

```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1024
yres=768
```

And after saving the file, run:

**$ sudo update-initramfs -u**
**$ sudo lilo**

-----

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)

---

### Post by gnrathon on 2008-11-18
Did every thing *** you said, again...., AND.........

no success :(

---

### Post by volanin on 2008-11-18
> **gnrathon said:**
> Did every thing *** you said, again...., AND.........
no success :(

Man... I am sorry than.
That was all I know.
:(


[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)

---

### Post by sjafri on 2008-11-18
they works great on my laptop but it's started on second box, but it's doesn't matter since it look cool. 
thanks

---

### Post by volanin on 2008-11-18
> **sjafri said:**
> they works great on my laptop but it's started on second box, but it's doesn't matter since it look cool. 
thanks

Yeah, you are right!
This "starting-in-the-second-box" thing is making me mad already!
I will try to fix it for the next version, if I don't go mad before!

Thank you a lot for the support!
:)

__________________

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)

---

### Post by Vadi on 2008-11-18
I don't think I'm getting the double bars anymore, however the shutdown bar is still pretty off :\

---

### Post by cszikszoy on 2008-11-18
Thanks for this!  Startup works great, shutdown however is a bit off.  The shutdown bar scrolls smoothly until it has about 40% left, then the system actually reboots.

---

### Post by volanin on 2008-11-19
> Thanks for this!
Startup works great, shutdown however is a bit off.
The shutdown bar scrolls smoothly until it has about 40% left, then the system actually reboots.

Does this happens in every shutdown?

Shutdown times are harder to predict. They change quite more than boot times,
since there are some shutdown scripts that sometimes take 1 second,
sometimes take 5... also, shutdown has other problems, for example,
the processes are killed seconds before rebooting, and yes, this
includes usplash.

So for shutdown I usually prefer to let the bar finish SOONER.
I mean, it will empty completely... and the system will shutdown a few seconds later.
With a nice theme implementation, this can be beautifully disguised.
And it will all feel more natural.

But if your bar is still 40% full when the system shuts down...
... that's very bad.


So many things to do... so little time!
:)


Anyway, next version will be out soon.
Thank you for the feedback!

__________________

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)

---

### Post by Martje_001 on 2008-11-19
The description is not correct (sorry):
> /usr/share/**ubuntu**-smooth
needs to be:
> /usr/share/**usplash**-smooth

---

### Post by Vadi on 2008-11-19
Maybe you should consider a bouncy bar for shutdown for now.

Also try logging the elapsed shutdown time to some file regularly, so when the process is killed, you'll at least know the time it took?

---

### Post by volanin on 2008-11-19
> needs to be:
/usr/share/usplash-smooth

Thanks a lot.
Already fixed for 0.4!


> Also try logging the elapsed shutdown time to some file regularly, so when the process is killed, you'll at least know the time it took?

That's exactly what is done now!
The problem is in the shutdown scripts that, by design, take variable amounts of time to complete.
I am already thinking on a solution, maybe for version 0.5, but keep the ideas coming!
:)


> Maybe you should consider a bouncy bar for shutdown for now.

This is theme-dependent!
In practice, I could even use one screen for boot, and another totally different for shutdown.
But for now I chose to use the default usplash, because everybody is used to it, and so it
helps me detect errors very quickly!

---

### Post by _mario_ on 2008-11-19
> **volanin said:**
> This is the original Ubuntu Usplash for Intrepid Ibex with an exciting twist!

**Now the progress bar is time-based!**

What does it means?
Well...

i didn't try the new package yet, but nevertheless i have a question: what happens if i have to enter a password during boot because of an encrypted file system? will the progress bar keep advancing and finally will show completion while the boot process is still halted waiting for my password?
or does the progress bar stop for user events?

ciao,
Mario

---

### Post by Martje_001 on 2008-11-19
OK, my usplash doesn't work anymore (even after removing the smooth package). Not that I care, but my family does. Can you help me troubleshoot? Where should I look first?

---

### Post by volanin on 2008-11-19
> OK, my usplash doesn't work anymore (even after removing the smooth package). Not that I care, but my family does. Can you help me troubleshoot? Where should I look first?

Try this:
[b]$ sudo aptitude reinstall usplash-theme-ubuntu
$ sudo update-alternatives --config usplash-artwork.so
$ sudo update-initramfs -u[/b]

> i didn't try the new package yet, but nevertheless i have a question: what happens if i have to enter a password during boot because of an encrypted file system? will the progress bar keep advancing and finally will show completion while the boot process is still halted waiting for my password? or does the progress bar stop for user events?

That's a very nice point.
In the current version, the progressbar will keep advancing.
This is something I have not thought about before, but I'll look into it for future versions!
:)

---

### Post by volanin on 2008-11-20
[b]Version 0.4 is out!
This is the version you all have been waiting for![/b]

[i]Changelog:

&#8226; Now the progressbar will freeze while ubuntu is performing a filesystem check.
And the status progress will be displayed in text below!

&#8226; Usplash-smooth now saves the correct boot time even if a filesystem check happens!
No more wrong boot times in the next boot.

&#8226; Fix the problem with the start of the animation during boot, that only appeared after the second block of the bar.
Now the animation is smooth since the beginning.

&#8226; Improved the package scripts, installation and description.

&#8226; Added the function time_elapsed() in libusplash-smooth, to give even more tools for theme creators to perform smooth animations.
Theme creators, version 0.5 will be dedicated for you.
Be prepared to create a smooth version of your theme!

TO-DO:

&#8226; The usplash themes for kubuntu, xubuntu and edubuntu will be released in the next version.

&#8226; Support for freezing the progressbar during user input is still missing.
This will require a few modifications in usplash source code to be done properly.
I'll submit some patches upstream, and ship a patched usplash for Intrepid bundled in a future version.[/i]

__________________

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)
__________________

**_Download here:_**

Usplash-Smooth in _[Gnome-Look.org]("http://gnome-look.org/content/show.php?content=93386")_ and _[Ubuntu-Art.org]("http://ubuntu-art.org/content/show.php?content=93394")_!
_[Usplash-Smooth PPA]("https://launchpad.net/~usplash-smooth/+archive")_!

---

### Post by oedipuss on 2008-11-20
Wow, it's remarkably accurate, isn't it?

For some reason I didn't think booting up would be so consistent..

---

### Post by Vadi on 2008-11-20
I think it depends on your setup and whatnot. For me it's +/- 2 seconds at times.

---

### Post by volanin on 2008-11-20
> **Vadi said:**
> I think it depends on your setup and whatnot. For me it's +/- 2 seconds at times.

These +/- 2 seconds are unavoidable.
Even in the MacOSX implementation these fluctuations occur.
They are intrinsec to this time-based progressbar design, because we are
not predicting boot times, just guessing it based on the previous boot.
:)

__________________

[b]Usplash Smooth version 0.4 is out!
_[Grab yours now]("http://gnome-look.org/content/show.php/Ubuntu+Usplash+Smooth?content=93386")_![/b]

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)

---

### Post by Vadi on 2008-11-20
Yeah, it's not an issue at all.

---

### Post by turezky on 2008-11-20
This tool is awesome ;)
However this stuff with +/- 2 seconds is solvable I think.
Why don't make prediction based on previous results, maybe some *exponential smoothing*? It's rather simple, and it would adjust time better. I think it's worth trying at least :) What you say?

---

### Post by Vadi on 2008-11-20
Question... what is considered to be the "homepage" of the project?

Like one you'd like people to go to after they've just heard about this.

---

### Post by Jay_Bee on 2008-11-20
Umm... great project man, but why did you put a link on Gnome-look to automatically vote good?
I would vote anyway, but still you should correct that.

---

### Post by Vadi on 2008-11-20
His link is [http://gnome-look.org/content/show.php?content=93386](http://gnome-look.org/content/show.php?content=93386) ... the link to vote is [http://gnome-look.org/content/show.php?content=93386](http://gnome-look.org/content/show.php?content=93386)**&vote=good**&tan=96249967&PHPSESSID=df5df8129c14f594bf30d83f653bb5fd

So I don't think his link votes :P

---

### Post by Jay_Bee on 2008-11-20
I was referring to his last post.

> **volanin said:**
> Version 0.4 is out!
**_Download here:_**

Usplash-Smooth in _[Gnome-Look.org]("http://gnome-look.org/content/show.php?content=93386&vote=good&tan=24597295")_
You see - [http://gnome-look.org/content/show.php?content=93386&](http://gnome-look.org/content/show.php?content=93386&)**vote=good**&tan=24597295

---

### Post by Starks on 2008-11-20
Shutdown animation works fine. Startup animation only appears for a second and no progress is made; rest of boot is either text or blank screen before GDM.

---

### Post by kspringer on 2008-11-20
Hmmm.

I hesitate to try this with Kubuntu. No joy for that, I fear, right?

k

---

### Post by Vadi on 2008-11-20
He hasn't made the kubuntu splash works with this yet afaik, the next version should do  that

---

### Post by mihai.ile on 2008-11-20
By the speed this is going (4 versions in 2 days?) the next version is what? tomorrow morning? :D
anyway great work and I hope you keep it like this until you have a finished product (a reasonable small amount of bugs in it) and don't lose the project somewhere in the middle where it is usable but not quite for everyone, just like many unfinished projects out there...

(In my opinion a simple finished project is more useful than a more complex and unfinished one)

---

### Post by volanin on 2008-11-20
Ok, a lot of posts since I last checked the thread!
That's a good sign, thank you all!
Let me try to answer everybody.

> **turezky]This tool is awesome
However this stuff with +/- 2 seconds is solvable I think.
Why don't make prediction based on previous results, maybe some exponential smoothing? It's rather simple, and it would adjust time better. I think it's worth trying at least[/QUOTE]

It's a nice idea, and not hard to try.
But think with me. At least in my computer, 4 in 5 times the usplash screen
shows for 12.99 seconds. In the other time it lasts for 14.10 seconds. If I
start to make the predictions based in many boot times, I would probably
have something along the lines of 13.3 to 13.5 seconds, which would be
wrong in the 4 cases it's correct now, and the 1 case where it's off!

That's just what I thought quickly here though.
I will try it in my experimental versions and see if it works!

[QUOTE=Vadi]Question... what is considered to be the "homepage" of the project?
Like one you'd like people to go to after they've just heard about this.[/QUOTE]

For now, there is no official homepage.
My "official" pages are this forum thread and the gnome-look.org pages.
I am coding this like crazy these last few days, and had no time for putting
one up. Maybe I'll cook something for the next version.
:)

[QUOTE=Jay_Bee]Umm... great project man, but why did you put a link on Gnome-look to automatically vote good?
I would vote anyway, but still you should correct that.[/QUOTE]

OMG!
That was my mistake.
I personally hate when people do that.
It's fixed, and I deeply apologize.

Anyway, each time you vote, gnome-look.org generates a new ID in the URL.
So, by using my wrong link, I was receiving many votes from the same ID,
and they are not considered. Damn, usplash-smooth should have been 90%
by now! Anyway, thanks for the warning.

[QUOTE=Starks]Shutdown animation works fine. Startup animation only appears for a second and no progress is made said:**
> 

Does this happens in every boot?
Does normal usplash works for you?

[QUOTE=kspringer]I hesitate to try this with Kubuntu. No joy for that, I fear, right?
[QUOTE=Vadi]He hasn't made the kubuntu splash works with this yet afaik, the next version should do that[/QUOTE]

Well, you can safely use the theme as is!
It will work nicely, but it will display the ubuntu artwork instead of kubuntu.
As Vadi said, the official kubuntu theme will be available in the next version!
:)

[QUOTE=mihai007]By the speed this is going (4 versions in 2 days?) the next version is what? tomorrow morning?
anyway great work and I hope you keep it like this until you have a finished product (a reasonable small amount of bugs in it) and don't lose the project somewhere in the middle where it is usable but not quite for everyone, just like many unfinished projects out there...

(In my opinion a simple finished project is more useful than a more complex and unfinished one)[/QUOTE]

Hahahaha no, not for tomorrow!
I have a friend's wedding to go tonight. Damn! :)

But you say very wise words there. For a time I had these thoughts of
grandeur and glory, and I even caught myself thinking about rewriting
all of usplash!!

But then I came to my senses:
"Man, this is just a progressbar, relax!"

Believe me:
This project will stay small, and will mature that way.
And I really hope it gets into shape for Jaunty. A simple and small
improvement to make the ubuntu boot screen greater and more refreshing!
:)

__________________

[b]Usplash Smooth version 0.4 is out!
_[Grab yours now]("http://gnome-look.org/content/show.php/Ubuntu+Usplash+Smooth?content=93386")_![/b]

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)

---

### Post by Vadi on 2008-11-20
> **volanin said:**
> 
Believe me:
This project will stay small, and will mature that way.
And I really hope it gets into shape for Jaunty. A simple and small
improvement to make the ubuntu boot screen greater and more refreshing!
:)

Yeah, that's a quite good goal. I hope you'll find something else you can improve, you're doing it great :)

---

### Post by Vadi on 2008-11-22
Submitted to Digg: [http://digg.com/linux_unix/Ubuntu_Usplash_Smooth](http://digg.com/linux_unix/Ubuntu_Usplash_Smooth)

Should add the link to the OP post

---

### Post by david_edmundson on 2008-11-22
I've hacked up a Kubuntu version here. Couldn't manage to change the debian name, so it will conflict with ubuntu-smooth-splash. I can code, but I can't figure out these control files...!

Anyhoo. here is a deb.
[http://www.sharpley.org.uk/uploads/usplash-smooth_0.4_i386.deb](http://www.sharpley.org.uk/uploads/usplash-smooth_0.4_i386.deb)

---

### Post by unimatrix on 2008-11-22
Dude, nice idea, but I see many problems with it... 
What happens on a laptop that sometimes boots on battery and sometimes on AC power? The boot times differ quite a lot, because of powersaving and stuff. Most of the times it will be very inaccurate. Unless maybe if you recorded both battery and AC boot times and make it figure out which one should be used.

Also what happens when fsck starts checking your harddrive? It always takes a different amount of time. (My suggestion would be to freeze it)

What about if for some reason a module fails to load or a daemon suddenly takes 10 times longer to load? These things happen. I suggest you also record the boot loading output every time and immediately revert to normal non-smooth progress bar if something is different from the last time.

---

### Post by david_edmundson on 2008-11-22
A fsck will pause the progress bar. In fact any init script can if it is modified to send the "pause" message

---

### Post by plagiats on 2008-11-23
I claim the original idea for this !
For those who read french : [http://linuxfr.org/~plagiats/9164.html](http://linuxfr.org/~plagiats/9164.html)

But more seriously, congratulations to volanin for making this a reality.

---

### Post by turezky on 2008-11-23
Hehe :)
Nice post for the user with the nick "plagiats" :)

---

### Post by volanin on 2008-11-23
[QUOTE=Vadi]Submitted to Digg: [http://digg.com/linux_unix/Ubuntu_Usplash_Smooth](http://digg.com/linux_unix/Ubuntu_Usplash_Smooth)[/QUOTE]

I just can't believe what I am seeing!
This really made it to Digg's frontpage!
Thank you for Vadi and everybody that dugg it! Oh... wow...
:)


[QUOTE=david_edmundson]I've hacked up a Kubuntu version here. Couldn't manage to change the debian name, so it will conflict with ubuntu-smooth-splash. I can code, but I can't figure out these control files...![/QUOTE]

Nice initiative!
:)

Anyway, I am just finishing some details of the next version.
And the "official" Kubuntu version is already ready!
It will be out Real Soon Now!


[QUOTE=unimatrix]What about if for some reason a module fails to load or a daemon suddenly takes 10 times longer to load? These things happen. I suggest you also record the boot loading output every time and immediately revert to normal non-smooth progress bar if something is different from the last time.[/QUOTE]

This can happen indeed.
But this is an exceptional case.
Anyway, usplash has a 15 second timeout, and if anything hangs up bad,
it will display the console with the appropriate error messages.

There is another solution proposed by graingert in Brainstorm and a few
more people that's really interesting, and should deal even with these
exceptional cases very cleanly. I'll implement it really soon as well!


[QUOTE=plagiats]
I claim the original idea for this !
For those who read french : [http://linuxfr.org/~plagiats/9164.html](http://linuxfr.org/~plagiats/9164.html)
But more seriously, congratulations to volanin for making this a reality.[/QUOTE]

Oh damn... my idea-stealing tic was discovered!
:)

---

### Post by zexarious on 2008-11-23
You should make a .deb, and a repo!!!

I don't want to install one version and then forget about it and never update!!!

Thanks a lot for this!

---

### Post by directhex on 2008-11-23
volanin, does your experience with USplash extend as far as making USplash able to deal correctly with non-4:3 framebuffer modes? Currently the "widescreen" support consists of knowing when a widescreen monitor is used, and using a squashed 4:3 theme which stretches to 16:9

---

### Post by CerebroJD on 2008-11-23
I support the idea of a repo as well, as it would be easier to update that way.

Widescreen detection and the utilization of wide-ratio images would be a definite benefit.  The squished bar and logo shouldnt really be necessary at this point. ;)

---

### Post by Vadi on 2008-11-23
> **zexarious said:**
> You should make a .deb, and a repo!!!

I don't want to install one version and then forget about it and never update!!!

Thanks a lot for this!

He actually did. There are 2 .debs in the .tar.gz file, and a PPA (repository)

---

### Post by Vadi on 2008-11-23
> **volanin said:**
> I just can't believe what I am seeing!
This really made it to Digg's frontpage!
Thank you for Vadi and everybody that dugg it! Oh... wow...
:)

Such a useful project deserves attention ;)

---

### Post by Baggers on 2008-11-24
Gave it a bash just because it sounded nice but I am truly floored at just how much of a difference it makes to my boot-up. It somehow feels like more is being done rather than stuttering its way through and yet I still get all the useful info.
Well done sir, still room for improvement but very nearly there. Hope to see this become default in future.

---

### Post by tbuht_1 on 2008-11-24
Hey guys, sorry but this just isn't working on mine...I reverted back to the original usplash on the directions you gave someone on how to uninstall. During my restart, my screen would go crazy and I wouldn't even see the bar...on the startup, it would work the same way as usual (not smooth). Any suggestions?

---

### Post by TVMA on 2008-11-26
this is awesome.. thanks!

---

### Post by volanin on 2008-11-26
[QUOTE=directhex]volanin, does your experience with USplash extend as far as making USplash able to deal correctly with non-4:3 framebuffer modes? Currently the "widescreen" support consists of knowing when a widescreen monitor is used, and using a squashed 4:3 theme which stretches to 16:9[/QUOTE]

The problem is that usplash uses SVGAlib as a backend.
And as far as I know, widescreen resolutions are not natively supported.
:( 


[QUOTE=Vadi]Such a useful project deserves attention[/QUOTE]

[QUOTE=Baggers]Gave it a bash just because it sounded nice but I am truly floored at just how much of a difference it makes to my boot-up. It somehow feels like more is being done rather than stuttering its way through and yet I still get all the useful info. Well done sir, still room for improvement but very nearly there. Hope to see this become default in future.[/QUOTE]

Well, it seems that plymouth is scheduled for discussion in Jaunty UDS!
If it becomes default in ubuntu, then we'll have something really great!
Anyway, thanks a lot for the incentive, and let's move on!
:)


[QUOTE=tbuht_1]Hey guys, sorry but this just isn't working on mine...I reverted back to the original usplash on the directions you gave someone on how to uninstall. During my restart, my screen would go crazy and I wouldn't even see the bar...on the startup, it would work the same way as usual (not smooth). Any suggestions?[/QUOTE]

It's strange because usplash-smooth uses the exactly same source code for
the ubuntu theme, with a few extra functions for the time-based progressbar.
So it shouldn't break easily if normal usplash works for you.

Neverthless, version 0.5 code and themes are already complete. I am just
touching up the documentation a little before releasing. Then you should
definitely give it another try!
:)

---

### Post by Jay_Bee on 2008-11-27
I tried it and it works great for starting up, but it doesn't work correctly on shutdown.
It starts unloading the bar slowly, after about 2 seconds it is restarted to full bar and again unloading... then the system shuts down with bar at about 1/5 from the full bar (meaning, it didn't actually move much).
What info could I provide you to help resolve this?

---

### Post by volanin on 2008-11-27
> **Jay_Bee said:**
> I tried it and it works great for starting up, but it doesn't work correctly on shutdown.
It starts unloading the bar slowly, after about 2 seconds it is restarted to full bar and again unloading... then the system shuts down with bar at about 1/5 from the full bar (meaning, it didn't actually move much).
What info could I provide you to help resolve this?

I have seem this happening in Jaunty, but not on Intrepid.
I am still investigating what might cause it though.
Thank you for the bug report!
:)

---

### Post by cszikszoy on 2008-11-28
> **Jay_Bee said:**
> I tried it and it works great for starting up, but it doesn't work correctly on shutdown.
It starts unloading the bar slowly, after about 2 seconds it is restarted to full bar and again unloading... then the system shuts down with bar at about 1/5 from the full bar (meaning, it didn't actually move much).
What info could I provide you to help resolve this?

I can confirm this on Intrepid as well.  Startup works fine, but on shutdown I have the same thing happening as the above poster.

---

### Post by Kevrox on 2008-11-28
I had the issue of big fat chunky boot and shutdown splash

When I did a hardy to intrepid upgrade... my nice clean crisp boot and shut down splash screen followed. The I decided to do a clean install... big fat chunky boot splash and loading bar.

Reloaded hardy and nice again.. ( all on it's own mind you no tweaking of startupmanager) then upgraded again and was still nice. The redid a clean install and yuk again.
The new install was done with the altenate iso, not sure if that has anything to do with it.
I found your smooth boot and liked it and hoped it would solve my problem. But no.

I ended up using startupmanager to get the res right (1280x1024)... boot splash is nice now but the shutdown one is like a negative of what it should be... all strange colours.  the original and the new smooth as well, not sure what to try next.. perhaps nvidia drivers 177.80 is the ssue???
any ideas???
Thanks Kev

---

### Post by kamitsukai on 2008-11-28
> **cszikszoy said:**
> I can confirm this on Intrepid as well.  Startup works fine, but on shutdown I have the same thing happening as the above poster.

I think this may slowly turn into an epidemic as mine started off fine for the first 10 or so reboots (on intrepid) but now it goes so far then starts from the beginning again on shutdown...

---

### Post by Kevrox on 2008-11-29
just for anyone that has the funny colours when they shut down..
I changed my colour bit rate from 8 to 24 in startupmanager and now have nice crisp correct colour on shutdown...
So for me Smooth usplash works great... thanks...

---

### Post by GSMX on 2008-11-29
I really like this :)
Great work, volanin!

It seems like it boots up faster, while it actually doesn't (I timed it ;) )

Although I do have the same issue with shutdown... shutdown is something like 5 times faster than bootup and at about 40%, it already shuts down.

I hope this will be default in jaunty!

---

### Post by AFarris01 on 2008-12-03
I'd love to see how this works, as i've seen so many positive comments about it... but unfortunately, the smooth usplash doesnt work on my laptop....

im running hardy, and the .4 version of the smooth usplash theme... whenever i boot up after installing it though, all i get is the text output, no splash screen at all :(

i tried installing startup manager to fix the problem, but no change... however if i switch back to the default theme, it works perfect,

---

### Post by AFarris01 on 2008-12-07
just tried on my desktop running hardy... same thing.

do i have to be using intrepid to be able to use .4?

---

### Post by Martje_001 on 2008-12-08
> **AFarris01 said:**
> just tried on my desktop running hardy... same thing.

do i have to be using intrepid to be able to use .4?
Yes, it does not work on Hardy.

---

### Post by QwUo173Hy on 2008-12-15
Just installed on Intrepid from the PPA. The startup works great but the shutdown progress bar is all over the place. I made a video to illustrate it. Download the AVI from my shared page:

[http://www.box.net/shared/cmc22j7zgc]("http://www.box.net/shared/cmc22j7zgc")

---

### Post by Skip Da Shu on 2008-12-28
Getting an 'invalid video mode' error at start up.  I can wait 30 seconds and let it go on and it seems to work but something isn't right.

I have it set to 1600x1200 (SyncMaster 204b) via Startup Manager.  This is the top entry in /boot/grub/menu.lst:

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		57a57cc2-abac-4c3a-afad-a0d35cdcaa5a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=57a57cc2-abac-4c3a-afad-a0d35cdcaa5a ro vga=799 splash quiet 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

PS: I am getting the grub background I expect but then I get some amount of booting text, then your smooth usplash.  Shouldn't "quiet" stop the boot text?

UPDATE:  Well screwed it up worse and ended up having to reconfig X-server...lost compiz and all usplash screens but... the text and the video mode error are gone... I'll go reinstall usplash and the smoothie.

---

### Post by vishalrao on 2008-12-28
MadsRH just blogged about this. Any idea when/if this will show up in Jaunty? [http://anotherubuntu.blogspot.com/2008/12/ubuntu-usplash-smooth.html](http://anotherubuntu.blogspot.com/2008/12/ubuntu-usplash-smooth.html)

---

### Post by Tom--d on 2008-12-29
I'm on Hardy.

Is it possiable to release a version for it please?

Thanks,
Tom :)

---

### Post by seanlano on 2009-02-02
Firstly, I LOVE this splash. It is just brilliant. 

But, here is how I got it to show properly on a 1280x800 widscreen laptop. 

I set /boot/grub/menu.lst to say:
```

title		Ubuntu 8.10 Intrepid Ibex
uuid		1dda3598-c186-434f-88d3-e0914a6daa28
kernel		/vmlinuz-2.6.27-7-generic... (blah blah)... ro quiet splash  **vga=0x0368**
initrd		/initrd.img-2.6.27-7-generic
quiet
```
where **vga=0x0368** corresponds to 1280x800, 24bit for my framebuffer, from the command:
```
sudo hwinfo --framebuffer
``` Obviously you need hwinfo installed. 

I then set startupmanager to have the usplash theme show at 1280x1024, 24bits. So I lose a bit of the black at the bottom, meaning the text and bar are a bit further down the screen, but it doesn't bother me, and it looks brilliant! I guess this can be applied to other resolutions as well, as long as the width in grub and in startupmanager are the same. 

Hope this helps someone. :)

---

### Post by smartboyathome on 2009-02-02
If that VGA line doesn't work, then you probably have an Intel graphics card, and need to install 915resolution (a static version at that so it can be built into the initramfs). Unfotunately, I only know how to do this on Arch, so you'd have to apply [these instructions]("http://wiki.archlinux.org/index.php/Uvesafb#Uvesafb_and_915resolution") generally to Ubuntu.

---

### Post by MadsRH on 2009-02-02
> **vishalrao said:**
> MadsRH just blogged about this. Any idea when/if this will show up in Jaunty? [http://anotherubuntu.blogspot.com/2008/12/ubuntu-usplash-smooth.html](http://anotherubuntu.blogspot.com/2008/12/ubuntu-usplash-smooth.html)

Thanks for mentioning it :D

I have no idea if this will make it into Jaunty. Has it been suggested to the related team? (desktop- / boot- / ???-team)

---

### Post by Vadi on 2009-02-02
Kernel team, I think. And I'm not sure.

---

### Post by kieranjones on 2009-03-13
Hi,

I was actually attempting to get Splashy to work and came accross this topic so instead decided to install your usplash-smooth package into the latest alpha of Jaunty (9.04) - at the moment though all I'm getting is text.

I've installed it and no errors are produced, but on reboot, shutdown or startup all I get is the text of what is happening rather than the smooth usplash screen I was so excited about getting.

Any ideas on how to fix this? I could give up and go back to my battle with splashy but this looked more interesting and I hate to give up!

Thanks for your help in advance!

---

### Post by Orlsend on 2009-03-14
Sadly usplash support in going to end in Karmic Koala, I really like Usplash. I can't never see that flickering they keep talking about.

I am downloading this one, It may be the last Usplash I use... STOOPID plymouth!

---

### Post by Sashin on 2009-04-25
Could you please make a Jaunty 64 version of this? One that uses the jaunty usplash theme as a base?

---

### Post by Orlsend on 2009-04-26
Hey has anyone got it running On Jaunty?

---

### Post by icanfly0307 on 2009-06-15
Will usplash-smooth work in Jaunty? I tried installing it but usplash doesn't work. Any suggestions? Thanks.

---

### Post by Sashin on 2009-06-20
I have no idea how to build this for jaunty.
I have no desire to learn it.
But nonetheless I'm getting really really annoyed that no one has made a jaunty version even after finding that plymouth is replacing usplash.

---

### Post by Lightbreeze on 2009-07-17
Actually usplash, and not plymouth, will land in Karmic now. Is anybody still active in this project?

---

### Post by icanfly0307 on 2009-07-17
I figured out a way to install USplash Smooth on Jaunty. It requires you to downgrade your usplash packages to intrepid's version, but all I can say is this: It's completely worth it. :) USplash Smooth works flawlessly on my Jaunty system. Here's how:

1. Go to packages.ubuntu.com, scroll down and search for usplash. Choose "intrepid" from the "Distribution" drop down menu.
2. Download these packages for your architecture: *usplash*, *libusplash0*, and *usplash-theme-ubuntu*.
3. Fire up a terminal and type in "*sudo apt-get remove usplash*". After the uninstallation is complete, type in "*sudo apt-get autoremove*".
4. Next, "cd" to the directory where you downloaded the packages mentioned above. Type "s*udo dpkg -i **". This will install intrepid's usplash packages.
5. Now download usplash smooth, extract the packages, install them and reboot. You should see usplash smooth working properly.

NOTE: On my computer, I had to reboot *twice* in order to get usplash smooth working properly. I'm guessing that usplash determines the boot time during the first reboot and then utilizes this time to get the progress bar working right.

Hope this helps. :)

---

