---
title: "Gnash 0.8.0 :)"
date: 2007-06-11
forum: Apple PPC Users
---

### Post by luckyd on 2007-06-11
The new Gnash 0.8.0 release with support for youtube is out.. Yah
The binaries will be comming out soon, if they arn't already in repositories...
If you just can't wait, you can grab the source here [ftp://ftp.gnu.org/pub/gnu/gnash/](ftp://ftp.gnu.org/pub/gnu/gnash/)

Yah for gnash

---

### Post by stmiller on 2007-06-11
Hey that's great news. I'll try it out shortly...

---

### Post by maxxum on 2007-06-12
Thanks for the info. I installed it (config and make) but I sill don't see youtube videos on firefox. Any ideas?

---

### Post by luckyd on 2007-06-12
DId you do "sudo make install"?
If you you didn't do it, do it and if you did, type > about:plugins into firefox and post the output.

---

### Post by maxxum on 2007-06-12
I did a make install and is appeared to be successful and when I type gnash in a terminal it gives various options to use with it. So it is installed I guess. However firefox does not know about its plugin.
The output of about:plugin in firefox is - 

Totem Web Browser Plugin 2.18.1
Windows Media Player Plug-in 10 (compatible; Totem)
DivXÂ® Web Player
QuickTime Plug-in 7.1.3

..and each of them have their associated media type listed below these headings.

---

### Post by stmiller on 2007-06-12
You have to compile with specific options. See this thread:

[http://ubuntuforums.org/showthread.php?t=460198](http://ubuntuforums.org/showthread.php?t=460198)

---

### Post by maxxum on 2007-06-12
okay, I installed agg2.5 (automake didn't work but make did). Then I configured gnash as:
```

./configure --enable-renderer=Agg --enable-media=GST

```

But it complained that if I want to enable klash, I need to have renderer as OGL (opengl) or else disable klash. Then I tried: 
./configure --enable-renderer=Agg --enable-media=GST --enable-renderer=OGL

which didn't work. Then I disabled klash:

 ./configure --enable-renderer=Agg --enable-media=GST --disable-klash

After this it gave an error that I need Gstreamer but also told me how to get it. I installed that library and after that the above configuration command went without error. However there were two warnings 1) I need Ming, 2) I need swfmill, both to run some tests. However I guess it should work without these too.
Now there are no errors but I still cannot see youtube videos.

---

### Post by stmiller on 2007-06-12
> **maxxum said:**
> 
After this it gave an error that I need Gstreamer but also told me how to get it. I installed that library and after that the above configuration command went without error. However there were two warnings 1) I need Ming, 2) I need swfmill, both to run some tests. However I guess it should work without these too.
Now there are no errors but I still cannot see youtube videos.

No, you need ming dev packages, I believe. Try other compile options, perhaps.

And after it compiles, it places the firefox plugin in /home/YOU/.mozilla/plugins/  or something like that. You might have to copy that plugin to the firefox plugin directory. 

Or just wait for a deb to come out. :)

---

### Post by maxxum on 2007-06-12
Well it says that libming is already the latest version. Also interestingly, I do not see the directory /home/ME/,mozilla .

---

### Post by stmiller on 2007-06-13
> **maxxum said:**
> Well it says that libming is already the latest version. Also interestingly, I do not see the directory /home/ME/,mozilla .

If the installer is complaining about ming, then you need to try and find what packages it needs. 
EDIT: I take that back- I see where it mentions ming for only running gnash tests.

And the gnash make install automatically puts the plugin in

/home/yourusername/.firefox/plugins

This is all in the gnash docs. I'm not making this up. :)

Type ./configure --help to see all options.

And I'm looking at my machine and it looks like I did fetch and compile swfmill from source. So I did do that. So it may be needed afterall.

I'm going to try and compile the new .8 release right now and see how it goes.

Anyways, you could wait for a ppc deb to come out. Check debian unstable or experimental.

---

### Post by stmiller on 2007-06-13
Okay I have success with the 0.8.0 release. It uses less CPU to playback youtube than the previous version from CVS.

I compiled with these options:

```
./configure --enable-renderer=Agg --enable-media=GST --disable-klash --disable-cygnal

```

My about: plugins in Firefox shows this:

```
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 - Gnash 0.8.0, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License . For more information about Gnash, see http://www.gnu.org/software/gnash.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

```

I think the default compile options (opengl) will be used for the deb releases, most likely. I need to read more to find out about the differences. So far, this is looking very good.

---

