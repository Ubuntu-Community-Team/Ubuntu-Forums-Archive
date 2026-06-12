---
title: "Most frustrating part of being a Ubuntu user, considering leaving"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-05-10
I need to know how to install a tar ball.
I have read multiple directions.  They aren't helping me

1) What directory do I place the extracted folder in?

I am pleading for help. Synaptic doesn't have everything I want to use, and I can't always find .deb
:confused: :confused:

---

### Post by taurus on 2007-05-10
You can save filename.tar.gz anywhere you want.  Usually when you download it, it would be saved to your ~/Desktop.

So, open a terminal and do

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf filename.tar.gz
cd filename

```
and read the INSTALL for further instructions.

```
more INSTALL
```

p.s.  What are you trying to install from source anyway?

---

### Post by Terl on 2007-05-10
Normally the site that you got the tarball from has all the directions you need.

As for the directory to start from I usually start from my home, unless the directions said otherwise.

What is the file/program you are trying to install?  If you could post the filename, including the extension, it will help.

---

### Post by silent1643 on 2007-05-10
> **mkjarema said:**
> I need to know how to install a tar ball.
I have read multiple directions.  They aren't helping me

1) What directory do I place the extracted folder in?

I am pleading for help. Synaptic doesn't have everything I want to use, and I can't always find .deb
:confused: :confused:


isn't a tar ball just a zipped up file in linux? you should be able to double click on it and it will open file roller, then hit extract to whereever you want, and yes  follow the instructions in the readme file or whatever

---

### Post by mkjarema on 2007-05-10
I found a .deb for NVU 

but juploadr.tar.gz is the one I am still working on. Photo uploader for flickr.com

Do the instructions
> Normally the site that you got the tarball from has all the directions you need.
will the source code tell the program which directories to deal with?

---

### Post by taurus on 2007-05-10
```
tar xvzf juploadr.tar.gz
cd juploadr
ls -la
```
Post the output of the last command.

---

### Post by bodhi.zazen on 2007-05-10
> **mkjarema said:**
> I need to know how to install a tar ball.
I have read multiple directions.  They aren't helping me

1) What directory do I place the extracted folder in?

I am pleading for help. Synaptic doesn't have everything I want to use, and I can't always find .deb
:confused: :confused:

It depends on what you are trying to install. A tar ball is nothing more then an archive, or zip file. They may contain source code or (python) scripts or even binary (binary = ready to run).

To extract, right click on the tar ball and select "open with archive manager" -> extract

LOOK IN THE EXTRACTED ARCHIVE FOR A README FILE. READ IT.

Her is a link that may help : [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/) 

What I do is make a directory in your home directory, src

Then I extract archives to ~/src/program_name

Then, in general, install build essential and checkinstall.

```
sudo aptitude install build-essential checkinstall
```

Open a termainal, 

cd into archive directory, install :```
cd ~/src/program_name
./configure
make
sudo checkinstall
```

check install generated a .deb file which makes it easier to manage.

---

### Post by Memory.Dump on 2007-05-10
the source code when you install it usually puts it in the directory it needs to be from usually you can run the tarball ./configure make and make install from your home dir or desktop with no difficulty, if it neesd to be in a certain location the INSTALL file if you gedit INSTALL after you extract it will tell you where it would need to be, if it doesn't say anything you should be able to run it from anywhere

---

### Post by mkjarema on 2007-05-10
[QUOTE=taurus;2628118]```
tar xvzf juploadr.tar.gz
cd juploadr
ls -la
```
Post the output of the last command.[/QUOTE

mjar@mjar-port:~$ tar xvzf juploadr.tar.gz
tar: juploadr.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mjar@mjar-port:~$

---

### Post by DJMatty on 2007-05-10
Hi

I just downloaded jUploadR and got it running with the following steps:

1) Download the tar, firefox saved the file to my Desktop
2) Double Click the tar file and it opens in the archive manager app
3) Extract the whole folder somewhere (I extracted it to Desktop)
4) Ensure that you have the right java installed (it needs something other than the default Java that was installed with my ubuntu setup)

Run this to see which java's you have installed:
```
sudo update-alternatives --config java
```

And I used synaptic to install sun's java 5 and 6 jre's and selected 5 as the default.

5) Run jUploadR by starting a terminal and 'cd' to the folder that you extracted the tar to (if you used Desktop it'll be something like '~/Desktop/jUploadr...' The foldername has more version information in it). Once you are in the folder use:
```
jUploadr
```
to start it.

The instructions are in the tar and on the website to get it running... but yeah, i'm pretty much a n00b with linux and I have been asking the 'where should I put folders with apps in?' type questions... do they go in home? Or should they go somewhere else like /var/bin/? At present anything I download I try to keep in my home folders, as I don't want them messing with the apps and files that synaptic installs.

Hope this helps

Matt

---

### Post by taurus on 2007-05-10
If you saved juploadr.tar.gz to ~/Desktop, you need to change to that directory first before you can unpack it.

```
cd ~/Desktop
tar xvzf juploadr.tar.gz
cd juploadr
ls -la
```

---

### Post by mkjarema on 2007-05-10
> 
What I do is make a directory in your home directory, src

Then I extract archives to ~/src/program_name



I don't have a src directory, should i make one?

---

### Post by DJMatty on 2007-05-10
Just read your reply to an earlier post...

the tar name for jUploadr (the latest version) is:

```
jUploadr-1.1.2-linuxGTK-i386.tar.gz
```

so I would think you would want:

```
tar xvzf jUploadr-1.1.2-linuxGTK-i386.tar.gz
cd jUploadr-1.1.2-linuxGTK-i386
ls -la
```

Matt

---

### Post by ericesque on 2007-05-10
is it just me, or is NVU available in add/remove programs? (Applications > Add/Remove Programs)



Side note:  Try to make the title of your post relate to the specific issue you are having.  It will make it easier for other users to find help on the topic.  If you need to vent a bit or express your frustration, it's better to do so in the actual post ;)

---

### Post by mkjarema on 2007-05-10
> **taurus said:**
> If you saved juploadr.tar.gz to ~/Desktop, you need to change to that directory first before you can unpack it.

```
cd ~/Desktop
tar xvzf juploadr.tar.gz
cd juploadr
ls -la
```

Thanks that makes sense
here is my output, 
```
mjar@mjar-port:~$ cd ~/Desktop
mjar@mjar-port:~/Desktop$ tar xvzf juploadr.tar.gz
jUploadr-1.1.2-linuxGTK-i386/lib/
jUploadr-1.1.2-linuxGTK-i386/plugins/
jUploadr-1.1.2-linuxGTK-i386/CHANGES
jUploadr-1.1.2-linuxGTK-i386/README
jUploadr-1.1.2-linuxGTK-i386/juploadr.ico
jUploadr-1.1.2-linuxGTK-i386/juploadr_icon.png
jUploadr-1.1.2-linuxGTK-i386/juploadr_min.ico
jUploadr-1.1.2-linuxGTK-i386/lib/BrowserLauncher2-10rc4.jar
jUploadr-1.1.2-linuxGTK-i386/lib/Piccolo.jar
jUploadr-1.1.2-linuxGTK-i386/lib/commons-beanutils.jar
jUploadr-1.1.2-linuxGTK-i386/lib/commons-codec-1.3.jar
jUploadr-1.1.2-linuxGTK-i386/lib/commons-httpclient-3.0-rc3.jar
jUploadr-1.1.2-linuxGTK-i386/lib/commons-logging.jar
jUploadr-1.1.2-linuxGTK-i386/lib/jai_codec.jar
jUploadr-1.1.2-linuxGTK-i386/lib/jai_core.jar
jUploadr-1.1.2-linuxGTK-i386/lib/jim-io.jar
jUploadr-1.1.2-linuxGTK-i386/lib/juploadr-mac-libs.jar
jUploadr-1.1.2-linuxGTK-i386/lib/juploadr.jar
jUploadr-1.1.2-linuxGTK-i386/lib/libswt-gtk-3232.so
jUploadr-1.1.2-linuxGTK-i386/lib/libswt-pi-gtk-3232.so
jUploadr-1.1.2-linuxGTK-i386/lib/swt.jar
jUploadr-1.1.2-linuxGTK-i386/plugins/restflickrapi.jar
jUploadr-1.1.2-linuxGTK-i386/plugins/zooomrapi.jar
jUploadr-1.1.2-linuxGTK-i386/jUploadr
mjar@mjar-port:~/Desktop$ cd juploadr
bash: cd: juploadr: No such file or direcory
```

---

### Post by mkjarema on 2007-05-10
> **ericesque said:**
> is it just me, or is NVU available in add/remove programs? (Applications > Add/Remove Programs)  I looked in synaptic, is add/remove different?



> Side note:  Try to make the title of your post relate to the specific issue you are having.  It will make it easier for other users to find help on the topic.  If you need to vent a bit or express your frustration, it's better to do so in the actual post ;) I have made a post about a week ago listing this concern, and I received two replies that didn't help very much, I then revised my title and question to make it clear-er, and I still received nothing, This has been my huge hang up from day one. I appreciate the advise, I guess I was posting out of frustration....:KS

---

### Post by taurus on 2007-05-10
```
cd ~/Desktop/jUploadr-1.1.2-linuxGTK-i386
more README
```
The README will tell you how to run it.  No need to run ./configure && make && sudo make install since it's a java app.  I hope you have already installed java on your machine.

```
java -version
```

---

### Post by dstew on 2007-05-10
The last command should be **cd jUploader**. It is case-sensitive.

---

### Post by DJMatty on 2007-05-10
The folder name that it has been extracted to is

"jUploadr-1.1.2-linuxGTK-i386"

Try this:

```

