---
title: "I tried to install a .tgz and well it didn't work."
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by ballad of false hope on 2006-11-20
user@Linux:~$ su -c 'make install''/home/user/Desktop/nautilus-scripts.tar.gz'
Password:
su: Authentication failure

I'm confused, please assist.

---

### Post by melancholeric on 2006-11-20
sudo not su

---

### Post by ballad of false hope on 2006-11-20
tar -zxvf nautilus-scripts.tar.gz
cd /home/user/Desktop/nautilus-scripts.tar.gz
./configure
make
sudo -c 'make install'

Is this right?

---

### Post by scxtt on 2006-11-20
closer ... you need to unzip it, then untar it ... i think tar can do both, not sure ...

gunzip nautilus-scripts.tar.gz
tar -xvf nautilus-scripts.tar

EDIT: i see that's what -z is for :p

so **tar -zxvf nautilus-scripts.tar.gz** will work, you just need to make sure you're not trying to cd into the .tar.gz file (no reason to, even if it was possible)

cd /home/user/Desktop/nautilus-scripts
./configure
make install

don't know that you'll have to be root, but use sudo instead of su -c (unless you have a root password)

also make sure you're in /home/user/Desktop before executing the 1st command ...

---

### Post by chalex on 2006-11-20
FYI:

./configure
make
make install

Those three steps are the STANDARD way to install *nix software.  Of course, you need to be inside the app's directory when you do this, which mean you probably want to tar -xvzf the tar.gz first.

Also, the last step needs to be modified for Ubuntu.  Typically, you would perform the installation as root, but since Ubuntu doesn't have a root account by default, you'll need to do "sudo make install" and enter your password.

---

### Post by ballad of false hope on 2006-11-20
scripts.tar.gz
nautilus-scripts/
nautilus-scripts/Archiving/
nautilus-scripts/Archiving/Compress__.bz2_
nautilus-scripts/Archiving/Compress__.gz_
nautilus-scripts/Archiving/Decompress
nautilus-scripts/Archiving/archiver-unarchiver
nautilus-scripts/Archiving/gnome-archive
nautilus-scripts/Archiving/super-extractor
nautilus-scripts/Archiving/unrar
nautilus-scripts/Execute/
nautilus-scripts/Execute/Open Terminal Here
nautilus-scripts/Execute/Play in XMMS
nautilus-scripts/Execute/XMMS
nautilus-scripts/Execute/command_prompt_here
nautilus-scripts/Execute/gedit
nautilus-scripts/Execute/ghex
nautilus-scripts/Execute/glimmer
nautilus-scripts/Execute/gnome2-terminal-here
nautilus-scripts/Execute/root-nautilus-here
nautilus-scripts/Execute/root-terminal-here
nautilus-scripts/Execute/run
nautilus-scripts/Execute/terminal-here
nautilus-scripts/Execute/xemacs
nautilus-scripts/Execute/xine
nautilus-scripts/Execute/xsu-terminal-here
nautilus-scripts/File Info/
nautilus-scripts/File Info/FileUsedBy
nautilus-scripts/File Info/Search Here
nautilus-scripts/File Info/Show MD5 Sum
nautilus-scripts/File Info/Show_Parameters
nautilus-scripts/File Info/filetype
nautilus-scripts/File Info/ggrep
nautilus-scripts/File Info/gtk-du
nautilus-scripts/File Info/gtk2-du
nautilus-scripts/File Info/gtk2-grep
nautilus-scripts/File Info/mimetype
nautilus-scripts/File Info/wordcount
nautilus-scripts/File Processing/
nautilus-scripts/File Processing/Mail In Evolution
nautilus-scripts/File Processing/New Text Document
nautilus-scripts/File Processing/concatenate
nautilus-scripts/File Processing/dos2unix
nautilus-scripts/File Processing/doublespace
nautilus-scripts/File Processing/latex
nautilus-scripts/File Processing/latex2ps
nautilus-scripts/File Processing/mail_file
nautilus-scripts/File Processing/mail_file2
nautilus-scripts/File Processing/maker
nautilus-scripts/File Processing/new-text-document
nautilus-scripts/File Processing/pdf2ps
nautilus-scripts/File Processing/pixdir2html.pl
nautilus-scripts/File Processing/pprint
nautilus-scripts/File Processing/print
nautilus-scripts/File Processing/print_with_openoffice
nautilus-scripts/File Processing/ps2pdf
nautilus-scripts/File Processing/scp2host
nautilus-scripts/File Processing/scp_to_host
nautilus-scripts/File Processing/search_n_replace
nautilus-scripts/File Processing/secure copy
nautilus-scripts/File Processing/superexec.py
nautilus-scripts/File System Management/
nautilus-scripts/File System Management/Get Photos
nautilus-scripts/File System Management/Junksorter.pl
nautilus-scripts/File System Management/Make Link
nautilus-scripts/File System Management/QuickBurn
nautilus-scripts/File System Management/Search Here
nautilus-scripts/File System Management/UnExec
nautilus-scripts/File System Management/burn_dir
nautilus-scripts/File System Management/burn_iso
nautilus-scripts/File System Management/change_name
nautilus-scripts/File System Management/chmod
nautilus-scripts/File System Management/chmog
nautilus-scripts/File System Management/copyhome
nautilus-scripts/File System Management/junksorter
nautilus-scripts/File System Management/linker
nautilus-scripts/File System Management/lowercase
nautilus-scripts/File System Management/mount_loopback
nautilus-scripts/File System Management/moveup
nautilus-scripts/File System Management/set_exec
nautilus-scripts/File System Management/set_read_only
nautilus-scripts/File System Management/shredder
nautilus-scripts/File System Management/uppercase
nautilus-scripts/Multimedia/
nautilus-scripts/Multimedia/Create_Thumbnail
nautilus-scripts/Multimedia/Naudilus
nautilus-scripts/Multimedia/Play_in_XMMS
nautilus-scripts/Multimedia/Queue to XMMS
nautilus-scripts/Multimedia/Show Digital Photo EXIF data
nautilus-scripts/Multimedia/XMMS_Enqueue
nautilus-scripts/Multimedia/convert_to_jpeg
nautilus-scripts/Multimedia/convert_to_png
nautilus-scripts/Multimedia/create-vcd
nautilus-scripts/Multimedia/dv_to_mpg
nautilus-scripts/Multimedia/mirror_jpg
nautilus-scripts/Multimedia/queue_to_xmms
nautilus-scripts/Multimedia/rotate
nautilus-scripts/Multimedia/rotate_image
nautilus-scripts/Multimedia/rotate_jpg_left
nautilus-scripts/Multimedia/rotate_jpg_right
nautilus-scripts/Multimedia/scale_image
nautilus-scripts/Multimedia/scale_image_to_sizes
nautilus-scripts/Multimedia/slideshow
nautilus-scripts/Multimedia/watermark
nautilus-scripts/Obsolete/
nautilus-scripts/Obsolete/RPM-install-update
nautilus-scripts/Obsolete/bzip2
nautilus-scripts/Obsolete/converter
nautilus-scripts/Obsolete/create-zip
nautilus-scripts/Obsolete/create_file
nautilus-scripts/Obsolete/create_targz
nautilus-scripts/Obsolete/gb-unzip
nautilus-scripts/Obsolete/gzip
nautilus-scripts/Obsolete/mail_image
nautilus-scripts/Obsolete/mailinbalsa
nautilus-scripts/Obsolete/to_upper
nautilus-scripts/Obsolete/uncompress_all
nautilus-scripts/System Configuration/
nautilus-scripts/System Configuration/Debian_Package
nautilus-scripts/System Configuration/Hide or Show Hidden Files
nautilus-scripts/System Configuration/Install to Palm
nautilus-scripts/System Configuration/Install_Galeon_Theme
nautilus-scripts/System Configuration/Query_RPM
nautilus-scripts/System Configuration/RPM-install-update
nautilus-scripts/System Configuration/RPM-tools
nautilus-scripts/System Configuration/Set image as Wallpaper
nautilus-scripts/System Configuration/Set_as_Directory_Icon
nautilus-scripts/System Configuration/Set_as_Wallpaper
nautilus-scripts/System Configuration/Show_Directory_Metafile
nautilus-scripts/System Configuration/archiver-config
nautilus-scripts/System Configuration/install_rpm
nautilus-scripts/System Configuration/make-nautilus-script
nautilus-scripts/System Configuration/make_launcher
nautilus-scripts/System Configuration/pseudo-nautilus
nautilus-scripts/System Configuration/pynautilus

