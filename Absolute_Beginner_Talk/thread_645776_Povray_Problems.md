---
title: "Povray Problems"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-12-20
I recently installed povray via Synaptic but when I try and run it from the terminal I get the following errors;

```

james@james-desktop:~$ povray
povray: cannot open the user configuration file /home/james/.povray/3.6/povray.conf: No such file or directory
Persistence of Vision(tm) Ray Tracer Version 3.6.1 (g++ 3.4.1 @
 i686-pc-linux-gnu)
This is an official version prepared by the POV-Ray Team. See the
 documentation on how to contact the authors or visit us on the
 internet at [http://www.povray.org/](http://www.povray.org/).
POV-Ray is based on DKBTrace 2.12 by David K. Buck & Aaron A. Collins
Copyright 1991-2003 Persistence of Vision Team
Copyright 2003-2004 Persistence of Vision Raytracer Pty. Ltd.

Primary POV-Ray 3.5/3.6 Developers: (Alphabetically)
  Chris Cason         Thorsten Froehlich  Nathan Kopp         Ron Parker        

Contributing Authors: (Alphabetically)
  Steve Anger         Eric Barish         Dieter Bayer        Steve A. Bennett  
  David K. Buck       Nicolas Calimet     Aaron A. Collins    Chris Dailey      
  Steve Demlow        Andreas Dilger      Alexander Enzmann   Dan Farmer        
  Mark Gordon         Christoph Hormann   Mike Hough          Chris Huff        
  Kari Kivisalo       Lutz Kretzschmar    Jochen Lippert      Pascal Massimino  
  Jim McElhiney       Douglas Muir        Juha Nieminen       Bill Pulver       
  Eduard Schwan       Wlodzimierz Skiba   Robert Skinner      Yvo Smellenbergh  
  Zsolt Szalavari     Scott Taylor        Massimo Valentini   Timothy Wegner    
  Drew Wells          Chris Young       

Other contributors are listed in the documentation.

Support libraries used by POV-Ray:
  ZLib 1.2.1, Copyright 1995-1998 Jean-loup Gailly and Mark Adler
  LibPNG 1.2.5, Copyright 1998-2002 Glenn Randers-Pehrson
  LibJPEG 6b, Copyright 1998 Thomas G. Lane
  LibTIFF 3.6.1, Copyright 1988-1997 Sam Leffler, 1991-1997 SGI

Usage: POVRAY [+/-]Option1 [+/-]Option2 ... (-h or -? for help)

  Example: POVRAY scene.ini +Iscene.pov +Oscene.tga +FT +W320 +H200
  Example: POVRAY +Iscene.pov +Oscene.tga +FT +W160 +H200 +V -D +X

The n or n.n (0.n) notation following a command-line option listed
below denotes an integer or a floating-point number, respectively.
Brackets mean that this number is optional.

The help screen is divided into several parts. To access one part
just enter the number of the screen after the -? option or the
-help option.

E.g. use -?5 or -help5 to see the help screen about the tracing
options.

  Number  Part
    1     Parsing Options
    2     Output Options
    3     Output Options - display related
    4     Output Options - file related
    5     Tracing Options
    6     Animation Options
    7     Redirecting Options

Parsing options

  I<name> = input file name
  HI<name>= header include file name
  L<name> = library path prefix
  MVn.n   = set compability to version n.n
  SU      = split bounded unions if children are finite
  UR      = remove unnecessary bounding objects

Output options

  Hn      = image height of n pixels
  Wn      = image width of n pixels

  SRn|0.n = start at row n | start row at n percent of image
  ERn|0.n = end   at row n | end   row at n percent of image
  SCn|0.n = start at col n | start col at n percent of image
  ECn|0.n = end   at col n | end   col at n percent of image

  C       = continue aborted trace
  P       = pause before exit
  V       = verbose messages on
  WLn     = set warning level to n
  X[n]    = enable early exit by key hit (every n pixels)

Output options - display related

  D[xy]   = display rendering (in format x, using palette option y)
  SPn     = display mosaic preview, start grid size = 2, 4, 8, 16, ...
  EPn     = display mosaic preview, end grid size   = 2, 4, 8, 16, ...
  UD      = draw vista rectangles

Output options - file related

  B[n]    = Use buffer (of n KB) for output file
  F[x]    = write output file (in format x)
            FC    - Compressed Targa with 24 or 32 bpp
            FN[n] - PNG (n bits/color, n = 5 to 16, default is 8)
            FP    - PPM
            FS    - System specific
            FT    - Uncompressed Targa with 24 or 32 bpp
  O<name> = output file name

  HTx     = write CPU utilization histogram in format x
            HTC - Comma separated values (CSV - spreadsheet)
            HTN - PNG grayscale
            HTP - PPM heightfield
            HTS - System specific
            HTT - Uncompressed TGA heightfield
            HTX - No histogram output
  HN<name>= histogram filename
  HSx.y   = histogram grid number of x, y divisions

Tracing options

  MB[n]   = use bounding slabs (if more than n objects)
  Qn      = image quality (0 = rough, 9 = full)

  A[0.n]  = perform antialiasing (if color change is above n percent)
  AMn     = use non-adaptive (n=1) or adaptive (n=2) supersampling
  J[n.n]  = set antialiasing-jitter (and amount)
  Rn      = set antialiasing-depth (use n X n rays/pixel)

  UA      = use alpha channel
  UL      = use light buffer
  UV      = use vista buffer

Animation options

  Kn.n    = set frame clock to n.n
  KFIn    = set initial frame number to n
  KFFn    = set final frame number to n
  KIn.n   = set initial clock value to n.n
  KFn.n   = set final clock value to n.n
  SFn|0.n = start subset at frame n | start at n percent in sequence
  EFn|0.n = end subset at frame n | end at n percent in sequence
  KC      = calculate clock value for cyclic animation

  UF      = use field rendering
  UO      = use odd lines in odd frames

Redirecting options

  GI<name>= write all .INI parameters to file name
  Gx<name>= write stream x to console (and/or optional file name)
            GA - All streams (except status)
            GD - Debug stream
            GF - Fatal stream
            GR - Render stream
            GS - Statistics stream
            GW - Warning stream

```

