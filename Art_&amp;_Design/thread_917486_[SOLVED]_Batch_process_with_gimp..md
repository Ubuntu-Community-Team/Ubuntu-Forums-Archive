---
title: "[SOLVED] Batch process with gimp."
date: 2008-09-11
forum: Art &amp; Design
---

### Post by VeeDubb on 2008-09-11
What I want to do, but don't know how to do, is use the gimp to batch convert a large number (i.e. over 1000) of images to black and white, using the absolutely wonderful B&W film simulation script that is currently included in Gimp. 

Can anyone help me figure out how to do this?  

I'm quite comfortable with the command line, but the most complicated programming I've ever done was on a Ti-83+ calculator.

Much thanks in advance.

---

### Post by VeeDubb on 2008-10-05
Really?  3 weeks and not a single reply?  I can't believe I'm the only person who ever wanted to do this sort of thing.  Gimp already has a batch processing feature, it's just not quite advanced enough for what I'm trying to do.

---

### Post by Chokkan on 2008-10-06
*bump*
I'd like to know too.

---

### Post by unutbu on 2008-10-11
VeeDubb, 4 weeks ago I read your post and since then have been dabbling off and on trying to find the answer. 
The good news is today I finally succeeded.
The bad news is in general it requires you to do some programming to access Gimp operations from the CLI.

Save this script in ~/.gimp-X.Y/plug-ins
Call it bw_film.py
[php]
#!/usr/bin/env python
__note__="""
This script is a derivative of Carol Spear's resize-batch.py script
See http://carol.gimp.org/gimp/scripting/routines.html#shell
"""
import sys 
import os
from gimpfu import *

def save_jpeg(image, new_file, comment):
    layer = pdb.gimp_image_flatten(image)
    quality = 0.85
    smoothing, optimize, progressive = 0.0, True, False
    subsmp, baseline, restart, dct = 1, False, 0, 0
    pdb.file_jpeg_save(image, layer, new_file, new_file, quality, 
                       smoothing, optimize, progressive, 
                       comment, subsmp, baseline, restart, dct)

def python_fu_bw_film(original_file,film,afilter,rename,newlayer,incLocalContrast,
                      autoLevels,dropGamma,saturate): 
    if os.path.isdir(original_file):
        files=os.listdir(original_file)
    else:
        files=[original_file]
    for original_file in files:
        original_dir,original_basename=os.path.split(original_file)
        (shortname, extension) = os.path.splitext(original_basename)     
        new_name = shortname + '-bw' + extension
        new_dir = os.path.join(original_dir, 'bw')
        if not os.path.isdir(new_dir):
            os.makedirs(new_dir)
        new_file = os.path.join(new_dir, new_name)
        try:
            print "Processing %s"%original_file,
            image = pdb.gimp_file_load(original_file, original_file)
            drawable = pdb.gimp_image_get_active_drawable(image)
            pdb.script_fu_bw_film(image,drawable,film,afilter,rename,newlayer,
                                  incLocalContrast,autoLevels,dropGamma,False)
            save_jpeg(image, new_file, '')
            pdb.gimp_image_delete(image) 
            print "... [OK]"
        except RuntimeError,err:
            print "... [FAILED]"

proc_name="python_fu_bw_film"
blurb="A CLI invokable wrapper for script-fu-bw-film"
help_s="python_fu_bw_film is a wrapper around Serge Mankovski script-fu-bw-film so that script-fu-bw-film can be called from the command line"
author="Unutbu"
copyright_s="Unutbu"
date="2008-10-10"
label="<Toolbox>/Xtns/Batch/_BW Film"
imagetypes=""
params=[(PF_FILE, "original_location", "Original location of the images", ""),
        (PF_INT, "film", "Film", 0),
        (PF_INT, "afilter", "Filter", 1),
        (PF_BOOL, "rename", "Rename", False),
        (PF_BOOL, "newlayer", "New Layer", False),
        (PF_BOOL, "incLocalContrast", "Increase Local Contrast", False),
        (PF_BOOL, "autoLevels", "Auto Levels", False),
        (PF_BOOL, "dropGamma", "Drop Gamma 10%", False),
        (PF_BOOL, "saturate", "Saturate", False),
        ]
results=[]
function=python_fu_bw_film
register(proc_name, blurb, help_s, author, copyright_s, date, label, imagetypes,
         params, results, function)

main()
[/php]
Make it executable:```

chmod -R +x ~/.gimp-X.Y/plug-ins

```
Of course, change ~/.gimp-X.Y to your real .gimp directory. The X,Y depend on the version of gimp you are using.

The script above works with gimp version 2.4. I have not tested it on later versions.

Test that the script works:

