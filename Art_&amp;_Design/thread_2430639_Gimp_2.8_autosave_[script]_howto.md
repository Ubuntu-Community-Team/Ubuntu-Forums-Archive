---
title: "Gimp 2.8 autosave [script] howto"
date: 2019-11-05
forum: Art &amp; Design
---

### Post by shantiq on 2019-11-05
I found Gimp 2.8 shutting down in the middle of work and not autosave as function not available. A python script by yahvuu allows this HUGE drawback to be circumvented



&#10122; copy and save in home folder
```
#!/usr/bin/env python


# Original (by yahvuu): http://www.gimpusers.com/forums/gimp-developer/11718-autosave-plugin
import tempfile, os
from time import *
from gimpfu import *


def autosave(image, layer):


    backupInterval = 10 * 60
    backupFiles = {}


    print "Autosave activated"


    while 1:
        sleep(backupInterval)


        print ctime(time())


        curImages = {}
        for k in gimp.image_list():
            curImages[k.ID] = k


            curIDs = curImages.keys()
            oldIDs = backupFiles.keys()


            newIDs = [x for x in curIDs if x not in oldIDs]; delIDs = [x for x in oldIDs if x not in curIDs];


        # create (empty) backup files for new images
        for id in newIDs:
            prefix = 'gimpbackup-ID' + str(id) + '-'
            fn = tempfile.mkstemp(prefix = prefix, suffix = '.xcf')
            os.close(fn[0])
            backupFiles[id] = fn[1]


        # remove closed images' backups 
        for id in delIDs:
            filename = backupFiles[id]
            del(backupFiles[id])


            try:
                os.remove(filename)
            except:
                print "ERROR: ", sys.exc_info()[0]


        # backup images 
        for id, filename in backupFiles.iteritems():
            img = curImages[id]


            try:
                print "saving " + img.name + '-' + str(id) + ' to ' + filename
                pdb.gimp_xcf_save(1, img, img.active_drawable, filename, filename)
            except:
                print "ERROR: ", sys.exc_info()[0]


register(
    "autosave",
    "Autosave dirty hack",
    "Periodically saves all opened images to a %temp% directory",
    "public domain",
    "public domain",
    "2016",
    "<Image>/File/Activate Autosave",
    "*",
    [],
    [],
    autosave)


main()
```


&#10123; 
```
sudo chmod +x gimp-autosave.py 

also >>

./gimp-autosave.py 
```


&#10124; do ```
sudo  ln gimp-autosave.py ~/.gimp-2.8/plug-ins/gimp-autosave.py
```


&#10125; start Gimp from terminal  ```
gimp
``` 


&#10126; Go File/New  then File/Activate Autosave [at the bottom]  now saved .xcf copies of your work can/should be found in /tmp

---

