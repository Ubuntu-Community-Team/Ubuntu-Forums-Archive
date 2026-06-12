---
title: "create .deb from bash script with dependencies??"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-09-07
Once upon a time I wrote a script to copy dvds, and it worked great. So I thought, why not try to screw it up by adding to it?? So after a great deal of trouble I finally added a neat little progress bar to the script, and would not like to be able to distibute the whole thing as a deb package. The problem is, I don't know the first thing about creating a deb package, and this one has a few dependencies. It depends upon all packages required to watch a dvd, as well as another package for which I will include the .deb. Would anyone be willing to help me get it packaged If I include all necessary info/scripts??

---

### Post by brennydoogles on 2007-09-07
bump

---

### Post by capink on 2007-09-08
Here are the steps to make the deb package:

1. Make a directory in current directory and call it whatever you want. I will call it deb:

```
mkdir deb
```

2. If you want the script to be executed by typing its name, it must be in one of the dirs in your $PATH. I suggest /usr/bin. If that what you have chosen, type the following

```
mkdir -p ./deb/usr/bin
```

3. Copy the script as follows:

```
cp /path/to/the/cpdvd.sh ./deb/usr/bin
```

4. Make A subdirectory called DEBIAN, this will host the package control file (the file that will point to the dependencies):

```
mkdir ./deb/DEBIAN
```

5. Create an empty control file using the following command:

```
touch ./deb/DEBIAN/control
```

6. Open the control file and copy the text below into it after modifying the relevant parts, Don't forget to mention all dependencies :

```
Package: Packagename [COLOR="Red"](no spaces or underscores allowed)[/COLOR]
Priority: optional
Section: misc
Maintainer: Maintainer Name <user@mail.com>
Architecture: all
Version: 1.0
Depends: package1, package2, .........
Description: short description here
 long description here [COLOR="Red"](don't remove the space at the beginning of this line)[/COLOR]
[COLOR="Red"](replace this with an empty line)[/COLOR]
```


Note: Delete the parts highlighted with [COLOR="Red"]red[/COLOR] from the control file, they are just notes made by me.

7. Change ownership:

```
sudo chown -R root.root ./deb
```

8. Create the Debian Package:

```
dpkg -b ./deb /path/you/choose/packagename.deb
```

---

### Post by brennydoogles on 2007-09-08
> **capink said:**
> Here are the steps to make the deb package:

1. Make a directory in current directory and call it whatever you want. I will call it deb:

```
mkdir deb
```

2. If you want the script to be executed by typing its name, it must be in one of the dirs in your $PATH. I suggest /usr/bin. If that what you have chosen, type the following

```
mkdir -p ./deb/usr/bin
```

3. Copy the script as follows:

```
cp /path/to/the/cpdvd.sh ./deb/usr/bin
```

4. Make A subdirectory called DEBIAN, this will host the package control file (the file that will point to the dependencies):

```
mkdir ./deb/DEBIAN
```

5. Create an empty control file using the following command:

```
touch ./deb/DEBIAN/control
```

6. Open the control file and copy the text below into it after modifying the relevant parts, Don't forget to mention all dependencies :

```
Package: Packagename [COLOR="Red"](no spaces or underscores allowed)[/COLOR]
Priority: optional
Section: misc
Maintainer: Maintainer Name <user@mail.com>
Architecture: all
Version: 1.0
Depends: package1, package2, .........
Description: short description here
 long description here [COLOR="Red"](don't remove the space at the beginning of this line)[/COLOR]
[COLOR="Red"](replace this with an empty line)[/COLOR]
```


Note: Delete the parts highlighted with [COLOR="Red"]red[/COLOR] from the control file, they are just notes made by me.

7. Change ownership:

```
sudo chown -R root.root ./deb
```

8. Create the Debian Package:

```
dpkg -b ./deb /path/you/choose/packagename.deb
```


Seems very simple, but I still have a few questions. The dependency "bar" is not available from the repos, will it automatically be included in the .deb by my computer, or do I need to specify a wget address so that it may be automatically downloaded and installed?? Thanks!!

---

### Post by Hendrixski on 2007-09-08
Whoa, something about the steps pointed out above seems excessive, there are scripts that do a lot of those things for you, like creating a control file template for you, etc. etc.

This is my favorite guide.  It takes about an hour to read through it, another 1 or 2 to do the examples and repeat the process on your own project.
[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html)

:-) you'll be a packaging master in 2 or 3 hours. :-)

---

### Post by cjssmo on 2007-09-08
I would suggest using debuild and pbuilder to build your package.  It would also be a good idea to run linda and lintian on your package as these will let you know about potential problems with your package.  I would suggest looking through the debian new maintainers guide and the ubuntu packaging guide located 

