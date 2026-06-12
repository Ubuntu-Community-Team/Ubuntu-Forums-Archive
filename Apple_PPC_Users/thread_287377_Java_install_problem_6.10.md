---
title: "Java install problem: 6.10"
date: 2006-10-28
forum: Apple PPC Users
---

### Post by soapboy on 2006-10-28
While trying to install Java via the directions here:

[http://joona.kuori.org/ubuntu-powerbook/](http://joona.kuori.org/ubuntu-powerbook/)

Java still isnt working.  It is an available option when I do:

update-alternatives --config java

But when I enter "java" at the command prompt I get the following error:

Error loading libstdc++.so.5: cannot open shared object file: No such file or directory

Any ideas?  I'm thinking that the required file isn't in the right place, but im not sure where to find it.

---

### Post by soapboy on 2006-10-28
OK, i tried to symb link the stdc binary in /usr/lib/libstdc++.so.6 to the /usr/lib/j2sdk library, but it still gives me the error, can anyone help?

EDIT:  It seems im using stdc ver 6 and not ver 5, like what java is looking for.  Any way to install stdc 5 or tell java to use ver 6?

---

### Post by soapboy on 2006-10-28
Yay, got it working, if anyone has this problem, just install libstdc++5 with apt-get

sudo apt-get install libstdc++5


Should fix the problem, my java is up and running now.  You have to use apt because Synaptic only has version 6.  :cool:

---

### Post by soapboy on 2006-10-28
Ok, maybe yay was a bit premature.... ;) 

Java works, but the firefox plugin definately does not.  Would there be any conflict with Java 1.5 SDK and firefox 2.0?  the symb link is in ~/.mozilla/plugins, but it doesnt load or appear in about:plugins

---

### Post by ivelasco on 2006-10-30
IBM java depends of two libs that MUST BE INSTALLED BEFORE the java package:
libstdc++5 and libgtk1.2 packages.

Uninstall java and do it in this way,you will see the plugin working.This is my about: plugins:My system is 6.10 firefox 2.0


IBM Java(TM) Plug-in: J2RE 1.5.0 IBM build jclxp32dev-20061002

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5 	Java 		Yes
Totem Web Browser Plugin 2.16.2

    File name: libtotem-basic-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Multimedia Ogg 	ogg 	Yes
video/mpeg 	Vídeo MPEG 	mpg, mpeg, mpe 	Yes
audio/wav 	Audio WAV 	wav 	Yes
audio/mpeg 	Audio MP3 	mp3 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	Documento RealAudio 	rpm 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	Vídeo AVI 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	Vídeo ASF 	asf, wmv 	Yes
video/x-msvideo 	Vídeo AVI 	asf, wmv 	Yes
video/x-ms-asf 	Vídeo ASF 	asf 	Yes
video/x-ms-wmv 	Vídeo WMV 	wmv 	Yes
video/x-wmv 	Vídeo WMV 	wmv 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	Vídeo AVI 	divx 	Yes
QuickTime Plug-in 7.0 (compatible; Totem)

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Vídeo QT 	mov 	Yes
Shockwave Flash 8.0

    File name: libgnashplugin.so
    Gnash 0.7.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License, with an additional special exception allowing linking with Mozilla, or any variant of Mozilla (such as Firefox), so long as the linking is through its standard plug-in interface. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash).

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 8.0 	swf 	Yes

---

### Post by IceBooger on 2006-11-04
After stumbling through multiple websites trying to figure out how to get Java working, I found your link above. This also helped me get my 12" Powerbook Airport Extreme working correctly. 

Thanks :D :D :D

---

### Post by joonahoi on 2006-11-06
Oh sorry, completely forgot the libstdc5++ and libgtk from the guide. It's upgraded now, thanks.

---

