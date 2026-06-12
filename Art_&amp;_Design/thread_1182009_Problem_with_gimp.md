---
title: "Problem with gimp"
date: 2009-06-08
forum: Art &amp; Design
---

### Post by bg11 on 2009-06-08
I've tried to run an example python-fu script posted [here]("http://ubuntuforums.org/showthread.php?t=917486&highlight=python-fu"), but keep getting the following error:

```

gimp -i --verbose --batch-interpreter python-fu-eval -b '(python-fu-bw-film RUN-NONINTERACTIVE "jolie.jpg" 0 1 FALSE FALSE FALSE FALSE FALSE FALSE)' -b '(gimp-quit 0)'

INIT: gimp_load_config
Parsing '/home/bg/.gimp-2.6/unitrc'
Parsing '/etc/gimp/2.0/gimprc'
Parsing '/home/bg/.gimp-2.6/gimprc'
gimp_composite: use=yes, verbose=no
Processor instruction sets: +mmx +sse +sse2 -3dnow -altivec -vis
INIT: gimp_initialize
INIT: gimp_real_initialize
INIT: gimp_restore
Parsing '/home/bg/.gimp-2.6/parasiterc'
Loading 'brush factory' data
Loading 'pattern factory' data
Loading 'palette factory' data
Loading 'gradient factory' data
Loading fonts
Parsing '/home/bg/.gimp-2.6/templaterc'
INIT: gimp_real_restore
Parsing '/home/bg/.gimp-2.6/pluginrc'
Initializing plug-in: '/usr/lib/gimp/2.0/plug-ins/btn4ws.py'
Initializing plug-in: '/usr/lib/gimp/2.0/plug-ins/layerfx.py'
Starting extension: 'extension-script-fu'
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 771, in _run
    return apply(func, params[1:])
  File "/usr/lib/gimp/2.0/plug-ins/python-eval.py", line 26, in code_eval
    exec code in globals()
  File "<string>", line 1
    (python-fu-bw-film RUN-NONINTERACTIVE "jolie.jpg" 0 1 FALSE FALSE FALSE FALSE FALSE FALSE)
                         ^
SyntaxError: invalid syntax
batch command experienced an execution error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 771, in _run
    return apply(func, params[1:])
  File "/usr/lib/gimp/2.0/plug-ins/python-eval.py", line 26, in code_eval
    exec code in globals()
  File "<string>", line 1
    (gimp-quit 0)
               ^
SyntaxError: invalid syntax
batch command experienced an execution error

```

The script is:

```

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

```

I'm using Python 2.5.4.  This script seemed to work fine for someone else who tested it.  Any ideas?

---

### Post by AJB2K3 on 2009-06-09
Only thing I can think off is.

What version of python does he use?

---

### Post by unutbu on 2009-06-09
Run the command like this
```

gimp -i -b '(python-fu-bw-film RUN-NONINTERACTIVE "jolie.jpg" 0 1 FALSE FALSE FALSE FALSE FALSE FALSE)' -b '(gimp-quit 0)'
```

without --batch-interpreter python-fu-eval.

My gimp/python-fu is not strong enough to tell you why. All I know is that I've tested the script and the above command with 

GNU Image Manipulation Program version 2.6.1
Python 2.5.2

and it works fine.

Also, be sure to check out batch_bw_film.py (the second script I posted in the other throad) -- it is a CLI front-end to the ghastly gimp call above.

---

### Post by bg11 on 2009-06-09
> **unutbu said:**
> Run the command like this
```

gimp -i -b '(python-fu-bw-film RUN-NONINTERACTIVE "jolie.jpg" 0 1 FALSE FALSE FALSE FALSE FALSE FALSE)' -b '(gimp-quit 0)'
```

without --batch-interpreter python-fu-eval.


That still gave me the same batch error as before, but...

> 
Also, be sure to check out batch_bw_film.py (the second script I posted in the other throad) -- it is a CLI front-end to the ghastly gimp call above.

Hey it worked perfectly using that script, no more error messages!  Cool, now to play around with it a bit.

---

### Post by kayosiii on 2009-06-10
Check RUN-NONINTERACTIVE vs RUN_NONINTERACTIVE
the former would mostly give an error as a dash '-' is usually interpreted as a minus symbol.

---