[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html)

[http://www.debian.org/doc/maint-guide/index.en.html#contents](http://www.debian.org/doc/maint-guide/index.en.html#contents)

:-D
Good luck

---

### Post by brennydoogles on 2007-09-08
> **Hendrixski said:**
> Whoa, something about the steps pointed out above seems excessive, there are scripts that do a lot of those things for you, like creating a control file template for you, etc. etc.

This is my favorite guide.  It takes about an hour to read through it, another 1 or 2 to do the examples and repeat the process on your own project.
[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html)

:-) you'll be a packaging master in 2 or 3 hours. :-)

seems a bit... complicated to me.....

---

### Post by capink on 2007-09-08
> **brennydoogles said:**
> Seems very simple, but I still have a few questions. The dependency "bar" is not available from the repos, will it automatically be included in the .deb by my computer, or do I need to specify a wget address so that it may be automatically downloaded and installed?? Thanks!!


This can be achieved by adding a postinst script to the package. But I would advise to simply tell people to add the appropriate repositories to their source.list or to give them the link to the bar package. If you are interested in the postinst solution I'm ready to help, but I would wait until you created the package successfully using the method above.

---

### Post by brennydoogles on 2007-09-08
> **capink said:**
> This can be achieved by adding a postinst script to the package. But I would advise to simply tell people to add the appropriate repositories to their source.list or to give them the link to the bar package. If you are interested in the postinst solution I'm ready to help, but I would wait until you created the package successfully using the method above.

ok, I think I would love to take you up on your offer. I believe I have created the .deb successfully, but I will attach it so that someone can double check. Thank you all for your time!!


p.s.-- I am having a hard time finding a name that is not already taken... any Ideas??

---

### Post by capink on 2007-09-09
The package is alright. Just two small modifications:

1. Remove bar from dependencies since it is not satisfiable. We will take of installing bar later.

2. Change the priority in the control file back to optional or extra. There are only five priorities for debian packages: required, important, standard, optional and extra. Never use any one of the first three priority levels for a package you create yourself. And don't capitalize the first letter of the priority (i.e use optional instead of Optional).





To add a postinst script you will do the same steps. But you will insert those extra steps between step 6 and step 7:

```
touch ./deb/DEBIAN/postinst
```

```
chmod a+x  ./deb/DEBIAN/postinst
```

Open postinst file and add the following code into it:

```
#!/bin/sh

# this will download and install the package bar
wget -c --directory-prefix=/tmp /url/to/bar/package.deb
dpkg -i /tmp/complete_name_of_the_bar_package.deb
```



Note1: If the dependencies of the package bar are not satisfied by default ubuntu installation, the postinst script might need some changing. So please give me the link of the bar package to examine its dependencies. Anyway, here is how the postinst would look like if the dependencies are some what complex:

```
#!/bin/sh
# this will download and install the package bar
wget -c --directory-prefix=/tmp/bar /url/to/bar/package.deb
apt-ftparchive packages /tmp/bar > /tmp/bar/Packages
sed  --in-place 's_Filename: '/tmp/bar'/_Filename: _' /tmp/bar/Packages
gzip -9c /tmp/bar/Packages > /tmp/bar/Packages.gz
echo "deb file:///tmp/bar ./" > /etc/apt/sources.list.d/tmp.list
apt-get update
apt-get -y --allow-unauthenticated install bar
rm -f /etc/apt/sources.list.d/tmp.list
rm -rf /tmp/bar
```

Note2: I don't like installing packages **automatically** this way. I would still advise you to simply tell people who are going to use your package to manually install the bar package. Or maybe adding the code of the postinst script as a function in the your script that would **interactively** tell people that the bar package is missing and offer to install it for them.


Note3: Some people have totem-gstreamer installed on their system. This would confilct with totem-xine which is listed as a dependency of your package. So, if both can work for your script, I would advise modifying the dependecy files so it looks as follows:

```
Depends: libdvdread3, libdvdcss2, totem-xine | totem-gstreamer
```

This will not install totem-xine for people who have totem-gstreamer and would not cause any conflict.

---

### Post by brennydoogles on 2007-09-09
> **capink said:**
> The package is alright. Just two small modifications:

1. Remove bar from dependencies since it is not satisfiable. We will take of installing bar later.

2. Change the priority in the control file back to optional or extra. There are only five priorities for debian packages: required, important, standard, optional and extra. Never use any one of the first three priority levels for a package you create yourself. And don't capitalize the first letter of the priority (i.e use optional instead of Optional).