cd ~/Desktop
tar xvzf juploadr.tar.gz
cd jUploadr-1.1.2-linuxGTK-i386
jUploadr

```

or even 'cd jUplo*' should do the trick to get you into the folder...

You should also have seen the folder appear on the desktop after you had run the tar command?

Or am I getting the wrong end of the stick? Does the output that tar generates show the contents of the paths stored in the archive or where it's putting the files it's extracting?

Matt

---

### Post by mkjarema on 2007-05-10
mjar@mjar-port:~/Desktop/jUploadr-1.1.2-linuxGTK-i386$ ls -la
total 192
drwxr-xr-x 4 mjar mjar   4096 2007-05-10 10:32 .
drwxr-xr-x 6 mjar mjar   4096 2007-05-10 10:32 ..
-rw-r--r-- 1 mjar mjar   7142 2007-03-20 23:41 CHANGES
-rwxr-xr-x 1 mjar mjar   2781 2007-03-20 23:41 jUploadr
-rw-r--r-- 1 mjar mjar 114518 2007-03-20 23:41 juploadr.ico
-rw-r--r-- 1 mjar mjar   5317 2007-03-20 23:41 juploadr_icon.png
-rw-r--r-- 1 mjar mjar  32038 2007-03-20 23:41 juploadr_min.ico
drwxr-xr-x 2 mjar mjar   4096 2007-05-10 10:32 lib
drwxr-xr-x 2 mjar mjar   4096 2007-05-10 10:32 plugins
-rw-r--r-- 1 mjar mjar   5285 2007-03-20 23:41 README
mjar@mjar-port:~/Desktop/jUploadr-1.1.2-linuxGTK-i386$

Part of my problem was I had changed the .tar.gz file name (for simplistic reasons only)
I re-download the file and kept original name, this is my outupt as requested

---

### Post by mkjarema on 2007-05-10
> **DJMatty said:**
> 

The instructions are in the tar and on the website to get it running... but yeah, i'm pretty much a n00b with linux and I have been asking the 'where should I put folders with apps in?' type questions... do they go in home? Or should they go somewhere else like /var/bin/? At present anything I download I try to keep in my home folders, as I don't want them messing with the apps and files that synaptic installs.

Hope this helps

Matt
i read the read me it gave the./jUpload command, but I didnt' see anywhere else for directions, I looked honestly.

Matt, can I then delete both folders off my desktop the tar.gz and the extracted one?

Also, what does the ls -la do? I know it lists something but what am I looking for when I do this?

---

### Post by DJMatty on 2007-05-10
If you don't want to use jUploadr anymore than yes delete the folders, however if you want to use jUploadr in the future then you will need to keep the one that the tar command created.

This is the thing I am trying to get to grips with, where should these go... for now I would copy the folder to a folder in your home folder. I am not sure what the 'standard' naming of folders would be in the *nix world, but I would make a folder like '~/apps' or perhaps '~/bin' and put the jUploadr folder in there.

Then to run it use:
```
cd ~/bin/jUploadr
./jUploadr

```

ls -la does a directory listing, the -la switches are:

-l - long listing format
-a - list all files (don't ignore ones with . in front of them)

Cheers

Matt

---

