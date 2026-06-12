---
title: "Usplash Problems"
date: 2009-10-01
forum: Art &amp; Design
---

### Post by zyxyellowxyz on 2009-10-01
I was able to make and complie my own usplash by using the script I found at gnome-look ([http://www.gnome-look.org/content/show.php/How+to+create+a+usplash+for+Jaunty?content=111163](http://www.gnome-look.org/content/show.php/How+to+create+a+usplash+for+Jaunty?content=111163)) and it compiled correctly when I followed the simple directions:
> Unzip the file.
Just replace the images
preserve the resolution
in a terminal, write
cd the folder of the theme
**make**
and, ready!

output from running make:```
make: Circular throbber_back.png <- throbber_back.png.c dependency dropped.
pngtousplash throbber_back.png > throbber_back.png.c
gcc  -g -Wall -fPIC -o throbber_back.png.c.o -c throbber_back.png.c
make: Circular throbber_back_16.png <- throbber_back_16.png.c dependency dropped.
pngtousplash throbber_back_16.png > throbber_back_16.png.c
gcc  -g -Wall -fPIC -o throbber_back_16.png.c.o -c throbber_back_16.png.c
make: Circular throbber_fore.png <- throbber_fore.png.c dependency dropped.
pngtousplash throbber_fore.png > throbber_fore.png.c
gcc  -g -Wall -fPIC -o throbber_fore.png.c.o -c throbber_fore.png.c
make: Circular throbber_fore_16.png <- throbber_fore_16.png.c dependency dropped.
pngtousplash throbber_fore_16.png > throbber_fore_16.png.c
gcc  -g -Wall -fPIC -o throbber_fore_16.png.c.o -c throbber_fore_16.png.c
make: Circular usplash_1024_768.png <- usplash_1024_768.png.c dependency dropped.
pngtousplash usplash_1024_768.png > usplash_1024_768.png.c
gcc  -g -Wall -fPIC -o usplash_1024_768.png.c.o -c usplash_1024_768.png.c
make: Circular usplash_1365_768_scaled.png <- usplash_1365_768_scaled.png.c dependency dropped.
pngtousplash usplash_1365_768_scaled.png > usplash_1365_768_scaled.png.c
gcc  -g -Wall -fPIC -o usplash_1365_768_scaled.png.c.o -c usplash_1365_768_scaled.png.c
make: Circular usplash_800_600.png <- usplash_800_600.png.c dependency dropped.
pngtousplash usplash_800_600.png > usplash_800_600.png.c
gcc  -g -Wall -fPIC -o usplash_800_600.png.c.o -c usplash_800_600.png.c
make: Circular usplash_640_400.png <- usplash_640_400.png.c dependency dropped.
pngtousplash usplash_640_400.png > usplash_640_400.png.c
gcc  -g -Wall -fPIC -o usplash_640_400.png.c.o -c usplash_640_400.png.c
make: Circular usplash_640_480.png <- usplash_640_480.png.c dependency dropped.
pngtousplash usplash_640_480.png > usplash_640_480.png.c
gcc  -g -Wall -fPIC -o usplash_640_480.png.c.o -c usplash_640_480.png.c
gcc  -g -Wall -fPIC -o usplash-theme-moon.c.o -c usplash-theme-moon.c
gcc  -g -Wall -fPIC -shared -o usplash-theme-moon.so throbber_back.png.c.o throbber_back_16.png.c.o throbber_fore.png.c.o throbber_fore_16.png.c.o usplash_1024_768.png.c.o usplash_1365_768_scaled.png.c.o usplash_800_600.png.c.o usplash_640_400.png.c.o usplash_640_480.png.c.o usplash-theme-moon.c.o
rm usplash_1024_768.png.c usplash_1365_768_scaled.png.c throbber_fore_16.png.c throbber_back.png.c usplash_640_480.png.c usplash_640_400.png.c throbber_back_16.png.c throbber_fore.png.c usplash_800_600.png.c
```

does anyone see any errors? I don't. All of my images were converted to 256, and all use the same pallet (saved it in GIMP so I don't lose it).

And here comes what I don't understand:
the throbber image never goes past the initial background image and I can see the box for the verbose output (and no text).
I would like to see the verbose output text in the box, and the throbber image. I didn't change anything in the supplied *.c file (except I changed the name to usplash-theme-moon.c from *-ubuntu.c because I didn't want to overwrite the original) and I changed the makefile to where it was looking for *-moon.c instead of *-ubuntu.c (so it wouldn't fail).

If it might help, here is the *.c file:```
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
}

void t_clear_progressbar(struct usplash_theme *theme) {
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back);
}

void t_clear_progressbar_16(struct usplash_theme *theme) {
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_16);
}

void t_draw_progressbar(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back.width * percentage / 100);
    if(percentage == 0)
        usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back);
    if(percentage < 0){/* Unloading */
        w *= -1;
        /* Draw background to left of foreground */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back.height, 
                         &pixmap_throbber_back, 0, 0);
        /* Draw foreground to right of background */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back.width - w,
                         pixmap_throbber_back.height, &pixmap_throbber_fore, w, 0);
    }
    else{/* Loading */
        /* Draw foreground to left of background */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back.height, 
                         &pixmap_throbber_fore, 0, 0);
        /* Draw background ot right of foreground */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back.width - w, pixmap_throbber_back.height, 
                         &pixmap_throbber_back, w, 0);
    }
}

void t_draw_progressbar_16(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back_16.width * percentage / 100);
    if (percentage == 0)
        usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back_16);
    if (percentage < 0){ /* Unloading */
        w *= -1;
        /* Draw background to left of foreground */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_16.height, 
                         &pixmap_throbber_back_16, 0, 0);
        /* Draw foreground to right of background */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back_16.width - w,
                         pixmap_throbber_back_16.height, &pixmap_throbber_fore_16, w, 0);
    }
    else{/* Loading */
        /* Draw foreground to left of background */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back_16.height, 
                         &pixmap_throbber_fore_16, 0, 0);
        /* Draw background to right of foreground */
        usplash_put_part(theme->progressbar_x + w, theme->progressbar_y, pixmap_throbber_back_16.width - w, pixmap_throbber_back_16.height, 
                         &pixmap_throbber_back_16, w, 0);
    }
}

void t_animate_step(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 56;
    static int step_width = 2;
    static int num_steps = 0;
    int x1;
    int x2;
    num_steps = (pixmap_throbber_fore.width - pulse_width)/2;

    if (pulsating) {
        if(pulsate_step < num_steps/2+1){
	        x1 = 2 * step_width * pulsate_step;
        }
        else{
	        x1 = pixmap_throbber_fore.width - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);
        }
        x2 = x1 + pulse_width;

        /* Draw progress bar background on left side of foreground 'pulse' */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, x1,
                         pixmap_throbber_back.height, &pixmap_throbber_back, 0, 0);
        /* Draw progress bar foreground 'pulse' */
        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_back.height, &pixmap_throbber_fore, x1, 0);
        /* Draw progress bar background on right side of foreground 'pulse' */
        usplash_put_part(theme->progressbar_x + x2, theme->progressbar_y, pixmap_throbber_back.width - x2,
                         pixmap_throbber_back.height, &pixmap_throbber_back, x2, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}

void t_animate_step_16(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 28;
    static int step_width = 2;
    static int num_steps = 0;
    int x1;
    int x2;
    num_steps = (pixmap_throbber_fore.width - pulse_width)/2;

    if (pulsating) {
        if(pulsate_step < num_steps/2+1){
	        x1 = 2 * step_width * pulsate_step;
        }
        else{
            x1 = pixmap_throbber_fore_16.width - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);
        }
        x2 = x1 + pulse_width;

        /* Draw progress bar background on left side of foreground 'pulse' */
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, x1,
                         pixmap_throbber_back_16.height, &pixmap_throbber_back_16, 0, 0);
        /* Draw progress bar foreground 'pulse' */
        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_back_16.height, &pixmap_throbber_fore_16, x1, 0);
        /* Draw progress bar background on right side of foreground 'pulse' */
        usplash_put_part(theme->progressbar_x + x2, theme->progressbar_y, pixmap_throbber_back_16.width - x2,
                         pixmap_throbber_back_16.height, &pixmap_throbber_back_16, x2, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}
```

and the Makefile:```
CC=gcc
CFLAGS=-g -Wall -fPIC
LDFLAGS=
INCLUDES=

COMPILE = $(CC) $(INCLUDES) $(CFLAGS)
LINK = $(CC) $(CFLAGS) $(LDFLAGS)

INSTALL = /usr/bin/install -c
INSTALL_DATA = $(INSTALL) -m 644
INSTALL_PROGRAM = $(INSTALL) -m 755

usplash-theme-moon.so: throbber_back.png.c.o throbber_back_16.png.c.o throbber_fore.png.c.o throbber_fore_16.png.c.o \
						 usplash_1024_768.png.c.o usplash_1365_768_scaled.png.c.o usplash_800_600.png.c.o \
						 usplash_640_400.png.c.o usplash_640_480.png.c.o usplash-theme-moon.c.o
	$(COMPILE) -shared -o $@ $^

%.png.c: %.png
	pngtousplash $< > $@

%.bdf.c: %.bdf
	bdftousplash $< > $@

%.c.o: %.c
	$(COMPILE) -o $@ -c $<

install:
	$(INSTALL) -d $(DESTDIR)/usr/lib/usplash
	$(INSTALL_PROGRAM) usplash-theme-moon.so $(DESTDIR)/usr/lib/usplash/usplash-theme-moon.so
clean:
	rm -f *.png.c *.bdf.c *.c.o *.so
```

Most programing languages are a little over my head so I can't tell if there is an error in them or not.

Any help would be greatly appreciated.

---

### Post by zyxyellowxyz on 2009-10-02
BUMP
I enabled show text during boot and its not showing up. I still have a black box for the verbose output (text box) and a black box where the throbber should load. I re-indexed the files, and recompiled it with no luck. I don't know what's wrong and would like some help. If need be, I will upload the all the files so someone else can mess with them.

---