```

gimp -i -b '(python-fu-bw-film RUN-NONINTERACTIVE "/path/to/filename.jpg" 0 1 FALSE FALSE FALSE FALSE FALSE FALSE)' -b '(gimp-quit 0)'
```
Change /path/to/filename.jpg to a real image file.
If it works you will see
```

batch command: executed successfully.
```
and you will have a new directory called "bw" in the same directory as filename.jpg. Inside bw will be a file called filename-bw.jpg. This is the output of the BW Film simulation script applied to filename.jpg.

Notice that the interface that GIMP provides for batch scripting is rather complicated. To simplify the interface and allow you to apply the command to all files in a directory, here is a second script which you should save as ~/bin/batch_bw_film.py:
[php]
#!/usr/bin/env python
import sys
import os
import optparse

film_l=["Agfa 200X","Agfapan 25","Agfapan 100","Agfapan 400","Ilford Delta 100",
        "Ilford Delta 400","Ilford Delta 400 Pro & 3200","Ilford FP4","Ilford HP5",
        "Ilford Pan F","Ilford SFX","Ilford XP2 Super","Kodak Tmax 100",
        "Kodak Tmax 400","Kodak Tri-X","Kodak HIE","Normal Contrast","High Contrast",
        "Generic BW","50/50"]
filter_l=["Yellow","Orange","Red","Green","Blue"]
film_s=("Film:\n    "+
        "\n    ".join(
                ["%s => %s"%(num,film) for num,film in enumerate(film_l)]))
filter_s=("Filter:\n    "+
          "\n    ".join(
                  ["%s => %s"%(num,a_filter) for num,a_filter in enumerate(filter_l)]))

usage = ("usage: %prog [options]\n"+
         "batch_bw_film operates on the current working directory!\n\n"+
         film_s+
         "\n\n"+
         filter_s)
parser = optparse.OptionParser(usage=usage)
parser.add_option("--film", dest="film", 
                  default=0,
                  type='int',
                  help="film type", 
                  metavar="NUM")
parser.add_option("--filter", dest="filter", 
                  default=1,
                  type='int',
                  help="filter type", 
                  metavar="NUM")
parser.add_option("--rename", dest="rename",
                  action="store_true", 
                  default=False,
                  help="Rename Layer?")
parser.add_option("--newlayer", dest="newlayer",
                  action="store_true", 
                  default=False,
                  help="New Layer?")
parser.add_option("--contrast", dest="contrast",
                  action="store_true", 
                  default=False,
                  help="Increase Local Contrast")
parser.add_option("--autolevels", dest="autolevels",
                  action="store_true", 
                  default=False,
                  help="Auto Levels")
parser.add_option("--dropgamma", dest="dropGamma",
                  action="store_true", 
                  default=False,
                  help="Drop Gamma 10%")
parser.add_option("--saturate", dest="saturate",
                  action="store_true", 
                  default=False,
                  help="Saturate")
(opt, args) = parser.parse_args()   

opt.filter+=1
def tf(a_bool):
    return 'TRUE' if a_bool else 'FALSE'

cmd=("gimp -i -b "+
     "'(python-fu-bw-film RUN-NONINTERACTIVE \"%s\" %s %s %s %s %s %s %s %s)' -b '(gimp-quit 0)'")%(
         '.',opt.film,opt.filter,tf(opt.rename), 
         tf(opt.newlayer),
         tf(opt.contrast),
         tf(opt.autolevels),
         tf(opt.dropGamma),
         tf(opt.saturate))

print cmd
os.system(cmd)
[/php]
Make it executable:```

chmod -R +x ~/bin
```
To see what options you have, first run
```

~/bin/batch_bw_film.py -h
```

You should see
```

Usage: batch_bw_film.py [options]
batch_bw_film operates on the current working directory!

Film:
    0 => Agfa 200X
    1 => Agfapan 25
    2 => Agfapan 100
    3 => Agfapan 400
    4 => Ilford Delta 100
    5 => Ilford Delta 400
    6 => Ilford Delta 400 Pro & 3200
    7 => Ilford FP4
    8 => Ilford HP5
    9 => Ilford Pan F
    10 => Ilford SFX
    11 => Ilford XP2 Super
    12 => Kodak Tmax 100
    13 => Kodak Tmax 400
    14 => Kodak Tri-X
    15 => Kodak HIE
    16 => Normal Contrast
    17 => High Contrast
    18 => Generic BW
    19 => 50/50

Filter:
    0 => Yellow
    1 => Orange
    2 => Red
    3 => Green
    4 => Blue

Options:
  -h, --help    show this help message and exit
  --film=NUM    film type
  --filter=NUM  filter type
  --rename      Rename Layer?
  --newlayer    New Layer?
  --contrast    Increase Local Contrast
  --autolevels  Auto Levels
  --dropgamma   Drop Gamma 10%
  --saturate    Saturate

```

