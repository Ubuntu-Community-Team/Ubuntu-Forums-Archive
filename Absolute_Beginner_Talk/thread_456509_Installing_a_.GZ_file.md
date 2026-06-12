---
title: "Installing a .GZ file"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-05-27
How do I install this?

> PIXART PAC7311 Support
One driver Upto 244 Webcams supported, thanks Linux .
until gspca v4l2 is finished, used:
gspcav1 "Generic Softwares Package for Camera Adapters" version 1.00.18 date: 08/05/2007
for kernel up from 2.6.11 : [gspcav1-20070508.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz")
for kernel below 2.6.11: spca5xx version 0.60.00-1: [URL="http://mxhaard.free.fr/spca50x/Download/spca5xx-v4l1goodbye.tar.gz"]spca5xx-v4l1goodbye.tar.gz
[/URL]
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)


And how do I find out which Kernal I have?

---

### Post by yabbadabbadont on 2007-05-27
```
uname -a
``` Will tell you which kernel you have.

Edit: Run that command in a terminal window, by the way.  ;)

---

### Post by Killtown on 2007-05-27
> **yabbadabbadont said:**
> ```
uname -a
``` Will tell you which kernel you have.

Edit: Run that command in a terminal window, by the way.  ;)
Ok, I need the up from 2.6.11 file.

How do I install it?

---

### Post by Killtown on 2007-05-27
Anyone?

---

### Post by yabbadabbadont on 2007-05-27
Okey dokey.  Now that I've downloaded the file and extracted it, I think I can help.  (even though I don't have a web cam ;))

You are going to need to install the build-essential package as well as the kernel headers for your kernel.  Since you are using Feisty, you are probably running the linux-generic kernel and the appropriate headers are already installed (linux-headers-generic)  If not, please post the output when you run the "uname -a" command and then wait for someone to get back to you with the correct packages to install.

Once you have the correct headers installed, you will need to install build-essential.  Use synaptic to search for it and install it.  "System->Administration->Synaptic"

Now open a terminal (if you haven't already) and change directory (cd) into the directory where you saved the file you downloaded.  In my case, I put the file into ~/tmp  (I created a tmp directory in my home directory).  Now you need to extract the files from the compressed tar archive that you downloaded.

In the terminal window, run: ```
/home/daffy/tmp $ tar xvzf gspcav1-20070508.tar.gz
```  You will see some directory and filenames fly by as they are extracted.  Note that "/home/daffy/tmp $" is the command prompt and is not part of the command to be run.  The command starts with "tar".

Now cd (change directory) into the gspcav1-20070508 directory that was created.  Run "sudo -s -H"  (without the quotes) to become root.  Your command prompt should change.

Now run "./gspca_build"  (without the quotes) to build the kernel module for your camera.

Example: ```
/home/daffy/tmp $ cd gspcav1-20070508
/home/daffy/tmp/gspcav1-20070508 $ ls -l
total 204
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Conexant
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Etoms
-rwx------ 1 daffy daffy   1957 2007-05-08 10:08 Makefile
-rw-r--r-- 1 daffy daffy   1672 2007-05-08 10:08 Makefile.kld
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Mars-Semi
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:54 Pixart
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Sonix
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Sunplus
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Sunplus-jpeg
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Transvision
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:49 Vimicro
-rw-r--r-- 1 daffy daffy   3569 2007-05-08 09:16 changelog
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 10:06 decoder
-rw------- 1 daffy daffy  13983 2007-05-08 08:54 gspca.h
-rwx------ 1 daffy daffy    919 2006-05-07 10:45 gspca_build
-rw------- 1 daffy daffy 124897 2007-05-08 09:15 gspca_core.c
drwxr-xr-x 2 daffy daffy   4096 2007-05-08 08:54 utils
/home/daffy/tmp/gspcav1-20070508 $ sudo -s -H
Password:
/home/daffy/tmp/gspcav1-20070508 # ./gspca_build 

```
NOTE: Your prompts will look different as I use custom prompts.  i.e.  /home/daffy/tmp/gspcav1-20070508 $   and  /home/daffy/tmp/gspcav1-20070508 # 

Hopefully there won't be any errors and the new module will be installed for you.

---