### Post by [censored] on 2007-06-13
wish it worked that easily for me. I'm stuck on ./configure. It insists I haven't got libming-dev installed, but dpkg insists that I do.

---

### Post by ssam on 2007-06-13
I found an easy way to compile/install it.

prevu is the tool the backporting team use, it lets you build feisty versions of packages in gutsy.

follow [https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu) to install and set up prevu. then run
```
prevu gnash
```
then launch synaptic, reload, and install gnash

youtube mostly work, apart from some graphical artifacts. (on a 1ghz G4)

---

### Post by stmiller on 2007-06-13
> **'[censored] said:**
> wish it worked that easily for me. I'm stuck on ./configure. It insists I haven't got libming-dev installed, but dpkg insists that I do.

What are the errors at the end of the make? I checked the gnash dev list, and some seem to have make errors at the end. The advice is to

cd gui

type 

make

then cd ..

and make

to continue the make.

---

### Post by [censored] on 2007-06-13
stmiller

>         WARNING: You need to have the Ming development and utilities packages
                 installed to run most of the tests in Gnash testsuite.
                 Install it from [http://ming.sourceforge.net](http://ming.sourceforge.net)
                 or .deb users: apt-get install libming-dev
        MTASC is /usr/bin/mtasc
        MTASC CLASSPATH is /usr/bin/std
        WARNING: You need to have the 'swfmill' tool installed
                 to run some of the tests in Gnash testsuite.
                 You can install it from [http://iterative.org/swfmill/](http://iterative.org/swfmill/)
        Z flags are: default include path
        Z libs are: -lz 

configure: error: Please install required packages


That's when I configure with ./configure --enable-renderer=Agg --enable-media=GST --disable-klash

Tried to make the stuff in gui/, but it didn't want to make.

---

### Post by kingmoffa on 2007-06-14
I can confirm it works on youtube if you manage to compile it. 

Upon having configure successfully complete, during the make process I had an error when the compile was looking for Intrinsic.h

I had to install  

sudo apt-get install  libxt-dev

To remedy.

Youtube works fine after a small amount of testing,  and although my cpu is pretty taxed the computer is still very much usable. (mac mini g4).

---

### Post by bieber on 2007-06-14
So, will we get an update through the update-manager in the near future?  Feisty *does* do real upgrades, and not just security fixes, right?

---

### Post by stmiller on 2007-06-14
You might be able to install the gutsy gnash packages, when 0.8.0 is updated there:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=gutsy&release=all)

---

### Post by Ububurns on 2007-06-15
I know this sounds impatient, but if three or so of you have the package compiled and working - 

Could someone just make a cheap and nasty checkinstall deb and post it up?  That would be great!

I am unable to compile it - I'm getting errors with libltdl3, boost, etc.

---

### Post by kugn on 2007-06-15
well one could change the repositories to gutsy, install just gnash, and then change it back them feisty =p

---

### Post by ssam on 2007-06-15
> **stmiller said:**
> You might be able to install the gutsy gnash packages, when 0.8.0 is updated there:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=gutsy&release=all)

the prevu method i posted above basically does that, but automatically recompiles them against the feisty libraries.

---

### Post by Ububurns on 2007-06-16
.

---

### Post by Ububurns on 2007-06-16
Here's an agg deb for anyone that wants it:

[Right click, save link as...]("http://filexoom.com/files/2007/5/2/72892/UbuntuPPC/agg_2.5-1_powerpc.deb")

---

### Post by [censored] on 2007-06-16
ssam tried that prevu method, exactly as you prescribed. At the end of it I just ended up with a deb for gnash 7.2, which probably works a bit more smoothly, but still won't play youtube.

---

### Post by stmiller on 2007-06-16
So get this: the Wii runs on a PowerPC Chip. And it has the Opera browser with flash!  Youtube, everything. So there is flash for PowerPC. I wonder if Nintendo developed it on their own? I'm going to hunt around google. It would be great to find a copy of that browser and flash and check it out...

Ok. It seems that the opera folks in developing Wii browser flash wrote it using the Adobe Flash 7 sdk, which you can pay Adobe to obtain:

