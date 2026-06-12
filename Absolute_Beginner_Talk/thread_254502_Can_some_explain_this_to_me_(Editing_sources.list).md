---
title: "Can some explain this to me? (Editing sources.list)"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-09-10
I need to install a software, which is available both as an .rpm file and also a .deb file. The process of installing the latter is provided here - 
[http://www.ap-i.net/skychart/page-32.html](http://www.ap-i.net/skychart/page-32.html) . The first line in the page says
> First become root and edit the file /etc/apt/sources.list to add the following line:

How do I do this? I tried ```
sudo edit /etc/apt/sources.list 
```; it doesn't seem to be right. 

I have also downloaded the rpm package, because the internet connection in Ubuntu is not very reliable, and I may need to install with something that I already have on the disk.

Thanks for any help.

---

### Post by aysiu on 2006-09-10
```
sudo nano -B /etc/apt/sources.list
``` should do the trick. To save when you're done, do Control-X, Y, and Enter.

To install a single .deb from your desktop: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` To install a single .rpm from your desktop: ```
sudo aptitude update
sudo aptitude install alien
cd ~/Desktop
sudo alien -i *.rpm
```

---

### Post by SkyNet2029 on 2006-09-10
A very simple to use editor would be nano, which you can access and use to edit the 'sources.list' file this way:

```
$sudo nano /etc/apt/sources.list
```

The operations to save your work when finished are listed plainly along the bottom of nano's input field. 

You could always use alien to install the .rpm, but it's generally less likely to foobar things if you stick with the .deb packages.

---

### Post by wildseven on 2006-09-10
if you would like to see a text editor you can

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by navneeth on 2006-09-10
Thanks for the replies.

I was able to add the line to the sources.list file. But now, as per the instructions, when I add 'apt-get update' I see the following lines...
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

Just wondering - what are the differences between ```
sudo nano -B /etc/apt/sources.list 
``` and ```
$sudo nano /etc/apt/sources.list
```, if any?

---

### Post by Malac on 2006-09-10
> **navneeth said:**
>  I was able to add the line to the sources.list file. But now, as per the instructions, when I add 'apt-get update' I see the following lines...
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

``` 

This is because apt-get is a "system" command which requires root privileges. The command should be:
```
sudo apt-get update
``` 
> **navneeth said:**
>  Just wondering - what are the differences between ```
sudo nano -B /etc/apt/sources.list 
``` and ```
$sudo nano /etc/apt/sources.list
```, if any? 
The -B option creates backups of edited files.

Most programs have a help list in them if you type the name of the app followed by --help, or sometimes -h, as in:
```
nano --help
Usage: nano [+LINE,COLUMN] [GNU long option] [option] [file]

Option          Long option             Meaning
 -h, -?         --help                  Show this message
 +LINE,COLUMN                           Start at line LINE, column COLUMN
 -A             --smarthome             Enable smart home key
 -B             --backup                Save backups of existing files
 -C [dir]       --backupdir=[dir]       Directory for saving unique backup files -E             --tabstospaces          Convert typed tabs to spaces
 -F             --multibuffer           Enable multiple file buffers
 -H             --historylog            Log & read search/replace string history -I             --ignorercfiles         Don't look at nanorc files
 -K             --rebindkeypad          Fix numeric keypad key confusion problem -L             --nonewlines            Don't add newlines to the ends of files
 -N             --noconvert             Don't convert files from DOS/Mac format
 -O             --morespace             Use more space for editing
 -Q [str]       --quotestr=[str]        Quoting string
 -R             --restricted            Restricted mode
 -S             --smooth                Smooth scrolling
 -T [#cols]     --tabsize=[#cols]       Set width of a tab in cols to #cols
 -U             --quickblank            Do quick statusbar blanking
 -V             --version               Print version information and exit
 -W             --wordbounds            Detect word boundaries more accurately
 -Y [str]       --syntax=[str]          Syntax definition to use
 -c             --const                 Constantly show cursor position
 -d             --rebinddelete          Fix Backspace/Delete confusion problem
 -i             --autoindent            Automatically indent new lines
 -k             --cut                   Cut from cursor to end of line
 -l             --nofollow              Don't follow symbolic links, overwrite
 -m             --mouse                 Enable mouse
 -o [dir]       --operatingdir=[dir]    Set operating directory
 -p             --preserve              Preserve XON (^Q) and XOFF (^S) keys
 -r [#cols]     --fill=[#cols]          Set fill cols to (wrap lines at) #cols
 -s [prog]      --speller=[prog]        Enable alternate speller
 -t             --tempfile              Auto save on exit, don't prompt
 -v             --view                  View (read only) mode
 -w             --nowrap                Don't wrap long lines
 -x             --nohelp                Don't show help window
 -z             --suspend               Enable suspend
 -a, -b, -e,
 -f, -g, -j                             (ignored, for Pico compatibility)

```
Hope this helps.

---

### Post by navneeth on 2006-09-10
Thanks, Malac. The software is being downloaded as I type. :)

---

### Post by Malac on 2006-09-10
You are most welcome. :)

---

