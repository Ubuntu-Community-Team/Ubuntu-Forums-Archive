---
title: "Help Installing Celtx"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Nodestar on 2008-04-13
I can't install this program any way I go about it. I think it's because of my lack of understanding of files and file paths in Ubuntu. 

This is a terminal install method suggested. 


cd /usr/local

sudo tar zxf /path/to/Celtx.tar.gz

(enter your password)

sudo /usr/local/celtx/celtx


I'm guessing that you need to replace the usr/local with your own information. But I'm not sure what that information is. My user name on Ubuntu us justin. When I download the Celtx.tar.gz file it's on my desktop. 

My error is

tar: /path/to/Celtx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
justin@justin-laptop:/usr/local$ 


Another method that didn't work for me was extracting the Celtx.tar.gz file to my Home folder and renaming it .Celtx and then clicking on the Celtx file.
A window appears saying celtx is an executable file and it gives me 4 options.

Run in Terminal
Display
Cancel
Run

I've tried Run in Terminal and Run and nothing happens for both of them.

Any information would be great.

---

### Post by kfir on 2008-04-13
tar: /path/to/Celtx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
justin@justin-laptop:/usr/local$ 

you have to put instead "path" the location of the file(where u download him)

---

### Post by Michael.Godawski on 2008-04-13
Here is a guide site which explains how to install applications in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

and here the section concerning tar files:
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Nodestar on 2008-04-13
If it's on my Desktop then what would that be?

I've tried 

/Desktop/to 
/home/justin/Desktop

and many others. I'm not familiar enough with the file system.

---

### Post by Michael.Godawski on 2008-04-13
When you open the terminal type
```
ls
```
This should display all folders and files in your home directory. One of them should be Desktop. To navigate into the Desktop folder run:
```
cd Desktop
```
The whole path to your Desktop is:
```
/home/username/Desktop
```

---

### Post by Michael.Godawski on 2008-04-13
```
cd /usr/local
```
This brings you into the /usr/local folder.
```

sudo tar zxf /home/justin/Desktop/Celtx.tar.gz
```
This should extract the tar.gz form your Desktop to the local folder.
```

sudo /usr/local/celtx/celtx
```
This seems to be the executable line.

---

### Post by Nodestar on 2008-04-13
Ok. I'm to the point of sudo /usr/local/celtx/celtx

I don't know what to replace usr or local with.. and I'm not really sure what that command line is doing.. am I looking for celtx or installing it?

---

### Post by Michael.Godawski on 2008-04-13
For me who do not know the exact files of the celtx folder
it seems that the line
```
sudo /usr/local/celtx/celtx
```
runs the executable file. I also think the application is already installed only by extracting it to the correct location.

And you do not need to replace /usr/local with anything. The directory exists in real.
When you go to Places > Computer > Filesystem > usr > local
you can navigate easily to it.

---

### Post by Nodestar on 2008-04-13
Alright. I've got all that worked out. But when putting in the last line I get an error.

error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

It's talked about on another install page

If you get an error error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory then you need to install a package that contains libstdc++.so.5. On Redhat and Ubuntu, this is the compat-libstdc++ package. On Gentoo, it's just called lib-compat. You might be able to install it using yum install compat-libstdc++

I don't have Yum and I can't install it the way the Terminal suggest. I've tryed useing the Synaptic Package Manager and I can search for compat-libstdc++ package and it finds it but I don't understand how to make it download it. If I look for it manually by scrolling through "All" in Alphabetical order I can't find it.

---

### Post by Michael.Godawski on 2008-04-13
If you find the needed package in synaptic that we are a step forward. You can use the search field  to find it. When the entry is displayed, check the box next to it and mark for installation. Then click on the Apply button, confirm and then the file should be downloaded and installed automatically.

---

### Post by isparkes on 2008-04-13
Stick with it, nearly there...

This is one of the nice/nasty things about the way Linux stuff works: Instead of putting all the bits and pieces that you need into a single install package, standard libraries are used instead. The nice bit is that it all remains fairly small on the disk ( no bloatware), the nasty side is that you have to install it separately, and it is not always that clear what to install.

Once you've got the hang of resolving these dependencies, you'll appreciate the tidiness that it brings.

I think you'll have to install the "libstdc++5" package. Once you have installed it, you can see the files that are inside the package, but I think you should be OK with this. You can install with Synaptic "System->Administration->Synaptic Package Manager".

Let me know...

---

### Post by Nodestar on 2008-04-13
Ok. I understand the Synaptic Package Manager a little more now. I can't find "libstdc++5" package with it. Even with the two 3rd party repositories that come with it enabled.

Another install site suggest trying this Terminal Command to download it 
yum install compat-libstdc++