To use batch_bw_film.py:
```

cd /path/to/image/dir
~/bin/batch_bw_film.py --film 16 --filter 2 --contrast --auto --drop --sat
```
--film 16 means "Normal Contrast"
--filter 2 means use the Red filter
--contrast, --auto, --drop, and --sat are flags which set each of these options to TRUE. If you don't include a flag it is set to FALSE. Notice that you don't have to write the full name of a flag: --sat means the same thing as --s means the same thing as --saturate.

I hope this helps. If you have any problems or questions, you know where to find me.

---

### Post by VeeDubb on 2008-10-11
I may not be much of a programmer, but I've been using linux long enough to be VERY good at following well laid out directions.  

I'll try this when I get home tonight, and if it works, you will seriously be my new hero.

---

### Post by VeeDubb on 2008-10-12
got home.

tried it.

I love you.

The only down side is that why I want this for, would be to batch convert 500-1000 images, which judging by the speed, will probably take about 12 hours.  On the upside, it will only take 1 minute to figure out which options I want and start the batch, and I can spend the other 11 hours, 59 minutes doing whatever the heck I want.

I can't thank you enough.  When I have the free time, I'll have to nose through your scripts and see how they work.

---

### Post by iponeverything on 2008-10-12
I can see what it took a little while for you get response on how to do this! Something tells me that if it possible to do this with photoshop it's not any easier.

---

### Post by unutbu on 2008-10-12
VeeDubb, I've modified the script with an eye on making it faster. 
The script was calling gimp once for each file. 
Now the script calls gimp only once.
A large job should run about twice as fast.

I've edited my first post to provide the new scripts.

---

### Post by VeeDubb on 2008-10-12
Wow!  Just, wow...

Not only is it now much faster, but instead of lots of seemingly useless feedback in the terminal, it is listing off the file names it's working on with [OK] after it finishes each file, which is awesome.

Again, thank you VERY much.  Simply amazing.  I'll be copying your scripts, as well as the directions for installation and storing them on my external drive for future reference.  This is absolutely top-notch.

---

### Post by VeeDubb on 2008-10-12
On a side note, I'm NOT using Gimp 2.4.  I'm using 2.6 compiled from source on 8.04 64bit, and your scripts still work flawlessly.

---

### Post by brunoscunha on 2008-11-23
Great script!! Is there a scrip to batch optmize jpg images? I have tons I need to optimize.
Thanks

---

### Post by unutbu on 2008-11-23
Save this in ~/.gimp-2.4/plug-ins/save_jpeg.py.
(Change 2.4 to the correct version number for your installation of GIMP.)

[PHP]
#!/usr/bin/env python
__note__="""
This script is a derivative of Carol Spear's resize-batch.py script
See http://carol.gimp.org/gimp/scripting/routines.html#shell
"""
import sys
import os
from gimpfu import *

def save_jpeg(path,quality,smoothing,optimize,progressive,comment,subsmp,baseline,
              restart,dct):
    if os.path.isdir(path):
        all_files=[]
        for root, dirs, files in os.walk(path,False):
            for name in files:
                filename=os.path.join(root, name)
                all_files.append(filename)
    else:
        all_files=[path]
    for filename in all_files:
        try:
            print "Processing %s"%filename,
            image = pdb.gimp_file_load(filename, filename)
            layer = pdb.gimp_image_flatten(image)
            pdb.file_jpeg_save(image, layer, filename, filename, quality, 
                               smoothing, optimize, progressive, 
                               comment, subsmp, baseline, restart, dct)
            pdb.gimp_image_delete(image) 
            print "... [OK]"
        except RuntimeError,err:
            print "... [FAILED]"


proc_name="python_fu_save_jpeg"
blurb="A CLI invokable wrapper for script-fu-save-jpeg"
help_s="python_fu_save_jpeg saves an image as a jpeg"
author="Unutbu"
copyright_s="Unutbu"
date="2008-11-23"
label="<Toolbox>/Xtns/Batch/_Save Jpeg"
imagetypes=""
params=[(PF_FILE, "path", "Filename", ""),
        (PF_FLOAT, "quality", "Quality", 0.80),
        (PF_FLOAT, "smoothing", "Smoothing", 0.0),
        (PF_BOOL, "optimize", "Optimize", True),
        (PF_BOOL, "progressive", "Progressive", False),
        (PF_STRING, "comment", "Comment", ''),
        (PF_INT, "subsmp", "Subsampling option number", 1),
        (PF_BOOL, "baseline", "Force creation of baseline JPEG", False),
        (PF_INT, "restart", "Frequency of restart markers in rows", 0),
        (PF_INT, "dct", "DCT algorithm to use (speed/quality tradeoff)", 0),
        ]
