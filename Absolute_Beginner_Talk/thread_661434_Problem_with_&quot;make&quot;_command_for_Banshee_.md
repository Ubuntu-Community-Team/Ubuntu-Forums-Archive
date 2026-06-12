---
title: "Problem with &quot;make&quot; command for Banshee installation.  Something with Mono.Zeroconf?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by bradleyviolin on 2008-01-07
Hello,

I'm new to Ubuntu and Linux, and loving it... I've dumped Windows altogether.  

However, with the loss of Windows, I've lost easy synch to my iRiver T30 via WMP.

So...trying Banshee...

...but when trying to install Banshee from within Terminal, after entering the "make" command, I get (at the end of it all):

** (../../../build/gconf-schema-extractor.exe:13980): WARNING **: The following assembly referenced from /home/bluewolf/Banshee/src/Plugins/Banshee.Plugins.Daap/Banshee.Plugins.Daap.dll could not be loaded:
     Assembly:   Mono.Zeroconf    (assemblyref_index=9)
     Version:    1.0.0.0
     Public Key: e60c4f4a95e1099e
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bluewolf/Banshee/src/Plugins/Banshee.Plugins.Daap/).


** (../../../build/gconf-schema-extractor.exe:13980): WARNING **: Could not load file or assembly 'Mono.Zeroconf, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e60c4f4a95e1099e' or one of its dependencies.

** (../../../build/gconf-schema-extractor.exe:13980): WARNING **: Could not load file or assembly 'Mono.Zeroconf, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e60c4f4a95e1099e' or one of its dependencies.

Unhandled Exception: System.Reflection.ReflectionTypeLoadException: The classes in the module cannot be loaded.
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (bool)
  at System.Reflection.Assembly.GetTypes () [0x00000] 
  at GConfSchemaExtractor.Main (System.String[] args) [0x00000] 
make[4]: *** [banshee-plugin-daap.schemas.in] Error 1
make[4]: Leaving directory `/home/bluewolf/Banshee/src/Plugins/Banshee.Plugins.Daap'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/bluewolf/Banshee/src/Plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bluewolf/Banshee/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bluewolf/Banshee'
make: *** [all] Error 2

Autogen completed with no problem, and "--enable-mtp" was passed with that command, but once I try "make", I get the code above.  Something about Mono.Zeroconf not being found in GAC?

Anyone out there that can tell me what I've done wrong? I'm just looking for a media player app that will synch with my iRiver T30 via MTP.  (I've already explored iRiver  firmware tweaks/upgrades to USB...don't want to/can't go that route.  No Windows machine access right now.) I'm hoping this Banshee installation will allow my T30 to be seen within in Ubuntu.  (Already tried Amarok to no avail.)  I've been working on this for a loooong time with no luck, and am now hung-up here...with some Mono.Zeroconf problem.  (It's already been installed from source, but maybe not in the right place?)  Any help is appreciated...

---

### Post by Nano Geek on 2008-01-08
Did you install the dependences for Banshee? > sudo apt-get build-dep banshee

---

### Post by bradleyviolin on 2008-01-08
Thanks for your response!  

Tried installing those, and then re-autogened the thing. Same snag during "make".

---

### Post by Nano Geek on 2008-01-08
May I ask why you are compiling from source?
Did the one in the repository not work out for you?
And also, what version of Banshee are you trying to compile?

---

### Post by launcher on 2008-01-08
> Did the one in the repository not work out for you?

Wait a second. Forgive me for being completely new when it comes to Ubuntu and linux; this is literally the first day that I have worked on this. I am having basically the same problem as bradleyviolin and I was wondering what the "one in the repository" was. 

I already foung the add/remove application to get software, but bansheee isn't in there. Is there something else I am missing, because if I didn't have to compile this that would be great.

---

### Post by Nano Geek on 2008-01-08
It should be in there.

In a drop-down box near the top of the **Add/Remove...** window, change it to **All available applications** and try the search again.

---

### Post by launcher on 2008-01-08
Oh, I found it. Thanks.

---

### Post by bradleyviolin on 2008-01-09
Thanks... asjdfwejqrfjcvm msz34rq33's Avatar  	
asjdfwejqrfjcvm msz34rq33.

To reply to your questions:

I'm compiling from source code because as I understand it, if use Synaptic, it will install a version without MTP support.

I finally got it to finish installing with:

./autogen.sh --enable-mtp --disable-daap

make

sudo make install

And now Banshee does recognize my iriver T30, it sees the files on it, can even erase them, but when I try to move or sync files from the banshee library to the T30, it essentially hangs...and the files don't seem to be transferring.

I'm under the impression that daap is essentially a requisite of file transfer to iPods or something with file sharing, no?

Any idea why the MTP transfer is hanging?

When I run banshee in debug mode, delete a file of the iriver, and then try to transfer one tune from the banshee library folder to the T30 via a manual sync, I get:

:/$ banshee --debug
** Running Banshee in Debug Mode **
** Running Mono with --debug   **
Debug: [1/9/2008 5:20:10 AM] (Loading audio profiles) - /usr/local/share/banshee/audio-profiles
Debug: [1/9/2008 5:20:10 AM] (GStreamer pipeline does not run) - audioconvert ! xingenc bitrate=128 ! id3v2mux
Debug: [1/9/2008 5:20:10 AM] (GStreamer pipeline does not run) - audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
Debug: [1/9/2008 5:20:10 AM] (Default player engine) - GStreamer 0.10
Debug: [1/9/2008 5:20:10 AM] (Audio CD Core Initialized) - 
Debug: [1/9/2008 5:20:10 AM] (Enabled multimedia keys support) - Using org.gnome.SettingsDaemon
Debug: [1/9/2008 5:20:35 AM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/usb_device_4102_1119_6cc618d3000000fd2db1c1b53195be54_if0
Debug: [1/9/2008 5:20:35 AM] (MTP: Starting initialization) - Name: Mtp Device, Device: 0, Bus:0
PTP: Opening session
Debug: [1/9/2008 5:20:36 AM] (MTP: device found) - vendor=0, prod=0
Debug: [1/9/2008 5:20:36 AM] (DAP has been added) - Banshee.Dap.Mtp.MtpDap: /org/freedesktop/Hal/devices/usb_device_4102_1119_6cc618d3000000fd2db1c1b53195be54_if0

(Banshee:7776): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

(Banshee:7776): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

(Banshee:7776): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

[ADD NAUSEUM...]


(Banshee:7776): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

(Banshee:7776): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

(Banshee:7776): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Removing: 196610
Sending: 0
Unknown OPFF type 5
Got: 196610
PTP: Closing session


Should I move this inquiry to the debugging/Bugzilla thing over at the Banshee site?

---

### Post by Nano Geek on 2008-01-09
That's weird. Just looking through your debug output, I don't see anything that look strange. You could try the unstable version which you can find [here]("http://www.banshee-project.org/Releases/CVS"). 
You'll need to install svn to download it first.```
sudo apt-get install svn-buildpackage
```But if it still doesn't work there, then yes I'd report a but either on their website or on Ubuntu's own Launchpad.net

---

### Post by copyright201 on 2008-02-24
bradleyviolin,

Would you mind posting how you fixed your problem with Mono.ZeroConfig?  I'm running into the same thing now...

Also, I'm glad to hear MTP is at least partially working with Banshee now.  That's what I'm compiling it for as well.

---