Any ideas on what I should do?

---

### Post by philinux on 2007-12-20
Check that 

/home/james/.povray/3.6/povray.conf

is there or try 

sudo povray

Cant see why you'd need sudo though

---

### Post by Matuku on 2007-12-20
/home/james/.povray doesn't even exist; but if I create it then I don't know what I would need in that .conf file.

(sudo povray didn't work either)

---

### Post by Matuku on 2007-12-21
*bump*

---

### Post by philinux on 2007-12-21
Just had a look in synaptic.

What did you install besides povray itself.

---

### Post by Matuku on 2007-12-21
Povray, povray-docs and povray-include.

---

### Post by philinux on 2007-12-21
I'll be honest you got me fascinated with this program. Went to there website. Some great images.

So off to synaptic and installed same as you along with the examples.

I got same error. So I create the folders .povray/3.6 in my home directory and copied these two files into it.
/etc/povray/3.6/povray.conf
/etc/povray/3.6/povray.ini 

Now running it is a pain, from man povray , it gives an example of useage. You have to specify the full path to the .ini and .pov files. Like this.

povray /home/philcb/Desktop/ambient.ini +I/home/philcb/Desktop/ambient.pov

And whoopee it works. It created a lot of these I suppose your supposed to string them together somehow to create an animation.

---

### Post by Matuku on 2007-12-21
So the linux version just does the rendering? It doesn't have a built in text editor, etc, like the windows version? It doesn't even have a GUI?

---

### Post by philinux on 2007-12-21
This is what the description says in synaptic.

> POV-Ray by itself is a command-line utility that will take scene
descriptions, written in a special easy-to-understand language, to
produce ray-traced images (or even a sequence of images, for animations).
You can either write those scene-descriptions by hand, or use external
tools to generate (parts of) the scene.

When it says by itself it sort of hints that there is a gui. Where ....:confused:

---

### Post by philinux on 2007-12-21
Found this. Read it and click the tools link. Interesting.

[http://www.linuxgraphic.org/section3d/povray/index-eng.php](http://www.linuxgraphic.org/section3d/povray/index-eng.php)

[edit] Good news, kpovmodeler is in synaptic

---

