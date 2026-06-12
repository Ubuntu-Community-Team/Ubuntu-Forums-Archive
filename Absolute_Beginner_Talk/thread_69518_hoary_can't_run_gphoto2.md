---
title: "hoary: can't run gphoto2"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by chinaski on 2005-09-27
hi all,

I tried to install gphoto2 with Synaptic (synaptic -> search -> gphoto2 -> mark for istall and so on) and got success message. i looked in the apps menu but no trace of it, so I choosed 'run application' -> gphoto2 and... nothing happened, just a sound as if the app was going to start but nothing.

but if I do sudo apt-get remove gphoto2 it find it and remove it.

does anyone experienced same issue? 

tanks :)

---

### Post by xmastree on 2005-09-27
Try running it from a terminal rather than 'Run application'. That way you will see any error messages which are genenrated, and might help uou to find out what's wrong.

---

### Post by chinaski on 2005-09-27
thank you xmastree! 

now I only have to find out how to launch an app from terminal :)

I'll let you know what happens ;)

---

### Post by xmastree on 2005-09-27
That's easy. Open a terminal, and type the name of the app you wish to run.

---

### Post by chinaski on 2005-09-27
wow, that's *really* easy! :)

thanks again xmastree ;)

---

### Post by chinaski on 2005-09-27
here's the output after typing 'gphoto2' in a terminal:

gphoto2 2.1.5

Copyright (c) 2000-2004 Lutz Mueller and others

gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.

This version of gphoto2 is using the following software versions and options:
gphoto2           2.1.5        gcc, no popt, exif, cdk, no aa, jpeg, readline
libgphoto2        2.1.5        gcc, EXIF, no ltdl, /proc/meminfo
libgphoto2_port   0.5.1        gcc, USB, serial without locking, no ltdl
Usage:
Short/long options (& argument)        Description
--------------------------------------------------------------------------------
      --debug                          Turn on debugging
 -q   --quiet                          Quiet output (default=verbose)
 -v   --version                        Display version and exit
 -h   --help                           Displays this help screen
      --list-cameras                   List supported camera models
      --list-ports                     List supported port devices
      --stdout                         Send file to stdout
      --stdout-size                    Print filesize before data
      --auto-detect                    List auto-detected cameras
      --port path                      Specify port device
      --speed speed                    Specify serial transfer speed
      --camera model                   Specify camera model
      --filename filename              Specify a filename
      --usbid usbid                    (expert only) Override USB IDs
 -a   --abilities                      Display camera abilities
 -f   --folder folder                  Specify camera folder (default="/")
 -R   --recurse                        Recursion (default for download)
      --no-recurse                     No recursion (default for deletion)
 -l   --list-folders                   List folders in folder
 -L   --list-files                     List files in folder
 -m   --mkdir name                     Create a directory
 -r   --rmdir name                     Remove a directory
 -n   --num-files                      Display number of files
 -p   --get-file range                 Get files given in range
 -P   --get-all-files                  Get all files from folder
 -t   --get-thumbnail range            Get thumbnails given in range
 -T   --get-all-thumbnails             Get all thumbnails from folder
 -r   --get-raw-data range             Get raw data given in range
      --get-all-raw-data               Get all raw data from folder
      --get-audio-data range           Get audio data given in range
      --get-all-audio-data             Get all audio data from folder
 -d   --delete-file range              Delete files given in range
 -D   --delete-all-files               Delete all files in folder
 -u   --upload-file filename           Upload a file to camera
      --config                         Configure
      --list-config                    List the configuration tree
      --get-config name                Get a configuration variable
 -F   --frames count                   Set number of frames to capture (default=infinite)
 -I   --interval seconds               Set capture interval in seconds
      --capture-preview                Capture a quick preview
      --capture-image                  Capture an image
      --capture-movie                  Capture a movie
      --capture-sound                  Capture an audio clip
      --show-exif range                Show EXIF information
      --show-info range                Show info
      --summary                        Summary of camera status
      --manual                         Camera driver manual
      --about                          About the camera driver
      --shell                          gPhoto shell
--------------------------------------------------------------------------------
[Use double-quotes around arguments]        [Picture numbers begin with one (1)]
---------------------------------------------------------------------------------

what am I supposed to do now? (sorry this sounds terribly silly... and it probably is...) :(

---

### Post by xmastree on 2005-09-27
[QUOTE=chinaski]what am I supposed to do now?[/QUOTE]Try ```
man gphoto2
```To get an idea how to use it.

Basically, it's looking for more on the command line. You need to tell it what you want to do.
Example, ```
gphoto2 -a
```Should tell you about the camera connected.

Here's what happened when I connected nine:```
chris@ubuntu:~$ gphoto2 -a
Abilities for camera             : Nikon DSC D70 (PTP mode)
Serial port support              : no
USB support                      : yes
Capture choices                  :
                                 : Capture not supported by the driver
Configuration support            : yes
Delete files on camera support   : yes
File preview (thumbnail) support : yes
File upload support              : yes

```
To download all pictures, use gphoto2 -P
```
chris@ubuntu:~$ gphoto2 -P
Downloading 'DSC_0458.JPG' from folder '/store_00010001/DCIM/100NCD70'...

```I suspect you were hoping for a nice GUI, but it doesn't seem to be the case. You might want to look at writing a few simple scripts to do frequent tasks, once you figure it out.

Good luck! :cool:

---

### Post by mtron on 2005-09-27
or install gtkam. It's the gtk interface for gphoto.

---

### Post by chinaski on 2005-09-27
thank you xmastree (BTW, nice camera you have, lucky you! ;) ) and yes, I expected a GUI to appear :)

I'll try mtron tip, for which I thank him/her ;)

---

### Post by xmastree on 2005-09-27
You're welcome. I would also use gtkam as suggested by mtron. I installed it and it certainly takes all that command line stuff out of it. You might as well get the gimp plug-in too. Then you can download pictures directly into gimp.

Having said all that, I still prefer to use my card reader. :rolleyes:

---

### Post by chinaski on 2005-10-02
ok, I succesfully installed everything needed but then found out my camera (Konica Minolta Dimage Z20) is not supported.

it's ok anyway. as I don't have card reader I just plug the camera to pc and make copy/paste, then format memory card on the camera.

---