results=[]
function=save_jpeg
register(proc_name, blurb, help_s, author, copyright_s, date, label, imagetypes,
         params, results, function)

main()[/PHP]

Make it executable:
```

chmod +x ~/.gimp-2.4/plug-ins/save_jpeg.py
```

Next, save this in ~/bin/batch_overwrite_save_jpeg.py.

[PHP]#!/usr/bin/env python
import os
import optparse

usage = "usage: %prog [options]"
parser = optparse.OptionParser(usage=usage)
parser.add_option(
    "--path", dest="path", default='.', help="directory path; default is the current working directory", 
    metavar="PATH"
    )
parser.add_option(
    "--quality", dest="quality", default=0.80, type='float', help="quality (0.0--1.0); default=0.80", 
    metavar="FLOAT"
    )
parser.add_option(
    "--smoothing", dest="smoothing", default=0.0, type='float', 
    metavar="FLOAT",
    help="smoothing; default=0.0"
    )
parser.add_option(
    "--optimize", dest="optimize", action="store_true", default=False,
    help="enable optimize"
    )
parser.add_option(
    "--progressive", dest="progressive", action="store_true", default=False,
    help="enable progressive"
    )
parser.add_option(
    "--comment", dest="comment", default='', type='string',
    help="comment"
    )
parser.add_option(
    "--subsmp", dest="subsmp", default=1, type='int',
    help="subsampling option number; default=1",
    metavar='INT'
    )
parser.add_option(
    "--baseline", dest="baseline", action="store_true", default=False,
    help="force creation of baseline JPEG"
    )
parser.add_option(
    "--restart", dest="restart", default=0, type='int',
    help="frequency of restart markers in rows; default=0",
    metavar='INT'
    )
parser.add_option(
    "--dct", dest="dct", default=0, type='int',
    help="DCT algorithm to use (speed/quality tradeoff), default=0",
    metavar='INT'
    )
(opt, args) = parser.parse_args()   

# print opt

def tf(a_bool):
    return 'TRUE' if a_bool else 'FALSE'

cmd=("gimp -i -b "+
     "'(python-fu-save-jpeg RUN-NONINTERACTIVE \"%s\" %s %s %s %s \"%s\" %s %s %s %s)' "+
     "-b '(gimp-quit 0)'")%(
         opt.path,
         opt.quality,
         opt.smoothing,
         tf(opt.optimize), 
         tf(opt.progressive),
         opt.comment,
         opt.subsmp,
         tf(opt.baseline),
         opt.restart,
         opt.dct,
         )

# print cmd
os.system(cmd)[/PHP]

Make it executable too:
```

chmod +x ~/bin/batch_overwrite_save_jpeg.py
```

This script does more than optimize -- it gives you full access to all the options in GIMP's file-jpeg-save command.

To see all the options run this:
```

% ~/bin/batch_overwrite_save_jpeg.py -h
Usage: batch_overwrite_save_jpeg.py [options]

Options:
  -h, --help         show this help message and exit
  --path=PATH        directory path; default is the current working directory
  --quality=FLOAT    quality (0.0--1.0); default=0.80
  --smoothing=FLOAT  smoothing; default=0.0
  --optimize         enable optimize
  --progressive      enable progressive
  --comment=COMMENT  comment
  --subsmp=INT       subsampling option number; default=1
  --baseline         force creation of baseline JPEG
  --restart=INT      frequency of restart markers in rows; default=0
  --dct=INT          DCT algorithm to use (speed/quality tradeoff), default=0

```
To batch optimize a directory of jpg images:
```

cd /path/to/image/directory
~/bin/batch_overwrite_save_jpeg.py --optimize

```
WARNING. Please note carefully that:
[list]
[*]batch_overwrite_save_jpeg.py OVERWRITES files. If you want to save the originals,
make a backup copy of the source directory with a command such as 
```

rsync -a source_dir/ target_dir/

```

[*]batch_overwrite_save_jpeg.py 'recursively' searches through subdirectories, processing each file that it finds. It assumes everything is an image file. If it fails to convert a file, it simply reports the failure and goes on to the next file.
[/list]

---

### Post by P3P on 2011-08-03
I've found a powerful GIMP plugin that implements several batch processing capabilities.
It's called [DBP (David's Batch Processor)]("http://members.ozemail.com.au/~hodsond/dbp.html") and it worked very well for me.


For Ubuntu 11.04 just follow these steps
install required packages:
```
sudo apt-get install libgimp2.0-dev
# NOTE: g++ also needed if not installed
```
download code from [http://members.ozemail.com.au/~hodsond/dbp.html](http://members.ozemail.com.au/~hodsond/dbp.html)
untar, enter directory and execute ```
make install
```

Additional information on [plugin website](http://members.ozemail.com.au/~hodsond/dbp.html)

---