To add a postinst script you will do the same steps. But you will insert those extra steps between step 6 and step 7:

```
touch ./deb/DEBIAN/postinst
```

```
chmod a+x  ./deb/DEBIAN/postinst
```

Open postinst file and add the following code into it:

```
#!/bin/sh

# this will download and install the package bar
wget -c --directory-prefix=/tmp /url/to/bar/package.deb
dpkg -i /tmp/complete_name_of_the_bar_package.deb
```



Note1: If the dependencies of the package bar are not satisfied by default ubuntu installation, the postinst script might need some changing. So please give me the link of the bar package to examine its dependencies. Anyway, here is how the postinst would look like if the dependencies are some what complex:

```
#!/bin/sh
# this will download and install the package bar
wget -c --directory-prefix=/tmp/bar /url/to/bar/package.deb
apt-ftparchive packages /tmp/bar > /tmp/bar/Packages
sed  --in-place 's_Filename: '/tmp/bar'/_Filename: _' /tmp/bar/Packages
gzip -9c /tmp/bar/Packages > /tmp/bar/Packages.gz
echo "deb file:///tmp/bar ./" > /etc/apt/sources.list.d/tmp.list
apt-get update
apt-get -y --allow-unauthenticated install bar
rm -f /etc/apt/sources.list.d/tmp.list
rm -rf /tmp/bar
```

Note2: I don't like installing packages **automatically** this way. I would still advise you to simply tell people who are going to use your package to manually install the bar package. Or maybe adding the code of the postinst script as a function in the your script that would **interactively** tell people that the bar package is missing and offer to install it for them.


Note3: Some people have totem-gstreamer installed on their system. This would confilct with totem-xine which is listed as a dependency of your package. So, if both can work for your script, I would advise modifying the dependecy files so it looks as follows:

```
Depends: libdvdread3, libdvdcss2, totem-xine | totem-gstreamer
```

This will not install totem-xine for people who have totem-gstreamer and would not cause any conflict.

ok,so I made the changes to priority and dependencies (because either totem plugin will work), and I agree that giving the user the ability to choose whether or not to install bar is a good idea. Will I need to basically write the script twice so that it can be run with or without bar?? [Here]("http://clpbar.sourceforge.net/") is a link to bar's sourceforge page (not a direct link to the .deb), and I believe that it has no dependencies. If you would be willing to help me get the contents of the postinst script into mine, that would be wonderful, and I will upload a copy of the current script and the script without the use of bar to help with that. Thank you all for your help!!

---

### Post by capink on 2007-09-09
Here is a function to include in your script to check for and install bar

```
check_bar ()
{
if [ -f /usr/bin/bar ]
then
	:
else
	echo -n 'bar is not installed, do you want to install it? (y,n)'
	read answer
	case $answer in
		y|Y|yes|Yes|YES)
			echo
			wget -c http://dfn.dl.sourceforge.net/sourceforge/clpbar/bar_1.10.9_i386.deb
			sudo dpkg -i bar_1.10.9_i386.deb
			;;
		n|N|no|No|NO)
			echo
			;;
		*)
			echo
			echo 'not a valid response'
			continue
			;;
	esac
fi
}
```

I have not yet tested the above code, but it should work alright.

I looked at the link you gave me. I found that the bar package has no dependencies. This would make things easier.

Another idea that came to me, why not include the bar and clidvdcp in the same debian pakcage. This is sometimes done provided that you add the following fields to the control file

```
Package: clidvdcp
Priority: optional
Section: misc
Maintainer: Brendon Dugan <wishingforayer@gmail.com>
Architecture: all
Version: 1.0
[COLOR="Red"]Provides: bar[/COLOR]
Depends: libdvdread3, libdvdcss2, totem-xine | totem-gstreamer
[COLOR="Red"]Replaces: bar
Conflicts: bar[/COLOR]
Description: Cli package to make exact copies of DVDs
 Cli script to create an ISO backup of any DVD or CD to a user-specified location.
```


So, I repackaged your clidvdcp, only this time it provides the bar in the same deb. It is attached below.

---

### Post by brennydoogles on 2007-09-09
> **capink said:**
> Here is a function to include in your script to check for and install bar

```
check_bar ()
{
if [ -f /usr/bin/bar ]
then
	:
else
	echo -n 'bar is not installed, do you want to install it? (y,n)'
	read answer
	case $answer in
		y|Y|yes|Yes|YES)
			echo
			wget -c http://dfn.dl.sourceforge.net/sourceforge/clpbar/bar_1.10.9_i386.deb
			sudo dpkg -i bar_1.10.9_i386.deb
			;;
		n|N|no|No|NO)
			echo
			;;
		*)
			echo
			echo 'not a valid response'
			continue
			;;
	esac
fi
}
```