I get the Error 

The program 'yum' is currently not installed.  You can install it by typing:
sudo apt-get install yum
bash: yum: command not found

I then type in sudo apt-get install yum

To try and download Yum.
And get this error.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What does that mean. What process could be using it?

---

### Post by Michael.Godawski on 2008-04-13
Close the synaptic package manager. Linux do not allow two or more installing or updating application to run simultaneously to avoid errors during the installation.

---

### Post by Nodestar on 2008-04-13
Ok. Got Yum to install with the Terminal then ran yum install compat-libstdc++

Got this Error


There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named cElementTree

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.5.1 (r251:54863, Mar  7 2008, 04:10:12) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)]

If you cannot solve this problem yourself, please send this
message to <yum@lists.linux.duke.edu>.



I have python 2.5 according to Add/Remove Applications. I'm guessing that close enough to 2.5.1. So I'm missing  cElementTree?? 

This doesn't even seem worth it anymore. I switched from Ubuntu to Windows to get rid of all the useless crap on my PC. And here I am downloading all kinds of weird stuff that doesn't work. 

I don't know where to go next.

---

### Post by Michael.Godawski on 2008-04-13
Weird. When I search for libstdc++5 ( I have 7.10 ubuntu) I already have it pre-installed. Perhaps you need to install also the dev version.
Run this in terminal to install the needed packages:
```
sudo apt-get install libstdc++5 libstdc++5-3.3-dev
```

---

### Post by Nodestar on 2008-04-13
Thank You. That worked. I typed in the last command sudo /usr/local/celtx/celtx and it came up.

Now I'm trying to put it in the Applications window and having no luck. I can't find the executionable file. Everyone says it's celtx/celtx

I can find the file. It just won't work by its self for some reason.

Edit:

Also I've tried the usr/local/celtx/celtx path as well as the home/justin/.celtx/celtx path that was leftover from my past attempts to install the software. Although now for some reason I cannot manipulate those folders in my home/justin because ubuntu is telling me I don't have privileges. I have the only account and I had the privileges before. So not sure what the deal is with that.


Edit: Ok. I think I found the problem. Just need to delete the old .celtx files. But it's not letting me. Anyway to bypass privileges?

I'm foolling around with sudo rm .celtx terminal commands. No luck yet.

---

### Post by isparkes on 2008-04-13
Ah, the dev packages as well, nice thought Michael, I didn't think of that.

You can add a launcher (an icon for the desktop) by right clicking on the desktop and selecting "Create Launcher". In the last tab you can put the full path to the executable. In the first tab you can add an icon and description etc. You can also add this to the menu if you want. It doesn't get added automatically because it is not an Ubuntu maintained app.

---

### Post by Nodestar on 2008-04-13
Just gota figure out how to delete the .celtx in my home and I should be good. One of the install guides says that needs to be deleted if it's only letting me run celtx from the root. I'm guessing that whats happening when my shortcuts or Launchers arn't working.

---

### Post by lswest on 2008-04-13
to delete the .celtx folder you can do this ```
sudo rm -r /home/justin/.celtx
``` which will delete the folder, but be sure to type it in right.  Also, you can do it from the gui by giving in ```
gksudo nautilus
``` and then browsing and deleting (gives you root permissions) - hit ctrl + h to show hidden files

---

### Post by isparkes on 2008-04-13
if you can show me the permissions on the directory with 'ls -la $HOME', we can work it out. I guess that the owner is root and you only have read permissions on the directory.

Just a note, the "." in front of the name is the Linux way of saying it is a hidden file, and the hidden files in the home directory are usually where apps stash their settings.

---

### Post by Nodestar on 2008-04-13
The Terminal Command worked for the /home/justin/.celtx

But I can't delete the Desktop Celtx file. Thats where I extracted it and then copied it to the  home/justin/.celtx. 

I can't find anything in the GUI with the gksudo nautilus command. I can go to desktop but it doesn't show the celtx file.

---

### Post by Nodestar on 2008-04-13
Well I am the App. I have the only account on this machine and my Ubuntu install is only 5 hours old. Also I have permission to view and altar every other file in those directories. Just not these. And I used to be able too. I'm the one that put these files there when I was originally trying to install Celtx in various ways. Now that it's installed another way I want them gone. Also when I was missing around with the Pack Manager I got a file on in my home directory that is also protected from being deleted by me. It's path is home/justin/Tom

Here is the info you asked for. I hope.

