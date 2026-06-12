---
title: "[SOLVED] apt-get update problems"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by cmittle on 2007-11-10
When I type sudo apt-get upgrade I get the following error
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  googleearth-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154259 files and directories currently installed.)
Removing googleearth-data ...

(update-desktop-database:17158): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing googleearth-data (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 googleearth-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What is this error exit status 139, and how can I resolve this problem?

Thank you,
Cory

---

### Post by trak87 on 2007-11-10
Try the "fix broken packages" option in Synaptic.

---

### Post by cmittle on 2007-11-10
This appeared to do nothing.  I clicked apply changes and I still get the same error message in the command line.

E: googleearth-data: subprocess post-removal script returned error exit status 139

Any way to force the removal of this?

Thanks,
Cory

---

### Post by taurus on 2007-11-10
Try removing that package.

```
sudo apt-get remove googleearth-data
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cmittle on 2007-11-10
Tried that already, here is what is output when I try removing

```
sudo apt-get remove googleearth-data
[sudo] password for cory:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  googleearth-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154259 files and directories currently installed.)
Removing googleearth-data ...

(update-desktop-database:21130): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing googleearth-data (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 googleearth-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks,
Cory

---

### Post by cmittle on 2007-11-13
I did some searching on the term in my errors "segmentation fault" and it seems to mean something about having a bad memory location.  I ran memtest from grub.  I let it run over night and it came up with 1 error out of 20 attempts.  The first column  (i didn't write down the name) listed 00019edd254-414.8MB.  The second column (Good column) 00000010, third (Bad column) 00200010.  The next column called Err-bits 00200000, and the Count column said 1.

Is there any way that this error could be what was causing this segmentation fault error?  How can I fix this problem?  Is there a way to tell my computer not to use certain segments of the RAM?

Thanks,
Cory

---

### Post by sin_bad on 2007-11-13
I dont know about this error , but try autoremove command 

sudo apt-get autoremove .......

---

### Post by cmittle on 2007-11-13
Auto remove didn't seem to help either.  It says there are 3 packages not fully installed or removed.  Is there a more forceful way to resolve these packages?
```
sudo apt-get autoremove
[sudo] password for cory:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  googleearth-data
0 upgraded, 0 newly installed, 1 to remove and 21 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154259 files and directories currently installed.)
Removing googleearth-data ...

(update-desktop-database:5776): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing googleearth-data (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 googleearth-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Today when I turned on my computer I see that there are updates to install.  I clicked on the icon and I get this message
"It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."
obviously I tried this and it did not help, I get the same message about google earth data error.

Please help me fix this problem I can't update or install or uninstall anything now.
Thank you,
Cory

---

### Post by ibbill on 2007-11-13
I'm a real newbie here also but I had that problem and instead of clicking Do you want to continue [Y/n]? y I clicked N and it seem to stop the problem you may want to try that.

Bill

---

### Post by cmittle on 2007-11-14
This just aborts the install/removal process, but I tried it anyway and then tried sudo apt-get upgrade and still no luck.

Thanks,
Cory

---

### Post by poudin on 2007-11-14
try this...go to Synaptic Package Manager

use the filters and check the Broken packages view...it may give you an option to remove or reinstall broken packages...if any are listed.

hope this helps.

---

### Post by cmittle on 2007-11-14
I opened synaptic and went to edit>fix broken packages.  It didn't really do anything noticeable.  I opened a terminal and tried sudo apt-get update upgrade and I'm still seeing the same errors.

EDIT:  I just reread your suggestion and opened synaptic and clicked on the broken filter and it doesn't show any packages as being broken.

Thanks,
Cory

---

### Post by zvacet on 2007-11-14
```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by ibbill on 2007-11-14
Sorry about that what I did was tried to install it again then when asked 

Do you want to continue [Y/n]?  I typed N

---

### Post by cmittle on 2007-11-14
> **zvacet said:**
> ```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

I have tried these commands several times with no luck.

---

### Post by Anicka on 2007-11-14
What happens if you do "sudo apt-get remove -f googleearth-data"?

---

### Post by anaconda on 2007-11-14
I had the same problem yesterday.
[http://ubuntuforums.org/showthread.php?t=612064](http://ubuntuforums.org/showthread.php?t=612064)

and the solution was to manually remove all references to that program from dpkg, aptitude and apt-get etc.. 

This solution obviously leaves the "broken" program to your machine, but removes all references to it.

---

### Post by anaconda on 2007-11-14
> 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.

hmm.. it seems that you have 3 packages that aren't fully installed or removed!!!

That means that you might have to repeat the steps for all 3 programs..

Good luck ;)

---

### Post by cmittle on 2007-11-15
What if I want one or all three of those programs installed on my computer?  Is there a way to resolve this and keep any of them, or reinstall them?

Thanks,
Cory

---

### Post by anaconda on 2007-11-15
If you follow the nstructions above, then you are only removing the references of those programs from apt-get, aptitude and dpkg, so that they will start working properly again. It doesn't remove any installed programs..  

Then you can keep them or try to install any of them again..

---

### Post by Gazneth on 2007-11-15
A little different idea to try.```
sudo dpkg &#8211;remove &#8211;force-remove-reinstreq Packagename
``` Especially after you have removed references to the program this code should return your apt-get to a useable state.

---

### Post by anaconda on 2007-11-15
> **Gazneth said:**
> A little different idea to try.```
sudo dpkg &#8211;remove &#8211;force-remove-reinstreq Packagename
``` Especially after you have removed references to the program this code should return your apt-get to a useable state.

well.. that didn't work for me, but removing the references returned everything back to "normal"

---

### Post by cmittle on 2007-11-15
I've deleted the references in these places and I no longer have any errors with blender, mplayer, or googleearth-data.  I'm now seeing the same errors with sound-juicer, and gnome-menus.  I've tried deleting the references to them and doing the same thing, but those errors keep coming back, when I sudo apt-get upgrade.
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gnome-menus (2.20.1-0ubuntu1) ...

(update-desktop-database:10704): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-menus (--configure):
 subprocess post-installation script returned error exit status 139
Setting up sound-juicer (2.20.1-0ubuntu1) ...

(update-desktop-database:10730): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gnome-menus
 sound-juicer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
After I saw this I tried all of the above mentioned commands again.  The "sudo dpkg –remove –force-remove-reinstreq Packagename" does not seem to help me at all.  This is the response I get from this.
```
cory@cory-laptop:~$ sudo dpkg –remove –force-remove-reinstreq gnome-menus
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

Any further help with this problem would be appreciated.

Thank you,
Cory

---

### Post by Partyboi2 on 2007-11-15
I was having a look around for something that might be able to help you, and came across this:
[http://www.debian-administration.org/articles/251](http://www.debian-administration.org/articles/251)
Not sure if it will help.

---

### Post by cmittle on 2007-11-15
Of course there were more updates today and out of habit, even though I hadn't fixed my apt-get problem I clicked to update.  Now when I try sudo aptitude upgrade I get a bunch more errors.  

```
cory@cory-laptop:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be upgraded:
  libsmbclient samba-common smbclient 
The following partially installed packages will be configured:
  eog evince file-roller gcalctool gedit gnome-about gnome-games 
  gnome-menus gnome-session 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8606kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com gutsy-security/main smbclient 3.0.26a-1ubuntu2.1 [4886kB]
Get:2 http://archive.ubuntu.com gutsy-security/main samba-common 3.0.26a-1ubuntu2.1 [2835kB]
Get:3 http://archive.ubuntu.com gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1 [885kB]
Fetched 8606kB in 52s (162kB/s)                                                 
Preconfiguring packages ...
(Reading database ... 149381 files and directories currently installed.)
Preparing to replace smbclient 3.0.26a-1ubuntu2 (using .../smbclient_3.0.26a-1ubuntu2.1_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 3.0.26a-1ubuntu2 (using .../samba-common_3.0.26a-1ubuntu2.1_i386.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 3.0.26a-1ubuntu2 (using .../libsmbclient_3.0.26a-1ubuntu2.1_i386.deb) ...
Unpacking replacement libsmbclient ...
Setting up eog (2.20.1-0ubuntu1) ...

(update-desktop-database:32128): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.20.1-0ubuntu1) ...

(update-desktop-database:32166): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.20.1-0ubuntu1) ...

(update-desktop-database:32200): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.20.2-0ubuntu1) ...

(update-desktop-database:32231): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit (2.20.3-0ubuntu1) ...

(update-desktop-database:32260): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gedit (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-about (1:2.20.1-0ubuntu1) ...

(update-desktop-database:32270): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-about (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-games (1:2.20.1-0ubuntu1) ...

(update-desktop-database:32276): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-games (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-menus (2.20.1-0ubuntu1) ...

(update-desktop-database:32281): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-menus (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-session (2.20.1-0ubuntu1) ...

(update-desktop-database:32323): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-session (--configure):
 subprocess post-installation script returned error exit status 139
Setting up samba-common (3.0.26a-1ubuntu2.1) ...

Setting up smbclient (3.0.26a-1ubuntu2.1) ...
Setting up libsmbclient (3.0.26a-1ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 eog
 evince
 file-roller
 gcalctool
 gedit
 gnome-about
 gnome-games
 gnome-menus
 gnome-session
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up eog (2.20.1-0ubuntu1) ...

(update-desktop-database:32408): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit (2.20.3-0ubuntu1) ...

(update-desktop-database:32433): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gedit (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-games (1:2.20.1-0ubuntu1) ...

(update-desktop-database:32446): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-games (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-menus (2.20.1-0ubuntu1) ...

(update-desktop-database:32451): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-menus (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.20.2-0ubuntu1) ...

(update-desktop-database:32484): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.20.1-0ubuntu1) ...

(update-desktop-database:32528): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-session (2.20.1-0ubuntu1) ...

(update-desktop-database:32564): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-session (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.20.1-0ubuntu1) ...

(update-desktop-database:32592): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-about (1:2.20.1-0ubuntu1) ...

(update-desktop-database:32597): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-about (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 eog
 gedit
 gnome-games
 gnome-menus
 gcalctool
 evince
 gnome-session
 file-roller
 gnome-about
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done  
```

I tried the suggestion of removing the -e from gnome-menus.postinst file and as you can see it still shows up as an error.  Is there an easy way to undo my update so I can remove all of these extra errors and get back to just two.  Does this indicate some sort of dpkg error rather than errors in individual files?  I don't know but it seems wierd that anything new installed or removed is having problems.


```
~$ sudo dpkg --configure gnome-session
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.20); however:
  Package gnome-control-center is not configured yet.
 gnome-session depends on gnome-control-center (<< 1:2.21); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-session
cory@cory-laptop:~$ sudo dpkg --configure gnome-control-center
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-menus (>= 2.12.0); however:
  Package gnome-menus is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-control-center

```

I was going to go back and retry the deleting references from /var/lib/dpkg and aptitude.  I typed sudo nautilus and bash didn't recognize the command somehow I deleted nautilus.  Using the terminal I managed to go back through and erase the references to nautilus, nautilus-cd-burner, gnome-menus, gnome-session, and alacarte.  This worked, then I used sudo apt-get install nautilus etc..  I can now use nautilus again and it seems that the others were installed again as well but none are configured.  I decided to try manually making each package configure so I tried sudo dpkg --configure gnome-session that tells me that gnome-control-center is not yet configured so I do sudo dpkg --configure gnome-control-center, all of this can be seen above.  This tells me that gnome-menus is not configured yet so I type sudo dpkg --configure gnome-menus.  This is the point where we run into a problem.  This is where we have a dpkg error as seen below
```
cory@cory-laptop:~$ sudo dpkg --configure gnome-menus
Setting up gnome-menus (2.20.1-0ubuntu1) ...

(update-desktop-database:6976): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-menus (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gnome-menus
```

It seems to me I'm getting hung up on this gnome-menus file.  Does any of the information I have offered help figure this business out?  Is there something else I can do that would offer more information?


Thank you,
Cory

---

### Post by rexxxlo on 2007-11-16
i get a very similar message 

> lolo@lolo-desktop:~$ sudo apt-get -f install
[sudo] password for lolo:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  swh-plugins blop cmt libcurl3 libfltk1.1 liblo0 libraptor1 liblrdf0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emifreq-applet (0.18-3ubuntu2) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emifreq-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by cmittle on 2007-11-16
I finally figured out what was wrong.  In my searches of other threads on this forum I remember reading something about how a particular line of test in files can cause something to fail.  I finally made the connection that when I installed GraphiteOne according to [this]("http://ubuntuforums.org/showthread.php?p=3588422") thread I was instructed to create a file that would put a link in my menu for launching this program.  I recently decided that GraphiteOne is not for me and uninstalled it, but I didn't delete this entry.  I finally made the connection today that since gnome-_MENUS_ is the thing that is failing maybe something associated with the menus that is causing this.

Here are the last few commands I've entered that seemed to resolve my problems.
```
cory@cory-laptop:/usr/share/applications$ ls *GraphiteOne*
GraphiteOne.desktop  GraphiteOne.desktop~
cory@cory-laptop:/usr/share/applications$ sudo rm *GraphiteOne*
cory@cory-laptop:/usr/share/applications$ ls *Graphite*
ls: *Graphite*: No such file or directory
cory@cory-laptop:/usr/share/applications$ cd ~/
cory@cory-laptop:~$ sudo dpkg --configure gnome-menus
Setting up gnome-menus (2.20.1-0ubuntu1) ...

cory@cory-laptop:~$ sudo dpkg --configure -a
Setting up eog (2.20.1-0ubuntu1) ...

Setting up gedit (2.20.3-0ubuntu1) ...

Setting up gnome-games (1:2.20.1-0ubuntu1) ...

Setting up gnome-control-center (1:2.20.0.1-0ubuntu5) ...

Setting up gcalctool (5.20.2-0ubuntu1) ...

Setting up evince (2.20.1-0ubuntu1) ...

Setting up gnome-session (2.20.1-0ubuntu1) ...

Setting up file-roller (2.20.1-0ubuntu1) ...

Setting up nautilus (1:2.20.0-0ubuntu7) ...

Setting up gnome-about (1:2.20.1-0ubuntu1) ...

Setting up nautilus-cd-burner (2.20.0-0ubuntu1) ...

Setting up gnome-panel (1:2.20.0.1-0ubuntu6) ...

Setting up alacarte (0.11.3-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Thank you Anaconda and Partyboi for the help with my problem.  I apologize I didn't realize that it was a dumb mistake on my part and figure this out sooner.

Cory

---