I have not yet tested the above code, but it should work alright.

I looked at the link you gave me. I found that the bar package has no dependencies. This would make things easier.

Another idea that came to me, why not include the bar and clidvdcp in the same debian pakcage. This is sometimes done provided that you add the following fields to the control file

```
Package: clidvdcp
Priority: optional
Section: misc
Maintainer: Brendon Dugan <wishingforayer@gmail.com>
Architecture: all
Version: 1.0
[COLOR="Red"]Provides: bar[/COLOR]
Depends: libdvdread3, libdvdcss2, totem-xine | totem-gstreamer
[COLOR="Red"]Replaces: bar
Conflicts: bar[/COLOR]
Description: Cli package to make exact copies of DVDs
 Cli script to create an ISO backup of any DVD or CD to a user-specified location.
```


So, I repackaged your clidvdcp, only this time it provides the bar in the same deb. It is attached below.

You are my hero. That is awesome. My next project will be to create a launcher for it (with Icons and all) in the multimedia section of the applications menu, but I am going to attempt that one on my own before I post back. Thanks for the help!!!!

---

### Post by Wiebelhaus on 2007-09-09
hell yea , subscribed to this thread , props for the progress indicating function! schweet! , things hella fast to.

---

### Post by brennydoogles on 2007-09-09
> **sx66gns said:**
> hell yea , subscribed to this thread.

lol

---

### Post by bobbocanfly on 2007-09-12
Brilliant tutorial managed to get it working first try. Didnt think it would be that simple!

---

### Post by brennydoogles on 2007-09-13
Ok, so I am working on version 2.0 which will include an entry in the applications/multimedia menu, but I am running into a few roadblocks. Here is the current directory structure for my .deb- ```
.
|-- DEBIAN
|   `-- control
`-- usr
    |-- bin
    |   |-- bar
    |   `-- clidvdcp
    `-- share
        |-- applications
        |   `-- Clidvdcp
        |-- doc
        |   `-- bar
        |       |-- changelog.gz
        |       `-- copyright
        |-- man
        |   `-- man1
        |       `-- bar.1.gz
        |-- menu
        |   `-- clidvdcp
        `-- pixmaps
            |-- clidvdcplg.png
            `-- clidvdcpsm.png

11 directories, 10 files

```
and here are the contents of my applications/Clidvdcp file and menu/clidvdcp file:
Menu:
```
?package(clidvdcp):needs="text" section="Apps/Sound"\
  title="Clidvdcp" command="/usr/bin/clidvdcp" \
  icon="/usr/share/pixmaps/clidvdcpsm.png"

```
Applications:
```
[Desktop Entry]
Encoding=UTF-8
Name=Clidvdcp
Comment=Make ISO copy of any disk
GenericName=clidvdcp
Exec=/usr/bin/clidvdcp
Icon=clidvdcpsm.png
Terminal=true
StartupNotify=true
Type=Application
Categories=Application;AudioVideo;

```

What am I doing wrong??

---

### Post by brennydoogles on 2007-09-13
::bump::

---

### Post by brennydoogles on 2007-09-13
::Polite Bump:: ?

---

### Post by capink on 2007-09-14
Rename /usr/share/applications/Clidvdcp into /usr/share/applications/Clidvdcp**.desktop**

---

### Post by brennydoogles on 2007-09-14
> **capink said:**
> Rename /usr/share/applications/Clidvdcp into /usr/share/applications/Clidvdcp**.desktop**

Hmm.... no luck with that on Xubuntu. Would anyone with a different WM be willing to try and see how it works??

---

### Post by capink on 2007-09-14
It is working for me in xfce. Try restarting xfce4-panel by typing:

```
pkill xfce4-panel
exec nohup xfce4-panel
```

Or you can do it graphically using alt+ctrl+esc to kill xfce4-panel. And start it by typing xfce4-panel in the runbox (alt+f2)

---

### Post by capink on 2007-09-14
Examinig your package it seems that you renamed the launcher in thunar which does not work. If you use the command:

```
ls /usr/share/applications
```

you will notice that the filename is still Clidvdcp. So rename it using the command line

```
sudo mv /usr/share/applications/Clidvdcp /usr/share/applications/Clidvdcp.desktop
```

If that does not work try the file attached below.

---

### Post by brennydoogles on 2007-09-14
> **capink said:**
> Examinig your package it seems that you renamed the launcher in thunar which does not work. If you use the command:

```
ls /usr/share/applications
```

