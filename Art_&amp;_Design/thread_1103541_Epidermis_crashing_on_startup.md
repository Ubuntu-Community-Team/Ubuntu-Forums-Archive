---
title: "Epidermis crashing on startup"
date: 2009-03-22
forum: Art &amp; Design
---

### Post by kcb064 on 2009-03-22
I Installed the latest version of Epidermis and Python today and after applying a skin from the repo it just hung on the install after downloading all the element. Now when i try to load Epidermis i get Programming error with the following output:
```
Traceback (most recent call last):
  File "/usr/bin/epidermis", line 15, <module>()
            import epidermis.epidermis
            epidermis.epidermis.main()
  variables: {'epidermis.epidermis.main': ('local', <function main at 0x844b374>)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 1430, main()
        """launches start(sys.argv)"""
        start(sys.argv)
  variables: {'start': ('global', <function start at 0x84456bc>), 'sys.argv': ('global', ['/usr/bin/epidermis'])}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 1403, start(args=['/usr/bin/epidermis'])
               print debuginfo.debuginfo()  
            app = EpidermisApp()
            gtk.main()
  variables: {'app': (None, None), 'EpidermisApp': ('global', <class epidermis.epidermis.EpidermisApp at 0x84462fc>)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 293, __init__(self=<epidermis.epidermis.EpidermisApp instance at 0xb7b9b30c>)
            # Load the skins
            self.find_and_load_installed_pigments()
            self.add_skins()
  variables: {'self.find_and_load_installed_pigments': ('local', <bound method EpidermisApp.find_and_load_installed_pigments of <epidermis.epidermis.EpidermisApp instance at 0xb7b9b30c>>)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 426, find_and_load_installed_pigments(self=<epidermis.epidermis.EpidermisApp instance at 0xb7b9b30c>)
                    self.installedPigments[pt] = managepigments.find_pigments(pt, \
                        [MY_DATA_HOME, const.SHARED_PIGMENT_DIR])
                except ep_exceptions.AttachmentNotFoundException, ee:
  variables: {'MY_DATA_HOME': ('global', '/home/kevin/.local/share/epidermis/'), 'const.SHARED_PIGMENT_DIR': ('global', '/usr/share/epidermis/pigments/')}
  File "/usr/lib/python2.5/site-packages/epidermis/managepigments.py", line 40, find_pigments(pigmentTypeStr='icons', directories=['/home/kevin/.local/share/epidermis/', '/usr/share/epidermis/pigments/'])
                    if os.path.exists(os.path.join(dirr, pt.directoryName, pigmDir, "pigment.xml")):
                        retPigments.append(load_pigment(pigmDir, pigmentTypeStr, [dirr]))
        return retPigments
  variables: {'dirr': ('local', '/home/kevin/.local/share/epidermis/'), 'load_pigment': ('global', <function load_pigment at 0x8445374>), 'retPigments.append': ('local', <built-in method append of list object at 0x87c9b0c>), 'pigmentTypeStr': ('local', 'icons'), 'pigmDir': ('local', 'bluman')}
  File "/usr/lib/python2.5/site-packages/epidermis/managepigments.py", line 57, load_pigment(pigment='bluman', pigmentType='icons', directories=['/home/kevin/.local/share/epidermis/'])
            if does_pigment_exist(pigment, pigmentType, dir):
                pp.read(os.path.join(dir, get_pigment_type(pigmentType)().directoryName, pigment, "pigment.xml"))
                pp.installationDirectory = dir
  variables: {'directoryName': (None, None), 'pigment': ('local', 'bluman'), 'get_pigment_type': ('global', <function get_pigment_type at 0x84453e4>), 'pp.read': ('local', <bound method Icons.read of <epidermis.pigments.icons.Icons instance at 0x87c3e2c>>), 'os.path.join': ('global', <function join at 0xb7de6224>), 'pigmentType': ('local', 'icons'), 'dir': ('local', '/home/kevin/.local/share/epidermis/')}
  File "/usr/lib/python2.5/site-packages/epidermis/pigments/icons.py", line 130, read(self=<epidermis.pigments.icons.Icons instance at 0x87c3e2c>, filePath='/home/kevin/.local/share/epidermis/icons/bluman/pigment.xml')
        def read(self, filePath):
            Pigment.read(self, filePath)
  variables: {'Pigment.read': ('global', <unbound method Pigment.read>), 'self': ('local', <epidermis.pigments.icons.Icons instance at 0x87c3e2c>), 'filePath': ('local', '/home/kevin/.local/share/epidermis/icons/bluman/pigment.xml')}
  File "/usr/lib/python2.5/site-packages/epidermis/pigments/pigment.py", line 528, read(self=<epidermis.pigments.icons.Icons instance at 0x87c3e2c>, filePath='/home/kevin/.local/share/epidermis/icons/bluman/pigment.xml', installationDirectory=None)
                    if os.path.exists(os.path.join(fileDir, self.previewFilename)):
                        self.set_preview_file(os.path.join(fileDir, self.previewFilename))
            else:
  variables: {'fileDir': ('local', '/home/kevin/.local/share/epidermis/icons/bluman/'), 'os.path.join': ('global', <function join at 0xb7de6224>), 'self.set_preview_file': ('local', <bound method Icons.set_preview_file of <epidermis.pigments.icons.Icons instance at 0x87c3e2c>>), 'self.previewFilename': ('local', u'blumani.png')}
  File "/usr/lib/python2.5/site-packages/epidermis/pigments/pigment.py", line 234, set_preview_file(self=<epidermis.pigments.icons.Icons instance at 0x87c3e2c>, filename=u'/home/kevin/.local/share/epidermis/icons/bluman/blumani.png')
                self.preview =  gtk.gdk.pixbuf_new_from_file_at_size(filename, \
                    100,75)
            else:
GError: Failed to open file '/home/kevin/.local/share/epidermis/icons/bluman/blumani.png': Permission denied

debuginfo.debuginfo error
```

---

### Post by Orlsend on 2009-03-23
Hi were you trying to install the new Bluman skin? what version of Ubuntu and python you Have?

---

### Post by kcb064 on 2009-03-23
Yeah I was. Running 8.10 with python 2.5.2

---

### Post by Flimm on 2009-03-23
This is a [known bug](https://bugs.launchpad.net/epidermis/+bug/346640) and a fix has been released. To delete the faulty pigment, type this in a terminal:
```
sudo rm -r ~/.local/share/epidermis/icons/bluman ~/.local/share/epidermis/skins/bluman
```
Then redownload the skin the normal way.

---

### Post by kcb064 on 2009-03-24
Fixed it for the bluman skin, and I was able to apply it to my desktop however it now hangs and doesn't move while installing the ubuntu-studio_skin. I didnt try any others, I went straight to that one

---

### Post by Flimm on 2009-03-24
Well done, you caught another badly packaged skin! We really should do more [testing](http://epidermis.tuxfamily.org/?q=contribute#test), shouldn't we?
It's been fixed.

---

