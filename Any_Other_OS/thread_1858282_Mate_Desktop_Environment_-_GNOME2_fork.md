---
title: "Mate Desktop Environment - GNOME2 fork"
date: 2011-10-12
forum: Any Other OS
---

### Post by Perberos on 2011-10-12
Hello everyone.
I've made a GNOME2 fork. I've called it "Mate".
My english is not so good. And so, maybe I can not give support in English.
Correct me if I'm wrong. Any suggestion is welcome.

...sorry about short description.

MATE Desktop Environment, a non-intuitive and unattractive desktop for users, using traditional computing desktop metaphor. Also known as the GNOME2 fork.

Repository: [http://mate.karapetsas.com/](http://mate.karapetsas.com/)
Homepage : [http://matsusoft.com.ar/projects/mate/](http://matsusoft.com.ar/projects/mate/)
GitHub: [https://github.com/Perberos/Mate-Desktop-Environment](https://github.com/Perberos/Mate-Desktop-Environment)
**Mailing Lists**: [https://sourceforge.net/p/matede/mailing-lists/](https://sourceforge.net/p/matede/mailing-lists/)
Feedback: perberos at gmail dotta com omg ugly spam bot
IRC: freenode.net at #mate channel or #archlinux or #archlinux-es

---

### Post by Perberos on 2011-10-12
**[COLOR="Red"]This method is not any more recommended.[/COLOR]**

Instructions for build on Ubuntu:

install git
```
sudo apt-get install git
```
get all source code from git
```
git clone https://github.com/perberos/Mate-Desktop-Environment.git
```

while, install all development headers and tools for build.
```
sudo apt-get install libxml2-dev libxslt1-dev libglib2.0-dev libidl-dev \
    libdbus-1-dev libdbus-glib-1-dev libpolkit-backend-1-dev flex libpopt-dev \
    bison libbz2-dev libgcrypt11-dev libcanberra-dev libgail-dev libgtk2.0-dev \
    libart-2.0-dev libglade2-dev libtasn1-3-bin libxklavier-dev libsoup2.4-dev \
    icon-naming-utils libunique-dev libcanberra-gtk-dev libwnck-dev \
    librsvg2-dev libpolkit-agent-1-dev gobject-introspection \
    libgirepository1.0-dev libupower-glib-dev intltool xsltproc \
    libtasn1-3-dev libtool gtk-doc-tools libgamin-dev \
    librarian-dev
```

When you got all installed, install mate-doc-utils.
```
cd Mate-Desktop-Environment/mate-doc-utils
./configure --prefix=/usr
make
sudo make install

```

Now you are ready to start to pack.
On each folder inside Mate-Desktop-Environment, you will find one called distro. Inside, there are scripts for build packages.

for example, to build mate-doc-utils, you need to run:
```
cd Mate-Desktop-Environment/mate-doc-utils/distro/ubuntu
./build
```
It will make 2 folders. pkg contains the files for the tarball .deb, and the src contains the source code, and some file binaries.
The file .deb will be generated. But if you had some problem, post on this thread.

The script do not check for dependency, so you need to follow this order and install it before you get the .deb:

```
mate-doc-utils
mate-common
mate-corba
mate-conf
libmatecomponent
mate-mime-data
mate-vfs
libmate
libmatecanvas
libmatecomponentui
libmatekeyring
mate-keyring
libmateui
libmatenotify
libmatekbd
libmateweather
mate-icon-theme
mate-dialogs
mate-desktop
mate-file-manager
mate-notification-daemon
mate-backgrounds
mate-menus
mate-window-manager
mate-settings-daemon
mate-control-center
mate-panel
mate-polkit
mate-session-manager
```

to install a .deb, use:
```
sudo dpkg -i name_of_pack_here.deb
```

Tip: How To Disable The Overlay Scrollbars In Ubuntu
[http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)

Tip: Disable resize gripper in windows
[http://askubuntu.com/questions/29209/disable-resize-gripper-in-windows](http://askubuntu.com/questions/29209/disable-resize-gripper-in-windows)

---

### Post by bs5765 on 2011-10-12
> **Perberos said:**
> a non-intuitive and unattractive desktop for users, using traditional computing desktop metaphor

Made me laugh out loud!

Great job, man. If I wasn't already running GNOME2, I would definitely try it out.

---

### Post by Metallion on 2011-10-12
Been reading your thread about this over at the Arch forum. Looks good. I'll give this a go if I ever find some free time.

---

### Post by Clement Lefebvre on 2011-10-12
Hi Perberos,

mate-doc-utils conflicts with gnome-doc-utils on /usr/bin/xml2po. 

More info:

clem@gateway ~/Mate-Desktop-Environment $ sudo dpkg -i mate-doc-utils/distro/ubuntu/mate-doc-utils_2011.9.26_amd64.deb 
Selecting previously deselected package mate-doc-utils.
(Reading database ... 186798 files and directories currently installed.)
Unpacking mate-doc-utils (from .../mate-doc-utils_2011.9.26_amd64.deb) ...
dpkg: error processing mate-doc-utils/distro/ubuntu/mate-doc-utils_2011.9.26_amd64.deb (--install):
 trying to overwrite '/usr/bin/xml2po', which is also in package gnome-doc-utils 0.20.6-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 mate-doc-utils/distro/ubuntu/mate-doc-utils_2011.9.26_amd64.deb

Clem.

---

### Post by kaldor on 2011-10-12
Nice work on this. It's quite an effort. I am very content with GNOME 3, but this should make many people very happy.

Also, "hello" to the Mint guy ;)

---

### Post by Clement Lefebvre on 2011-10-12
Hi Kaldor ;)

Ok... I'm facing a compilation error now: 

make[2]: Leaving directory `/home/clem/Mate-Desktop-Environment/mate-vfs/distro/ubuntu/src/mate-vfs/doc'
make[1]: Leaving directory `/home/clem/Mate-Desktop-Environment/mate-vfs/distro/ubuntu/src/mate-vfs/doc'
Making install in programs
make[1]: Entering directory `/home/clem/Mate-Desktop-Environment/mate-vfs/distro/ubuntu/src/mate-vfs/programs'
/bin/bash ../libtool --tag=CC   --mode=link gcc -std=gnu99  -g -O2   -o matevfs-info matevfs-info.o ../libmatevfs/libmatevfs-2.la -pthread -lmateconf-2 -lgthread-2.0 -lrt -lglib-2.0    -lselinux -lutil -lrt -lrt 
libtool: link: gcc -std=gnu99 -g -O2 -o .libs/matevfs-info matevfs-info.o -pthread  ../libmatevfs/.libs/libmatevfs-2.so /usr/lib/libmateconf-2.so /usr/lib/libgthread-2.0.so /usr/lib/libglib-2.0.so -lselinux -lutil -lrt -pthread
/usr/bin/ld: matevfs-info.o: undefined reference to symbol 'g_object_get'
/usr/bin/ld: note: 'g_object_get' is defined in DSO /usr/lib64/libgobject-2.0.so.0 so try adding it to the linker command line
/usr/lib64/libgobject-2.0.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[1]: *** [matevfs-info] Error 1
make[1]: Leaving directory `/home/clem/Mate-Desktop-Environment/mate-vfs/distro/ubuntu/src/mate-vfs/programs'
make: *** [install-recursive] Error 1
dpkg-deb: building package `mate-vfs' in `mate-vfs_2011.9.26_amd64.deb'.

---

### Post by Clement Lefebvre on 2011-10-12
I've been trying these on a Gnome 2x desktop running LMDE. I'll switch to an Ubuntu 11.10 base running Gnome 3 and see if it makes a difference. I'll check glib and gnome-doc-utils there as well.

---

### Post by Clement Lefebvre on 2011-10-12
OK, it conflicts with gnome-doc-utils on Ubuntu 11.10 as well, but on a different file:



clem@mint:~/Mate-Desktop-Environment/mate-doc-utils/distro/ubuntu$ sudo dpkg -i mate-doc-utils_2011.9.26_amd64.deb
Selecting previously deselected package mate-doc-utils.
(Reading database ... 168688 files and directories currently installed.)
Unpacking mate-doc-utils (from mate-doc-utils_2011.9.26_amd64.deb) ...
dpkg: error processing mate-doc-utils_2011.9.26_amd64.deb (--install):
 trying to overwrite '/usr/lib/python2.7/dist-packages/xml2po/modes/mallard.py', which is also in package gnome-doc-utils 0.20.6-1ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 mate-doc-utils_2011.9.26_amd64.deb

---

### Post by Paqman on 2011-10-12
> **Perberos said:**
> Instructions for build on Ubuntu:


Have you considered providing a PPA?

---

### Post by Clement Lefebvre on 2011-10-12
mate-doc-utils -> OK, but pkg conflicts with gnome-doc-utils mate-common -> OK mate-corba -> OK mate-conf -> OK libmatecomponent -> OK mate-mime-data -> OK mate-vfs -> OK libmate -> OK libmatecanvas -> OK libmatecomponentui -> OK libmatekeyring -> OK mate-keyring -> OK

Looking good far... still to compile/package/install/test the following:

libmateui libmatenotify libmatekbd libmateweather mate-icon-theme mate-dialogs mate-desktop mate-file-manager mate-notification-daemon mate-backgrounds mate-menus mate-window-manager mate-settings-daemon mate-control-center mate-panel mate-polkit mate-session-manager

---

### Post by Perberos on 2011-10-12
Sorry about mate-doc-utils. It was fixed on git.
[https://github.com/Perberos/Mate-Desktop-Environment/commit/57ae88de7d8f88b11259c161ed9a6b8346884604](https://github.com/Perberos/Mate-Desktop-Environment/commit/57ae88de7d8f88b11259c161ed9a6b8346884604)

> **Paqman said:**
> Have you considered providing a PPA?
Yes, but I am lazy.

---

### Post by Paqman on 2011-10-12
> **Perberos said:**
> 
Yes, but I am lazy.

Lol, fair enough, you'd get more people testing it on Ubuntu if you did though, and you'd be able to push updates out to them. IIRC Launchpad does play nicely with git these days. Sounds like a job for a keen Mate fan running Ubuntu.

---

### Post by pinguy on 2011-10-12
Thanks for this. Pinguy OS and Mint will be using this in 11.10

But a PPA would make are life easier.

---

### Post by myprip on 2011-10-12
If you provide a PPA of this for oneiric I'll kiss you on the mouth passionately. Or alternatively just be lifelong grateful.

---

### Post by DoubleClicker on 2011-10-12
Perberos,
While I am very grateful to you,  for forking Gnome to a new desktop environment, I believe it is a serious mistake to name it Maté.

First of all it will be hard to gain a high google rank, do to the fact that, it will be most often be spelled identical spelling with the english word mate (like in the title of this thread).  The word mate has many meanings, all of which have millions of listings on google.  

Second there will be a big confusion over pronunciation, as most English speakers will pronounce it like the english word mate. This will seriously reduce "brand recognition".  

Third one of the definitions for the English word mate is to copulate (copular in spanish), which some people might find offensive.

It is still early enough for you to be able to change the name without loosing much momentum, as Maté is still not well known.

The best name would be something completely unique, with obvious pronunciation to speakers of most languages.  If you fell like you must name it after something, try to find something you expect to be less popular than your desktop environment. For example "beer" would be a far worse choice than "slivovitz"; and you would do much better on google naming it "imbira", than you would naming it "guitar".

---

### Post by kaldor on 2011-10-12
In my honest opinion, I think that the best idea for projects like Pinguy, Mint, etc (from a technical user's point of view) would be to work on making GNOME 3 a great and familiar experience. Fallback mode is not mature, but it does have a lot of potential. And it [_can still_]("http://ubuntuone.com/0c7eQwyQe1rEhrN7N3lUNW") be [_customized_]("http://i.imgur.com/M43HR.png") to [_work_]("http://i.imgur.com/M43HR.png") like it should.

Maintaining old software often doesn't turn out as expected. GNOME 3 offers a lot of advancements that users enjoy, and I assume that having both Mate and GNOME 3 installed on the same system would be impossible due to conflicts. GNOME 3 is going to keep progressing with new features, while Mate will eventually begin to feel old and outdated. I'm not saying hop on the GNOME Shell/Unity/Whatever bandwagon; I'm saying that it would possibly be easier and more effective in the long term if work was done on GNOME 3's fallback mode to bring it back to the same level as GNOME 2.x's panels. This way, the experience would still be familiar and the software from upstream will keep getting better. 

I really am not trying to sound like I know what's best for any Linux project. As I said earlier in the thread, I'm thankful that some people are actually taking up interest in Mate. But overall, I think the best idea is to work with new technology and make it better.

---

### Post by pinguy on 2011-10-12
> **kaldor said:**
> In my honest opinion, I think that the best idea for projects like Pinguy, Mint, etc (from a technical user's point of view) would be to work on making GNOME 3 a great and familiar experience. Fallback mode is not mature, but it does have a lot of potential. And it [_can still_]("http://ubuntuone.com/0c7eQwyQe1rEhrN7N3lUNW") be customized to work like it should.

Maintaining old software often doesn't turn out as expected. GNOME 3 offers a lot of advancements that users enjoy, and I assume that having both Mate and GNOME 3 installed on the same system would be impossible due to conflicts. GNOME 3 is going to keep progressing with new features, while Mate will eventually begin to feel old and outdated. I'm not saying hop on the GNOME Shell/Unity/Whatever bandwagon; I'm saying that it would possibly be easier and more effective in the long term if work was done on GNOME 3's fallback mode to bring it back to the same level as GNOME 2.x's panels. This way, the experience would still be familiar and the software from upstream will keep getting better. 

I really am not trying to sound like I know what's best for any Linux project. As I said earlier in the thread, I'm thankful that some people are actually taking up interest in Mate. But overall, I think the best idea is to work with new technology and make it better.

The plan is to have a Gnome Shell version. But its just not there yet. So while work gets done on Gnome 3 users can still use what they are familiar with. 

I am working on Gnome 3 and it will be part of 11.10, but it not fully ready yet. So I am going to use MATE and also work on Gnome 3.

"Maintaining old software often doesn't turn out as expected." This is a moot argument. If that was the case nothing would work with XFCE because its using GTK2. Also nothing works with gnome3 yet. Devs are still busy away getting their apps working in gnome 3.

Put it this way I am willing to bet my left nut that this version of Ubuntu is going to be the most buggiest, where hardly any software works with it. People will not like it. I have been working with it for 2 Months and its no where near ready. I can not believe they are releasing it tomorrow. This will be the Ubuntu version that gets the most bad reviews.

I really hope this don't get deleted because I speak badly of Ubuntu. I would like to reference this post in the future. Just to tell people "I told you so"

---

### Post by kaldor on 2011-10-12
> **pinguy said:**
> The plan is to have a Gnome Shell version. But its just not there yet. So while work gets done on Gnome 3 users can still use what they are familiar with. 

I am working on Gnome 3 and it will be part of 11.10, but it not fully ready yet. So I am going to use MATE and also work on Gnome 3.

"Maintaining old software often doesn't turn out as expected." is a mute argument. If that was the case nothing would work with XFCE because its using GTK2. Also nothing works with gnome yet. Devs are still busy away getting their apps working.

Put it this way I am willing to bet my left nut that this version of Ubuntu is going to be the most buggiest with hardly any software that works with.

I'm talking about making the fallback mode better than it is, not using GNOME Shell.

Regarding Ubuntu 11.10 being buggy, I agree very much. But that said, do you see yourself using GNOME 2.3.x three years from now? Devs may be still busy getting stuff working for GNOME 3, but that's just it; they'll be using newer stuff.

Edit for a nutshell:

GNOME 3 is more than just GNOME Shell. If you don't like Shell (very understandable) there's Fallback mode. My idea is that developers wanting a traditional experience could work on making GNOME 3's Fallback mode much more usable than it currently is, without the need to depend on old projects.

---

### Post by pinguy on 2011-10-12
My views about the state of desktops: [http://blog.pinguyos.com/post/9242644632/omg-ubuntu-comments-system-sucks-also-my-thoughts-on](http://blog.pinguyos.com/post/9242644632/omg-ubuntu-comments-system-sucks-also-my-thoughts-on) Also read the comments.

Also you need to know that one of the head devs for Gnome does have an agenda. Miguel de Lcaza owns [http://xamarin.com/](http://xamarin.com/) So it is in his interest to make sure that Gnome is tablet friendly.

source: [http://www.itwriting.com/blog/4925-miguel-de-icaza-talks-about-windows-8-and-the-failure-of-linux-on-the-desktop.html](http://www.itwriting.com/blog/4925-miguel-de-icaza-talks-about-windows-8-and-the-failure-of-linux-on-the-desktop.html)

This is what I like about MATE. Unlike Unity and Gnome where they don't care about Desktop PCs, MATE is carrying on an environment that is built and made for the Desktop PC without any other agenda then just keeping a well made Desktop Environment alive.

---

### Post by Mr. Picklesworth on 2011-10-12
Perberos, I notice that Mate renames *a lot* of Gnome 2 things to mate-[whatever], and I'm wondering if it's really necessary for you to support all of them. Are you aiming to trim these off in the future? It strikes me as a bit excessive to be maintaining a duplicate of gnome-session and gnome-keyring, for example. It would probably be better for everyone if you were able to talk to *the* gnome-session instead.

Also, there is no such thing as live.mate.org. Every link that was to gnome.org, which is in just about every README file in your git repository, is broken and should probably be fixed. Here's one: [https://github.com/Perberos/Mate-Desktop-Environment/blob/master/mate-session-manager/mate-session/README](https://github.com/Perberos/Mate-Desktop-Environment/blob/master/mate-session-manager/mate-session/README)

Same with your AUTHORS and MAINTAINERS files, where it's a slightly more serious problem: [https://github.com/Perberos/Mate-Desktop-Environment/blob/master/mate-session-manager/AUTHORS](https://github.com/Perberos/Mate-Desktop-Environment/blob/master/mate-session-manager/AUTHORS)

You might want to go through and update these manually. You should probably make it clear that the current maintainer of the Mate stuff is you (or other Mate developers), not the people who maintain the gnome- packages. They won't like it if they start getting emails from people about software they don't maintain. And you should link to the original source for each of these, because each one has its own license text. (It just happens that each one is GPL2).

---

### Post by Perberos on 2011-10-13
sed does a good work :-\"

thanks all for the feedback

---

### Post by Clement Lefebvre on 2011-10-13
Check out regexxer, you'll love it :)

Ok, jokes appart.. people touched on a couple of interesting topics. 

**The name**

I fully agree with the comments made here. The name won't help brand recognition, promotion or the project to get momentum. It's a common word in English, almost slangish, which does have a few inappropriate meanings. It's not too late to change it.

**The fallback mode**

The fallback mode is not here to stay. The plan is for Gnome Shell to work with a larger set of hardware and for the fallback mode to disappear. 

In terms of UI, the fallback mode is something nobody wants. Gnome 3 enthusiasts don't like its Gnome2-like design. Gnome 2 fans hate the fact that it simply doesn't work. Of course, it works.... but it looks like it doesn't work. And the reason for this is simple... it looks and gives people the impression they're running Gnome 2, only they're not. They're actually running Gnome 3 on top of GTK3 and without compatibility with Bonobo and panel applets. Once the user understands he can use the Alt key to interact with the panel, he gets a bit of false hopes... until he goes further and realize no Bonobo Gnome applet will run on this Fallback mode. To Mint users, basically, that means no mintMenu.

Why would we port mintMenu to GTK3 and DBUS just to make it work with fallback mode when this mode is set to disappear and we've got a stable 2.32 base which isn't going to change in the future? It would make no sense.

**Gnome 3 itself**

Mate and Gnome 3 can be run on the same system. If they can't right now, at least they will be in the future. 

Gnome 3 is a fantastic piece of technology and it's also a brand new desktop. It's something we can extend and improve with our own ideas, whether it's via extensions, configuration or even by porting applications such as mintMenu to work with Gnome Shell. 

As far as we're concerned we want to get started with Gnome 3, but we also want to continue to provide what is still the most popular Linux desktop out there: Gnome 2.32.

5 years from now do we plan on using Gnome 2? Well... what's the thing you want the most this month? Five years ago, were you even thinking about it? 

So 5 years from now, we'll be doing the exact same thing as we're doing now: We'll choose the best components for our users. Today this includes both Gnome 2 and Gnome 3.

---

### Post by Clement Lefebvre on 2011-10-13
Perberos, about the conflicts:

The files which conflict still need to be there in Mate, so people can run Mate without depending on Gnome. If someone has both installed, then of course, only one is needed. 

The way to do this is by defining a new package in which we put all the conflicting files, for instance mate-overlap, which conflicts with gnome-doc-utils. 

Then you remove these files from mate-doc-utils and make mate-doc-utils depend on "mate-overlap | gnome-doc-utils". 

This way, Mate users get the files via mate-overlap, Gnome users get them via gnome-doc-utils. People who use both Gnome 3 and Mate have mate-doc-utils and gnome-doc-utils installed.

---

### Post by Clement Lefebvre on 2011-10-13
mate-dialogs has no distro/ubuntu/build script..

---

### Post by Clement Lefebvre on 2011-10-13
Compilation error with mate-file-manager:

make  all-recursive
make[1]: Entering directory `/home/clem/Mate-Desktop-Environment/mate-file-manager/distro/ubuntu/src/mate-file-manager'
Making all in eel
make[2]: Entering directory `/home/clem/Mate-Desktop-Environment/mate-file-manager/distro/ubuntu/src/mate-file-manager/eel'
  CC     eel-alert-dialog.lo
In file included from eel-alert-dialog.c:24:0:
eel-i18n.h:31:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'char'
eel-alert-dialog.c: In function 'eel_alert_dialog_class_init':
eel-alert-dialog.c:114:43: warning: passing argument 2 of 'g_param_spec_int' makes pointer from integer without a cast [enabled by default]
/usr/include/glib-2.0/gobject/gparamspecs.h:993:13: note: expected 'const gchar *' but argument is of type 'int'
eel-alert-dialog.c:114:43: warning: passing argument 3 of 'g_param_spec_int' makes pointer from integer without a cast [enabled by default]
/usr/include/glib-2.0/gobject/gparamspecs.h:993:13: note: expected 'const gchar *' but argument is of type 'int'
eel-alert-dialog.c:123:35: warning: passing argument 2 of 'g_param_spec_enum' makes pointer from integer without a cast [enabled by default]
/usr/include/glib-2.0/gobject/gparamspecs.h:1040:13: note: expected 'const gchar *' but argument is of type 'int'
eel-alert-dialog.c:123:35: warning: passing argument 3 of 'g_param_spec_enum' makes pointer from integer without a cast [enabled by default]
/usr/include/glib-2.0/gobject/gparamspecs.h:1040:13: note: expected 'const gchar *' but argument is of type 'int'
eel-alert-dialog.c:132:35: warning: passing argument 2 of 'g_param_spec_enum' makes pointer from integer without a cast [enabled by default]
/usr/include/glib-2.0/gobject/gparamspecs.h:1040:13: note: expected 'const gchar *' but argument is of type 'int'
eel-alert-dialog.c:132:35: warning: passing argument 3 of 'g_param_spec_enum' makes pointer from integer without a cast [enabled by default]
/usr/include/glib-2.0/gobject/gparamspecs.h:1040:13: note: expected 'const gchar *' but argument is of type 'int'
eel-alert-dialog.c: In function 'eel_alert_dialog_init':
eel-alert-dialog.c:193:2: warning: passing argument 1 of 'gtk_expander_new_with_mnemonic' makes pointer from integer without a cast [enabled by default]
/usr/include/gtk-2.0/gtk/gtkexpander.h:66:23: note: expected 'const gchar *' but argument is of type 'int'
make[2]: *** [eel-alert-dialog.lo] Error 1
make[2]: Leaving directory `/home/clem/Mate-Desktop-Environment/mate-file-manager/distro/ubuntu/src/mate-file-manager/eel'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/clem/Mate-Desktop-Environment/mate-file-manager/distro/ubuntu/src/mate-file-manager'
make: *** [all] Error 2

Note that I didn't compile/install mate-dialogs (because of the missing build script). I don't know if it's related.

---

### Post by Dry Lips on 2011-10-13
I'm sorry if I'm don't completely grasp the technical aspects of this discussion. 
So I apologise in advance if I have misunderstood something here...   

 > **Clement Lefebvre said:**
>                        
Gnome 3 is a fantastic piece of technology and it's also a brand new desktop. It's something we can extend and improve with our own ideas, whether it's via extensions, configuration or even by porting applications such as mintMenu to work with Gnome Shell. 


You mean that the traditional Mint interface will be like before, but that it somehow 
is built on top of Gnome Shell? Or that you will use Gnome Shell as it is, with a few 
minor changes?
 
 > Why would we port mintMenu to GTK3 and DBUS just to make it work with fallback mode when this mode is set to disappear and we've got a stable 2.32 base which isn't going to change in the future? It would make no sense.
[...]
Mate and Gnome 3 can be run on the same system. If they can't right now, at least they will be in the future.
 So what you're describing here is:  
 **a)** a tweaked and customised version of Gnome3/Gnome Shell that looks like Gnome2?
 **b)** Traditional Gnome2 instead of the Gnome3 fallback mode.
 
In other words Gnome3/2 running on the same system... Or did I misunderstand something here?

---

### Post by Dry Lips on 2011-10-13
**@Perberos:** I agree with the other guys that you ought to find a new name for your 
project. Why not have an informal naming contest? I'm sure this community ought to 
be able to come up with a few nice suggestions!

What about **Tapajós**?

---

### Post by Dry Lips on 2011-10-13
**@Pinguy**:       

 On your [blog]("http://blog.pinguyos.com/post/9242644632/omg-ubuntu-comments-system-sucks-also-my-thoughts-on/") you write:
 
 [I]"For one I am asking for a Gnome 3 port. Not Gnome 2. Also in that article 
[/I][I]you barely explain anything. Just that you can kinda make Gnome 3 look 
[/I]*like Gnome 2. I can do a better job then what you have to make Gnome 3*
[I] look more like Gnome 2. But I am using an older version of gnome-panel. 
[/I]*The one that works.*
 *[...]*
[I]I want to see an updated Gnome 2.3 that is using GTK3. Thats all. Nothing 
[/I]*more nothing less. A true fallback mode that mimics Gnome 2.3 exactly but*
[I] has all the latest advantages of Gnome Shell. This way any app made for 
[/I]*Gnome Shell will work with the Gnome 2.3 clone."*
 
 I believe that if someone are going to fork Gnome3, why not continue to 
develop it further? I too think that a fork of Gnome3 that looks similar to 
Gnome2 is something that is sorely needed, but I also think that traditional 
Gnome2 has room for improvement. Gnome2 is by far my favourite DE, 
but I don't think that it ought to &#8220;freeze&#8221; and be left untouched for time and
 eternity. A gnome2 like interface ought to be developed further. One thing 
that I personally would love to see, is support for KDE-like widgets, although 
I'm sure that it would be an ambitious project to implement. 
(I'm no programmer;)) As long as Xfce is available as a lightweight DE, 
I dream of an alternative to Gnome3/KDE that is continually developed 
and improved.

If a complete fork of Gnome3 is too ambitious, then the next best thing 
would be a heavily tweaked Gnome3, in other words something that looks 
like the fallback mode.

---

### Post by Mr. Picklesworth on 2011-10-13
> **Clement Lefebvre said:**
> Why would we port mintMenu to GTK3 and DBUS just to make it work with fallback mode when this mode is set to disappear and we've got a stable 2.32 base which isn't going to change in the future? It would make no sense.

Wouldn't porting to Gtk3 + new panel lib and maintaining gnome-panel 3 (if *is* ever dropped) alongside the current version of every other Gnome module be a lot less effort than maintaining the *entirety* of Gnome 2 on an inferior UI toolkit + Bonobo?

---

### Post by crdlb on 2011-10-13
> **Clement Lefebvre said:**
> Why would we port mintMenu to GTK3 and DBUS just to make it work with fallback mode when this mode is set to disappear and we've got a stable 2.32 base which isn't going to change in the future? It would make no sense.

Gnome-panel 2.32 already supports the d-bus API, with bonobo applets supported in a compatibility module. If you're going to stick with gnome 2, you might as well remove the last vestiges of the abomination that is libbonobo.

---

### Post by DoubleClicker on 2011-10-13
"Perberos Desktop Environment" would actually be a great name.  it is unique, pronounceable and will rank high in google.

---

### Post by AlexVSharp on 2011-10-13
> **DoubleClicker said:**
> "Perberos Desktop Environment" would actually be a great name.  it is unique, pronounceable and will rank high in google.
I'm inclined to agree with this. However I also believe there should be some kind of name-picking contest. Perhaps OMG Ubuntu can lend a hand here? If you recall, "Polly", the upcoming multi-column Twitter application had its name picked and voted on by the community through their site. Might be worth a shot?

So if this project really is going through, something I'm really hoping for, then you should consider two things: 1) a testers PPA and 2) a better name. I'm cheering for ya! ;)

---

### Post by cariboo on 2011-10-13
I have to ask, why bother? With gnome-session-fallback available in the Oneiric repositories, this seems to be a lot of work for nothing, a duplication of effort. I'd suggest that the time would be better spent on making gnome-session-fallback better, instead of trying to fork old code.

---

### Post by &quot;Lex on 2011-10-14
Why? Well, I can tell you some reasons:

1) Gnome devs says that they are not going to support fallback mode for long. Want it or not, you just have to get used to a DE made for tablet\smartphones (Shell, Unity...) and give up your old but perfectly customizable and ready to use DE
2) GNU/Linux is free and if you don't like something you can always fork it and create something else that suit your tastes. 
3)Damn, there are over 200 distros, but less than 10 DE out there, why not? Plus his project is a good idea, also suggested by Torvalds himself (he wrote that hoped that someone would fork Gnome 2)

Also i agree with "Mate Desktop Environment" being used as a name. You can always call it "MDE" just like you don't call KDE "Kool" or LXDE "Lightweight X11"

Go for it Perberos! I'll install your DE and report every bug i find on github. ;)

---

### Post by pinguy on 2011-10-14
> **"Lex said:**
> Why? Well, I can tell you some reasons:

1) Gnome devs says that they are not going to support fallback mode for long. Want it or not, you just have to get used to a DE made for tablet\smartphones (Shell, Unity...) and give up your old but perfectly customizable and ready to use DE
2) GNU/Linux is free and if you don't like something you can always fork it and create something else that suit your tastes. 
3)Damn, there are over 200 distros, but less than 10 DE out there, why not? Plus his project is a good idea, also suggested by Torvalds himself (he wrote that hoped that someone would fork Gnome 2)

Also i agree with "Mate Desktop Environment" being used as a name. You can always call it "MDE" just like you don't call KDE "Kool" or LXDE "Lightweight X11"

Go for it Perberos! I'll install your DE and report every bug i find on github. ;)

Well said, and MDE is fine for a name.

---

### Post by cariboo on 2011-10-14
> **"Lex said:**
> Why? Well, I can tell you some reasons:

1) Gnome devs says that they are not going to support fallback mode for long. Want it or not, you just have to get used to a DE made for tablet\smartphones (Shell, Unity...) and give up your old but perfectly customizable and ready to use DE
2) GNU/Linux is free and if you don't like something you can always fork it and create something else that suit your tastes. 
3)Damn, there are over 200 distros, but less than 10 DE out there, why not? Plus his project is a good idea, also suggested by Torvalds himself (he wrote that hoped that someone would fork Gnome 2)

Also i agree with "Mate Desktop Environment" being used as a name. You can always call it "MDE" just like you don't call KDE "Kool" or LXDE "Lightweight X11"

Go for it Perberos! I'll install your DE and report every bug i find on github. ;)

There is a bit of a problem with MDE too, as far as I can tell there is only one developer working on it, what happens if he gives up, gets sick, gets a new job etc.

If you want a different desktop, whats to stop you from creating a new one yourself? The developer that maintains compiz, started out with very little programming knowledge and now he is the lead developer and working for Canonical.

---

### Post by &quot;Lex on 2011-10-14
And what if others join him? Every project started with one person, even Linux itself. And if two or more people wants the same kind of desktop (a Gnome 2 fork, in this case) and have the knowledge to make it, why can't they join and work together? Still rooting for him. IMHO, Shell and Unity are not good as Panel was and if he's going to continue, i will use his DE from now on, that's it.

---

### Post by Larkspur on 2011-10-14
Wouldn't it make more sense to concentrate on bringing the fallback session closer to the feel of gnome 2 then, if/when gnome drops it, forking that instead?  That way, the project can continue with gnome 3 (BTW, what happens when apps are no longer being written/updated for gnome 2?) and the developer doesn't have so much work to do. Maintaining a fast-depreciating code base seems a whole lot of work just to have the ability to customise a panel.

---

### Post by &quot;Lex on 2011-10-14
It's exactly what he's doing: forking Gnome 2 and updating it with GTK 3

---

### Post by Larkspur on 2011-10-14
> **"Lex said:**
> It's exactly what he's doing: forking Gnome 2 and updating it with GTK 3

What I meant was the package gnome-session-fallback in Gnome 3 could be forked.  As I understand it, Mate is currently a fork of the entirety of the Gnome 2 environment.

---

### Post by jbicha on 2011-10-14
I agree with several of the more recent comments: it's much wiser to improve gnome-panel than to try to keep GNOME 2 alive.

Clement, I understand you are trying to please your users but porting the Mint Menu as either a GNOME Shell extension or a gnome-panel 3 compatible applet is actually going to be less headache, take less time, and be more sustainable than teaming up with one guy who's trying to do the impossible. Clement, I don't think you have the extra time and development energy to implement the co-installable GNOME 2 idea.

Here's the current status of gnome-panel as I see it. Very few GNOME developers actually use gnome-panel as their primary desktop (in fact I don't know of any). gnome-panel is still part of GNOME Core and is the official fallback environment. However, only minimal maintenance is being done on it so it continues to work but it's not really getting any improvements. At some unspecified time in the future, several GNOME developers would like to drop gnome-panel from GNOME Core. Additionally, I believe the GNOME developers would be very appreciate of any patches that improve the way gnome-panel works, especially as they don't have the time (or interest, honestly) in doing that work themselves but are happy to take volunteer contributions.

Huge benefits of contributing to gnome-panel upstream: Already existing code hosting, wiki, bugtracker, release schedule, Google juice, and distro inclusion (every distro already packages GNOME's gnome-panel). Official status instead of trying to gain acceptance for an obsolete and incompatible fork. Each applet that you port to
gnome-panel 3 has a good chance of being picked up by distros and you're probably not the only guy that's trying to get applets ported but good luck trying to convince distros to package your GNOME 2 thing. Here's a big one: if gnome-panel is being actively maintained then GNOME will not kill it, at the most it will drop from being GNOME Core to being community maintained.

Or you could try to keep the entirety of GNOME 2 around but GNOME has already killed it (in the same way that no one is going to bother keeping GNOME 3.2 alive once GNOME 3.4 is out). And GNOME 2 will look less and less appealing with time. What if users want to use the nicer looking gnome-control-center 3? Do you really plan to port all of the new chat protocols to Empathy 2? I hear Evolution 3 is quite a bit nicer than Evolution 2 was. Here's a hint for you: Generally speaking, you can't mix and match GNOME components that are different versions and still be happy....

---

### Post by jbicha on 2011-10-14
Oh, and I forgot to mention that Debian unstable [today]("http://www.0d.be/debian/debian-gnome-3.0-status.html") got gnome-shell and gnome-panel 3. I don't know how updates in your Debian Mint version works but unless Debian presses the pause button, you've got 10 days until GNOME 3 hits the testing repository.

---

### Post by &quot;Lex on 2011-10-14
Still none of this convinced me not to believe in him. Still want Gnome 2 along many other people. The fact that it would be better to do it another way does not mean that can't be done in any other way. If it would really work like you said, then, we should group all the distros into the most popular one, and also terminate KDE, LXDE, XCFE and so on and group everyone into Gnome 3\Ubuntu. You realize this isn't happening, right?

---

### Post by PRC09 on 2011-10-14
Not sure how dead Gnome 2 actually is when Centos 6 is a fairly current release and they are using Gnome 2.28 and that is supported until 2017.....

---

### Post by jbicha on 2011-10-14
And KDE 3.5 is supported in Red Hat Enterprise Linux 5 until 2014. That doesn't change the fact that KDE3 has been dead for years. In fact KDE5 development has already begun.

I'm all in favor of choice. I personally contributed to GNOME Shell & Fallback being easy to install and use in Ubuntu 11.10. I'm also quite happy that Lubuntu appears to have had a good release and have suggested Xubuntu for many months for those who want a GNOME 2 style interface.

On the other hand, I am warning the GNOME 2 developer-fans that if y'all want gnome-panel to actually improve and continue getting GNOME support, you should work upstream instead of working against GNOME.

---

### Post by luk1don on 2011-10-15
Hi dear developer;)

Is this (Mate) better and more functional, configurable than gnome-session-fallback (gnome-panel)?
I've found your DEB packages, e.g. i386:

[http://matsusoft.com.ar/repository/ubuntu/mate/i386/](http://matsusoft.com.ar/repository/ubuntu/mate/i386/)

Is this work like PPA? (probably not)
Can I install these packages in Ubuntu 11.10?
But I have to install debs by the hand?
Please do something like PPA to easy install, like:
```
sudo apt-get install mate-desktop
```

---

### Post by kansasnoob on 2011-10-15
While I've changed over to Lubuntu for many things, and hopefully provided some useful Lubuntu testing during the Oneiric dev cycle, I still find myself reverting to Natty with a true gnome 2 environment when I'm pressed for time and have a project to complete. Of course I could do likewise with Lucid :)

Why? Well copy-n-paste doesn't seem to work as well in Lubuntu even after numerous tweaks, and even though I love pcmanfm I'm just so used to Nautilus that I miss it when I'm busy. I'm old and nearly blind so familiarity is very important ;)

And IMHO gnome 3 has a bunch of problems "under the hood", such as poor screensaver and power management. I hate not being able to inhibit screen blanking, it's absolutely infuriating,and I could point out several discussions about that in Oneiric testing archives.

I could go on and on about infuriating changes in gnome (regardless of whether it's Unity, gnome-shell, or fallback-session) but I'd certainly love to see a true gnome 2 fork that would work in Ubuntu and/or Debian.

After all gnome 2 is supported through Lucid until April 2013 and I'm guessing a bit beyond that in Debian stable. So if someone has the know how and the desire to create a fork I'd love it.

I'd love to be able to use the newest Linux kernel, Xorg, etc. with a familiar and reliable DE. I suspect that if Clem pulls this off Mint will pull far ahead of Ubuntu for at least a little while.

All of this is, of course, just my opinion ;)

Of course then I'll have to figure out how to break Mint's Synaptic to make it act like Debian's synaptic, but I already break a lot of Ubuntu stuff to make it work like Debian.

---

### Post by cro on 2011-10-16
I've always wanted to seriously contribute to Linux and proeprly learn how to develop for it. Until now though there's never been anything that interested me enough to spend the time outside my day job to get up to speed (as it were).

However, the shift to Unity or Gnome3/Gnome Shell have had such a detrimental effect on my ability to do my day to day job that it is actually cost-effective for me to spend work hours on learning how to help with this fork of Gnome than to try and continue working with Unity or Gnome3/Gnome shell.

So, what can I contribute?

---

### Post by gsmanners on 2011-10-16
Looks to me like the most useful thing is work for gnome-panel. I'm not sure what needs to be done, but I think some redesign might be a good idea. Frankly, setting exact positions for applets was always problematic, so switching to something like Xfce's design might be a good idea there.

---

### Post by screaminj3sus on 2011-10-16
I don't get why people are trying to fork gnome 2, what a maintenence nightmare... Why not fork gnome 3 and improve the fallback session? Gnome 3 fallback is pretty similar to gnome 2, its just more rough around the edges and needs some polsihing love. Its already based on gnome 3/GTK3 as well.

The main problem people have with gnome 3 fallback is with the gnome panel. Really just forking (or contributing fixes upstream) the panel would go a long way.

---

### Post by seatex on 2011-10-16
> **screaminj3sus said:**
> I don't get why people are trying to fork gnome 2, what a maintenence nightmare... Why not fork gnome 3 and improve the fallback session? Gnome 3 fallback is pretty similar to gnome 2, its just more rough around the edges and needs some polsihing love. Its already based on gnome 3/GTK3 as well.

The problem with this is that Gnome 2 should be the main session and we don't care about even having a Gnome 3 option.

Just my thought.

---

### Post by &quot;Lex on 2011-10-16
> **seatex said:**
> The problem with this is that Gnome 2 should be the main session and we don't care about even having a Gnome 3 option.

Just my thought.
Word. Dunno why they decided to do that... Yeah, i know tablet and stuff, but why don't make a "Gnome Tablet" official fork and upgrade Gnome Panel to GTK 3? I really can't understand... All the Gnome Shell functions and graphics could be also made in Gnome Panel with applications like Docky and some work on menus, instead they made...that thing. I just don't know....

---

### Post by c@ssie on 2011-10-16
> **luk1don said:**
> Hi dear developer;)

Is this (Mate) better and more functional, configurable than gnome-session-fallback (gnome-panel)?
I've found your DEB packages, e.g. i386:

[http://matsusoft.com.ar/repository/ubuntu/mate/i386/](http://matsusoft.com.ar/repository/ubuntu/mate/i386/)

Is this work like PPA? (probably not)
Can I install these packages in Ubuntu 11.10?
But I have to install debs by the hand?
Please do something like PPA to easy install, like:
```
sudo apt-get install mate-desktop
```

is there going to be a 64 bit repository?

---

### Post by cro on 2011-10-16
> **c@ssie said:**
> is there going to be a 64 bit repository?

I hope so :) Until then, I'll just compile from source.

---

### Post by cro on 2011-10-16
Came across a couple of installations errors. mate-vfs complains of missing schemas, and mate-panel just complains:
```

cro@shiny:~/Workspace/Mate/mate-panel/distro/ubuntu$ sudo dpkg -i mate-panel_2011.10.13-1_amd64.deb 
Selecting previously deselected package mate-panel.
(Reading database ... 302002 files and directories currently installed.)
Unpacking mate-panel (from mate-panel_2011.10.13-1_amd64.deb) ...
Setting up mate-panel (2011.10.13) ...
/var/lib/dpkg/info/mate-panel.postinst: 5: usr/bin/mateconftool-2: not found

(mateconftool-2:8256): MateConf-CRITICAL **: mateconf_engine_get_local_for_addresses: assertion `addresses != NULL' failed
**
MateConf:ERROR:mateconftool.c:961:main: assertion failed: (err != NULL)
Aborted
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...

```

---

### Post by c@ssie on 2011-10-16
I didn't even get that far


```
checking for LIBMATECOMPONENT... no
configure: error: Package requirements (    MateCORBA-2.0 >= 2.11.2     MateCORBA-CosNaming-2.0 >= 2.11.2     gmodule-2.0 >= 2.0.1     glib-2.0 >= 2.25.7     gobject-2.0 >= 2.25.7     gthread-2.0 >= 2.25.7         gio-2.0 >= 2.25.7) were not met:

No package 'MateCORBA-2.0' found
No package 'MateCORBA-CosNaming-2.0' found
```

---

### Post by cro on 2011-10-16
Here's how I did it:

* Get all the source from git (see post #2)
* Add the dependencies (also post #2)
* CD into each folder's /distro/ubuntu/ folder
* run ./build
* install the package using sudo dpkg -i {packagename}
* Do this for each folder in the list in post #2. There are two extra folders downloaded - ignore them.

Log out, and log back in to the MATE session. From a shell, run mate-session-properties and disable all the autostart programs you don't need, including any residual copies of old Gnome programs.

It may seem odd - the build scripts redownload the source to build the .debs, but it worked for me.

There are elements missing, and some inconsitencies with other packages, but this will allow you to build and run a fork of Gnome 2.32 on Ubuntu 11.10. 

Things missing so far:
* sound indicator (**FIXED** if you add gnome-sound-applet to startup programs, or run it manually)
* dbus notifications from ALSA (mute, unute etc)
  (Actually these two may be unrelated to MDE, as my mute/unmute softkeys are running through compiz "Commands")
* notifications in general, along with configuration of these. (I can configure them, but they're always top-right, with a fixed theme regardless of settings)
* **(working now)** keyboard input switcher (I use EN/TH/JA keyboards)
* gconf-editor support (I make changes, nothing happens)
* some various indicators (for example system tools)
* Some specific indicators - Rhythmbox for example can't be controlled any more as it's been integrated into the sound menu.

Things partially working:
* Compiz. Most effects work but there are focus and window placement issues with the cube. Plus there's a major redraw issue when rotating or using expo. This is primarily restricted to the cube effect, but issues also appear in desktop wall. I guess this is more related to Compiz than MDE :) Most other effects seem fine though.
* Fan control. The fans seems to run faster than they did under Gnome/11.04. Might be related to 11.10 though.
* New window placement. The top panel is not restricted space and new windows have a habit of appearing with their title bars underneath the panel.

Things that appear to be working fine:
* themes (even clearlooks themes, although clearlooks is missing)
* Skype and it's notification-area icon
* Dropbox and it's notification-area icon

I've got some project work coming in the next few days which will give me a good chance to see how stable this is, but so far, so good.

---

### Post by kansasnoob on 2011-10-19
A few things to add from my last post.

I'm just setting up a new system for streaming on-line video (full screen flash) and even though I can work around the gnome 3 screensaver BS by replacing it with xscreensaver, how can I handle CPU frequency scaling in gnome 3?

I'm sorry, but gnome 3 was just not ready for prime time :(

Did anyone notice that even Ubuntu-studio now went to xfce :confused:

Please get this into a ppa so dummies like me can use it :lolflag:

---

### Post by cro on 2011-10-20
I've been porting extra bits the past few days. I've managed to partially port gnome-applets-2.32.1 (I couldn't resolve dependencies for a few of them so I removed those I couldn't get working and managed to ostly compile it all. That's still a work in progress.

I did have some larger success with gnome-power-manager-2.32.1, and have successfully ported and compiled (and am currently running) it as `mate-power-manager`. This means I get the nice battery icon back, and I can actually set power management functions using `mate-power-settings`. And My laptop suspends when I shut the lid now, rather than having to do it manually.

There's still some issues with startup scripts, but I'm getting there.

The ported source is only on my local machine at the moment though.

---

### Post by cro on 2011-10-20
Getting closer!

I now have the following applets compiling and installing properly, although I think I have a configuration setting missing somewhere as I can't actually add them to the Mate Panel, even though they appear in the add-to-panel list. mate-panel-test-applets also loads them into the selection list, but won't actually execute them. No errors are shown either :(

So here's the list:
* accessx-status-applet
* drivemount_applet2
* gweather-applet-2
* battstat-applet-2
* cpufreq-applet
* trashapplet

The source for these is downloaded from the gnome FTP server, and they're all gnome-2.32.1, ported to compile against the MATE fork.

---

### Post by krapp on 2011-10-20
> **screaminj3sus said:**
> I don't get why people are trying to fork gnome 2, what a maintenence nightmare... Why not fork gnome 3 and improve the fallback session? Gnome 3 fallback is pretty similar to gnome 2, its just more rough around the edges and needs some polsihing love. Its already based on gnome 3/GTK3 as well.

The main problem people have with gnome 3 fallback is with the gnome panel. Really just forking (or contributing fixes upstream) the panel would go a long way.

Most sensible response to the hysteria!

---

### Post by cro on 2011-10-20
> **krapp said:**
> Most sensible response to the hysteria!

My two-penneth:

gnome-fallback has a dependency on gnome3. Which breaks a whole lot of desktop environment paradigms and removes a lot of the old supporting libraries. Along with the stated desire of the Gnome developers to move away from the Gnome2 style of interface towards a netbook/tablet-style interface leaves long-term support for the supporting libraries needed by gnome-fallback in jeopardy.

The biggest initial issue with deciding between forking gnome2 or contributing upstream fixes to gnome-fallback is that some of the libraries to support old gnome2 applets or add-ons just plain don't exist anymore, neccesitating not a patch or two, but a complete rewrite of some elements.

Even simple things appear to be missing,like the single-button menu with all elements, support for drawers, moveable elements of the menu (might just be me, but I couldn't move the clock from the center of the top panel in gnome-fallback), and the lack of proper theme support. If the Gnome3 developers were serious about supporting this paradign, then they would have ported gnome-panel themselves, not created a new "fallback" version. (And compiz integration seems utterly broken for me - there's a lot of tweaks in compiz tht make my daily life uch simpler)

I had a working desktop in Gnome 2.32.1. It was fast, responsive and had all the bells and whistles and tweaks I needed to maximise my productivity and the amount of information the OS gave me about my desktop environment in the minimum amount of space, whilst given me the workspace expansiveness I need in my day job to support the sheer number of open programs I use.

Unity and Gnome3 killed that desktop, and gnome-fallback is even less useful and with less features than XFCE or LXDE (no offense to either, I've used both quite considerably but they're both lacking certain elements I need).

(As an aside, my work machine is now permanently locked to Ubuntu 11.04. I can't afford to upgrade to 11.10+Unity/Gnome3 - it would cost me too much in lost earnings trying to get a working environment in place that matched the efficiency 11.04+gnome2 gives me. And yes, I have tried both Unity and Gnome3.)

---

### Post by Mr. Picklesworth on 2011-10-20
> **cro said:**
> Even simple things appear to be missing,like the single-button menu with all elements, support for drawers, moveable elements of the menu (might just be me, but I couldn't move the clock from the center of the top panel in gnome-fallback), and the lack of proper theme support. If the Gnome3 developers were serious about supporting this paradign, then they would have ported gnome-panel themselves, not created a new "fallback" version. (And compiz integration seems utterly broken for me - there's a lot of tweaks in compiz tht make my daily life uch simpler)

They *did*, actually, and that's the point. As well as being moved to GTK3, there were a bunch of changes to make the panel cleaner and more 
reliable, both for users and for developers. Unfortunately drawers were a casualty, but I still can't help but think building and maintaining a drawers patch for an active project (which might even be accepted upstream) would be less trouble than maintaining gnome-settings-manager.

I'll let Vincent's blog post do the talking about Panel 3:

[http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel!](http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel!)

---

### Post by cro on 2011-10-21
> **Mr. Picklesworth said:**
> They *did*, actually, and that's the point. As well as being moved to GTK3, there were a bunch of changes to make the panel cleaner and more 
reliable, both for users and for developers. Unfortunately drawers were a casualty, but I still can't help but think building and maintaining a drawers patch for an active project (which might even be accepted upstream) would be less trouble than maintaining gnome-settings-manager.

I'll let Vincent's blog post do the talking about Panel 3:

[http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel!](http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel!)

**Updated again with this URL:** [http://www.jemmatzan.com/2011/10/unity-is-the-end-of-ubuntu.html](http://www.jemmatzan.com/2011/10/unity-is-the-end-of-ubuntu.html). A very eloquent a cogent explanation of why I'm trying to work at porting Gnome2 to the 3.x kernel, or why I'll downgrade from 11.10 to 11.04.

**(Updated. I did a complete clean install of 11.10 onto a blank disk, fully updated it, installed dual monitors, and gnome-session-fallback. The edits below now reflect my experience with a clean install)**

I've spent some more time with gnome-session-fallback now. I'm going to focus on the negatives, as they far outweight the positives:

The good:
* gnome-session-fallback runs.

The bad:
* gnome-session-fallback inteferes with the way I work. Gnome shell is even worse, and actively hides information and makes it harder to move between applications and application windows.
* **update: this works now** *gnome shell doesn't run. At all. I get my background picture, and have to switch to an alternate login screen to force-restart gdm or lightdm to choose a different shell.*
* **update: this works now** *no network indicator icon (this came back on a reboot)*
* I can't remove bluez without removing gnome-session-fallback (huh?)
* installing gnome-session-fallback forces installation of unity, unity-shell, gnome-shell and banshee(?!) among others
* alt-right click to modify the panel only works if your window manager is metacity. If it's anything else, you're SOL. This took quite some figuring out and I only realised it when I saw reference to changing the right-click modifier as a function of metacity in gconf.
* **Update: This is actually worse on a clean install and on first run compiz --replace will actuall disable every single plugin and run unity-window-decorator, forcing you to go back into ccsm and re-enable all the plugins you had previously enabled.** Compiz doesn't play nicely anymore:
- **update: this is even worse on a clean install. Update 2: This happens in default Unity as well** Compiz rotate cube causes visual errors, including a flash-redraw of the previous desktop which removes focus from the top window in the window stack on the destination workspace
- There are window focus problems.
- **update: again this is even worse on a clean install as the delay bewteen moving workspaces and the window snapping back is slightly longer** You CANNOT move a window between workspaces using the "ctrl-alt-shift" method. The windows move with the workspace move, then snap back to their original positions on their original workspaces. Windows MUST be moved using the mouse. (Also, the title-bar "move to workspace" doesn't work). This applies equally in Compiz and Metacity.
* System settings are missing a number of configuration items. Why should I have to install an unsupported third-party tool to change my window theme or mouse cursors?
* The default theme sets for gnome-session-fallback are visually unappealing and provide insufficient visual feedback of the deliniation between icons in the task bar.
* I haven't figured out yet how to add an application to the panel.
* There are a large number of bugs in the way add-ons are implemented, bugs that did not exist in their previous gnome 2.32.1 versions (adding additional cities for timezone information for example - you can't see the extra cities until you close the preferences window and use the drop down. In addition, you can't have the city list expanded by default, it always reverts to being closed in the applet's dropdown)
* gdm is no longer supported. Which means it gets marked for auto-removal. lightdm has a segfault crash that causes the machine to get locked into a start->crash->start->crash infinite loop that can't be broken out of without booting to a root shell and replacing the default login greeter.
* Installing unity (which is required to install gnome-session-fallback) installs and enables the unity plugin in compiz - which means that gnome-panel *AND* unity both run on first login. The unity plugin has to be manually disabled in CCSM (which is also a non-default install!)
* Synaptic package manager segfaults unless you go into accessibility settings and turn the screenreader first on, then off. Seriously? Yes, there's a bug logged against this, but it's marked as low priority. It's also missing from the default menus. Ubuntu Software Center is at best a partial replacement for Synaptic, and does a very good job of hiding the software I want to install, and running very very slowly.
* **update: this is part of gnome-session-fallback** *From what I can gather, the only reason I currently have a trashcan applet that I can add to the panel is because I compiled it from the Gnome2 source and accidentally installed the applet file in the right location for gnome-fallback to find it.*
* **Update: keyboard shortcuts work, but they seem to exist solely to run pre-defined applications** Keyboard shortcuts don't work. Especially those assigned against the SUPER key. I've lost all of my normal shortcuts, including the one that opened Nautilus.
* The new nautilus removes functionality when compared to the old. The icon resize buttons are missing, gnome-thumbnailer no longer thumbnails certain video types (which is an incredible difficulty as I run a subscription-based company that contains more than 4,000 hours of streaming video...), the location bar no longer displays unless I manually press ctrl-l, and for some god-awful reason it completely ignores my theme settings and has a dark background. eog, totem and evince are the same. I have a light theme installed, pale window borders, light icons, yet all gnome-based applications have a dark grey background within the main application window.
* **update: this has reappeared** I can't find the power management settings. They appear to be completely missing, so I can't set my laptop to suspend when I shut the lid (it keeps running!). Until I recompiled gnome-power-manager I had to manually suspend my laptop, the close the lid. Resume from suspend was also originally broken, and it doesn't lock the screen like it used to, even though I have this option selected.

It really feels now that Gnome 3 and Unity are toy desktops that are designed to make the user work in a particular way. The similarity between the design goals of both environments and MacOSX are close enough that there's not really anything to choose between them any more, and both Gnome Shell and Unity seem to me moving wholesale towards a tablet-based interface where the interactions allowed are limited to what the OS provider thinks is a good idea.

Which is what both Microsoft and Apple do - you can do whatever you like with those two operating systems, as long as it's what they want to let you do.

Linux has always been a little free-er. Unity and Gnome Shell seems to be moving rapidly down the path of locking the user out of any form of customisation or choice in the way of working.

The more I work with Gnome 3 and Unity, the more time and effort (and cashy money) I will spend on forking Gnome 2, or updating XFCE or LXDE so that I have a desktop interface that actually helps me do my job, rather than one that forces me into working in a particular way because an interface designer thinks the next big thing that everyone will use is single-screen interfaces where we only use one program at a time. *Right now* I have 35 windows open spread across 4 workspaces on a dual monitor system, to do my job. I can't and don't focus on one full-screen application at a time.

Also, I'll leave this quote from the Gnome3 post you linked:
> Sure, the fallback mode is not our target in terms of design, but that doesn't mean it's unloved. 
Anything that's not the target of design always falls by the wayside. Effort is not expended, and regressions are not tested against non-roadmap items.

Inevitably the fallback mode will be removed as being too difficult to maintain and as not being part of the roadmap.

---

### Post by aptituder on 2011-10-21
Why not just use gnome shell with docky (or plank) in panel mode? Doesn't that provide the same amount of functionality as classic gnome 2?

---

### Post by gsmanners on 2011-10-22
I might try out tint2 or xfce-panel with Gnome Shell to see what that's like. :D

---

### Post by kvvv on 2011-10-22
> **aptituder said:**
> Why not just use gnome shell with docky (or plank) in panel mode? Doesn't that provide the same amount of functionality as classic gnome 2?

> **gsmanners said:**
> I might try out tint2 or xfce-panel with Gnome Shell to see what that's like. :D

Does it conflict with the bottom notification thingy in gnome shell?

---

### Post by gsmanners on 2011-10-22
> **kvvv said:**
> Does it conflict with the bottom notification thingy in gnome shell?

I don't know. I imagine it might, so I probably better try it in various positions. (Nice thing about Xfce. You can configure things like that pretty easily.)

---

### Post by KingYaba on 2011-10-22
I think, tomorrow, I'm going to try this out.

---

### Post by cro on 2011-10-22
> **aptituder said:**
> Why not just use gnome shell with docky (or plank) in panel mode? Doesn't that provide the same amount of functionality as classic gnome 2?

For me, no. At the end of the day, the design decisions made for the interface in both Unity and Gnome shell mean that too much information is hidden from me when I am working. The global menu is actually a severe hindrance to the way I work and actually slows me down when I am moving between windows.

Working on a laptop means I have no middle mouse, so the default "use middle mouse to open a new window" paradigm is not an option for me, meaning opening a new window if a right-click then a left click with mouse movement inbetween.

What seems to be being missed everywhere in these discussions is that the design decisions in both Unity and Gnome shell are designed around the one-window usage paradigm. You only ever have one window open, and it's maximised. You never need to move quickly to another window. You never need to move between multiple windows quickly. And accessing any information at all about other windows is next to impossible. I often run with 4 or 5 windows laid out across dual monitors in such a way that I can see all their information all at once. If I need to access a programs menu, I click on the menu bar. In Unity however, I first have to give that program focus, then move to the top-left of the visible work area. Now, if the program I want is running in a small window bottom-right, I have to traverse the entire screen real estate to access that window's menu. After giving it focus of course.

I know the new alt-tab functionality in 11.10 is being touted as a big refinement over 11.04 - but why? Why was this functionality degraded in the first place? I used to have two forms of alt-tab: alt-tab between programs on the current workspace, alt-shift-tab between programs on all workspaces (and shift-tab between tabs in a program). So, all of this functionality is *new* in 11.10? But I've been using it for the past 6 releases? Colour me confused.

So no, Gnome shell and Docky don't provide the same level of functionality as I used to get in Gnome2. Even Gnome3 in classic mode doesn't give me the same level of functionality, and I've spent the past day trying to get it working in a form that allows me to work efficiently.

---

### Post by cro on 2011-10-22
Right, enough thread hijacking, back to Mate:

There's now an extras repository:
[https://github.com/Perberos/Mate-Extra](https://github.com/Perberos/Mate-Extra)

Most packages don't have Ubuntu build scripts just yet though. I've hacked about and been creating .debs for the packages listed below.

Manual build order:
* mate-file-manager-sendto
* mate-bluetooth (depends on sendto)

Other successful builds (into .deb packages) **UPDATED**
* mate-power-manager
* mate-applets **update** make sure you have all the necessary dev libraries installed for gstreamer, selinux and avahi.
* mate-conf-editor
* mate-calc
* mate-text-editor (requires libgtksourceview-2.0.dev. compiles as a replacement for gedit)
* mate-image-viewer (requires libjpeg62-dev). **update: latest git source corrects the python issue**. Also, see [https://github.com/Perberos/Mate-Extra/issues/4/](https://github.com/Perberos/Mate-Extra/issues/4/) if you have a python version detection error.
* mate-character-map (read the build script for dependencies. run ./autogen.sh before trying to build)

---

### Post by adam.d.clemons on 2011-10-25
I'd love to get involved with this, I have tried and tried to get used to Unity, and Gnome3 and I like them both, but the workflow does not work for me. I'm not much of a programmer, but I've been an Ubuntu user for 6 years now and I've used a lot of other Linux distros and would be more than happy to test any updates or changes. I'd like to see Gnome2 (Mate) become an updated and cutting edge Environment that is still familiar to everyone.

---

### Post by Sorinux on 2011-10-25
cro you are absolutely correct!

---

### Post by cro on 2011-10-25
A build update: I've been going through [https://github.com/Perberos/Mate-Desktop-Environment](https://github.com/Perberos/Mate-Desktop-Environment) and rebuilding and reinstalling each of the packages as they're updated. The /distro/ubuntu/build script works to download the source from sourceforge, however this isn't always the latest git source.

Not all the git sources in Mate-Desktop-Environment build at the moment, see [https://github.com/Perberos/Mate-Desktop-Environment/issues/22](https://github.com/Perberos/Mate-Desktop-Environment/issues/22) for a list of the packages which will build using the distro script but not from source, and I'm still going through the packages in [https://github.com/Perberos/Mate-Extra](https://github.com/Perberos/Mate-Extra) and writing my own build scripts for thos that don't have them, so see the above post for the list of currently-compiling.

(As a side note, I use the script to craete a .deb, based on Perderos' scripts, which I then install, rather than configure && make && make install)

I'm using Mate on a daily basis. There are some issues for me presently, but as may be obvious I'm something of a power user :)

---

### Post by vagrale13 on 2011-10-25
I test Mate and i think, would be reason for more users in future to don' t leave Ubuntu.

For some reason missing from menu the terminal (gnome-terminal)

---

### Post by cro on 2011-10-25
More builds from Mate-Extra

* mate-disk-utility
* mate-media

---

### Post by Perberos on 2011-10-26
> Perberos, you do not have permission to access this page. This could be due to one of several reasons:

    Your user account has less than 50 posts.
    Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
    If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.
Let's spammmm
:guitar:

I wish I could give better support, but ubuntu in virtualbox with low ram, makes me mad. I stay 5 hours to do a full compile of basic modules.
:cry:

I was fighting with the [COLOR="DarkRed"]**Deprecated War**[/COLOR]™, very entertaining, but I want to make the PPA thing.
We need to complete the depends and makedepends array.

> **vagrale13 said:**
> For some reason missing from menu the terminal (gnome-terminal)
Maybe the gnome-terminal.desktop had a 'showonly=GNOME' property


Thanks for using github's issue system.

---

### Post by vagrale13 on 2011-10-26
> **Perberos said:**
> Maybe the gnome-terminal.desktop had a 'showonly=GNOME' property


Thanks for using github's issue system.
Yes, that's it! :popcorn:

---

### Post by SevenUp on 2011-10-26
> **DoubleClicker said:**
> ..Perberos,
While I am very grateful to you,  for forking Gnome to a new desktop environment, I believe it is a serious mistake to name it Maté..

Getting back to the concerns that have been expressed for "Maté" as the name for this project, given the various meanings attached to the word "Mate" in English, it's important to remember the following. 

Maté, also known as Chimarrão in Portuguese, is a traditional South American drink popular in Uruguay, Argentina, Paraguay, the southern states of Brazil, southern Chile, and the Bolivian Chaco. Prepared from steeping dried leaves of yerba mate (llex paraguariensis, known in Portuguese as erva mate) in hot water, it produces a sense of wellbeing and increased energy that make it a near perfect choice for a project name from the standpoint of its Argentine developer. 

Not saying that "Maté" doesn't present certain difficulties when translated as "Mate" in English, just that understanding the origin of the Spanish/Portuguese word itself is important to keep in mind as this discussion goes forward.

---

### Post by DoubleClicker on 2011-10-26
> **SevenUp said:**
> Getting back to the concerns that have been expressed for "Maté" as the name for this project, given the various meanings attached to the word "Mate" in English, it's important to remember the following. 

Maté, also known as Chimarrão in Portuguese, is a traditional South American drink popular in Uruguay, Argentina, Paraguay, the southern states of Brazil, southern Chile, and the Bolivian Chaco. Prepared from steeping dried leaves of yerba mate (llex paraguariensis, known in Portuguese as erva mate) in hot water, it produces a sense of wellbeing and increased energy that make it a near perfect choice for a project name from the standpoint of its Argentine developer. 

Not saying that "Maté" doesn't present certain difficulties when translated as "Mate" in English, just that understanding the origin of the Spanish/Portuguese word itself is important to keep in mind as this discussion goes forward.

You have just stated one of the biggest reasons NOT to name it Mate. Mate has too much common usage.  Apple made a big mistake calling there email program "Mail", there spreadsheet "Numbers" and there Word processor "Pages".  It's fairly hard to google those words and get useful information about those applications.   Windows, on the other hand, had the power of Microsoft building the brand name for years before Google existed.  Now when you google "windows," it's hard to get information about the thing you look out of.  

Chimarrao would be bettter name than Mate for gaining "google juice", since the desktop could easily become more referenced, than the drink by that name.  However, Chimarrao still suffers from being 4 syllables long, and hard for the non-Spanish speaking people to pronounce.

"Mate being a perfect name from standpoint of its Argentine developer", is a clear example of why big companies don't let the developer give the product it's name, and have a marketing department to do it.  Developers give there products names, that are meaningful to them, but don't consider how it helps the product gain marketshare.

---

### Post by kurt18947 on 2011-10-26
> **cro said:**
> For me, no. At the end of the day, the design decisions made for the interface in both Unity and Gnome shell mean that too much information is hidden from me when I am working. The global menu is actually a severe hindrance to the way I work and actually slows me down when I am moving between windows.

Working on a laptop means I have no middle mouse, so the default "use middle mouse to open a new window" paradigm is not an option for me, meaning opening a new window if a right-click then a left click with mouse movement inbetween.

What seems to be being missed everywhere in these discussions is that the design decisions in both Unity and Gnome shell are designed around the one-window usage paradigm. You only ever have one window open, and it's maximised. You never need to move quickly to another window. You never need to move between multiple windows quickly. And accessing any information at all about other windows is next to impossible. I often run with 4 or 5 windows laid out across dual monitors in such a way that I can see all their information all at once. If I need to access a programs menu, I click on the menu bar. In Unity however, I first have to give that program focus, then move to the top-left of the visible work area. Now, if the program I want is running in a small window bottom-right, I have to traverse the entire screen real estate to access that window's menu. After giving it focus of course.

I know the new alt-tab functionality in 11.10 is being touted as a big refinement over 11.04 - but why? Why was this functionality degraded in the first place? I used to have two forms of alt-tab: alt-tab between programs on the current workspace, alt-shift-tab between programs on all workspaces (and shift-tab between tabs in a program). So, all of this functionality is *new* in 11.10? But I've been using it for the past 6 releases? Colour me confused.

So no, Gnome shell and Docky don't provide the same level of functionality as I used to get in Gnome2. Even Gnome3 in classic mode doesn't give me the same level of functionality, and I've spent the past day trying to get it working in a form that allows me to work efficiently.

Giving continuing life to the hijack :tongue:  If the window switching means is your primary problem, do you know about tint2? It puts a bar at the botton of the screen of both Unity and Gnome-shell.  It's primarily a window switcher as far as i can tell so it may help you. I can see about 17 open windows at one time.  It's in the main repository and documentation is easily found via Google.  I had problems with auto-hide so turned it off.

---

### Post by Perberos on 2011-10-26
[java]("http://en.wikipedia.org/wiki/Java_%28disambiguation%29") wat

I already read how to PPA on LunchPad (sorry, It's my humor sense) and I don't want made it as debian style (because I am lazy). so if anyone want to maintain a PPA, welcome!

---

### Post by vagrale13 on 2011-10-27
The alacarte doesn' t open to edit menu

```
:~$ alacarte
Traceback (most recent call last):
  File "/usr/local/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
ImportError: No module named Alacarte.MainWindow
```

---

### Post by pinguy on 2011-10-27
[http://www.zevenos.com/allgemein/good-old-mate-gnome-2-is-back.html](http://www.zevenos.com/allgemein/good-old-mate-gnome-2-is-back.html)
They have the Mate desktop in their repo

deb [http://zevenos.dyndns.org/repo](http://zevenos.dyndns.org/repo) sid main

---

### Post by Amanas on 2011-10-27
I plan on setting up a ppa this weekend. I'll report back once it's up.

---

### Post by saxonjf on 2011-10-28
Let me begin by saying that both Unity and Gnome Shell made me grind my teeth to nubs when I found out that I lost all the easy functionality that Gnome 2 had offered on Ubuntu. Gnome 2 was an excellent bit of software, and deserved better treatment than to be tossed aside like so much garbage.  Let me also say that when KDE 4 came out, there was anger, but not to such an extent that forking the old version and maintaining into the future was really viewed as a viable option.

I even tried Fallback, but that was very frustrating itself.  The alt-rightclick, the limited functionality.  Everythig *looked* mostly right, but everything *felt* mostly wrong.

So I have switched over the LXDE, and with some time and effort, I have been able to approximate the look and feel of Gnome 2 in a way which is far more satisfying than even Fallback.

Let me just say that, as an end-user with limited understanding and almost no support in the real world, I will be very excited if Mate is a successful.  I am shocked that Ubuntu and Gnome are not listening to their angry users and forging ahead with these frustrating and broken pieces of software with no real options.

Keep it up, Perberos.  Don't listen to the naysayers tell you that just going with the flow is the best option.  As soon it becomes simple enough for the average idiot end-user to install Mate onto Ubuntu via PPAs or with a DEB, I will do so gladly.   can't wait.

---

### Post by cro on 2011-10-28
> **Amanas said:**
> I plan on setting up a ppa this weekend. I'll report back once it's up.

Well, I was going to ask myself if I could set up a PPA for this, but since Perberos has given his go-ahead to someone else setting up a PPA, and you've kindly volunteered I shall step back :)

I'll keep posting my efforts at Ubuntu-based configuring and compiling. I have a marginally customised build script/support script now, but given I have almost no experience in the Makefile system whenever I run into a configuration error I have to wait for someone else to fix it.

I am teaching myself the current art around Makefile and configure, but it's been almost 20 years since I last did any real C development (the last time I wrote a C program was in 1994!) so it's slow going, also given I've got a day job ;)

My system is mostly stable, but there are still issues with Caja and some configuration items (that might be caused by the way my system has evolved over the past couple of years, and my ham-fisted hacking about in configuration files)

I'm also going to check out the ZevenOS repo :)

---

### Post by cro on 2011-10-28
> **kurt18947 said:**
> Giving continuing life to the hijack :tongue:  If the window switching means is your primary problem, do you know about tint2? It puts a bar at the botton of the screen of both Unity and Gnome-shell.  It's primarily a window switcher as far as i can tell so it may help you. I can see about 17 open windows at one time.  It's in the main repository and documentation is easily found via Google.  I had problems with auto-hide so turned it off.

I have seen this. I have a customised setup using Cairo Dock at the bottom (auto-hide) for quick access to my most used programs, and the window list at the top of the screen. I've always worked this way (even with MS Windows) so I find the window list at the bottom slightly odd these days :) Not that I couldn't get used to it though.

The panel itself, the window controls on the left, and the global menu are all non-starters though. The global menu is one of the single most annoying things ever about any OS, and is one of the things I hate most about MacOS (and I wasn't that much of a fan of it on the Amiga or Atari either)

It goes back to what I said before: I don't work in only one program at a time, and the global menu assumes I do.

---

### Post by cro on 2011-10-28
(couldn't figure out how to delete this post)

---

### Post by c@ssie on 2011-10-28
> **pinguy said:**
> [http://www.zevenos.com/allgemein/good-old-mate-gnome-2-is-back.html](http://www.zevenos.com/allgemein/good-old-mate-gnome-2-is-back.html)
They have the Mate desktop in their repo

deb [http://zevenos.dyndns.org/repo](http://zevenos.dyndns.org/repo) sid main


it appears that they only have 32 bit, is someone doing a 64 bit PPA?

---

### Post by Amanas on 2011-10-28
> **c@ssie said:**
> it appears that they only have 32 bit, is someone doing a 64 bit PPA?

I'll be setting up a ppa for both 32 and 64 bit.

---

### Post by Quarkrad on 2011-10-29
Sorry for dumb question.  I'm hoping to install 64bit Mate/MDE when it is available through PPA.  Do you remove unity and then install MDE or do you just install over the top of unity?

---

### Post by cro on 2011-10-29
> **Quarkrad said:**
> Sorry for dumb question.  I'm hoping to install 64bit Mate/MDE when it is available through PPA.  Do you remove unity and then install MDE or do you just install over the top of unity?

They run side-by-side, so you can have both installed. You select MATE the same way you select any shell, at the login prompt.

Note: MATE is a fork of GNOME, so it does conflict with some elements of GNOME, so take the above with a grain of salt (there are some packages in MATE which provide the same libraries as GNOME, so you have to remove the GNOME packages to use MATE. At least at the moment.)

---

### Post by vagrale13 on 2011-10-29
[B]@Quarkrad
[/B]I think would be something like this!

---

### Post by Valpskott on 2011-10-30
I'd like to submit "Gnoblin" (Goblin with an extra n) as a possible name instead of Mate.

Reasons:
1 - Whenever I think of the word "Gnome", little small earth dwelling troll like creatures springs to mind. Goblins beeing kind of a not to distant relative to them.

2 - Putting the extra "n" into "Goblin" so it becomes "Gnoblin" both increase the name potency on Google and also hints to it's Gnome origins.

3 - As far as impact, "Mate" is very bland. Even thou "Mate" could possibly mean "sexual reproduction" it is one of the tamest ways of naming that activity. Still, I don't think the intended aim here was to associate it with sexual reproduction. The word itself just seem too bland. Simple is good, but It's just too simple. It lacks "sting".

4 - Perberos even describes the project with the words "unattractive desktop for users", I don't know his reasons for this, I surely hope it will have full gnome 2.3 compatibility in the future(gnome 2.3 could be made to look really beautiful). But as far as "unattractive" goes, sure I have some friends(mates) that could have benefitted from better phenotypes, but none of them really compares with your average Goblin ;)




I'm also wondering about the rights to name a project. A fork of gnome has been sought after since at least April 2011. Perberos was to my knowledge the first to go public with this attempt, so, is he the only one that has the final word in the matter?

Don't get me wrong, I'm not trying to advocate a name change against Perberos concent. After all, to me, a fork is more important than the name. But as others have pointed out, a name change could greatly benefit this fork and it's better to do it now while the project is young. But reading though the posts I can't help but feel that Perberos isn't paying any attention to this issue. Almost like he has his own agenda in staying quiet while longing for the days when a name change will be considered too late.

My apologies if I've missed a post where he addressed the issue.

For clarification, if I'm perceived as being passionate about this issue, it's not because I want my name submission to be implemented, I surely wouldn't mind if it was, but the main motivation is that I feel this fork is a really great initiative and I want this to get as much attention as possible. I'd really like to see more possible names submitted and a vote on the issue. If this is OK with Perberos of course.

---

### Post by brucemartin on 2011-10-31
> **Amanas said:**
> I'll be setting up a ppa for both 32 and 64 bit.

will you also include the mate extras?

---

### Post by Amanas on 2011-10-31
> **brucemartin said:**
> will you also include the mate extras?

Yep. I'll take care of those as well.

---

### Post by cariboo on 2011-10-31
> **cro said:**
> They run side-by-side, so you can have both installed. You select MATE the same way you select any shell, at the login prompt.

Note: MATE is a fork of GNOME, so it does conflict with some elements of GNOME, so take the above with a grain of salt (there are some packages in MATE which provide the same libraries as GNOME, so you have to remove the GNOME packages to use MATE. At least at the moment.)

This is getting sillier as it goes along, why install Mate along side Unity, when Gnome Classic, is already available and there are no conflicts. There are people working on Gnome Classic to add the same functionality as what Mate is trying to do.

This split in effort isn't helping anything. Please put the effort into making Gnome Classic better instead.

---

### Post by maxiecool2 on 2011-11-01
tried to install mate-vfs but had dependency issues,
mate-vfs depends on gtk-doc-utils
i have searched google but was not able to find this package
keep up the good work
mat

---

### Post by Amanas on 2011-11-01
> **maxiecool2 said:**
> tried to install mate-vfs but had dependency issues,
mate-vfs depends on gtk-doc-utils
i have searched google but was not able to find this package
keep up the good work
mat

try gtk-doc-tools instead

---

### Post by Glenn nl on 2011-11-01
I don´t really agree with forking the entire GNOME project.
Mate is meant to be to deliver the Gnome 2 experience (as far as I know).
Nautilus and Metacity are being forked I believe, but they haven´t changed that much!
Why not simply take gnome-panel, gdm and other stuff that _really_ changed, port it to gtk3 and done?
This way you have less to maintain.

Just my 2 cents. :popcorn:

---

### Post by pqwoerituytrueiwoq on 2011-11-01
if i am not happy with gnome3/unity by april 2013 (10.04 EOL date) i hope this is still around (assuming certain old apps not get on my nerves and force me to change from 10.04 sooner)
having a flex applet in panels would be nice like xfce has (firefox has these in it also)

---

### Post by ninhalo5 on 2011-11-01
> **Amanas said:**
> try gtk-doc-tools instead
I'm having the same issue, no gtk-doc-utils.  I checked and I do have gtk-doc-tools installed at it's latest version 1.18-1 and did find gnome-doc-utils-0.20.6 at sourceforge  both are installed and still I get the same error 
Error: Dependency is not satisfiable: gtk-doc-utils

I'm out of guesses

---

### Post by Amanas on 2011-11-01
> **ninhalo5 said:**
> I'm having the same issue, no gtk-doc-utils.  I checked and I do have gtk-doc-tools installed at it's latest version 1.18-1 and did find gnome-doc-utils-0.20.6 at sourceforge  both are installed and still I get the same error 
Error: Dependency is not satisfiable: gtk-doc-utils

I'm out of guesses

If you're building with the build script in distro/ubuntu, you'll want to edit the file and replace gtk-doc-utils with gtk-doc-tools. Otherwise, it will keep looking for gtk-doc-utils.

---

### Post by ninhalo5 on 2011-11-01
Great that got it, thank you

---

### Post by raster on 2011-11-01
> **cro said:**
> * alt-right click to modify the panel only works if your window manager is metacity. If it's anything else, you're SOL. This took quite some figuring out and I only realised it when I saw reference to changing the right-click modifier as a function of metacity in gconf.

To be able to work the ALT-Right click with Compiz, you must change the "Move window -> Initiate Window Move" key to one diferent than ALT, to avoid interferences. I put it to "Super", and I can work fine with Compiz and Gnome3-panel.

About the Cube: yes, I have the same problem, but seems a bug in the new compiz version. While it gets fixed, I'm using Desktop Wall, which works fine.

---

### Post by maxiecool2 on 2011-11-02
great thanks!

---

### Post by philinux on 2011-11-02
Moved to Desktop Environment forum.

---

### Post by maxiecool2 on 2011-11-02
i am now getting a error in the mate-keyring package
trying to overwrite '/usr/lib/libgcr.so.0.0.0', which is also in package libgcr0 2.92.92.is.2.32.1-0ubuntu2.1
can i ignore the error?

---

### Post by phDaemon on 2011-11-02
Sweet, good luck with this project!! I'm extremely happy with gnome-shell but to me, linux is all about choice, and a lot of users are not happy with the new gnome changes, so I'm sure this will make them extremely happy!! Hopefully the project will keep gaining momentum and even pick up a few ppl willing to help!

---

### Post by crdlb on 2011-11-02
> **maxiecool2 said:**
> i am now getting a error in the mate-keyring package
trying to overwrite '/usr/lib/libgcr.so.0.0.0', which is also in package libgcr0 2.92.92.is.2.32.1-0ubuntu2.1
can i ignore the error?

It appears that libgcr0 has been removed from Oneiric, so you can just remove that package.

---

### Post by spcwingo on 2011-11-02
> **cariboo907 said:**
> This split in effort isn't helping anything. Please put the effort into making Gnome Classic better instead.

With that train of thought, why is Unity being developed?  Shouldn't that effort and resources be put towards a stronger Gnome-Shell?  Just my $0.02.

---

### Post by &quot;Lex on 2011-11-02
Amanas, how is your PPA going? Will be ready soon?

---

### Post by Amanas on 2011-11-02
> **"Lex said:**
> Amanas, how is your PPA going? Will be ready soon?

It's coming along. I have a good portion of the files uploaded. Still need to upload the rest and finish testing.

---

### Post by spcwingo on 2011-11-02
> **Amanas said:**
> It's coming along. I have a good portion of the files uploaded. Still need to upload the rest and finish testing.

That's great news!  I can't wait to test it.  :)

---

### Post by maxiecool2 on 2011-11-02
cool thanks
but i didnt get far
 now its 
trying to overwrite '/usr/lib/libgp11.so.0.0.0', which is also in package libgp11-0 2.92.92.is.2.32.1-0ubuntu2.1

---

### Post by ondrejch on 2011-11-02
What prerequisites are there for Mate-Extras? I have a problem compiling any of them :/

---

### Post by jimbo99 on 2011-11-02
> **cariboo907 said:**
> This is getting sillier as it goes along, why install Mate along side Unity, when Gnome Classic, is already available and there are no conflicts. There are people working on Gnome Classic to add the same functionality as what Mate is trying to do.

This split in effort isn't helping anything. Please put the effort into making Gnome Classic better instead.

Because the gnome-fallback isn't gnome.  It is some awful crippled imitation masquerading as gnome developed by the gnome3 devs as a mechanism to fall back to in case gnome3 fails.

And how about you guys just making gnome2 available instead of screwing with how it is developed?  Just give us ppas and leave it at that.

---

### Post by thatguruguy on 2011-11-02
> **jimbo99 said:**
> Because the gnome-fallback isn't gnome.  It is some awful crippled imitation masquerading as gnome developed by the gnome3 devs as a mechanism to fall back to in case gnome3 fails.

And how about you guys just making gnome2 available instead of screwing with how it is developed?  Just give us ppas and leave it at that.

Who are these "you guys" you're referring to?

---

### Post by crdlb on 2011-11-03
> **maxiecool2 said:**
> cool thanks
but i didnt get far
 now its 
trying to overwrite '/usr/lib/libgp11.so.0.0.0', which is also in package libgp11-0 2.92.92.is.2.32.1-0ubuntu2.1

Same story there; you can remove it. I guess mate-keyring should have some Conflicts/Replaces for those packages (disclaimer: I know almost nothing about packaging). Either that, or rename the libraries.

---

### Post by nilarimogard on 2011-11-03
> **jimbo99 said:**
> Because the gnome-fallback isn't gnome.  It is some awful crippled imitation masquerading as gnome developed by the gnome3 devs as a mechanism to fall back to in case gnome3 fails.

And how about you guys just making gnome2 available instead of screwing with how it is developed?  Just give us ppas and leave it at that.

Now it's less crippled thanks to indicator applet being ported to GTK3: [http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

---

### Post by cro on 2011-11-05
OK, I had to reinstall Ubuntu today, so I backed up my entire partition and tried the "Upgrade 11.10 to 11.04" route, which failed, so I just wiped the partition and re-installed 11.04.

Mate stopped working for me at all, which I attribute to the parlous state of my install (continuous upgrades, tweaks and hacks from 9.04 to 11.10 on the same machine will do that!). It got to the point where a complete recompile and resinstall of all components left me with a ate login, but no panels (even though mate-panel was running), and no way to reset them to default (the standard way using mateconftool-2 didn't work)

That said, the 11.10 upgrade had some major issues with regressions anyway:
* Mute/unmute button stopped working
* Mute button light stopped working
* Headphone jack detection stopped working
* Front-microphone jack detection stopped working
* Wireless indicator light stopped working
* fn keys stopped working
* Gnome shell would not load
* Unity would not load
* nVidia graphics would not auto-detect
* Boot up time was measured in the minutes
* Plymouth failed to work on shutdown, and on bootup showed a black screen.
* Compiz cube stopped working (there's a couple of bugs listed against this, but they're so low priority they've not been assigned to anyone yet)

I'm back to 11.04 with Gnome 2 now, have completely purged Unity from the machine, and have disabled the upgrade alert. I won't make the mistake of "upgrading" to 11.10 again.

Although it would be nice to upgrade to the new 3.x kernel.

---

### Post by ShinIori319 on 2011-11-06
I'm trying to build the environment, but looks like I'm getting troubles. I'm trying to build [COLOR=Red]mate-doc-utils[COLOR=Black] but make gets stuck on this:
[/COLOR][/COLOR]> Running xsldoc checks
Should I wait for this to take a while, or is something wrong?

---

### Post by alessandro on 2011-11-07
Hello,

I have successfully installed all the packages from amanas ppa. My problem is that there is no Mate session option in gdm (yes gdm, lightdm does no work here as it segfault).

I have also tried the startx/.xinitrc method desribed in the Arch wiki whith no luck.

Any idea?

---

### Post by Perberos on 2011-11-07
> **ShinIori319 said:**
> I'm trying to build the environment, but looks like I'm getting troubles. I'm trying to build [COLOR=Red]mate-doc-utils[COLOR=Black] but make gets stuck on this:
[/COLOR][/COLOR]
Should I wait for this to take a while, or is something wrong?

something wrong. I does testing, but I don't have idea why you have that problem.
Try to grab a precompiled package.

---

### Post by Amanas on 2011-11-07
> **alessandro said:**
> Hello,

I have successfully installed all the packages from amanas ppa. My problem is that there is no Mate session option in gdm (yes gdm, lightdm does no work here as it segfault).

I have also tried the startx/.xinitrc method desribed in the Arch wiki whith no luck.

Any idea?

I haven't uploaded mate-session-manager yet. Should be up within the next couple of days.

---

### Post by alessandro on 2011-11-08
> **Amanas said:**
> I haven't uploaded mate-session-manager yet. Should be up within the next couple of days.

Thanks Amanas, I will keep an eye on your ppa

---

### Post by alessandro on 2011-11-08
Amanas,

There is a problem with your mate-control-center:
```
$ sudo apt-get install mate-control-center 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mate-control-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2738 kB of archives.
After this operation, 10,5 MB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/amanas/mate-desktop/ubuntu/ oneiric/main mate-control-center i386 1.0.0-1ubuntu1ppa3 [2738 kB]
Fetched 2738 kB in 1s (2671 kB/s)              
(Reading database ... 304463 files and directories currently installed.)
Unpacking mate-control-center (from .../mate-control-center_1.0.0-1ubuntu1ppa3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mate-control-center_1.0.0-1ubuntu1ppa3_i386.deb (--unpack):
 trying to overwrite '/usr/share/mime/globs', which is also in package mate-file-manager 1.0.0-1ubuntu1ppa5
```

---

### Post by Amanas on 2011-11-08
> **alessandro said:**
> Amanas,

There is a problem with your mate-control-center:


I've believe I have fixed this. Give it another try.

---

### Post by glebihan on 2011-11-09
> **jimbo99 said:**
> Because the gnome-fallback isn't gnome.  It is some awful crippled imitation masquerading as gnome developed by the gnome3 devs as a mechanism to fall back to in case gnome3 fails.

And how about you guys just making gnome2 available instead of screwing with how it is developed?  Just give us ppas and leave it at that.

gnome2 and gnome3 are not compatible so there is no way to "just make gnome2 available". A ppa wouldn't help.

---

### Post by maxiecool2 on 2011-11-09
is there a debuging and logging option available
i dont have any panel bars showing no main menu and notification bar and no window bar

---

### Post by alessandro on 2011-11-09
> **Amanas said:**
> I've believe I have fixed this. Give it another try.

Thanks, it's ok now.

---

### Post by glebihan on 2011-11-09
> **maxiecool2 said:**
> is there a debuging and logging option available
i dont have any panel bars showing no main menu and notification bar and no window bar

I'm having the same issue. The thing is that there are actually no error messages at all.
The issue comes from themes (or something related to it).
Try launching mate-appearance-properties and selecting another theme (one for which there isn't a warning about the theme engine) and the panel should show up.
It seems that this is a conflict in either libgtk2 or cairo, but couldn't figure out exactly what yet.

---

### Post by maxiecool2 on 2011-11-09
great some progress, only one theme came up without an error.
and installed some themes!!
next point keying is not remembering wireless password

so far so good!!

---

### Post by CalcProgrammer1 on 2011-11-10
This is a great project!  Anyone tried to install this on Debian Testing?  I switched from Ubuntu because I hated Unity, and now Debian has dumped GNOME 3 upon its userbase.  With the entire universe of Linux falling to pieces, this project seems like the only solution.

---

### Post by Perberos on 2011-11-11
Hello there

I am searching a hosting to put mate debian packages (ubuntu compatible). A mirror one, with ftp access to update it quickly.
If interested, connect to freenode irc #mate.

Thankyou

EDIT: we got one

---

### Post by CalcProgrammer1 on 2011-11-11
I just followed your instructions at the beginning of the thread to install MATE.  It worked perfectly except for building mate-file-manager deb package, but it did install with make install.  I'm currently running Mate on Debian Wheezy 64 bit and it seems to play nicely with Xfce and GNOME 3 except for some default application misconfiguration (may be my Xfce changes though, Thunar is the default file manager and terminal is missing).

---

### Post by poo_22 on 2011-11-11
I just want to say thank you for doing this - it's very much needed because unity/gnome3 is sort of unusable imo. I think your project needs a website though. I'll do my best to spread the word.

---

### Post by Perberos on 2011-11-11
> **CalcProgrammer1 said:**
> I just followed your instructions at the beginning of the thread to install MATE.  It worked perfectly except for building mate-file-manager deb package, but it did install with make install.  I'm currently running Mate on Debian Wheezy 64 bit and it seems to play nicely with Xfce and GNOME 3 except for some default application misconfiguration (may be my Xfce changes though, Thunar is the default file manager and terminal is missing).

yes, it's exo.

---

### Post by Perberos on 2011-11-12
new mailing list
[https://sourceforge.net/p/matede/mailing-lists/]("https://sourceforge.net/p/matede/mailing-lists/")

---

### Post by ShinIori319 on 2011-11-13
Okay, I added [Amana's]("https://launchpad.net/%7Eamanas/+archive/mate-desktop") and [Karapetsa's]("http://mate.karapetsas.com:81/") repositories, and tried to install the packages. However, Synaptic tells me that I need to remove both GNOME and KDE, core packages like ubuntu-desktop, and I'm not really willing to risk breaking the whole system cause of that.

Some of the packages are:
[B]mate-notification-daemon [COLOR=Red](This happens in both Karapetsas' and Amanas' repositories)[/COLOR]
mate-display-manager [COLOR=Red](I haven't seen this package in Amanas' repo yet)[/COLOR]

EDIT: [/B]Now I have installed most of the packages listed in the topic's first posts, plus a few other extras, and I found some of the packages still conflict with GNOME's files:
> E: /var/cache/apt/archives/mate-applets_1.0.2-1_i386.deb: attempting to overwrite `/usr/share/omf/accessx-status/accessx-status-bg.omf', also found in the package gnome-applets-data 3.2.0-0ubuntu1
E: /var/cache/apt/archives/mate-media_1.0.3-1_i386.deb: attempting to overwrite `/usr/share/icons/hicolor/24x24/apps/multimedia-volume-control.png', also found in the package gnome-control-center-data 1:3.2.1-0ubuntu1I have also noticed that the Menus don't work the same way. The (MATE's) Menu Editor still displays GNOME's program groups, but MATE only displays some default groups, plus a "**[COLOR=DarkGreen]#hidden[/COLOR]**" one. Under **Places** there's only **Desktop**, **Home Folder**, **Bookmarks**, **Computer**, as well as hard drive units and extractable units (USB, CD/DVD...), as well as the **Recent documents**. There aren't entries for **Documents**, **Downloads**, **Pictures**, **Videos** or **Music**. (Unless it is disabled by default I guess)

MATE will not recognize GTK engines like Murrine, and thus these will  not work appropiately with some themes (like Ambiance/Radiance) and will  even cause the panels not to show. By changing the theme, the panels show back up, though. There are some applets missing in the Panels (I assume this is the **mate-applets** package, the one that came in Kara's repo conflict with GNOME like I mentioned before), and thus I have no notifications, Pidgin integration, or an user menu (the one with the username that contains options such as Shutdown). I could not find the MATE Control Center either.

Despite the bugs, I really think its going well. I really hope these conflicts and bugs get solved. I would help, but sadly I have no experience with programming.

---

### Post by Bert Mariën on 2011-11-14
Many Thanks!

I haven't tried MATE Desktop yet, but will do so very soon. I downloaded the ZevenOS-Mate, and soon Linux Mint 12 final also will have MATE.
Cannot wait.

---

### Post by maxiecool2 on 2011-11-15
[LEFT]best to let everyone know there is a few file error differences between  [Amana's]("https://launchpad.net/%7Eamanas/+archive/mate-desktop") and [Karapetsa's]("http://mate.karapetsas.com:81/") repositories, so far its pick one or the other. can we get some kind of [COLOR=#333333]collaboration between them?
[/COLOR][/LEFT]

---

### Post by ShinIori319 on 2011-11-15
> **maxiecool2 said:**
> [LEFT]best to let everyone know there is a few file error differences between  [Amana's]("https://launchpad.net/%7Eamanas/+archive/mate-desktop") and [Karapetsa's]("http://mate.karapetsas.com:81/") repositories, so far its pick one or the other. can we get some kind of [COLOR=#333333]collaboration between them?
[/COLOR][/LEFT]


And well, they both have their pros and cons.

Amana's repo is not complete yet. Karapetsa's one is slow as hell, and probably might be outdated right now.

---

### Post by spcwingo on 2011-11-15
Hi all, I just wanted to let you know that Karapetsa's repo, although slow, works.  Just to show that it does I have included a screenshot of a build that I did from an Oneiric command line install.  For those that do not want / can't do their own build, I plan on installing remastersys and running a dist backup to be released at a later date.  Keep in mind that this is all tentative and could change at any time according to my free time and/or work schedule.  Well, enough blabbing, on to the screenie!  :)

---

### Post by intheup on 2011-11-16
so... what distros can i download so i can try mate?

and i have one sugestion: change the default icons in menu-tray, like sound, ethernet, etc. make some icons like gnome3 by default.

sorry about my english

---

### Post by pqwoerituytrueiwoq on 2011-11-16
> **intheup said:**
> so... what distros can i download so i can try mate?

and i have one sugestion: change the default icons in menu-tray, like sound, ethernet, etc. make some icons like gnome3 by default.

sorry about my english
it is preinstalled in the linux mint 12 rc
access same was you would get into classic on natty

---

### Post by intheup on 2011-11-16
ok but i realy dont want gnome 3 at all... so.. im looking for some distro that has mate as default de without any other de.. just like an mate-spin.

is that any distro that does the job?

---

### Post by KBD47 on 2011-11-16
Well I've tried it out in the Mint 12 RC and it really feels unfinished. Couldn't get any volume control or even put a speaker/sound control icon on my desktop. Also no battery indicator and the wireless network indicator is running off of the page. I wish everyone well with this project, but at least in Mint 12 it needs much work.

---

### Post by KBD47 on 2011-11-16
Forgot to mention that font rendering in MATE also needs a bit of work.

---

### Post by spcwingo on 2011-11-16
> **intheup said:**
> ok but i realy dont want gnome 3 at all... so.. im looking for some distro that has mate as default de without any other de.. just like an mate-spin.

is that any distro that does the job?

Ask and ye shall receive:

[http://www.zevenos.com/download/zevenos-neptune-2]("http://www.zevenos.com/download/zevenos-neptune-2")

Look all the way down at the bottom of the page.  ;)

---

### Post by oldrocker99 on 2011-11-16
Linux Mint 12 RC (which I'm using now) comes with GNOME 3 and Mate, which is pretty good for a newish GUI; at least it shows the System menu!

---

### Post by Bert Mariën on 2011-11-16
> **intheup said:**
> ok but i realy dont want gnome 3 at all... so.. im looking for some distro that has mate as default de without any other de.. just like an mate-spin.

is that any distro that does the job?

Go and see at 
[http://www.zevenos.com/download/zevenos-neptune-2](http://www.zevenos.com/download/zevenos-neptune-2)

Neptune-2 Unofficial spin.

You have to search for it, but it is there.

I have installed it myself.


Edited: I just saw I came in second.
Sorry.

---

### Post by Bert Mariën on 2011-11-16
> **oldrocker99 said:**
> Linux Mint 12 RC (which I'm using now) comes with GNOME 3 and Mate, which is pretty good for a newish GUI; at least it shows the System menu!

Alas, I could not install it. Ubiquity hangs on my computer.
Hopefully this will be fixed with the final release.

---

### Post by sdavmor on 2011-11-16
> **spcwingo said:**
> Ask and ye shall receive:

[http://www.zevenos.com/download/zevenos-neptune-2]("http://www.zevenos.com/download/zevenos-neptune-2")

Look all the way down at the bottom of the page.  ;)

Looks good.  I shall test-drive that on one of my older low-RAM laptops today that is currently using lubuntu and see how it runs.

---

### Post by Bert Mariën on 2011-11-16
> **sdavmor said:**
> Looks good.  I shall test-drive that on one of my older low-RAM laptops today that is currently using lubuntu and see how it runs.

Do not expect too much for the time being.
It works, and it works well, but e.g. the config editor is very minimal. As so is the rest.

I assume this is going to change rather soon.

---

### Post by sdavmor on 2011-11-16
Caveat Emptor on the Neptune v2 with Mate.  The Live CD/Installer is in German so be aware of that before you get started. Not a show-stopper here but a hurdle nonetheless that may make some want to wait for Mate on ubuntu 11.10 to get a bit further along before diving in.

---

### Post by Perberos on 2011-11-16
copy paste on terminals, is evil

---

### Post by A_T on 2011-11-17
Hi just looking at the PPA here: [https://launchpad.net/~amanas/+archive/mate-desktop](https://launchpad.net/~amanas/+archive/mate-desktop)

Which packages do I need to install to have Mate running successfully  alongside gnome-shell and Unity?

---

### Post by Anastasis on 2011-11-18
[IMG]http://i947.photobucket.com/albums/ad313/Archangelos2010/mate-desktop.png[/IMG]

---

### Post by KBD47 on 2011-11-18
Looks like I may have to eat my words about MATE not being ready for prime time yet:
[http://forums.linuxmint.com/viewtopic.php?f=60&t=85146&p=497149#p497149](http://forums.linuxmint.com/viewtopic.php?f=60&t=85146&p=497149#p497149)

more info: OK, I actually have a working MATE desktop in Mint 12. Call me impressed :-)
MATE thread at Mint forum:
[http://forums.linuxmint.com/viewtopic.php?f=18&t=86026](http://forums.linuxmint.com/viewtopic.php?f=18&t=86026)

---

### Post by malspa on 2011-11-18
Looking at the last two screen shots (posted by Anastasis and KBD47) makes me wonder if there's any reason to use MATE instead of Xfce.

---

### Post by IcyEyeG on 2011-11-18
> **malspa said:**
> Looking at the last two screen shots (posted by Anastasis and KBD47) makes me wonder if there's any reason to use MATE instead of Xfce.
I prefer MATE for the following reasons:
- Can use a bunch of applets that aren't present in Xfce (Applications/Places/System menu, Force-quit application, Connect to server, just to name a few)
- Can use Caja (nautilus 2 fork)
- Can use Compiz without loosing windows decorations (not possible with xfwm4 decoration)

If Xfce gets a better Nautilus and Compiz integration and the applets get ported as plugins, then, as far as I'm concerned, MATE looses its purpose, because you can put Xfce looking like a Gnome 2.x session almost without difference in usability.

Regarding MATE, I've been testing it on a VM on Linux Mint 12 and looks great! :grin:  However, I found some problems with it:
- Can't see submenus - I installed the Ubuntu Studio packages and although I see the audio and video production submeus activated in Alacarte, they don't appear in the menu applet.
- There are applets missing like trash, indicator applet, system monitor, etc.
- When I activate compiz, windows border decoration gets stuck in Mint-X theme.

I also would like to know if it's possible to make Nautilus 3 as the default file manager in MATE, instead of Caja.

---

### Post by KBD47 on 2011-11-18
> **malspa said:**
> Looking at the last two screen shots (posted by Anastasis and KBD47) makes me wonder if there's any reason to use MATE instead of Xfce.

Yes, Mint menu :-)

---

### Post by malspa on 2011-11-18
> **IcyEyeG said:**
> I prefer MATE for the following reasons:
- Can use a bunch of applets that aren't present in Xfce (Applications/Places/System menu, Force-quit application, Connect to server, just to name a few)
- Can use Caja (nautilus 2 fork)
- Can use Compiz without loosing windows decorations (not possible with xfwm4 decoration)

Okay, thanks. Not sure that any of those would apply here. I do know that in Xfce you can easily create an icon to click on when you want to force-quit an app, but I usually use **xkill** anyway.

> **KBD47 said:**
> Yes, Mint menu :-)

Never warmed up to the Mint menu. Isn't that available in the Xfce version of Mint?

---

### Post by KBD47 on 2011-11-18
Yes, but the Xfce version of Mint is Debian, not as user friendly as the Ubuntu based versions.
 I'm actually a big fan of Xfce/Xubuntu and have it booting on my computer. I suggested a few months ago that Main Mint ought to go with Xfce. But I think there is potential in MATE and I hope it gets better and better.

---

### Post by jimrew111 on 2011-11-18
I have this problem every time I try to clone...

fatal: [https://github.com/Perberos/Mate-desktop-Environment.git/info/refs](https://github.com/Perberos/Mate-desktop-Environment.git/info/refs) not found:
did you run git update-server-info on the server?

any idea's ?:confused:

I really hate unity and g3-shell (fallback is pretty good :)).
and I saw this and I was like wow! wow! so I want to try it :guitar:.

---

### Post by jimrew111 on 2011-11-19
so will someone  tell me how to fix this???

---

### Post by Elfy on 2011-11-19
Thread moved to Other OS/Distro Talk.

---

### Post by IcyEyeG on 2011-11-19
> **malspa said:**
> Okay, thanks. Not sure that any of those would apply here. I do know that in Xfce you can easily create an icon to click on when you want to force-quit an app, but I usually use **xkill** anyway.


Yes, that's true, I use a panel launcher with xkill on xfce, but it's not as user friendly.

---

### Post by jimrew111 on 2011-11-20
when I run git to install I get this problem :fatal did you run git-update-server-info on the server? any idea's?:confused:

---

### Post by Anastasis on 2011-11-20
Perberos, the MATE desktop environment gets you respect, dude. Not even playin right now, man. You get straight up kudos for this, mate.

I cannot believe what I am seeing right now. The updates to Gnome 3 and MATE that are coming down the pike at this very hour from Linux Mint are something to see. It's almost being debugged and rewritten by the hour. Whether Gnome 3 works or not really isn't the question, because the Mint team is 'making' it work, like it's making MATE work. These dudes must be working around the clock right now.

I now actually have a functioning, multitasking, application oriented desktop again! Astounding work! Hats go off to Perberos first,  and also the Mint Mate team. You have single-handedly saved the Linux desktop.

I kid you not. I'm telling you, once MATE is ported to GTK3, it's game ovah. Unbelievable.

---

### Post by stefano-karapetsas on 2011-11-20
> **jimrew111 said:**
> when I run git to install I get this problem :fatal did you run git-update-server-info on the server? any idea's?:confused:

use git over ssh:

```
git clone git://github.com/perberos/Mate-Desktop-Environment.git
```

---

### Post by jimrew111 on 2011-11-20
Good job Perberos now I have a real desktop that a human can use:guitar:
5 stars for you :P :KS:KS:KS:KS:KS
game over for gnome 3.\\:D/

---

### Post by jimrew111 on 2011-11-20
grrr when I run ./configure --prefix=/usr
it gives me an error.

:configure: error: Package requirements (
                          libxml-2.0 >=2.6.12
                          libxslt    >= 1.1.8
                          rarian
                       (were not met:
                        
                     No packae 'rarian' found

stupid error need help.

---

### Post by Amanas on 2011-11-20
> **jimrew111 said:**
> grrr when I run ./configure --prefix=/usr
it gives me an error.

:configure: error: Package requirements (
                          libxml-2.0 >=2.6.12
                          libxslt    >= 1.1.8
                          rarian
                       (were not met:
                        
                     No packae 'rarian' found

stupid error need help.

Since you didn't list what package this error is from, I can't be sure of the exact rarian dependency, but try rarian-compat. If that doesn't work, you can give librarian0 or librarian-dev a shot.

---

### Post by jimrew111 on 2011-11-21
I don't know much about how to work that stuff. you need to tell me in depth how to get it working. btw how long do you think perb will keep up mate? a long time I hope.

---

### Post by Amanas on 2011-11-21
> **jimrew111 said:**
> I don't know much about how to work that stuff. you need to tell me in depth how to get it working. btw how long do you think perb will keep up mate? a long time I hope.

Which package are you trying to install?

---

### Post by jimrew111 on 2011-11-21
after I use git to git MATE and then I run  ./configure --prefix=/usr.
:configure: error: Package requirements (
                          libxml-2.0 >=2.6.12
                          libxslt    >= 1.1.8
                          rarian
                       (were not met:
                        
                     No packae 'rarian' found 

thats it nothing else.

---

### Post by &quot;Lex on 2011-11-21
What about an official thread on Mint's forum? Since Mate is goint to be in Mint Main 12, it could be useful.

---

### Post by jimrew111 on 2011-11-21
-.- no.
I thought someone would package it for ubuntu? like a repo?
and I just help from here thank you.

---

### Post by stefano-karapetsas on 2011-11-21
> **jimrew111 said:**
> I thought someone would package it for ubuntu? like a repo?
and I just help from here thank you.

see [https://github.com/perberos/Mate-Desktop-Environment/wiki/Download](https://github.com/perberos/Mate-Desktop-Environment/wiki/Download)
there are two repositories for ubuntu

---

### Post by jimrew111 on 2011-11-21
ok good :) 
I'm happy someone is bringing back g2. and when I install it then it will be my main UI FOREVER!! (not kidding at all) keep up the good work perberos :P

thank you :)

---

### Post by KBD47 on 2011-11-21
> **"Lex said:**
> What about an official thread on Mint's forum? Since Mate is goint to be in Mint Main 12, it could be useful.

There is a thread for MATE on Mint forum:
[http://forums.linuxmint.com/viewtopic.php?f=18&t=86026](http://forums.linuxmint.com/viewtopic.php?f=18&t=86026)

---

### Post by KBD47 on 2011-11-21
I'm impressed at how quickly this project has come together. I think it needs just a few things to put it in the same league as other desktops. How difficult is it to get nice font rendering in MATE? This is one thing I very much miss about Gnome 2, the font rendering was better. Right now MATE has about the same kind of font rendering I see in Puppy Linux, it is kind of weak. Power management needs to show up in the icon list on the panel. And volume control from the keyboard is needed. I think with a bit more polish MATE could stand up against any desktop. I don't want to sound like I'm being critical, I really like MATE, but I would love to see it improve in these areas. If I knew more about writing code I'd do it myself, but I have to depend upon you excellent developers.
Thanks!
KBD47

---

### Post by TransitMan on 2011-11-22
I 've got MATE running in Debian Testing and I must say, I am impressed.

I'll be watching this one for some time to come.

---

### Post by jimrew111 on 2011-11-23
someone sticky this thread.:guitar:

---

### Post by sfbi on 2011-11-24
Thank god, my favorite DE is back. Back from Xfce;)

---

### Post by jimrew111 on 2011-11-25
hah that's the way I feel too :)

---

### Post by ShinIori319 on 2011-11-25
I really love how is this project coming out. The items I've managed to install are working fine, but I still have problems.

1. The theme engines are not detected by the DM.
2. mate-notifications-daemon still tries to get me to uninstall KDE, GNOME and core system packages. I managed to install the one from the Linux Mint repos without problem, but it seems to be out of date already.

---

### Post by stefano-karapetsas on 2011-11-26
> **ShinIori319 said:**
> mate-notifications-daemon still tries to get me to uninstall KDE, GNOME and core system packages. I managed to install the one from the Linux Mint repos without problem, but it seems to be out of date already.

where did you get the conflicting mate-notification-daemon package?

---

### Post by ShinIori319 on 2011-11-26
> **stefano-karapetsas said:**
> where did you get the conflicting mate-notification-daemon package?
The one that did not conflict was from the Linux Mint repositories, but it's the out-of-date one.
The rest of the repos (Amana's Tridex's and yours) have a more up-to-date package, but it will not let me install without risking my actual KDE and GNOME installations.

---

### Post by sophia911 on 2011-11-27
Great Job . 
Thank you for sharing . I will try to test it .

---

### Post by Starks on 2011-11-27
MATE is ridiculously overhyped.

The GNOME 2 lineage is a dead-end for innovation.

---

### Post by mauvebic on 2011-11-27
> **Starks said:**
> MATE is ridiculously overhyped.

The GNOME 2 lineage is a dead-end for innovation.

As much as unity supporters dont want to hear criticism, yours is neither welcome here.

Besides, what are you afraid of?

----------

I usually don't get involved in OS stuff, but im afraid if not enough people get behind MATE, we wont have a viable desktop left. Let me know how i can help (i also speak/write English/French and Klingon)

---

### Post by spcwingo on 2011-11-27
> **Starks said:**
> MATE is ridiculously overhyped.

The GNOME 2 lineage is a dead-end for innovation.

Gnome-shell and Unity are both "ridiculously overhyped", as well.  Not all of us want change for the sake of change and are more than happy with our "dinosaur" of a desktop environment.  Have fun with your "innovation", I have to go get some actual work done in my non-innovative, dinosaur, desktop environment.

---

### Post by Perberos on 2011-11-27
Innovation come from brilliant minds, not from a desktop.

---

### Post by kansasnoob on 2011-11-27
> **jbicha said:**
> I agree with several of the more recent comments: it's much wiser to improve gnome-panel than to try to keep GNOME 2 alive.

Clement, I understand you are trying to please your users but porting the Mint Menu as either a GNOME Shell extension or a gnome-panel 3 compatible applet is actually going to be less headache, take less time, and be more sustainable than teaming up with one guy who's trying to do the impossible. Clement, I don't think you have the extra time and development energy to implement the co-installable GNOME 2 idea.

Here's the current status of gnome-panel as I see it. Very few GNOME developers actually use gnome-panel as their primary desktop (in fact I don't know of any). gnome-panel is still part of GNOME Core and is the official fallback environment. However, only minimal maintenance is being done on it so it continues to work but it's not really getting any improvements. At some unspecified time in the future, several GNOME developers would like to drop gnome-panel from GNOME Core. Additionally, I believe the GNOME developers would be very appreciate of any patches that improve the way gnome-panel works, especially as they don't have the time (or interest, honestly) in doing that work themselves but are happy to take volunteer contributions.

Huge benefits of contributing to gnome-panel upstream: Already existing code hosting, wiki, bugtracker, release schedule, Google juice, and distro inclusion (every distro already packages GNOME's gnome-panel). Official status instead of trying to gain acceptance for an obsolete and incompatible fork. Each applet that you port to
gnome-panel 3 has a good chance of being picked up by distros and you're probably not the only guy that's trying to get applets ported but good luck trying to convince distros to package your GNOME 2 thing. Here's a big one: if gnome-panel is being actively maintained then GNOME will not kill it, at the most it will drop from being GNOME Core to being community maintained.

Or you could try to keep the entirety of GNOME 2 around but GNOME has already killed it (in the same way that no one is going to bother keeping GNOME 3.2 alive once GNOME 3.4 is out). And GNOME 2 will look less and less appealing with time. What if users want to use the nicer looking gnome-control-center 3? Do you really plan to port all of the new chat protocols to Empathy 2? I hear Evolution 3 is quite a bit nicer than Evolution 2 was. Here's a hint for you: Generally speaking, you can't mix and match GNOME components that are different versions and still be happy....

If you still read this at all I just wanted to let you know that you were the inspiration behind this:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

---

### Post by Perberos on 2011-11-27
> **Starks said:**
> MATE is ridiculously overhyped.
I believe the same

---

### Post by stefano-karapetsas on 2011-11-27
> **ShinIori319 said:**
> The one that did not conflict was from the Linux Mint repositories, but it's the out-of-date one.
The rest of the repos (Amana's Tridex's and yours) have a more up-to-date package, but it will not let me install without risking my actual KDE and GNOME installations.

I think the bug is solved in tridex repository. The mate-notification-daemon provides and conflicts with notification-daemon. You need only one of them. You can use notification-daemon instead of mate-notification-daemon without problems.

---

### Post by bornagainpenguin on 2011-11-27
> **Starks said:**
> MATE is ridiculously overhyped.

The GNOME 2 lineage is a dead-end for innovation.

Funny...I was going to say the same thing--only with regards to Canonical's myopic obsession with Unity.

The only reason I'm at all hopeful about Linux these days is because of this project, the MATE desktop.  If it fails I give up on this Linux experiment that I've been doing for the last decade or so off and on.  More on in the last five years than ever in the sense that I currently run Lucid on nearly all the hardware I have.

I joined these forums almost from the moment they started.  Ubuntu was the first distro that ever "just worked" with most of my hardware and was the first to recognize the WiFi on my old HP laptop and I loved it for that despite the loss of battery life over Windows.  When I got my ASUS eeepc it was with Ubuntu in mind and I ended up making the choice to go with Ubuntu over Windows XP on it despite any battery losses because I simply worked better in its Gnome desktop.

Now Canonical wants to toss me and many others who have been using their distro out in the cold.  Why?  Because it thinks it can get new users by changing everything we liked into something we hate.  Worse, they're going out of their way to bolt down the changes and make any customization impossible.

That's fine, I wish Canonical well in its quixotic quest--I just have one question...  Are you guys sure you can get enough newbies to replace all of us old timers who are leaving?

--bornagainpenguin

---

### Post by vasa1 on 2011-11-27
> **bornagainpenguin said:**
> ...I just have one question...  Are you guys sure you can get enough newbies to replace all of us old timers who are leaving?

--bornagainpenguin

Rhetorical question?

---

### Post by mauvebic on 2011-11-27
> **bornagainpenguin said:**
> 

That's fine, I wish Canonical well in its quixotic quest--I just have one question...  Are you guys sure you can get enough newbies to replace all of us old timers who are leaving?

--bornagainpenguin

> **vasa1 said:**
> Rhetorical question?

Seriously, the only thing keeping me with linux is XFCE, let's hope they don't screw it up, unity and gnome shell make XP look good.

---

### Post by ShinIori319 on 2011-11-27
> **stefano-karapetsas said:**
> I think the bug is solved in tridex repository. The mate-notification-daemon provides and conflicts with notification-daemon. You need only one of them. You can use notification-daemon instead of mate-notification-daemon without problems.

Nope. It still wants me to uninstall KDE and GNOME in order to update that package. I managed to update the rest of the packages that needed it without problems though.

These are the packages it wants me to remove:
> [COLOR=Red][B]gnome
gnome-core
kde-full
kde-plasma-desktop
kde-plasma-netbook
kde-standard
kde-window-manager
kde-workspace
kde-workspace-bin
kdeartwork
kdebase-workspace
kscreensaver
kscreensaver-xsavers
notification-daemon [COLOR=SeaGreen](I guess I should expect this one somewhat, but the one from Linux Mint installed without problems)[/COLOR]
notify-osd
plasma-desktop
plasma-netbook
plasma-widgets-workspace
ubuntu-desktop[/B][/COLOR]And trying to remove the package also wants me to remove these:
> [B][COLOR=Red]mate-core
mate-desktop-environment
mate-power-manager[/COLOR][/B]Also, I lol'd at what I just found:

---

### Post by stefano-karapetsas on 2011-11-27
> **ShinIori319 said:**
> Nope. It still wants me to uninstall KDE and GNOME in order to update that package

can you tell me which distro are you using? and your /etc/apt/sources.list ? I like to solve this issue. Thanks :)

---

### Post by ShinIori319 on 2011-11-27
> **stefano-karapetsas said:**
> can you tell me which distro are you using? and your /etc/apt/sources.list ? I like to solve this issue. Thanks :)
I'm using Ubuntu 11.10. And this is my sources.list file:
```
[COLOR=SeaGreen]# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb-src http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security multiverse
# deb http://ppa.launchpad.net/openmetaverse/ppa/ubuntu lucid main

# Repository for SecondLife.

# deb http://archive.ubuntu.com/ubuntu lucid main
# deb-src http://archive.ubuntu.com/ubuntu lucid main
# deb http://archive.ubuntu.com/ubuntu lucid universe
# deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu oneiric-backports restricted main multiverse universe
# deb http://www.vollstreckernet.de/ubuntu/ intrepid amule-stable
# deb-src http://www.vollstreckernet.de/ubuntu/ intrepid amule-stable
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
# deb http://mozilla.debian.net/ squeeze-backports iceweasel-release #Iceweasel Repository
# deb http://backports.debian.org/debian-backports squeeze-backports main #Debian Squeeze Repo
# deb http://packages.linuxmint.com/ lisa main upstream import #Linux Mint 12 repo
# deb-src http://packages.linuxmint.com/ lisa main upstream import #Linux Mint 12 Repo (src)
deb http://lumiera.org/debian/ maverick experimental
deb-src http://lumiera.org/debian/ maverick experimental
# deb http://tridex.net/repo/ubuntu oneiric main #Tridex's Repo for MATE
# deb-src http://tridex.net/repo/ubuntu oneiric main #Tridex's Repo for MATE (src)[/COLOR]

```
I don't see Amana's repo here. I think it would be somewhere in /etc/apt/sources.list.d

---

### Post by beew on 2011-11-27
> **mauvebic said:**
> Seriously, the only thing keeping me with linux is XFCE, let's hope they don't screw it up, unity and gnome shell make XP look good.

In your opinion. I think "Quixotic" (to quote bornagainpenguin) is indeed the correct word for something like Mate. The whole code base is moving towards gtk3 so why keep gnome2 on life support? Let it die gracefully.

I am quite happy with Unity (with a few caveats) but I can see the value of an "old fashion" interface for people who are used to a certain way of work, there is definitely room here. When all major OSes are moving towards a more "tablet like" interface (though Unity isn't really) I definitely agree that there is value for projects that appear to be swimming against the tide and it is possible in Linux because of its diversity and lacks of central command. If you don't like Ubuntu, switch, if you don't like Unity and Gnome 3 don't use them. There are always choice and Canonical doesn't dictate terms. That is great and healthy.

But there are other options than to hang on to gnome 2. For example, more development in xfce, making a UI that looks like gnome2 but based on gnome3, the Mint shell (gnome 3 based). They just seem to  make a lot more sense.

---

### Post by bluexrider on 2011-11-27
> **ShinIori319 said:**
> Nope. It still wants me to uninstall KDE and GNOME in order to update that package. I managed to update the rest of the packages that needed it without problems though.

These are the packages it wants me to remove:
And trying to remove the package also wants me to remove these:
Also, I lol'd at what I just found:


seriously if you are going to all that trouble why not just install Mint 12?

---

### Post by beew on 2011-11-27
> **mauvebic said:**
> Seriously, the only thing keeping me with linux is XFCE, let's hope they don't screw it up, unity and gnome shell make XP look good.

 There is this meme that Unity haters are the advanced Linux users. I am sure some are, but many are probably just intermediate users who think they are advanced users. I don't think any self respecting umber Linux man(or woman) would throw a temper tantrum and say that if XXX company (in this case Canonical) doesn't give me what I want I will be quiting Linux and go back to the warm embrace of MicroSoft or Apple. The advanced user would probably contribute to some projects that he/she finds more suitable for his/her need or starts one, such is the spirit of Linux. Now for many of us this may not be feasible but then most of us aren't advanced users and don't fancy ourselves as such :)

---

### Post by mauvebic on 2011-11-27
> **beew said:**
> In your opinion. I think "Quixotic" (to quote bornagainpenguin) is indeed the correct word for something like Mate. The whole code base is moving towards gtk3 so why keep gnome2 on life support? Let it die gracefully.

I am quite happy with Unity (with a few caveats) but I can see the value of an "old fashion" interface for people who are used to a certain way of work, there is definitely room here. When all major OSes are moving towards a more "tablet like" interface (though Unity isn't really) I definitely agree that there is value for projects that appear to be swimming against the tide and it is possible in Linux because of its diversity and lacks of central command. If you don't like Ubuntu, switch, if you don't like Unity and Gnome 3 don't use them. There are always choice and Canonical doesn't dictate terms. That is great and healthy.

But there are other options than to hang on to gnome 2. For example, more development in xfce, making a UI that looks like gnome2 but based on gnome3, the Mint shell (gnome 3 based). They just seem to  make a lot more sense.

If people wanna keep gnome 2 let them, i dont see why it has to die other than the fact some people feel threatened by it's continued existence. I just cant picture a touch interface on my 24" screen, it looks ridiculous. Hopefully XFCE doesn't go down the same road, otherwise Mate will become alot more appealing (and ill be glad its still around).

---

### Post by jimrew111 on 2011-11-27
**XFCE will never be like gnome 3, it will allways be a **[B]traditional desktop.
read the about page on there site.... [http://www.xfce.org/about](http://www.xfce.org/about)
[/B]

---

### Post by KBD47 on 2011-11-27
I have used an iPad and I cannot imagine using Unity on one, it would be just as irritating to me on a tablet as a computer. I think that is the desktop heading for a dead end. I can actually imagine Gnome Shell on a tablet, and it would probably be fine there, but not on my computer, at least not without a bunch of extensions to make it usable as Mint is doing. I suspect LXDE, KDE, Xfce, and MATE will be around long after some others are gone. BTW it only goes to show how crazy the Gnome devs are that they cannot race quickly enough to get rid of the last sane computer desktop they made--Gnome Classic/Fallback.
KBD47

---

### Post by mauvebic on 2011-11-28
> **jimrew111 said:**
> **XFCE will never be like gnome 3, it will allways be a **[B]traditional desktop.
read the about page on there site.... [http://www.xfce.org/about](http://www.xfce.org/about)
[/B]

They say that now yes, but two years ago no one thought the powerful and productive gnome would turn into a bitchy obstructive fat chick.

> **KBD47 said:**
> I have used an iPad and I cannot imagine using Unity on one, it would be just as irritating to me on a tablet as a computer. I think that is the desktop heading for a dead end. I can actually imagine Gnome Shell on a tablet, and it would probably be fine there, but not on my computer, at least not without a bunch of extensions to make it usable as Mint is doing. I suspect LXDE, KDE, Xfce, and MATE will be around long after some others are gone. BTW it only goes to show how crazy the Gnome devs are that they cannot race quickly enough to get rid of the last sane computer desktop they made--Gnome Classic/Fallback.
KBD47

Please, every time some new gadget or technology comes out people claim it's the death of their predecessor. There will always be a  place for desktops, and people will eventually realize that local storage is a lot better than giving up control of your files to some cloud provider, which, like most .com at one time or another, could go belly up. Besides, with a lot of ISP's imposing draconian bandwidth caps and surcharges in my neck of the woods, the last thing i wanna do is start going through the internet to access my own files.

Tablets are nice for the consumption of media, but i dont see myself writing even a pragraph on a touchscreen keyboard, nor is it comfortable to constantly hold it up (or tilt your head down) to do it.

Netbooks/laptops are the happy medium, not quite as powerful as desktops, but not impotent as a tablet when it comes to getting real work done either.

and Desktops themselves, well, i haven't owned a TV or radio in years. I hardly remember what a commercial looks like (thank god). And my files are my own, not subject to every new piece of legislation imposed on online service providers and ISPs. My computer is my home cinema, my newspaper, and telecommunications.  (and thats why all the hype is on uber-expensive new gadgets with comparatively poor storage capacity, cuz they wont make money off you if you can save your content locally, they'd rather you constantly pay to maintain access)

Dont get me wrong, i dont agree in principal with piracy, but when the industry relies on planned obsolescence to make people re-purchase the same titles you bought in VHS as DVDs, and then a few years later doing it again with bluray, i have to take exception. Worse still, i did spend a small fortune buying my favorite titles on DVD, and after 2-3 years, half the discs dont play or skip. (but try getting them to ship you a new disc, they wont care that you already legally bought the title).

IMHO, ditching the traditional desktop interface was jumping the gun. Besides, do you really think OEMs are going to ditch iOS and Android in favor of Touch Ubuntu?

---

### Post by vasa1 on 2011-11-28
How much time is spent on the desktop? I spend most of my time using programs such as the browser or LibreOffice. The way people are going on, I get the feeling that the desktop is the end point.

---

### Post by bornagainpenguin on 2011-11-28
> **beew said:**
> There is this meme that Unity haters are the advanced Linux users. I am sure some are, but many are probably just intermediate users who think they are advanced users.

Huh?

I'm not sure where that meme started either.  Maybe its because those who have been around a little, have used Ubuntu for a longer period of time and are familiar with how it works, those people are the ones annoyed by the complete loss of their working knowledge at how to get around their desktop?  Think that might make sense?

> **beew said:**
> I don't think any self respecting umber Linux man(or woman) would throw a temper tantrum and say that if XXX company (in this case Canonical) doesn't give me what I want I will be quiting Linux and go back to the warm embrace of MicroSoft or Apple.

Why not?  Most of the time those types of people are the ones who already mastered those operating systems before coming to Linux in search of a better fit.  Why wouldn't they go back to the operating system they already know how to use rather than keep fighting with Linux?

You forget how many people distro hop before settling in on the distro that fits them best, when that distro stops working for them they may resume distro hopping or they may give it up as a bad bargain because they've tried the rest *already* and weren't impressed by them.

One of the biggest issues with Linux is the upgrade treadmill, you have to keep upgrading your *system* to keep getting your **application** upgrades.  Most of the time that works out alright, you get better hardware support, faster desktop performance, your applications gain new features and integrate into the desktop better, win-win.  Other times, such as this when Canonical has decided to force "Unity" and make it completely unconfigurable it can become a royal pain.

At least in those other operating systems I can continue to get newer applications without requiring a system upgrade.  I can configure things without having those configurations wiped out by a system update.  So why wouldn't such a person already capable in that other operating system go back to it if they find Canonical completely unreasonable, completely unwilling to allow user control of their desktops?

> **beew said:**
> The advanced user would probably contribute to some projects that he/she finds more suitable for his/her need or starts one, such is the spirit of Linux. Now for many of us this may not be feasible but then most of us aren't advanced users and don't fancy ourselves as such :)

Ah, but they ***are***!  That's what people in this thread are doing, testing out the changes here and contributing back bug reports.  Eventually I fully expect the MATE desktop to spawn its own distro, initially built on Ubuntu but perhaps eventually rebasing itself on Debian proper.  That seems to be a trend lately, I wonder why...

--bornagainpenguin

---

### Post by KBD47 on 2011-11-28
I think one of the smartest things Ubuntu has done is to make 5 year Long Term Support releases starting next Spring. And one of the smartest things Mint has done is to embrace MATE including it in their distribution.
KBD47

---

### Post by bluexrider on 2011-11-28
> **KBD47 said:**
> I think one of the smartest things Ubuntu has done is to make 5 year Long Term Support releases starting next Spring. And one of the smartest things Mint has done is to embrace MATE including it in their distribution.
KBD47

Its going to be nice with 12.04 LTS cause I'm ready for a upgrade on my box. This will be the time to do it.

We'll see how far Mint gets with Mate. I was in the forums yesterday and OMG the mods that they are doing should have been in the release not after.

---

### Post by KBD47 on 2011-11-29
I guess I'm willing to cut Mint some slack because of how hard they are trying to Make Gnome 3 usable, and at the same time trying to keep a traditional desktop with MATE. I would have been more willing to cut Ubuntu some slack if they had only let users modify and move Unity. Take a look at both of those scenes and you can see how hard Mint is trying to please their users. But we have both Lubuntu and Xubuntu so I don't get too disgusted with Ubuntu :-)

---

### Post by Israeru on 2011-11-29
Wow tenia que ser un latino el que saliera con un proyecto de rescate de el maravilloso y juicioso Gnome 2. 

Espero que este proyecto siga rindiendo frutos y siga provocando justas discusiones sobre lo que queremos los usuarios vs lo que quiere imponernos canonical y la gente de gnome3

---

### Post by yagogak on 2011-11-30
Hi All

is there a sample /usr/share/xsessions/mate.desktop 
The build is sucessful but i can't run mate now.

---

### Post by spcwingo on 2011-12-05
I just wrote a small script to be used when building up a Mate desktop from a command line install (either from the mini.iso or from the alternate CD).  To use the script just install the command line system then run these commands after logging in to your new install (after reboot, of course).

```
wget -O install_mate.sh http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV
```

followed by:

```
chmod +x ./install_mate.sh
```

then:

```
./install_mate.sh
```

Profit!  ;)

Now for the fun disclaimers...remember, I am not responsible for any and/or all damage to your system (although this works perfectly fine for me).  YMMV

EDIT:  This is only for Oneiric officially, although I have begun testing this same repo on Precise...all's well so far.

---

### Post by ShinIori319 on 2011-12-06
I am amazed. Perhaps this is a good moment to switch to MATE as my default desktop environment.
I managed to remove the MATE notification daemon without conflicting anymore with anything (Ubuntu's daemon works just fine on MATE), but now I have run across another issue. The panels.

They seem to look just fine if I switch theme from the default-old school one to one, like for example, Ambiance. But upon rebooting/relogging, they won't load anymore unless I switch back to the default theme.

---

### Post by Perberos on 2011-12-08
Hello there. I fixed the keybinding problem. It was a recently GTK update that broke the key detect code. Now it work fine. The version with the fix is in mate-control-center and mate-settings-daemon on 2011.12.08

---

### Post by ShinIori319 on 2011-12-17
I have a question.
I just found out the Indicator applet for MATE, and it is a MUST if I am going to switch to MATE as my main Desktop Environment. However, it is only a source.
My question is this: I have the Indicator applet ports for GNOME Fallback, and obviously the one that comes with Unity. So... if I compile and "sudo make install" it, would it cause any conflict with the other two?
Same goes for the MATE Menu Editor. (Since MATE Menus seems to have a different config than GNOME Menus)

---

### Post by sdavmor on 2011-12-20
Just added MATE to Software Sources (tridex repo). Installed it, logged out of Ubuntu Classic. Selected MATE. Logged back in and voila! I have my old Gnome2 desktop. Been using it for a couple of hours with no glitches.  Other than fonts seem not as crisp, but that may change if I play around with some settings. This is a very impressive fork. Well done. (applause)

---

### Post by Perberos on 2011-12-20
I do not know the current state of the ubuntu's indicator applet. It's on the repo, but I do not know if it work (I do not use ubuntu)

if the panel do not show, it's because your are not using 2.24.8 or up
(bug issue: [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/889019](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/889019))

If problems with the keybinding of power, session and media (like volume), it's because is missing mate-power-manager, mate-screensaver and compile mate-settings-daemon with pulseaudio support.

---

### Post by Perberos on 2011-12-20
the menu bugs/issues are still under development.

---

### Post by enigmaster on 2011-12-27
Thank you Perberos and contributors for your great job! I'm still on Gnome 2.30.2 on both Ubuntu Lucid and Debian Squeeze, but already appreciating your efforts to keep up to date this great environment, and sure I'll use it when I'll need to upgrade!

---

### Post by stefano-karapetsas on 2011-12-28
> **ShinIori319 said:**
> I have a question.
I just found out the Indicator applet for MATE, and it is a MUST if I am going to switch to MATE as my main Desktop Environment. However, it is only a source.


I packaged mate-indicator-applet. It's in the tridex repository. You need to install indicator-*-gtk2 packages to have indicators.

---

### Post by ShinIori319 on 2012-01-02
> **stefano-karapetsas said:**
> I packaged mate-indicator-applet. It's in the tridex repository. You need to install indicator-*-gtk2 packages to have indicators.
I managed to install all the GTK2 indicators and the **mate-indicator-applet** package. I have this applet available now, although it is telling me that there are no indicators installed, even with the **indicator-*-gtk2** packages installed.

These are the packages I installed.
[B]mate-indicator-applet
indicator-sound-gtk2
indicator-appmenu-gtk2
indicator-datetime-gtk2
indicator-messages-gtk2
indicator-application-gtk2
indicator-session-gtk2

[/B]Also, been wanting to report some other bug. Upon logging off, there's a chance the desktop environment will not save the settings. It has happened more when using "Log off" than "Shut down"

---

### Post by davethewave83 on 2012-01-12
> **spcwingo said:**
> I just wrote a small script to be used when building up a Mate desktop from a command line install (either from the mini.iso or from the alternate CD).  To use the script just install the command line system then run these commands after logging in to your new install (after reboot, of course).

```
wget -O install_mate.sh http://goo.gl/JoNRI
```

followed by:

```
chmod +x ./install_mate.sh
```

then:

```
./install_mate.sh
```

Profit!  ;)

Now for the fun disclaimers...remember, I am not responsible for any and/or all damage to your system (although this works perfectly fine for me).  YMMV

EDIT:  This is only for Oneiric officially, although I have begun testing this same repo on Precise...all's well so far.


this gives me a internal server error 500 
Resolving goo.gl... 173.194.33.44, 173.194.33.32, 173.194.33.45, ...
Connecting to goo.gl|173.194.33.44|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV](http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV) [following]
--2012-01-12 08:20:36--  [http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV](http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV)
Resolving ubuntuone.com... 91.189.89.205, 91.189.89.204
Connecting to ubuntuone.com|91.189.89.205|:80... connected.
HTTP request sent, awaiting response... 500 Internal Server Error
2012-01-12 08:20:37 ERROR 500: Internal Server Error.

---

### Post by spcwingo on 2012-01-12
> **davethewave83 said:**
> this gives me a internal server error 500 
Resolving goo.gl... 173.194.33.44, 173.194.33.32, 173.194.33.45, ...
Connecting to goo.gl|173.194.33.44|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV](http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV) [following]
--2012-01-12 08:20:36--  [http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV](http://ubuntuone.com/6ttviwLzXXRNTAMW6KS7TV)
Resolving ubuntuone.com... 91.189.89.205, 91.189.89.204
Connecting to ubuntuone.com|91.189.89.205|:80... connected.
HTTP request sent, awaiting response... 500 Internal Server Error
2012-01-12 08:20:37 ERROR 500: Internal Server Error.

That just means that the server (UbuntuOne) hosting my script was having problems at the time that you tried to wget it.  I would suggest trying again.  Let me know if it works now or not.

---

### Post by bongmaster2 on 2012-01-17
are play pause next/prev track hotkeys working for you?
for me they stopped working some time ago.

im runing latest tridex repos on 2 machines.

---

### Post by spcwingo on 2012-01-17
> **bongmaster2 said:**
> are play pause next/prev track hotkeys working for you?
for me they stopped working some time ago.

im runing latest tridex repos on 2 machines.

Yes, they're working on my test laptop (HP DV4000 running Ubuntu 12.04 Alpha 2).  The weird part is that they just have started working as of about a week or two ago.

---

### Post by Amanas on 2012-01-18
Please report all bugs to [the mate-desktop github]("https://github.com/mate-desktop") from now on. We are no longer using Perberos' github issues page. More info can be found [here]("http://mate-desktop.org/2012/01/18/reporting-bugs/").

Thanks.

---

### Post by benedictbrown on 2012-01-25
I've just installed mate on oneiric from the tridex PPA.  I'm thrilled that gnome 2.x has been forked for ongoing maintnance, but I can't get mate-panel to run properly.  It reserves space but doesn't display.

I've found various posts about this around the web from late 2011 that seem to conclude it's (a) a conflict with the murrine theme engine, and (b) should be fixed.  Has that updated version been packaged through tridex?  On my system tridex's mate-panel doesn't work with any theme I've tested, including nodoku that was reported to work.  I've tested it under the full mate environment and with mate-panel running under lxde.

Many thanks,
Benedict Brown

---

### Post by Amanas on 2012-01-26
> **benedictbrown said:**
> I've just installed mate on oneiric from the tridex PPA.  I'm thrilled that gnome 2.x has been forked for ongoing maintnance, but I can't get mate-panel to run properly.  It reserves space but doesn't display.

I've found various posts about this around the web from late 2011 that seem to conclude it's (a) a conflict with the murrine theme engine, and (b) should be fixed.  Has that updated version been packaged through tridex?  On my system tridex's mate-panel doesn't work with any theme I've tested, including nodoku that was reported to work.  I've tested it under the full mate environment and with mate-panel running under lxde.

Many thanks,
Benedict Brown

The gtk patch that fixes the murrine theme engine is not available in oneiric.

---

### Post by sdavmor on 2012-01-31
> **spcwingo said:**
> I just wrote a small script to be used when building up a Mate desktop from a command line install (either from the mini.iso or from the alternate CD).  To use the script just install the command line system then run these commands after logging in to your new install (after reboot, of course).

```
wget -O install_mate.sh http://goo.gl/JoNRI
```

followed by:

```
chmod +x ./install_mate.sh
```

then:

```
./install_mate.sh
```

Profit!  ;)

Now for the fun disclaimers...remember, I am not responsible for any and/or all damage to your system (although this works perfectly fine for me).  YMMV

EDIT:  This is only for Oneiric officially, although I have begun testing this same repo on Precise...all's well so far.

I had to reinstall 11.10 from scratch due to a hard drive crash.  So I tried this out as soon as I had 11.10 Unity up and running.  Worked just like downtown in the big city!  (applause)

---

### Post by spcwingo on 2012-01-31
> **sdavmor said:**
> I had to reinstall 11.10 from scratch due to a hard drive crash.  So I tried this out as soon as I had 11.10 Unity up and running.  Worked just like downtown in the big city!  (applause)

Thanks, I'm glad that you found it useful.  :)

---

### Post by sdavmor on 2012-01-31
> **spcwingo said:**
> Thanks, I'm glad that you found it useful.  :)

Seriously useful.  Your scripting saved me a bunch of time and it put it all together in a very clean straightforward way. Instead of fiddling around I was able to get on with recovery of data from the damaged drive. Nice. My dad has been using the Gnome 3 fallback on 11.10 but not for much longer. I'll point him to this script today so he can put the Mate desktop on his machine. "And there was much rejoicing...". :D

---

### Post by spcwingo on 2012-02-05
For those interested, I have created an install-able Ubuntu Oneiric live CD with ONLY the MATE Desktop Environment.  It can be downloaded here:

[http://ubuntuone.com/7Jc21BRUktEUku9khruNBs]("http://ubuntuone.com/7Jc21BRUktEUku9khruNBs")

After extracting the 7zip archive please have a look at the README.txt before firing it up.

Okay, okay, enough babble.  How about a screenie?  :)

EDIT:  BTW, I threw this spin together in one day, so don't expect too much.  ;)

---

### Post by Virus666 on 2012-02-10
> **spcwingo said:**
> For those interested, I have created an install-able Ubuntu Oneiric live CD with ONLY the MATE Desktop Environment.  It can be downloaded here:

[http://goo.gl/XwfMY](http://goo.gl/XwfMY)

After extracting the 7zip archive please have a look at the README.txt before firing it up.

Okay, okay, enough babble.  How about a screenie?  :)

EDIT:  BTW, I threw this spin together in one day, so don't expect too much.  ;)

Good job! :-) Can it be installed via USB stick?

---

### Post by spcwingo on 2012-02-10
> **Virus666 said:**
> Good job! :-) Can it be installed via USB stick?

Yes!  I have installed on two systems so far via USB flash (I used Multisystem to write the image although I'm sure something like unetbootin will work also).

---

### Post by bornagainpenguin on 2012-02-12
> **spcwingo said:**
> For those interested, I have created an install-able Ubuntu Oneiric live CD with ONLY the MATE Desktop Environment.  It can be downloaded here:

[http://goo.gl/XwfMY]("http://goo.gl/XwfMY")

After extracting the 7zip archive please have a look at the README.txt before firing it up.

Okay, okay, enough babble.  How about a screenie?  :)

EDIT:  BTW, I threw this spin together in one day, so don't expect too much.  ;)

Also giving it a download now in hopes of using it on my eeepc!

--bornagainpenguin

---

### Post by spcwingo on 2012-02-13
For those that have tried my remix, please let me know how it turned out for you.  I have very limited test hardware and would like to know if there is any show-stopping issues.  Thanks.

---

### Post by Xpander69 on 2012-02-14
been using MATE about 2 months now on Mint 12
and i must say its damn stable atm.
there were few issues at the beginning but atm no issues and old gnome2 panel applets are quite easy to compile for MATE also.

Keep up the good work there! :popcorn:


[http://dl.dropbox.com/u/28788188/Screenshot%20at%202012-02-06%2018%3A22%3A10.png](http://dl.dropbox.com/u/28788188/Screenshot%20at%202012-02-06%2018%3A22%3A10.png)

---

### Post by sdavmor on 2012-03-01
> **spcwingo said:**
> For those that have tried my remix, please let me know how it turned out for you.  I have very limited test hardware and would like to know if there is any show-stopping issues.  Thanks.

What would be useful to me is this MATE remix tied to the Alternate install CD.  I need that because of issues I have run into doing RAID setups.  So having an install CD that doesn't bring the Unity baggage with it when setting up a RAID system would be excellent. I'm going to try this remix now.  If there's any issues I'll let you know. One thing I did run into before was issues with the ATI graphics (and compiz on Unity) once I installed MATE. Graphics went all glitchy and double-vision -- quite like being *very* drunk. Deactivating the proprietary driver seemed to solve it temporarily. And after applying some updates it seemed to go away permanently. But it would be nice not to have to deal with any of that stuff.

---

### Post by MZ250Supa5 on 2012-03-04
Maté &#8211; a desktop for human beings... ?

With the imminent arrival of Ubuntu 12.04 it's crucial that I have a LTS version that I can use.  I have the beta on a CD that I have run live, and I'm sure it's a great tablet/mobile phone interface, (not that I'm an expert on these things - my mobile is a 13 yr old Philips C12, simple, intuitive and does more than I want it to: it receives SMS messages) but not good for a desktop.  I am awaiting the release of the Maté 12.04 ppa so that I can experiment pending full implementation of it when 10.04 is no longer suported, (or sooner if Maté matures sooner and includes a lot of the bells and whistles that were available in Gnome 2.32)

I migrated to Linux from Windows some three and a half years ago, initially trying out several different distros.  I settled on Ubuntu as I intuitively liked the Gnome 2 DE.  It's demise in Ubuntu and the prospect of being forced to accept a dumbed down desktop had made me consider switching distros, yet all suffered to a greater or lesser degree in having adopted what the devs in their arrogance had decided people wanted in terms of the DE used.  Okay, this may not apply (yet) XFCE or LXDE, (which I use on my laptop - nice, but not as many bells and whistles as Gnome 2.32 and hardly any Welsh language localisation available - and it's blue as default!).  

The Maté project will have my support.

---

### Post by bornagainpenguin on 2012-03-05
> **spcwingo said:**
> For those that have tried my remix, please let me know how it turned out for you.  I have very limited test hardware and would like to know if there is any show-stopping issues.  Thanks.

It was crashy and painful to use.  This is less a reflection on your remix and the MATE desktop and more of an indicator of how crappy Ubuntu has grown over the years.  I haven't really been happy with any major Ubuntu releases since Hardy on my eeepc, since every release since then seems to have introduced stupid bugs and removed useful features one after the other.

I have managed to get Lucid running to a degree but I'm beginning to think I will be migrating to Debian once Lucid is no longer supported.  Once they switch to Gnome Shell, I'm hoping MATE will have been completed and can be used instead.

--bornagainpenguin

---

### Post by spcwingo on 2012-03-06
> **bornagainpenguin said:**
> It was crashy and painful to use.  This is less a reflection on your remix and the MATE desktop and more of an indicator of how crappy Ubuntu has grown over the years.  I haven't really been happy with any major Ubuntu releases since Hardy on my eeepc, since every release since then seems to have introduced stupid bugs and removed useful features one after the other.

I have managed to get Lucid running to a degree but I'm beginning to think I will be migrating to Debian once Lucid is no longer supported.  Once they switch to Gnome Shell, I'm hoping MATE will have been completed and can be used instead.

--bornagainpenguin

Thanks for the feedback.  I agree that the bugginess of Ubuntu releases has become more widespread, but we can all hope against hope that 12.04 will be better (I've been testing and bug reporting since Alpha 1).  I'm sorry that it didn't perform for you, but I will be giving this another whirl when 12.04 releases pending a repo from the MATE devs.

---

### Post by VanR on 2012-03-07
Maybe I did something wrong, but I downloaded this and burned a CD and it wouldn't boot when I tried to run it live. Anyone got any idea what I did wrong? I'm not new to burning disc and running it live to check out distros.

---

### Post by spcwingo on 2012-03-07
> **VanR said:**
> Maybe I did something wrong, but I downloaded this and burned a CD and it wouldn't boot when I tried to run it live. Anyone got any idea what I did wrong? I'm not new to burning disc and running it live to check out distros.

Did you check the md5 hash provided in the archive?  Also, did you read the README.txt also provided in the archive?  If the answer is yes to both questions, try booting, but this time at the boot prompt edit the kernel line to remove "quiet splash".  If it stops again please let me know where it stops.  Sincerely, I appreciate the feedback and I hope I can help to get you going so you can at least try my little spin.  :)

---

### Post by Drakonis on 2012-03-18
> **spcwingo said:**
> For those interested, I have created an install-able Ubuntu Oneiric live CD with ONLY the MATE Desktop Environment.  It can be downloaded here:

[http://goo.gl/XwfMY]("http://goo.gl/XwfMY")

After extracting the 7zip archive please have a look at the README.txt before firing it up.

Okay, okay, enough babble.  How about a screenie?  :)

EDIT:  BTW, I threw this spin together in one day, so don't expect too much.  ;)

So does this mean we should expect to see a MUbuntu in the future?  I hope so because I'm still running 10.04 simply because I can't stand Unity.

---

### Post by spcwingo on 2012-03-18
> **Drakonis said:**
> So does this mean we should expect to see a MUbuntu in the future?  I hope so because I'm still running 10.04 simply because I can't stand Unity.

Ha! I wish.  This is just a small project that I did to combat boredom/my own testing purposes.  I just like to share my work with others.  :)

I, too, am still using Lucid on my main rig...simply for stability.

---

### Post by Drakonis on 2012-03-18
> **spcwingo said:**
> Ha! I wish.  This is just a small project that I did to combat boredom/my own testing purposes.  I just like to share my work with others.  :)

I, too, am still using Lucid on my main rig...simply for stability.

Too bad, I'd definitely be switching distros if it was.

---

### Post by rotata on 2012-04-14
After yet another disaster "update" with Ubuntu, I installed Linux Mint. On a lark, I clicked on Mate. Hey, I like it! Now my netbook looks the way "I" want it to look.

---

### Post by jbicha on 2012-04-14
> **bornagainpenguin said:**
> 
I have managed to get Lucid running to a degree but I'm beginning to think I will be migrating to Debian once Lucid is no longer supported.  Once they switch to Gnome Shell, I'm hoping MATE will have been completed and can be used instead.

--bornagainpenguin

Switching to Debian won't help you too much if you don't like GNOME 3. The current stable Debian release (squeeze) will only get security updates for one year after wheezy is released. Wheezy won't have Mate or GNOME 2 and will be released probably next winter.

---

### Post by shawnhcorey on 2012-04-15
If you're thinking of switching to Debian, consider [Linux Mint Debian Edition (LMDE)]("http://blog.linuxmint.com/?p=1967"). Linux Mint has recent came out with a new release candidate. It comes with MATE, a fork of the old GNOME 2, just in case you don't like GNOME 3. :)

---

### Post by KBD47 on 2012-04-15
I'm using MATE on the LMDE RC right now and am hard pressed to find any difference between MATE and Gnome 2. Back in the Fall MATE on Mint 12 felt very unfinished, not so now.
   Will Ubuntu 12.04 have MATE in the repos? Will users be able to install it through the software center? And finally, does Precise allow users to auto-login to other desktops, or must they manually login for other desktops?
From a happy MATE user.
KBD47

---

### Post by Myrddin Emrys on 2012-04-16
> **KBD47 said:**
> Will Ubuntu 12.04 have MATE in the repos? Will users be able to install it through the software center? 

Not the official repositories, but there's already a 12.04 repos on the developers' site. Add this to your system and you can use any of the standard tools, including the software centre, to install MATE:

[http://mate-desktop.org/](http://mate-desktop.org/)
[http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)
[http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/](http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/)

It's probably time I added those links to my signature...

---

### Post by KBD47 on 2012-04-16
> **Myrddin Emrys said:**
> Not the official repositories, but there's already a 12.04 repos on the developers' site. Add this to your system and you can use any of the standard tools, including the software centre, to install MATE:

[http://mate-desktop.org/](http://mate-desktop.org/)
[http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)
[http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/](http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/)

It's probably time I added those links to my signature...

Thanks! That last link is priceless and will save a lot of headaches on the message board for those who are updating Lucid but want nothing to do with Unity.
KBD47

---

### Post by spcwingo on 2012-04-24
I have written a new script to be used when building up from a Precise mini install.  You can use the script as folows:

From you newly installed mini system enter:

```
wget -O install_mate.sh http://ubuntuone.com/57jkIERnelnWEdytcHc8SA
```

then

```
chmod +x ./install_mate.sh
```

finally:

```
./install_mate.sh
```

I hope this helps someone.

[COLOR="Red"]Disclaimer:[/COLOR]
Although this works perfectly fine for me, YMMV.  I am in no way responsible for any/all damages to your system.

---

### Post by vDub2000 on 2012-04-26
I loved that Mate exists. I absolutely hate Unity and Mate has allowed me to make Ubuntu looked the way that it used to. However, I'm having a couple of issues with it and I was wondering if someone could help me. I'm currently running Ubuntu 12.04

1) When I changed the appearance to the Ambiance theme to match the normal colors of Ubuntu, it doesn't extend to the top and bottom panels so while the bar that contains the Applications, Places, and System menus are a new color, the top and bottom panels are still white.

2) Mate doesn't allow Firefox to change the desktop background. It stays the standard blue, unless I use one of the stock wallpapers already included with Ubuntu.

---

### Post by vDub2000 on 2012-04-26
I've also noticed that when using Mate, it has duplicated some of the program entries in the Applications menus.

---

### Post by Amanas on 2012-04-26
> **vDub2000 said:**
> 1) When I changed the appearance to the Ambiance theme to match the normal colors of Ubuntu, it doesn't extend to the top and bottom panels so while the bar that contains the Applications, Places, and System menus are a new color, the top and bottom panels are still white.

[https://bugs.launchpad.net/light-themes/+bug/986032](https://bugs.launchpad.net/light-themes/+bug/986032)

---

### Post by Simplicius on 2012-04-27
I've just installed Mate on Precise and like a commenter above I've found myself with a lot of duplicate things. For instance, in Applications->Accessories I have two Archive Managers and two calculators.

Also, according to synaptic I have lots of what to me (a noob!) look like duplicates, except for slightly different name (EOM instead of EOG, etc.

Question: is there a quick way to get rid of all unnecessary things now that I want to only keep Mate? How about I remove 'ubuntu-desktop'?

---

### Post by sdavmor on 2012-04-27
I feel no need to rush in to the 12.04 release.  As I did with 11.10 I'll give it a month or so before I think about upgrading to let any gremlins be dealt with. But once I do upgrade it will be nice to get to a LTS release with Mate/Gnome 2 and ignore Unity for a long time.

---

### Post by cshin9 on 2012-05-30
> **Drakonis said:**
> So does this mean we should expect to see a MUbuntu in the future?  I hope so because I'm still running 10.04 simply because I can't stand Unity.
We may want to bring back the original orange/brown theme from before Lucid while we're at it. :D

---

### Post by shawnhcorey on 2012-05-30
> **Drakonis said:**
> So does this mean we should expect to see a MUbuntu in the future?  I hope so because I'm still running 10.04 simply because I can't stand Unity.

There already is one at [Linux Mint]("http://www.linuxmint.com/"). It's based on Ubuntu and you can run MATE on it.

---

### Post by spcwingo on 2012-05-30
> **shawnhcorey said:**
> There already is one at [Linux Mint]("http://www.linuxmint.com/"). It's based on Ubuntu and you can run MATE on it.

There's also Snow Linux "Cream".  It's Ubuntu 12.04 based and comes ONLY with Mate.  :)

[http://www.snowlinux.de/]("http://www.snowlinux.de/")

---

### Post by frytek on 2012-06-03
I believe I still have my gnome 2 settings folder in my home directory. But when I installed Mint with Mate, the panels are gone except for the default one on the bottom.

Is there a way to import some settings? Just panel settings with icons of them would do. 

Probably I need to copy something ... but I have no clue. 

Can anybody help?

---

### Post by Dry Lips on 2012-06-06
> **spcwingo said:**
> There's also Snow Linux "Cream".  It's Ubuntu 12.04 based and comes ONLY with Mate.  :)

[http://www.snowlinux.de/](http://www.snowlinux.de/)

No, have a second look... It comes with cinnamon as well! What's really the difference between Snow Linux and Mint? Seems like there is little to tell Snow Linux apart from Cinnamon... Perhaps I'm wrong, I've never tried it...

---

### Post by wheeze on 2012-06-06
I'm happily running a custom MATE/Precise/Mint setup here, built to my spec starting from the mini.iso. Very snappy performance on this old machine.

I added the Mint Maya repo instead of the MATE Precise repo since I like some of the Mint tools and Mint has an updated version of mate-keyring. I know Clem is on the MATE team so it should be pretty well maintained there.

Does anyone know if Mint updates their repo when new/updated MATE packages come out?

---

### Post by spcwingo on 2012-06-06
> **Dry Lips said:**
> No, have a second look... It comes with cinnamon as well! What's really the difference between Snow Linux and Mint? Seems like there is little to tell Snow Linux apart from Cinnamon... Perhaps I'm wrong, I've never tried it...

The one little thing that I have noticed with Mint is that when you add PPAs you always end up getting 404s.  The reason being that Mint 13 lsb_release info yields "Maya" instead of "Precise" so you have to manually edit the entry in /etc/apt/sources.list.d/ to change it.  Snow Linux doesn't exhibit this behavior.  That's why, at the moment, I prefer Snow Linux over Mint.  I realize that is a small annoyance, but I also dislike the Mint specific apps.  IE:  Mint Menu, Mint Update, etc.

---

### Post by Dry Lips on 2012-06-07
> **spcwingo said:**
> The one little thing that I have noticed with Mint is that when you add PPAs you always end up getting 404s.  The reason being that Mint 13 lsb_release info yields "Maya" instead of "Precise" so you have to manually edit the entry in /etc/apt/sources.list.d/ to change it.

Just out of curiosity, what does the lsb_release have to do with PPAs? All my sources are listed as "precise" in my  /etc/apt/sources.list, with the exception of the mint repos...

---

### Post by BigBadJohn28 on 2012-06-07
> **spcwingo said:**
> I have written a new script to be used when building up from a Precise mini install.  You can use the script as folows:

From you newly installed mini system enter:

```
wget -O install_mate.sh http://ubuntuone.com/57jkIERnelnWEdytcHc8SA
```then

```
chmod +x ./install_mate.sh
```finally:

```
./install_mate.sh
```I hope this helps someone.

[COLOR=Red]Disclaimer:[/COLOR]
Although this works perfectly fine for me, YMMV.  I am in no way responsible for any/all damages to your system.


after doing all that I keep getting these errors.. any thoughts?

"Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
  404  Not Found [IP: 91.189.91.29 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
  404  Not Found [IP: 91.189.91.29 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources
  404  Not Found [IP: 91.189.91.29 80]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.29 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 42.1 kB in 9s (4,332 B/s)
W: GPG error: [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead."](*,)

---

### Post by spcwingo on 2012-06-07
> **Dry Lips said:**
> Just out of curiosity, what does the lsb_release have to do with PPAs? All my sources are listed as "precise" in my  /etc/apt/sources.list, with the exception of the mint repos...

For example I open a terminal and enter:

```
sudo add-apt-repository ppa:webupd8team/java
```

Instead of within the entry in /etc/apt/sources.list.d having:

```
deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main 
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
```

It will have:

```
deb http://ppa.launchpad.net/webupd8team/java/ubuntu maya main 
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu maya main
```

So when after adding the repo you try to:

```
sudo apt-get update
```

It will 404 because of the above mentioned issue.  YMMV, but this had been the case on my Mint 13 install (now overwritten).

---

### Post by spcwingo on 2012-06-07
> **BigBadJohn28 said:**
> after doing all that I keep getting these errors.. any thoughts?

"Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
  404  Not Found [IP: 91.189.91.29 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
  404  Not Found [IP: 91.189.91.29 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources
  404  Not Found [IP: 91.189.91.29 80]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.29 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 42.1 kB in 9s (4,332 B/s)
W: GPG error: [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.29 80]

W: Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead."](*,)

Please post the output of this command in a terminal:

```
cat /etc/apt/sources.list && cat /etc/apt/sources.list.d/*.list
```

---

### Post by frytek on 2012-06-27
> **spcwingo said:**
>  I also dislike the Mint specific apps.  IE:  Mint Menu, Mint Update, etc.

I have to say that I like it. As long as they do not remove standard gnome menu. **This is exactly how it is supposed to be done: an option, not a must.**
The main mistake of Canonical was to force people to use Unity. If this was only an option, I would use Ubuntu till now, instead of Mint.

---

### Post by madmax75 on 2012-07-11
MATE works very nicely in my Mint 13 installation. Couldn't be happier! \\:D/

The only thing it needs is some more themes (both desktop and MDM themes)... :D

So yeah, it's excellent!

---

### Post by kurt18947 on 2012-07-11
> **frytek said:**
> I have to say that I like it. As long as they do not remove standard gnome menu. **This is exactly how it is supposed to be done: an option, not a must.**
The main mistake of Canonical was to force people to use Unity. If this was only an option, I would use Ubuntu till now, instead of Mint.

No one is **forced** to use Unity.  I used Unity only long enough to install Gnome-shell/XFCE/Lxde/Cinnamon (I didn't install muffin) MATE etc. etc.

---

### Post by tedpome on 2012-09-08
Thank you Perberos, for setting up MATE. It is a very good desktop environment and builds on user skills and experience. Somehow Ubuntu forgot that humans have learning parameters and to waste experience with heedless innovation is a shame.
Thank you, tedpome

---

### Post by Linux_junkie on 2012-09-12
As Mate is a fork of Gnome 2 and can use all of Gnome 2 applications, are those same Gnome 2 applications still being developed?

I'm not talking about the Mate apps like Nautilus (or whatever its called under Mate) but other 3rd party apps for Gnome 2 (Mate).

---

### Post by wheeze on 2012-09-12
> **shawnhcorey said:**
> If you're thinking of switching to Debian, consider [Linux Mint Debian Edition (LMDE)]("http://blog.linuxmint.com/?p=1967"). Linux Mint has recent came out with a new release candidate. It comes with MATE, a fork of the old GNOME 2, just in case you don't like GNOME 3. :)

Clem from Mint just announced that the newest release of LMDE (UP5) will have a MATE-only version. The current LMDE release has MATE combined with Cinnamon, so you end up with a MATE/GNOME 3 mish-mash.

The new MATE-only version will be a welcome release!

---

### Post by Lyfang on 2012-09-13
> **Linux_junkie said:**
> As Mate is a fork of Gnome 2 and can use all of Gnome 2 applications, are those same Gnome 2 applications still being developed?

I'm not talking about the Mate apps like Nautilus (or whatever its called under Mate) but other 3rd party apps for Gnome 2 (Mate).
Plans could be to migrate Mate to GTK3. I doubt that GTK+ 2.x applications will be developed in the future. Currently however GTK+ 3.0 is much slower than GTK+ 2.x, see: [https://bugzilla.gnome.org/show_bug.cgi?id=655214](https://bugzilla.gnome.org/show_bug.cgi?id=655214)

---

### Post by tatsugama on 2013-08-11
I know this is an OLD thread but I just wanted to say thank you SO much for forking GNOME 2 to MATE! You saved me and I'm sure thousands of other people from being stuck with only GNOME 3. You have my deepest gratitude. Long live GNOME 2! Long live MATE! :p

---