you will notice that the filename is still Clidvdcp. So rename it using the command line

```
sudo mv /usr/share/applications/Clidvdcp /usr/share/applications/Clidvdcp.desktop
```

If that does not work try the file attached below.

ah... I see. I am usually a Gnome man, but I have a crappy old laptop that does not perform well with Gnome, so I use Xubuntu on it. I will take care of that when I return to my computer, and there will be a new .deb up by tonight!!

---

### Post by brennydoogles on 2007-09-16
Ok, so I am kinda going to go a different direction with this thread for a minute, but exactly is the Anatomy of an Ubuntu/Debian approved .deb?? The reason I asked was that I have been inspired to write a script to create the directory structure for a Debian installer, and package it for you once you have added all of the necessary components ( actually pausing to give you time to edit the control file and add some files before it even gives you the option to package). But the moral of the story is that in order to make ONLY debian compliant .debs I need to know exactly which directories are needed, what needs to go in them,and if there are any special configuration files, specifics on what those should be, and an example if anyone is willing to contribute one (btw capink, if possible may I use your example control file as the default for the script??). Any Help would be greatly appreciated, and I promise to make the .deb available as soon as everything is complete!!

---

### Post by capink on 2007-09-17
There is a good book called :The Debian System - Concepts and Techniques. It was available at the world wide web last year in the no starch press website, but it is now removed. I don't have a copy of the book anymore. This book contained a lot of things about debian including details about debian packages.

Another two links that might be of some value:

[The Debian Policy.]("http://www.debian.org/doc/debian-policy/index.html")
[Google Video: Anatomy of a Debian Package.]("http://video.google.com/url?docid=-6726522426109060914&esrc=sr1&ev=v&len=3376&q=debian%2Bpackage&srcurl=http%3A%2F%2Fvideo.google.com%2Fvideoplay%3Fdocid%3D-6726522426109060914&vidurl=%2Fvideoplay%3Fdocid%3D-6726522426109060914%26q%3Ddebian%2Bpackage%26total%3D23%26start%3D0%26num%3D10%26so%3D0%26type%3Dsearch%26plindex%3D0&usg=AL29H221CM5xEq3ZFTXJ0DraeuHvkWw7VQ")

And of course you can use the control file. It is not mine, it is a file created form the debian policy specs.

---

### Post by brennydoogles on 2007-09-17
> **capink said:**
> There is a good book called :The Debian System - Concepts and Techniques. It was available at the world wide web last year in the no starch press website, but it is now removed. I don't have a copy of the book anymore. This book contained a lot of things about debian including details about debian packages.

Another two links that might be of some value:

[The Debian Policy.]("http://www.debian.org/doc/debian-policy/index.html")
[Google Video: Anatomy of a Debian Package.]("http://video.google.com/url?docid=-6726522426109060914&esrc=sr1&ev=v&len=3376&q=debian%2Bpackage&srcurl=http%3A%2F%2Fvideo.google.com%2Fvideoplay%3Fdocid%3D-6726522426109060914&vidurl=%2Fvideoplay%3Fdocid%3D-6726522426109060914%26q%3Ddebian%2Bpackage%26total%3D23%26start%3D0%26num%3D10%26so%3D0%26type%3Dsearch%26plindex%3D0&usg=AL29H221CM5xEq3ZFTXJ0DraeuHvkWw7VQ")

And of course you can use the control file. It is not mine, it is a file created form the debian policy specs.


Thank you very much for your help. I will look at the video after class today, and see what all I can get out of it. You guys RAWK!!!!

---

### Post by brennydoogles on 2007-09-22
Ok, so after a long pause, here is the first version of my script to create custom debs. I would love to have a few people try it and see if they can crash it (so i can fix it), and if anyone has any ideas on how to make it better, I would love to hear them!!

---

### Post by brennydoogles on 2007-09-24
> **brennydoogles said:**
> Ok, so after a long pause, here is the first version of my script to create custom debs. I would love to have a few people try it and see if they can crash it (so i can fix it), and if anyone has any ideas on how to make it better, I would love to hear them!!

Has anyone given it a try yet??

---

### Post by jcp2mill on 2008-03-31
Hi,

I realize you may have moved on from this now but this script doesn't seem to create the mydeb folder when I run it.

The script itself is a great idea I spent ages trying to create a deb of some scripts I wrote and all the tutorials I look at seem to be for people wanting to make debs from source code.:guitar:

Thanks

---

### Post by jcp2mill on 2008-03-31
Hi,

Found the problem the script won't run unless you run it as sudo otherwiise you get "permission denied"

because you run it as sudo $USER returns root and thus files are created in the root directory.:)

---