I got that after I used the tar -zxvf /home/user/Desktop/nautilus-scripts.tar.gz

Then I used this command and you see the result.

cd /home/userl/Desktop/nautilus-scripts
bash: cd: /home/user/Desktop/nautilus-scripts: No such file or directory
user@PC:~$ ./configure
bash: ./configure: No such file or directory

What can I do?

---

### Post by DaveBorealis on 2006-11-20
Hello,

It looks like this is a collection of scripts used for doing various chores, rather than a package of source code to be compiled and installed.  Where'd you get it from?

Dave

---

### Post by ballad of false hope on 2006-11-20
Here you go Dave
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

Also I am truly stumped about how to get that to work.

---

### Post by scxtt on 2006-11-20
from what i can remember, those are just scripts that need to be put in a specific directory (don't remember which "hidden directory" that is, not using gnome) and will allow you to right-click on specific MIME-types of files to perfrom a scripted action ... so no "installation" (in the typical sense) required ... you can also see from your tar output above there there is no "makefile" ...

---

### Post by ballad of false hope on 2006-11-20
I guess a make file is a file that allows there to be a autoinstall performed. Also when you say it the way you said it, you mean it won't work with GNOME? Also if you could, give me a test file it that would be the case to test how to install .tgz files. I want to leanr Linux, but as a complete newb to it I have to start from stupid and rise up.

---

### Post by melancholeric on 2006-11-21
> so you can just extract the entire archive into ~/.gnome and you are good to go.
~ means home directory. So, copy the whole thing into /home/user/.gnome/

.gnome is a hidden directory, by the way, so you won't see that in nautilus by default. To see it, choose view -> check "Show hidden files". You may want to disable this after you've moved the scripts.

---

### Post by elementadiobam on 2006-11-21
I get the same bash thing when trying to run ./configure, but I am trying to compile teamspeak2 rc2. Does anyone know how to fix my problem?

---

### Post by ciscosurfer on 2006-11-21
> **melancholeric said:**
> ~ means home directory. So, copy the whole thing into /home/user/.gnome/

.gnome is a hidden directory, by the way, so you won't see that in nautilus by default. To see it, choose view -> check "Show hidden files". You may want to disable this after you've moved the scripts.Extract it to ~/.gnome2/nautilus-scripts 

There's no need to configure anything.  They don't install, they get placed.

---