justin@justin-laptop:~$ ls -la $HOME
total 212
drwxr-xr-x 34 justin justin  4096 2008-04-13 05:41 .
drwxr-xr-x  3 root   root    4096 2008-04-12 19:20 ..
drwx------  3 justin justin  4096 2008-04-13 02:28 .adobe
-rw-------  1 justin justin  1640 2008-04-13 05:42 .bash_history
-rw-r--r--  1 justin justin   220 2008-04-12 19:20 .bash_logout
-rw-r--r--  1 justin justin  2298 2008-04-12 19:20 .bashrc
drwxr-xr-x  3 justin justin  4096 2008-04-12 19:34 .cache
drwxr-xr-x  6 justin justin  4096 2008-04-13 01:56 .config
drwx------  2 justin justin  4096 2008-04-12 20:59 .dbus-keyrings
drwxr-xr-x  3 justin justin  4096 2008-04-13 05:27 Desktop
-rw-------  1 justin justin    28 2008-04-13 01:04 .dmrc
drwxr-xr-x  3 justin justin  4096 2008-04-13 01:42 Documents
-rw-------  1 justin justin    16 2008-04-12 19:34 .esd_auth
lrwxrwxrwx  1 justin justin    26 2008-04-12 19:20 Examples -> /usr/share/example-content
drwx------  3 justin justin  4096 2008-04-13 03:04 file:
drwxr-xr-x  2 justin justin  4096 2008-04-12 19:34 .fontconfig
drwx------  5 justin justin  4096 2008-04-13 01:31 .gconf
drwx------  2 justin justin  4096 2008-04-13 05:42 .gconfd
-rw-r-----  1 justin justin     0 2008-04-13 04:53 .gksu.lock
drwxr-xr-x  3 justin justin  4096 2008-04-12 19:34 .gnome
drwx------ 12 justin justin  4096 2008-04-13 02:33 .gnome2
drwx------  2 justin justin  4096 2008-04-12 19:34 .gnome2_private
drwx------  3 root   root    4096 2008-04-13 05:02 .greyfirst
drwxr-xr-x  2 justin justin  4096 2008-04-13 01:52 .gstreamer-0.10
-rw-r--r--  1 justin justin   112 2008-04-13 01:04 .gtk-bookmarks
-rw-r--r--  1 justin justin    88 2008-04-12 19:34 .gtkrc-1.2-gnome2
-rw-------  1 justin justin   173 2008-04-13 01:04 .ICEauthority
drwxr-xr-x  3 justin justin  4096 2008-04-12 19:34 .local
drwx------  3 justin justin  4096 2008-04-13 02:28 .macromedia
drwx------  3 justin justin  4096 2008-04-12 20:26 .mozilla
drwxr-xr-x  2 justin justin  4096 2008-04-13 01:46 Music
drwxr-xr-x  3 justin justin  4096 2008-04-13 01:02 .nautilus
drwxr-xr-x  3 justin justin  4096 2008-04-13 01:42 Pictures
-rw-r--r--  1 justin justin   566 2008-04-12 19:20 .profile
drwxr-xr-x  2 justin justin  4096 2008-04-12 19:34 Public
drwx------  5 justin justin  4096 2008-04-13 04:00 .purple
drwxr-xr-x  2 justin justin  4096 2008-04-13 01:07 QuickStart
-rw-r--r--  1 justin justin  3298 2008-04-13 05:27 .recently-used.xbel
-rw-r--r--  1 justin justin     0 2008-04-12 19:35 .sudo_as_admin_successful
drwxr-xr-x  2 justin justin  4096 2008-04-12 19:34 Templates
drwx------  3 justin justin  4096 2008-04-13 04:35 .thumbnails
drwxr-xr-x  2 root   root    4096 2008-04-13 04:19 Tom
drwx------  2 justin justin  4096 2008-04-13 04:28 .Trash
drwxr-xr-x  2 justin justin  4096 2008-04-12 19:37 .update-manager-core
drwx------  2 justin justin  4096 2008-04-12 20:59 .update-notifier
drwxr-xr-x  2 justin justin  4096 2008-04-12 19:34 Videos
drwx------  2 justin justin  4096 2008-04-13 02:38 .w3m
-rw-------  1 justin justin   124 2008-04-13 01:04 .Xauthority
-rw-r--r--  1 justin justin 31521 2008-04-13 05:27 .xsession-errors
justin@justin-laptop:~$

---

### Post by Nodestar on 2008-04-13
Everything is deleted. All good there.

Still can't get the short cuts to work. I think it has somthing to do with my weird loss of being the king user or whatever. The only time I can run Celtx is in the command line and only with sudo /usr/local/celtx/celtx

Sudo in front. Other than that I can't even make it run by going to the path myself and double clicking on it.


Edit:

I belive the exact problem to be that the file isn't owned by me but owned by root. 

Any known fixes?

---

