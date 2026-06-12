---
title: "HowTo: 'Cheese' (App like PhotoBooth)"
date: 2007-06-28
forum: Apple Intel Users
---

### Post by cyberdork33 on 2007-06-28
[COLOR=Red][B][SIZE=3]NOTE: Cheese will be included with gnome 2.22 and will follow the gnome release schedule. The current release (2.21.5) requires gstreamer 0.10.15 and the version of gsteamer in the repos is 0.10.14, thus the latest release will not compile unless you first get a newer version of gstreamer. You can check your version of gstreamer with
[/SIZE][/B][/COLOR] ```
pkg-config --modversion gstreamer-0.10
```[SIZE=3][COLOR=Red]**Cheese is available in the Universe repository for Gutsy Gibbon.**[/COLOR][/SIZE]
[http://packages.ubuntu.com/gutsy/gnome/cheese](http://packages.ubuntu.com/gutsy/gnome/cheese)

[COLOR=Red][B][SIZE=3][SIZE=2]Alternative Ubuntu deb Packages are available at:[/SIZE]
[/SIZE][/B][/COLOR][http://www.getdeb.net/app.php?name=Cheese](http://www.getdeb.net/app.php?name=Cheese)



This involves compiling, but don't leave. It's easy!

**First get your iSight working**
Before running the application, make sure you have your iSight working as instructed at [http://ubuntuforums.org/showthread.php?t=491381](http://ubuntuforums.org/showthread.php?t=491381)

**Get the latest source release**
Go here and get the latest package:
[http://www.gnome.org/projects/cheese/]("http://live.gnome.org/Cheese#head-08215120a619c27294d53bff4e68e1cf8d658f99")

Open a terminal and navigate to the location where you downloaded the archive.
Now extract the source code:
```
$ tar -xzvf cheese*.tar.gz
``````
$ cd cheese*
```**Now the compiling**
Requirements according to website ([_http://www.gnome.org/projects/cheese/_]("http://www.gnome.org/projects/cheese/")):[LIST]
[*]glib-2.0 >= 2.12.1
[*]gobject-2.0
[*]gtk+-2.0 >= 2.10.0
[*]libglade-2.0 >= 2.0.0
[*]gdk-2.0
[*]dbus-1
[*]hal
[*]cairo
[*]gstreamer-0.10 >= 0.10.15
[*]gstreamer-plugins-base-0.10  >= 0.10.15
[*]gstreamer-plugins-good-0.10  >= 0.10.15
[*]gnome-vfs-2.0
[*]libgnomeui-2.0
[*]xf86vidmodeproto
[*]libebook-1.2 (evolution-data-server)
[*]postr for Flickr export (optional)
[*]f-spot for F-Spot export (optional)
[*]a webcam (a v4l2-webcam is highly recommended)
[*]a brain[/LIST]Here are all the packages I installed, some may not be required, and more may be required to use all features. I am using Ubuntu 7.04 Feisty Fawn.
```
$ sudo aptitude install build-essential libglib2.0-dev python-gobject-dev libgtk2.0-dev libglade2-dev libdbus-1-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev gstreamer0.10-plugins-good libpango1.0-dev libgnomevfs2-dev libcairo2-dev libgnomeui-dev libebook1.2-dev libxxf86vm-dev
```First we need to configure the build environment:
```
$ ./configure
```Now we can build the binary:
```
$ make
```Finally, install:
```
$ sudo make install
```**Running the app**
Cheese should appear in Applications > Accessories > cheese

Corrections / Change Suggestions are welcome.

---

### Post by ronocdh on 2007-06-28
Now this is a freaking how-to! STICKY! :D

---

### Post by xfile087 on 2007-06-29
Incredible. I found out about this app the earlier in the week but couldn't install it nor could I find out how-to anywhere - i'm a bit of n00b really - so anyway I gave up.

Now I see your thread and WOW I got it working! Well done on making this how-to!!!

---

### Post by André Schnabel on 2007-06-29
Awesome app with nice effects. Some interface improvements like dragging photos would be nice, but except for that it's great. Oh and I like the fact, that it's written using GTK+, so it perfectly integrates in my Gnome environment. :D

---

### Post by cyberdork33 on 2007-06-29
This app is still very early in development. (It was started April 2007). If you have feature suggestions or want to contribute (he needs translations I am sure) then you can go to the Cheese website: [http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)

He has contact information there, as well as planned additions (video support!)

---

### Post by ivesjd on 2007-06-29
haha, with a fresh Ubuntu Install it works! yay!

---

### Post by JordiMac on 2007-07-01
[http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)

[IMG]http://live.gnome.org/Cheese?action=AttachFile&do=get&target=cheese-big.png[/IMG]

> WARNING: in version 0.1.2, Cheese isn't shown in your task list (<alt>-<tab> and the taskbar). To fix that behavior, simply set the line <property name="skip_taskbar_hint">True</property> to <property name="skip_taskbar_hint">False</property> in data/cheese.glade (line 11). This is already fixed in the repository
 WARNING: Cheese doesn't support V4L at the moment. The reason for this is unknown, if anybody has a hint for me (as i don't own a V4L-Device), drop a line!

[http://live.gnome.org/Cheese/Releases](http://live.gnome.org/Cheese/Releases)

Requirements

Requirements:

glib-2.0 >= 2.12.0

gobject-2.0
gtk+-2.0 >= 2.10.0

libglade-2.0 >= 2.0.0

gdk-2.0
dbus-1
gstreamer-0.10 >= 0.10.12

gstreamer-plugins-base-0.10 >= 0.10.12

gstreamer-plugins-good-0.10 >= 0.10.12

gnome-vfs-2.0
cairo
a webcam
a brain

I cannot install it, single as root works and in terminal

---

### Post by cyberdork33 on 2007-07-01
Thanks for the update notification! The Icon looks nice.

---

### Post by ivesjd on 2007-07-01
Just downloaded the latest release (July 1st, 2007)

* ./configure
* make
* sudo make install

and thats it. Well other then setting gstreamer-properties to the iSight.

---

### Post by cyberdork33 on 2007-07-01
> **ivesjd said:**
> Just downloaded the latest release (July 1st, 2007)

* ./configure
* make
* sudo make install

and thats it. Well other then setting gstreamer-properties to the iSight.

YAY... ok modifying OP

EDIT: Is anyone else getting a really slow response with the video? Like the window's video lags? It looks fine in ekiga and the gstreamer test...

---

### Post by cyberdork33 on 2007-07-02
Just saw the developer's homepage:
[http://home.cs.tum.edu/~siegel/](http://home.cs.tum.edu/~siegel/)
**"this is for the ubuntu guys"**

Nice tip of the hat. Please give him bug reports and maybe a little support ;)

---

### Post by JordiMac on 2007-07-02
now if that works thanks :popcorn: :popcorn: ;);)

---

### Post by cyberdork33 on 2007-07-02
> **cyberdork33 said:**
> EDIT: Is anyone else getting a really slow response with the video? Like the window's video lags? It looks fine in ekiga and the gstreamer test...

To answer my own question...
>  ATTENTION: If you are getting a really slow response with the video, the video is sluggish and everything looks quite slow, like as the video lags, you may have set "ximagesink" (X Window System (No Xv)) as video-output. This means, that your cpu is doing all the work. Change it to "xvimagesink" (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.

Also cheese 0.1.3 has been released.

---

### Post by ivesjd on 2007-07-03
LOL. 0.1.3 already? they just released 0.1.2 on The 1st.  Although, they seem to be important fixes.

---

### Post by wigglydiggly on 2007-07-04
During make I got this error:

@Macbook:~/Desktop/cheese-0.1.3$ sudo make
Making 'all' in /home/brad/Desktop/cheese-0.1.3/src
cc -o ../mkdep-toc2 /home/brad/Desktop/cheese-0.1.3/toc2/bin/mkdep-toc2.c
COMPILE C [cheese.c] ...
COMPILE C [pipeline-photo.c] ...
COMPILE C [fileutil.c] ...
COMPILE C [thumbnails.c] ...
COMPILE C [window.c] ...
COMPILE C [cairo-custom.c] ...
CXX [cheese] ...
Making 'all' in /home/brad/Desktop/cheese-0.1.3/po
Makefile:6: *** Could not find msgfmt in PATH. Cannot generate cs.mo.  Stop.
make: *** [po] Error 2

Does anyone have any ideas.  Running on MacBook C2D.

Thanks in advance!

---

### Post by cyberdork33 on 2007-07-04
well I don't know why you don't have it, but try this:
```
$ sudo aptitude install gettext
``` then try again

---

### Post by wigglydiggly on 2007-07-05
well I don't know why you don't have it, but try this:
Code:

$ sudo aptitude install gettext

Thank you cyberdork that fixed it.

---

### Post by marcos.linux on 2007-07-06
I made a .deb for AMD64 users :-) (using gutsy)

[http://www.bashterritory.com/cheese_0.1.3-1_amd64.deb]("http://www.bashterritory.com/cheese_0.1.3-1_amd64.deb")

---

### Post by JordiMac on 2007-07-15
[http://www.getdeb.net/app.php?name=Cheese](http://www.getdeb.net/app.php?name=Cheese)

---

### Post by cyberdork33 on 2007-08-15
Cheese 0.2.0 is now released with video support.

---

### Post by benanzo on 2007-08-15
> **cyberdork33 said:**
> Cheese 0.2.0 is now released with video support.

did you get it to compile?  it's telling my I need gstreamer-0.12 even though the requirements are gstreamer-0.10 >= 0.10.12

---

### Post by cyberdork33 on 2007-08-15
> **benanzo said:**
> did you get it to compile?  it's telling my I need gstreamer-0.12 even though the requirements are gstreamer-0.10 >= 0.10.12
yes. I had a new requirement for libgnomeui, that was it. I didn't get anything about gstreamer.

---

### Post by FreakinSyco on 2007-08-18
I keep getting the following error:

Configure failed, sorry! Please make shure that you have installed libgnomeui-2.0 

But I cant find that package in synaptic or any decent information in a google search. Any hints?

EDIT: and lol @ the misspelling of "sure"

EDIT 2: gnomeui-dev package fixed it.

---

### Post by cyberdork33 on 2007-08-19
> **FreakinSyco said:**
> Configure failed, sorry! Please make sure that you have installed libgnomeui-2.0
Fixed Opening post.

---

### Post by teolemon on 2007-08-22
0.2.2 is available as a Feisty deb (both 32 and 64 bit) on GetDeb
[http://www.getdeb.net/app.php?name=Cheese](http://www.getdeb.net/app.php?name=Cheese)

---

### Post by cyberdork33 on 2007-08-22
Just a note. I got a linkback from the developer's site on my how to... Nice.

Also, According to the dev, the 0.2.1 version is ~= 1.0 full release. Enjoy! Also V4L (as opposed to V4L2) now works.

Cheese has been included in the Gutsy Universe repository:
[http://packages.ubuntu.com/gutsy/gnome/cheese](http://packages.ubuntu.com/gutsy/gnome/cheese)

---

### Post by FreakinSyco on 2007-08-22
Fantastic program. Been lookng for something like this for awhile.

---

### Post by cyberdork33 on 2007-08-22
Just an update. I am getting some issues with my iMac. 0.2.0 worked fine, but with 0.2.2, there is no video preview in the photo-mode, but works fine in video mode, anyone getting the same problem?

---

### Post by teolemon on 2007-08-26
There were some issues fixed in the dev version. The next version should be out soon.

---

### Post by cyberdork33 on 2007-08-26
> **teolemon said:**
> There were some issues fixed in the dev version. The next version should be out soon.

Oh yea the dev version works much better.

---

### Post by ivesjd on 2007-09-03
I updated my how to. You should add this line.
```
 sudo apt-get install libxxf86vm-dev 
```
Although it still would not compile for me. (Ended up just going with the 0.2.2 deb)

---

### Post by cyberdork33 on 2007-09-03
> **ivesjd said:**
> I updated my how to. You should add this line.
```
 sudo apt-get install libxxf86vm-dev 
```Although it still would not compile for me. (Ended up just going with the 0.2.2 deb)
If you can show the error...

0.2.2 has some pretty ugly bugs, at least for some people. 0.2.3 is now released and in the gutsy repository and is on getdeb.net for feisty: [http://www.getdeb.net/release.php?id=1367](http://www.getdeb.net/release.php?id=1367)

---

### Post by ivesjd on 2007-09-03
If I get time I'll try to reporduce the errors, (that requires downloading cheese again) And somehow I missed 0.2.3 on getdeb. Not sure how I did that.

---

### Post by cyberdork33 on 2007-09-04
> **ivesjd said:**
> If I get time I'll try to reporduce the errors, (that requires downloading cheese again) And somehow I missed 0.2.3 on getdeb. Not sure how I did that.

It is in a different location. The cheese website always has the latest links.
[http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)

---

### Post by Bossieman on 2008-01-02
I cant compile 0.3 :(

```
checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.10.0   gtk+-2.0 >= 2.10.0   libgnomeui-2.0 >= 2.14.0   libglade-2.0 >= 2.6.0   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.15   gstreamer-plugins-base-0.10 >= 0.10.15   gnome-vfs-2.0 >= 2.18.0   libebook-1.2 >= 1.12.0   cairo >= 1.2.4   dbus-1 >= 1.0   hal >= 0.5.9   dbus-glib-1 >= 0.7   xxf86vm) were not met:

Requested 'gstreamer-0.10 >= 0.10.15' but version of GStreamer is 0.10.14
Requested 'gstreamer-plugins-base-0.10 >= 0.10.15' but version of GStreamer Base Plugins Libraries is 0.10.14

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

leif@Znote-6224W:~/cheese-0.3.0$ 

```

Any suggestions?

---

### Post by cyberdork33 on 2008-01-03
you do not meet the requirements of the software. you need a newer version of gstreamer, and that version is not in the repos yet. You can check your version of gstreamer with 
```
pkg-config --modversion gstreamer-0.10
```

This will likely return that you have version 0.10.14 and 0.10.15 is needed.

---

### Post by cyberdork33 on 2008-01-16
I just found out that cheese is slated to be release as part of Gnome in version 2.22. Cheese releases will now follow the GNOME Release Cycle, and thus version 2.21.5 has been released.

From what I understand, it is planned to eventually be integrated into Gnome, much like the isight API is in OSX (taking user pictures, etc).

---

### Post by chochem on 2008-02-02
> **cyberdork33 said:**
> I just found out that cheese is slated to be release as part of Gnome in version 2.22. Cheese releases will now follow the GNOME Release Cycle, and thus version 2.21.5 has been released.

From what I understand, it is planned to eventually be integrated into Gnome, much like the isight API is in OSX (taking user pictures, etc).

Which I take it means that in all likelihood it will appear in the final release of Hardy? (tried checking the GNOME road map but it doesn't seem to be big on dates...)

Anyway, isn't there some way to get gstreamer0.10 v. 0.10.15/0.10.16/0.10.17 (on Gutsy)? Short of compiling that as well? An alternative repository?

EDIT: Oh and can anybody say if the 2.21etc version is more uhm agile than the one in the repositories? The program itself is up and running in an instant but it takes something a full minute to get the feed from the webcam.

---

### Post by cyberdork33 on 2008-02-03
> **chochem said:**
> Which I take it means that in all likelihood it will appear in the final release of Hardy? (tried checking the GNOME road map but it doesn't seem to be big on dates...) I believe that to be the case.

> **chochem said:**
>  Anyway, isn't there some way to get gstreamer0.10 v. 0.10.15/0.10.16/0.10.17 (on Gutsy)? Short of compiling that as well? An alternative repository?I don't know of any repositories carrying it, compiling is really your only option.

> **chochem said:**
>  EDIT: Oh and can anybody say if the 2.21etc version is more uhm agile than the one in the repositories? The program itself is up and running in an instant but it takes something a full minute to get the feed from the webcam.that version is the same as 0.3 I believe which is much newer than the one in the repos.

---

### Post by chochem on 2008-02-03
> **cyberdork33 said:**
> I believe that to be the case.

> **cyberdork33 said:**
> I don't know of any repositories carrying it, compiling is really your only option.

Thanks. In that case I'll just wait it out :)

---

### Post by cyberdork33 on 2008-02-03
> **chochem said:**
> Thanks. In that case I'll just wait it out :)I am in the same boat. This may have already been merged into the latest Alpha if you would like to try it out.

---

### Post by cowanh00 on 2008-02-15
Get Deb have [updated]("http://www.getdeb.net/app.php?name=Cheese") Cheese for Gutsy to the latest version! Just thought I will let everyone know!!

---

### Post by trash on 2008-03-30
Love this program!
The only thing i think really needs changing is where images and video's are saved to... ~/.gnome2/cheese/images is a bit silly, is there a way I can change it to ~/cheese/images

---

### Post by trash on 2008-03-30
> **cowanh00 said:**
> Get Deb have [updated]("http://www.getdeb.net/app.php?name=Cheese") Cheese for Gutsy to the latest version! Just thought I will let everyone know!!

This update doesn't work, don't download it.

---

### Post by cyberdork33 on 2008-04-01
> **trash said:**
> Love this program!
The only thing i think really needs changing is where images and video's are saved to... ~/.gnome2/cheese/images is a bit silly, is there a way I can change it to ~/cheese/imagesI am pretty sure they will not change it, but you can make a request directly to the cheese devs if you like.

> **trash said:**
> This update doesn't work, don't download it. The latest release is in the Hardy repo. There is no need to get an "update" anyway.

---

### Post by trash on 2008-04-01
> **cyberdork33 said:**
> I am pretty sure they will not change it, but you can make a request directly to the cheese devs if you like.

I don't see why they wouldn't change something as totally ilogical as saving a document I create in a hidden directory but it may not matter anyway, just found this on the Cheese website...
[http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)

"all hell broke loose yesterday: i got a phone call yesterday by a nice lady, which presented herself as a former advocate of apple. she told me that the objective of her team was to find copyright and patent violations and therefore she called me: 

obviously i did something wrong by starting such a project as cheese, which is a pure clone of photo booth. this would violate the us patent IC 009. US 021 023 026 036 038. G & S: computer software used for image editing, image acquisition, and image viewing, which was filed on february the 28th 2006 and as gnome is registered and known as an organization of the usa, this patent would be applicable. 

i thought, that such patents would just apply, if there is some commercial interest behind it, but she knew it better: as i created cheese in the summer of code program, i "worked" for google, which makes everything a commercial project, even if now i "probably" do not get any money. in addition the full us patent law applies, as i a) worked for google in the usa for the summer of code program and b) cheese is now included in gnome, which is an organization registered in the usa. 

she also told me, that of course there are similar applications like photo booth, but cheese acts as a clone and therefore an illegal copy because it works on intel based macs and therefore would be a competitor of photo booth. the fact, that cheese just runs on linux on the intel based macs was worthless by her. 

so it looks pretty bad for me now.. i got a deadline of 5 work days to remove cheese code and binary versions from all places i have access to (probably svn.gnome.org, ftp.gnome.org, ...). 

i already contacted a lawyer, which thinks he can help me, but of course it is david against goliath... 

so, if you know a way out of this, please contact me!"

---

### Post by cowanh00 on 2008-04-01
> **trash said:**
>  just found this on the Cheese website...
[http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)

"all hell broke loose yesterday: i got a phone call yesterday by a nice lady, which presented herself as a former advocate of apple. she told me that the objective of her team was to find copyright and patent violations and therefore she called me: 

obviously i did something wrong by starting such a project as cheese, which is a pure clone of photo booth. this would violate the us patent IC 009. US 021 023 026 036 038. G & S: computer software used for image editing, image acquisition, and image viewing, which was filed on february the 28th 2006 and as gnome is registered and known as an organization of the usa, this patent would be applicable. 

i thought, that such patents would just apply, if there is some commercial interest behind it, but she knew it better: as i created cheese in the summer of code program, i "worked" for google, which makes everything a commercial project, even if now i "probably" do not get any money. in addition the full us patent law applies, as i a) worked for google in the usa for the summer of code program and b) cheese is now included in gnome, which is an organization registered in the usa. 

she also told me, that of course there are similar applications like photo booth, but cheese acts as a clone and therefore an illegal copy because it works on intel based macs and therefore would be a competitor of photo booth. the fact, that cheese just runs on linux on the intel based macs was worthless by her. 

so it looks pretty bad for me now.. i got a deadline of 5 work days to remove cheese code and binary versions from all places i have access to (probably svn.gnome.org, ftp.gnome.org, ...). 

i already contacted a lawyer, which thinks he can help me, but of course it is david against goliath... 

so, if you know a way out of this, please contact me!"

It's got to be an April's Fool joke!

---

### Post by trash on 2008-04-01
> **cowanh00 said:**
> It's got to be an April's Fool joke!

could be! I totaly forgot it was April 1st:lolflag:

---

### Post by cyberdork33 on 2008-04-01
> **trash said:**
> I don't see why they wouldn't change something as totally ilogical as saving a document I create in a hidden directoryBecause that is how they designed it to work (It is an Apple-esque thing to do, blame them). I think that Photobooth might do the same thing, and I know that iPhoto does now. You can drag the pictures out of cheese into any folder you want, so it is not relevant. 

> **cowanh00 said:**
> It's got to be an April's Fool joke!
Yea, I am thinking that as well. The reasoning doesn't make any sense, especially since it is not a "clone" of Photobooth.

---

### Post by cyberdork33 on 2008-04-01
Apparently Daniel's post about cheese stirred some controversy:
[http://home.cs.tum.edu/~siegel/news/2008_04_02-about_that_april_fools_joke](http://home.cs.tum.edu/~siegel/news/2008_04_02-about_that_april_fools_joke)

---

### Post by trash on 2008-04-01
> **cyberdork33 said:**
> Because that is how they designed it to work (It is an Apple-esque thing to do, blame them). I think that Photobooth might do the same thing, and I know that iPhoto does now. You can drag the pictures out of cheese into any folder you want, so it is not relevant.

I'm not looking to blame anybody, just improve it's functionality. None of my programs default save to a hidden directory. There is NO indication anywhere that tells a user where it's saving to. There is NO option to change the default location.

Fortunately David Siegal(sp?) is a reasonable guy(from my limited experience chatting with him), so i do hope he would consider changes since they do request that people make suggestions... we'll see I guess.

---

### Post by cyberdork33 on 2008-04-01
> **trash said:**
> I'm not looking to blame anybody
I didn't really mean it that way.... but that's fine.

Daniel is the original creator of that program.

---

### Post by trash on 2008-04-01
> **cyberdork33 said:**
> Apparently Daniel's post about cheese stirred some controversy:
[http://home.cs.tum.edu/~siegel/news/2008_04_02-about_that_april_fools_joke](http://home.cs.tum.edu/~siegel/news/2008_04_02-about_that_april_fools_joke)

After being reminded it was April 1st i did think it was funny, but I totally see how it could have been a panic for some... guess there are more people out there besides me who lose track of time/days of the week lol.

---

### Post by trash on 2008-04-01
So here's the response to my feedback/request...

"we are facing this issue here:
[http://bugzilla.gnome.org/show_bug.cgi?id=509475](http://bugzilla.gnome.org/show_bug.cgi?id=509475)
 
as more and more people want to have this feature, we probably will fix
it for gnome 2.24
daniel"

---

### Post by pierrelux on 2008-04-09
I got the iSight built-in camera to work with my Macbook 4.1 simply by installing:
sudo apt-get install isight-firmware-tools (said "no" at the prompt"). You can use cheese after having configured gstreamer:
Launch gstreamer-properties, in the "Video" tab, select "Built-in iSight" in the "Default Input" section.

Sorry for those who are still struggling with their iSight. I'm surprised it's been that easy...

(Running hardy 64 bit)

---

### Post by cyberdork33 on 2008-04-09
you must have already extracted the firmware before because it will not work without that.

---

### Post by pierrelux on 2008-04-10
Sounds weird... but no, I have not extracted any firmware from a DVD or whatsoever.

If I look at the command history, I can tell you I just did:

sudo apt-get install isight-firmware-tools

---

### Post by cyberdork33 on 2008-04-10
> **pierrelux said:**
> Sounds weird... but no, I have not extracted any firmware from a DVD or whatsoever.

If I look at the command history, I can tell you I just did:

sudo apt-get install isight-firmware-tools
look in /lib/firmware/ you should have isight.fw there.

Also, iSight firmware tools are not in the Ubuntu repos, it is in the mactel ppa.

---

### Post by tigerplug on 2008-04-17
I like it... but the quality just isn't the same... does anyone else find that?

---

### Post by cyberdork33 on 2008-04-17
> **tigerplug said:**
> I like it... but the quality just isn't the same... does anyone else find that?
are you talking about Cheese or just the iSight under linux in general?

It is just raw video in Linux, I think that OSX does some adjustment of the picture.

---

### Post by max littlemore on 2008-04-20
I'm finding the quality isn't all that good.

It's fine when running, but captured video is woeful. Is there anyway of changing the default compression/resolution?  Using an HP Pavillion notebook and the camera is capable of a lot more than cheese lets it do.

---

### Post by cyberdork33 on 2008-04-20
> **max littlemore said:**
> I'm finding the quality isn't all that good.

It's fine when running, but captured video is woeful. Is there anyway of changing the default compression/resolution?  Using an HP Pavillion notebook and the camera is capable of a lot more than cheese lets it do.I think you will have to talk to the cheese devs.

[http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)

---

### Post by Kapitän Rotbart on 2008-05-08
Wow, Cheese is indeed awesome!

I installed it using the Hardy repos (in Hardy) and it works like a charm. In fact, I went out and bought a new webcam (I tested it in Cheese and aMSN in Ubuntu before buying it, yet it wouldn't work with Camorama). The lady at the shop got so mad at me for **not** booting Windows XP SP2... I told her I have a native driver for webcams already and I was looking for one that would work well with that driver. She told me that Win XP SP2 doesn't require any driver install for that webcam (however there was a driver install disc for all Windows predating XP SP2, going back to Win 98 ). I tried the webcam in my Windows XP SP2 virtual machine using Sun's VirtualBox with USB support and it certainly didn't work out of the box. Then I tried installing the driver, and it still wouldn't work (and the driver is unsigned so Windows not only discourages its install, but Windows also asked me to insert the Windows XP install disc to restore certain files).

I couldn't care too much about how well the webcam works in Windows, provided it works in Linux. While I was at the shop, I tested Cheese with half a dozen webcams. There were a couple that wouldn't be recognized by Cheese and a couple more that wouldn't work in Camorama (so far Cheese has the best webcam detection I've seen in Linux so far). There were a couple that gave inferior images compared to using them in Windows, however that would be a driver issue. The one I got gave a great image w00t!

Taking pictures with Cheese works perfectly (I could never get taking pictures to work in Camorama). Taking videos alsooo works nicely (saves to ogg format and can be played with quite a few apps perfectly). Would there be a way to get sound input for videos recorded with Cheese, even if the webcam's built-in microphone isn't supported? The click button on the webcam won't take pictures, however I wonder to what extent that would be a driver issue and to what extent it would be a software issue. It would be cool if the driver allows it that Cheese would automatically take a snapshot when the button on the webcam is clicked. Fortunately, the built-in LED lights do work when it's dark (automatically) :p

What would also be nice would be if Cheese would let me resize the window and continue to display the webcam image (when I resize, the image disappears). It would also be neat if the image would appear in a screenshot taken by the gnome-screenshot and would be even neater if the image could be distorted by compiz instead of disappearing. Other than working with other supported applications, the only thing I can think of to add would be more effects.:popcorn:

---

### Post by mkarnicki on 2008-06-08
I need some help guys, please:

```
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.15.5   gio-2.0 >= 2.15.5   gtk+-2.0 >= 2.10.0   libgnomeui-2.0 >= 2.14.0   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.15   gstreamer-plugins-base-0.10 >= 0.10.15   gnome-vfs-2.0 >= 2.18.0   libebook-1.2 >= 1.12.0   cairo >= 1.2.4   dbus-1 >= 1.0   hal >= 0.5.9   dbus-glib-1 >= 0.7   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0   xxf86vm) were not met:

No package 'hal' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I do have these packages installed. I'm on AMD64, maybe that's the case? What should I do? I tried to install latest stable version of cheese (I mean compile, not install).

---

### Post by cyberdork33 on 2008-06-11
> **mkarnicki said:**
> I do have these packages installed. I'm on AMD64, maybe that's the case? What should I do? I tried to install latest stable version of cheese (I mean compile, not install).

You need the dev versions of the required packages in order to compile against them. You can do this rather quickly by doing:
```
sudo apt-get build-dep cheese
```This will install all the build dependencies. If you are compiling from svn or something, then you still might have issues with the need for newer versions of libraries that are not in the Ubuntu repos.

Please post further questions in the new Apple Users forum as this is now just an archive:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by mkarnicki on 2008-06-13
Woooops! I'm sorry. I did find this post via Search. I didn't even spot it was for apple users, thanks.

HP pavilion user.

---

