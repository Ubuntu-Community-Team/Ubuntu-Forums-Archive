---
title: "Gimp deletes exif data.."
date: 2013-10-13
forum: Art &amp; Design
---

### Post by Baldrick_NZ on 2013-10-13
Hi all,

It would appear that Gimp 2.8.6 (in the repos) deletes exif data from photos. The data includes camera make & model, aperture settings, etc...

I'm using Ubuntu 13.04 atm.

How can I stop this from happening?

Any help greatfully received!

---

### Post by ofnuts on 2013-10-13
You can check that the exifs are loaded properly. Load the picture (that should be the only picture in Gimp for the following code to work), open the python-fu console and enter:
```

image=gimp.image_list()[0]
exif=image.parasite_find('exif-data')
print len(exif.data)

```

Either you get some value in the thousands (this is the size in bytes of the EXIF data, the image I tried from my DSLR gives 15401) or you get some nastygram because the exif data isn't there.

---

### Post by Baldrick_NZ on 2013-10-13
> **ofnuts said:**
> You can check that the exifs are loaded properly. Load the picture (that should be the only picture in Gimp for the following code to work), open the python-fu console and enter:
```

image=gimp.image_list()[0]
exif=image.parasite_find('exif-data')
print len(exif.data)

```

Either you get some value in the thousands (this is the size in bytes of the EXIF data, the image I tried from my DSLR gives 15401) or you get some nastygram because the exif data isn't there.

Interesting. Thanks for that.

A bit of background... I use Aftershot Pro to edit RAW images, and that either saves them to tif or jpg. When I saved a sample of both, both had relevant EXIF using gthumb. After using Gimp to further edit the previously saved tif and jpg images, Gimp stripped away the EXIF info from the tif, and the jpg.

Aftershot Pro RAW saved as Jpg, then reopened and edited in Gimp seems to pass the EXIF info intact.

So, here's the results I have from both files saved under Aftershot Pro, reopened in Gimp with only the script you gave me run...

Tif...
```
>>> image=gimp.image_list()[0]
>>> exif=image.parasite_find('exif-data')
>>> print len(exif.data)
Traceback (most recent call last):
  File "<input>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'data'
```

Jpg...
```
>>> >>> image=gimp.image_list()[0]
  File "<input>", line 1
    >>> image=gimp.image_list()[0]
     ^
SyntaxError: invalid syntax
>>> >>> exif=image.parasite_find('exif-data')
  File "<input>", line 1
    >>> exif=image.parasite_find('exif-data')
     ^
SyntaxError: invalid syntax
>>> >>> print len(exif.data)
  File "<input>", line 1
    >>> print len(exif.data)
     ^
SyntaxError: invalid syntax
>>> Traceback (most recent call last):
  File "<input>", line 1
    Traceback (most recent call last):
                         ^
SyntaxError: invalid syntax
>>>   File "<input>", line 1, in <module>
  File "<input>", line 1
    File "<input>", line 1, in <module>
   ^
IndentationError: unexpected indent
>>> AttributeError: 'NoneType' object has no attribute 'data'
```

Hope this helps...

---

### Post by ofnuts on 2013-10-14
For TIFF, there is no EXIF (but I'm not sure Gimp reads/saves EXIF in TIFF).

For JPG, you copy/pasted the leading ">>>", redo without...

You can also use the exiftool utility (from your favorite repo) to check the presence of EXIF data in the file (and in case GImp is at fault, you can use that same utility to transfer the EXIF data between the original and the edited version)

---