[http://www.adobe.com/products/flashplayer_sdk/](http://www.adobe.com/products/flashplayer_sdk/)

[http://my.opera.com/community/forums/topic.dml?id=171703&abc=&page=2&skip=50&show=&perscreen=50](http://my.opera.com/community/forums/topic.dml?id=171703&abc=&page=2&skip=50&show=&perscreen=50)

Hmm... It would be great to find that flash plugin on the internet somewhere. Or does anyone have a Wii? :)

---

### Post by ssam on 2007-06-16
> **'[censored] said:**
> ssam tried that prevu method, exactly as you prescribed. At the end of it I just ended up with a deb for gnash 7.2, which probably works a bit more smoothly, but still won't play youtube.

did you add the gutsy source repository to your /etc/apt/sources.list ?

did you do a
```
sudo apt-get update
```

(I'll add that to the wiki page, as it does not seem to be there)

---

### Post by ShareBuntu on 2007-06-16
Compiled for me using:

./configure
make
sudo make install

I can confirm YouTube audio and video working. Controls are a little buggy though. Still needs a lot work but Gnash is doing a super job.

---

### Post by maddog39 on 2007-06-16
Its kind of hard to right click on a PowerBook G4 lol. I made a deb for 0.7.2 a while back and distributed it. But what are the dependencies, it took me a while to figure out *all* of them. Is it really as simple as a standard compile procedure?

---

### Post by ShareBuntu on 2007-06-16
> **maddog39 said:**
> Its kind of hard to right click on a PowerBook G4 lol. I made a deb for 0.7.2 a while back and distributed it. But what are the dependencies, it took me a while to figure out *all* of them. Is it really as simple as a standard compile procedure?
I just installed the dependencies it reported missing one-by-one. I had to download two packages from their web pages and compile them separately before Gnash resolved. Give it a shot and if you get stuck I'll help you out.

---

### Post by [censored] on 2007-06-17
ssam

> **ssam said:**
> did you add the gutsy source repository to your /etc/apt/sources.list ?


No. Can u tell me what line to add to the sources.list file?

---

### Post by ShareBuntu on 2007-06-17
You don't need to add anything to sources.list. Just download [ftp://ftp.gnu.org/pub/gnu/gnash/0.8.0/gnash-0.8.0.tar.gz]("ftp://ftp.gnu.org/pub/gnu/gnash/0.8.0/gnash-0.8.0.tar.gz") , extract and compile.

---

### Post by [censored] on 2007-06-17
See my post on page 2 Ace.

---

### Post by ShareBuntu on 2007-06-17
> **'[censored] said:**
> See my post on page 2 Ace.
Grab Ming from here: [http://prdownloads.sourceforge.net/ming/ming-0.3.0.tar.gz?download]("http://prdownloads.sourceforge.net/ming/ming-0.3.0.tar.gz?download"). Extract it and compile using ./configure, make and sudo make install.

Then grab swfmill here: [http://swfmill.org/releases/swfmill-0.2.12.tar.gz]("http://swfmill.org/releases/swfmill-0.2.12.tar.gz"). Do the same as Ming. Extract, ./configure, make and sudo make install. It might ask for another package that you'll need to install using aptitude.

After you've done that, try compiling Gnash again.

---

### Post by maddog39 on 2007-06-18
Okay well I got all the required packages but it still fails to compile. I get the following GCC error:
```

 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../server -I../server/parser -I../server/vm -I../libltdl -I../libbase -I../backend -I../libgeometry -DLOCALEDIR=\"/usr/local/share/locale\" -I/usr/include/libxml2 -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/SDL -I/usr/include -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -DPKGDATADIR=\"/usr/local/share/gnash\" -DRENDERER_CONFIG=\"opengl\" -DGUI_CONFIG=\"gtk\" -DMEDIA_CONFIG=\"none\" -DTARGET_CONFIG=\"\" -g -O2 -pthread -W -Wall -Wcast-align -Wcast-qual -Wpointer-arith -Wreturn-type -MT gtk.lo -MD -MP -MF .deps/gtk.Tpo -c gtk.cpp  -fPIC -DPIC -o .libs/gtk.o
In file included from gtk.cpp:30:
gtksup.h:35:23: error: gtk/gtkgl.h: No such file or directory
gtk_glue_gtkglext.h:54: error: ISO C++ forbids declaration of 'GdkGLConfig' with no type
gtk_glue_gtkglext.h:54: error: expected ';' before '*' token
gtksup.h:159: error: ISO C++ forbids declaration of 'GdkGLConfig' with no type
gtksup.h:159: error: expected ';' before '*' token
make[3]: *** [gtk.lo] Error 1
make[3]: Leaving directory `/home/maddog39/Desktop/gnash-0.8.0/gui'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/maddog39/Desktop/gnash-0.8.0/gui'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/maddog39/Desktop/gnash-0.8.0'
make: *** [all] Error 2
maddog39@laptop:~/Desktop/gnash-0.8.0$ 

```

---

### Post by mambro on 2007-06-19
is there a deb package for feisty? i can't compile it :(

---

### Post by Calash on 2007-06-19
I am having issues with this as well on my iBook, the clamshell model. I finally got it to compile using the following line

```

./configure --enable-renderer=Agg --enable-media=GST --disable-klash --disable-cygnal

```

The "make install" did not put the plugin in the correct spot so I had to move it to the .mozilla/plugin directory (it was in .firefox/plugin but it did not even see it there.  Now it shows up in about:plugins

However going to Youtube and trying to view a movie get me the loading screen followed by a blank white window.  I am not sure where to look next, compiling took a good hour and I do not want to do it again until I have an idea of what may be wrong.

Any pointers?

Thanks :)

---

### Post by P_Badger on 2007-06-19
Add the gutsy repos to your source.list, update, apt-get install gnash (0.8.0), then remove or blank out the gutsy repositories, update again.

---

### Post by STUMPOFWAR on 2007-06-19
I think the guy is asking for directions on how to do that....

---

### Post by STUMPOFWAR on 2007-06-19
I downloaded the deb.......got a dependency error for libc6

downloaded libc6 and I got "conflicts with installed package tzdata"

Can I uninstall with tzdata? .....and then install libc6 -----> gnash?

Shawn

---

### Post by Calash on 2007-06-19
Not so much on how to do it, but why it does not work the way I did it.  I also followed the instructions a few pages back to get the gutsy version via prevu however I ended up with the same version that Feisty gives me.  Just downloading the .deb gets me the libc6 conflict as noted above.

My question is more along the lines of how can I get info on why it is not working....error logs, terminal output...some kind of feedback to better diagnose the problem.

---

### Post by STUMPOFWAR on 2007-06-20
Yea, prevu gave me the old version as well......I went and added the Gutsy repos and got the package. Firefox shows the new version of gnash but youtube still doesn't work.  que sera sera.....

---

### Post by stmiller on 2007-06-20
Depending on how the gutsy package of gnash is compiled, it may require you have a proper ati or nvidia driver loaded, particularly if gnash is compiled with opengl rendering.

---

### Post by Calash on 2007-06-21
Recompiled the package from the source, compiled and installed AGG as well.  Took FOREVER....like days to finish.  Not sure if it is just because the system is slow or what.

End result, nada.  I go to Youtube, look at movie and it starts to load with the black screen and the controls at the bottom.  Then if flickers and goes white.

I am wondering if it may be a video driver issue, but I have no idea what type of card is in this system.  Was there a standard config for the old iBooks (1999 - Clamshell with no Firewire).

---

### Post by ssam on 2007-06-21
looks like it will probably be officially backported

[https://bugs.launchpad.net/feisty-backports/+bug/120990](https://bugs.launchpad.net/feisty-backports/+bug/120990)

---

### Post by fuoco on 2007-06-22
The prevu method is really the best, but you need to know how to install and configure prevu first. 
the problem is that the gutsy deb is using opengl and i'd rather use agg. not sure how to alter it so that prevu makes it with agg. any ideas?

---

### Post by dpny on 2007-06-23
Just tried it with the prevu method, and it seemed to go well. Prevu installed and configured. I was able to build gnash .8 using prevu. Reloaded Synaptic and installed. About:plugins shows gnash at 0.8. However, when I go to YouTube, clicking on any video freezes up the machine so hard a reboot is required. It's a 500 MHz Pismo.

Any ideas?

---

### Post by mambro on 2007-07-11
If someone can build a package he should post here [https://bugs.launchpad.net/feisty-backports/+bug/120990](https://bugs.launchpad.net/feisty-backports/+bug/120990)

They are looking for somone that can build a backport package

---

### Post by stmiller on 2007-07-11
> **dpny said:**
> Just tried it with the prevu method, and it seemed to go well. Prevu installed and configured. I was able to build gnash .8 using prevu. Reloaded Synaptic and installed. About:plugins shows gnash at 0.8. However, when I go to YouTube, clicking on any video freezes up the machine so hard a reboot is required. It's a 500 MHz Pismo.

Any ideas?

I believe the default gnash 0.8.0 plugin uses opengl to render the video. Unfortunately this factors in your opengl performance, which is something that has not been so great under PowerPC Linux.
The more cpu-friendly way is to compile gnash from source with AGG as the renderer. Though this is more complicated to do, you might have to resort to this. There's a thread about compiling gnash 0.8.0 with AGG somewhere on this forum.

Note that a 500Mhz PPC processor is the minimum recommended requirement for Adobe Flash video according to Adobe, so youtube may tax your cpu quite a bit even with Gnash.

---

