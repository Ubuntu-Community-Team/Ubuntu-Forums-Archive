---
title: "I want to install airclick manager but I'm haing newbie problems"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Scotty562 on 2007-02-12
I have an airclick blootooth remote that will control my music for me and I found a piece of software that will work with linux.

Website:
[http://www.sodan.ecc.u-tokyo.ac.jp/~okayama/airclick-mngr/](http://www.sodan.ecc.u-tokyo.ac.jp/~okayama/airclick-mngr/)

That is the goal. Now, I downloaded it reinstalled it and did the ./configure like it asked and it says

"configure: error: GAI not found!"

Awesome, I didn't know if it was installed or not so I went to Synaptic and typed in GAI, nothing.  I then tried General Applet Interface, nothing.  So I tried Google, found a package and downloaded it.

GAI:
[http://www.icewalkers.com/Linux/Software/520740/GAI.html](http://www.icewalkers.com/Linux/Software/520740/GAI.html)

So now I try and install this. ./configure works fine. make gives me this:

(cd gai;make all)
make[1]: Entering directory `/home/aries/Desktop/gai-0.5.6/gai'
gcc -Wall -O2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include        -c -o gai.o gai.c
In file included from /usr/include/pango-1.0/pango/pangofc-font.h:25,
                 from /usr/include/pango-1.0/pango/pangoft2.h:29,
                 from gai.c:39:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from /usr/include/pango-1.0/pango/pangoft2.h:29,
                 from gai.c:39:
/usr/include/pango-1.0/pango/pangofc-font.h:26:10: error: #include expects "FILENAME" or <FILENAME>
In file included from /usr/include/pango-1.0/pango/pangoft2.h:29,
                 from gai.c:39:
/usr/include/pango-1.0/pango/pangofc-font.h:147: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;pango_fc_font_lock_face&#8217;
In file included from gai.c:39:
/usr/include/pango-1.0/pango/pangoft2.h:48: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pango-1.0/pango/pangoft2.h:53: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pango-1.0/pango/pangoft2.h:60: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pango-1.0/pango/pangoft2.h:64: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pango-1.0/pango/pangoft2.h:68: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pango-1.0/pango/pangoft2.h:72: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/pango-1.0/pango/pangoft2.h:103: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;pango_ft2_font_get_face&#8217;
gai.c: In function &#8216;gai_text_create&#8217;:
gai.c:1337: error: &#8216;FT_Bitmap&#8217; undeclared (first use in this function)
gai.c:1337: error: (Each undeclared identifier is reported only once
gai.c:1337: error: for each function it appears in.)
gai.c:1337: error: expected &#8216;;&#8217; before &#8216;bitmap&#8217;
gai.c:1377: error: &#8216;bitmap&#8217; undeclared (first use in this function)
gai.c:1382: error: &#8216;ft_pixel_mode_grays&#8217; undeclared (first use in this function)
gai.c:1384: warning: implicit declaration of function &#8216;pango_ft2_render_layout&#8217;
gai.c: In function &#8216;gai_text_create_simple&#8217;:
gai.c:1440: error: &#8216;FT_Bitmap&#8217; undeclared (first use in this function)
gai.c:1440: error: expected &#8216;;&#8217; before &#8216;bitmap&#8217;
gai.c:1466: error: &#8216;bitmap&#8217; undeclared (first use in this function)
gai.c:1471: error: &#8216;ft_pixel_mode_grays&#8217; undeclared (first use in this function)
make[1]: *** [gai.o] Error 1
make[1]: Leaving directory `/home/aries/Desktop/gai-0.5.6/gai'
make: *** [all] Error 2

It looks like something with pango is awry so I went to Synaptic and reinstalled it and it didn't fix the problem. It looks like they're is a missing folder freetype in there somewhere.

So this is where I'm at and now I'm at a dead end.  Any help would be greatly appreciated = D.

Thanks.

Edit: 

A symlink fixed the problem with freetpye/config but now I get
"In function &#8216;on_close_button_clicked&#8217;:"

---

### Post by Scotty562 on 2007-02-12
Hopin this bump helps.

---

### Post by bryan.taylor on 2007-07-08
I couldn't get it to work properly either, even though I got it to compile.  So, I took some of the code from airclick-mngr-0.6 and wrapped it up in some classes that I had lying around.  My brother's airclick remote now works, but it doesn't have a gui (applet).  Instead, it uses a configuration file located at ~/.airclick/airclick.conf.  This is better than airclick-mngr IMHO because you can make the remote control any application that you like.  The file looks like this:
```
# device node
DeviceFilename		"/dev/hiddev0"
InitialRepeatDelay	.75
RepeatDelay		.2

#
# for the gnome-terminal app
#
BeginSection
	Application	"gnome-terminal"
	IgnoreCase	true
	BeginMacro
		Button "Previous"
		BeginCombination
			Control_L
			Page_Up
		EndCombination
	EndMacro
	BeginMacro
		Button "Next"
		BeginCombination
			Control_L
			Page_Down
		EndCombination
	EndMacro
EndSection

#
# for totem
#
BeginSection
	Application	"totem"
	IgnoreCase	true
	BeginMacro
		Button "Play/Pause"
		BeginCombination
			space
		EndCombination
	EndMacro
	BeginMacro
		Button "Previous"
		BeginCombination
			Left
		EndCombination
	EndMacro
	BeginMacro
		Button "Next"
		BeginCombination
			Right
		EndCombination
	EndMacro
	BeginMacro
		Button "VolumeUp"
		BeginCombination
			Up
		EndCombination
	EndMacro
	BeginMacro
		Button "VolumeDown"
		BeginCombination
			Down
		EndCombination
	EndMacro
EndSection

#
# defaults - configured for my amarok hotkeys
#
BeginSection
	Application	default
	BeginMacro
		Button "Play/Pause"
		BeginCombination
			Super_L
			Home
		EndCombination
	EndMacro
	BeginMacro
		Button "Previous"
		BeginCombination
			Super_L
			Page_Up
		EndCombination
	EndMacro
	BeginMacro
		Button "Next"
		BeginCombination
			Super_L
			Page_Down
		EndCombination
	EndMacro
	BeginMacro
		Button "VolumeUp"
		BeginCombination
			Super_L
			KP_Add
		EndCombination
	EndMacro
	BeginMacro
		Button "VolumeDown"
		BeginCombination
			Super_L
			KP_Subtract
		EndCombination
	EndMacro
	#
	# this macro will execute when you press the volume down and previous buttons simultaneously
	#
	BeginMacro
		Button "VolumeDown"
		Button "Previous"
		BeginCombination
			Super_L
			m
		EndCombination
	EndMacro
EndSection
```

If you're still in need of a solution for your airclick remote, then I'd be happy to give you this one.

---

### Post by brundlelinux on 2008-03-25
One trick I have used with various amounts of success (usually good though) when having dependency-type errors from a source install is to go to Synaptic and search for whatever I was having an error message about.  Then I make sure to grab the -dev files, which are the development files for that app or code.  It's probably overkill in most situations, but it is a shotgun blast approach that *usually* solves my problem without much hassle.  And, having a little extra code around that isn't being used isn't that big of a deal to me.

Also, if the last poster's code worked for you, please remember to mark this thread as solved.  If not, then I just bumped ya.

---

### Post by bryan.taylor on 2008-03-25
Since I made my last post above, I've created a sourceforge project for my application:
[http://sourceforge.net/projects/airclick/](http://sourceforge.net/projects/airclick/)

Also, if you encounter installation troubles please check this forum thread:
[http://ubuntuforums.org/showthread.php?t=504906](http://ubuntuforums.org/showthread.php?t=504906)

Basically, you'll need to install a compiler (build-essential is an easy package to use), libx11-dev, and libxtst-dev.

Then you follow the normal installation process:
./configure
make
sudo make install

You'll need to copy the airclick.sample.conf to ~/.airclick/airclick.conf.  Depending on what version of ubuntu you're running, your remote will probably show up as /dev/hiddev0 or /dev/usb/hiddev0.  You'll need to specify which one it is at the top of the airclick.conf file.

The configuration file is heavily commented, but if you have any additional questions about how to set it up then just post back in either this thread or the other forum thread listed above.

---

