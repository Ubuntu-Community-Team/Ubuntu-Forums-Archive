---
title: "Tapioca for Edgy??"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Z13 on 2006-11-02
I like very much the Tapioca VoIP application but after moving from Dapper to Edgy I found out there is no available package for this new version.
I tried compiling the source code but didn't work (I'm new in such things).

My question: **is there any way we can make Tapioca 0.3.9 work on Ubuntu Edgy Eft too?** I really need Tapioca's voice capabilities (Gaim still doesn't have this option).

Thank you.

---

### Post by Z13 on 2006-11-03
Anyone???

---

### Post by po0f on 2006-11-03
Z13,

Can you post the problems you were having compiling it?

---

### Post by maciej on 2006-11-26
Hi,

here is how I got it working on edgy:
add this to your/etc/apt/sources.list :
deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) testing main

then run:
sudo apt-get update
sudo apt-get install tapiocaui0.3

at this stage it will complain about missing library:

maciej@EA60-155:~$ tapiocaui
tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

because edgy has newer version I created a symlink:
maciej@EA60-155:~$ locate libdbus-1.so
/usr/lib/libdbus-1.so.3
/usr/lib/libdbus-1.so.3.0.0
sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

and tada!

hope this helps,

Maciej

---

### Post by dvarsam on 2006-11-29
> **Z13 said:**
> 
I like the Tapioca VoIP application.
After moving from Dapper to Edgy, I found there is no available package for this new version.
I tried compiling the source code but didn't work (I'm new in such things).

My question:
**is there any way to make Tapioca 0.3.9 work on Ubuntu Edgy Eft too?**
I need Tapioca's voice capabilities (Gaim still doesn't have this option).


Hello!

Voice Chat with "Tapioca"...

This seems very interesting!

I would be interested for this too!

Hopefully, after we manage to have it implemented in Ubuntu, then we can all hope for Video Chat too!

How was it?

Did the sound come out crisp & clear when you Video-chatted in Dapper?

Thanks.

---

### Post by fre4k on 2006-12-08
i installed as per maciej's instructions, but no sound when i am in a call and neither can the other person hear me. :(

---

### Post by dvarsam on 2006-12-11
Dear user "fre4k",

[QUOTE=fre4k]I installed as per maciej's instructions, but no sound when I am in a call & neither can the other person hear me. :([/QUOTE]

If you go from the Menu "**Applications\Sound & Video\Sound Recorder**", when you record sound with your microphone, can you hear/listen to your recorded sound?

Thanks.

---

### Post by arnieboy on 2006-12-28
> **maciej said:**
> Hi,

here is how I got it working on edgy:
add this to your/etc/apt/sources.list :
deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) testing main

then run:
sudo apt-get update
sudo apt-get install tapiocaui0.3

at this stage it will complain about missing library:

maciej@EA60-155:~$ tapiocaui
tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

because edgy has newer version I created a symlink:
maciej@EA60-155:~$ locate libdbus-1.so
/usr/lib/libdbus-1.so.3
/usr/lib/libdbus-1.so.3.0.0
sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

and tada!

hope this helps,

Maciej
yes that works! Thanks.

---

### Post by michote on 2006-12-29
it works 
but I don't have any sound
my microphone works ([http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone](http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone))

michote

---

### Post by arnieboy on 2006-12-29
> **michote said:**
> it works 
but I don't have any sound
my microphone works ([http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone](http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone))

michote
make sure "capture" is not muted in gnome volume control. By default it is.

---

### Post by michote on 2006-12-30
Where I find "capture"
al I have in the Alsamixer is this:
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=21903&stc=1&d=1167473985[/IMG]



It is the same on the notebook of my wife.
it works but no sound
there it  alsamixer has microbost also but no capture!???

---

### Post by Obor on 2007-01-07
> **maciej said:**
> Hi,

here is how I got it working on edgy:
add this to your/etc/apt/sources.list :
deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) testing main

then run:
sudo apt-get update
sudo apt-get install tapiocaui0.3

at this stage it will complain about missing library:

maciej@EA60-155:~$ tapiocaui
tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

because edgy has newer version I created a symlink:
maciej@EA60-155:~$ locate libdbus-1.so
/usr/lib/libdbus-1.so.3
/usr/lib/libdbus-1.so.3.0.0
sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

and tada!

hope this helps,

Maciej

Thanks, I always wanted to talk to people on gtalk. Sweet. :-D

---

### Post by kd7swh on 2007-01-11
Installs but I click log in and nothing happens

---

### Post by akman360 on 2007-01-20
> **maciej said:**
> Hi,

here is how I got it working on edgy:
add this to your/etc/apt/sources.list :
deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) testing main

then run:
sudo apt-get update
sudo apt-get install tapiocaui0.3

at this stage it will complain about missing library:

maciej@EA60-155:~$ tapiocaui
tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

because edgy has newer version I created a symlink:
maciej@EA60-155:~$ locate libdbus-1.so
/usr/lib/libdbus-1.so.3
/usr/lib/libdbus-1.so.3.0.0
sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

and tada!

hope this helps,

Maciej
 
:D Thanks. I've been trying to get this to work, but with no success. Now it works!

---

### Post by dphan on 2007-01-20
> **maciej said:**
> Hi,

here is how I got it working on edgy:
add this to your/etc/apt/sources.list :
deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) testing main

then run:
sudo apt-get update
sudo apt-get install tapiocaui0.3

at this stage it will complain about missing library:

maciej@EA60-155:~$ tapiocaui
tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

because edgy has newer version I created a symlink:
maciej@EA60-155:~$ locate libdbus-1.so
/usr/lib/libdbus-1.so.3
/usr/lib/libdbus-1.so.3.0.0
sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

and tada!

hope this helps,

Maciej

Hi,
I worked it out with the above instruction for installing Tapioca0.3/Edgy6.10. Thanks a lot.
However, I stuck one thing and so now I have no solution for that. It is when I install tapiocaui0.3 it is processed okay but afterward, it is warned a dep. lib (farsight) as below. This doesnt effect the Tapioca running, but it blocked me to install new soft/apps or updating my system. Any one give me a hint to sort it out please?
----------------------------------------------------
root@Bluez:/home/dphan/dl1/soft/farsight-0.1.3.1# apt-get install tapiocaui0.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnl1-pre6 network-manager libnm-util0 dhcdbd phalanx
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  farsight0.1-plugins-rtp libtapioca0.3-client-0 tapioca0.3-xmpp
The following NEW packages will be installed:
  farsight0.1-plugins-rtp libtapioca0.3-client-0 tapioca0.3-xmpp tapiocaui0.3
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 198kB/255kB of archives.
After unpacking 836kB of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  farsight0.1-plugins-rtp libtapioca0.3-client-0 tapioca0.3-xmpp tapiocaui0.3
Install these packages without verification [y/N]? y
Get:1 [http://extindt01.indt.org](http://extindt01.indt.org) testing/main tapioca0.3-xmpp 0.3.9-0indt1 [113kB]
Get:2 [http://extindt01.indt.org](http://extindt01.indt.org) testing/main tapiocaui0.3 0.3.9-0indt1 [85.0kB]
Fetched 198kB in 2s (69.7kB/s)       
(Reading database ... 146382 files and directories currently installed.)
Unpacking farsight0.1-plugins-rtp (from .../farsight0.1-plugins-rtp_0.1.3-11indt1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/farsight0.1-plugins-rtp_0.1.3-11indt1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/farsight-0.1/librtp.so', which is also in package farsight0.1-rtp
Selecting previously deselected package libtapioca0.3-client-0.
Unpacking libtapioca0.3-client-0 (from .../libtapioca0.3-client-0_0.3.9-1indt1_i386.deb) ...
Selecting previously deselected package tapioca0.3-xmpp.
Unpacking tapioca0.3-xmpp (from .../tapioca0.3-xmpp_0.3.9-0indt1_i386.deb) ...
Selecting previously deselected package tapiocaui0.3.
Unpacking tapiocaui0.3 (from .../tapiocaui0.3_0.3.9-0indt1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/farsight0.1-plugins-rtp_0.1.3-11indt1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Bluez:/home/dphan/dl1/soft/farsight-0.1.3.1# 
--------------------------------------------------------------
regards,
D,Phan

---

### Post by dvarsam on 2007-01-21
Hello!

[QUOTE=maciej]Here is how I got it working on edgy:

**1.** Add this to your/etc/apt/sources.list:

deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) testing main

**2.** Then run:

sudo apt-get update
sudo apt-get install tapiocaui0.3

At this stage it will complain about missing library:

maciej@EA60-155:~$ tapiocaui
tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

because edgy has newer version I created a symlink:
maciej@EA60-155:~$ locate libdbus-1.so
/usr/lib/libdbus-1.so.3
/usr/lib/libdbus-1.so.3.0.0

**3.** sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

Maciej[/QUOTE]

I followed all your steps above & everything worked great!!!

However, I have the following problem:

I have 2 e-mail accounts:

1. Hotmail
2. Yahoo

Whenever I try to connect to any one of them, I get the following error:

[quote=dvarsam][color="red"]Error: A network error has occurred during login. Please check your network settings.[/color][/quote]

I visited the developer's site:
[http://tapioca-voip.sourceforge.net/wiki/index.php?title=FAQ&redirect=no](http://tapioca-voip.sourceforge.net/wiki/index.php?title=FAQ&redirect=no)

... but found nothing regarding this, no operating manual, or any other help...
What am I doing wrong & how do I fix this?

Thanks.

---

### Post by kadalz on 2007-01-24
> **maciej said:**
> Hi,

here is how I got it working on edgy:
add this to your/etc/apt/sources.list :
deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) testing main

then run:
sudo apt-get update
sudo apt-get install tapiocaui0.3

at this stage it will complain about missing library:

maciej@EA60-155:~$ tapiocaui
tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

because edgy has newer version I created a symlink:
maciej@EA60-155:~$ locate libdbus-1.so
/usr/lib/libdbus-1.so.3
/usr/lib/libdbus-1.so.3.0.0
sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

and tada!

hope this helps,

Maciej

Hello:

I followed Maciej's steps, and it went perfectly without any errors. But I unable to run it. It's like starting (loading application) and then disappeared. Any body could give me some suggestions here? What did I do wrong?

Thank you,
Kadalz

---

### Post by dvarsam on 2007-01-24
[QUOTE=kadalz]Hello:

I followed Maciej's steps, and it went perfectly without any errors. But I unable to run it. It's like starting (loading application) and then disappeared. Any body could give me some suggestions here? What did I do wrong?[/QUOTE]

It had happened to me too!
It is because I had not typed this (in the Terminal):

**3.** sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

When you do it, everything should work fine after this...
Good Luck

P.S.> Anybody able to answer my question?
I.e. Can I connect to a Hotmail or Yahoo account?
What type of account do I need to have to be able to voice chat?
Thanks

---

### Post by kadalz on 2007-01-24
> **dvarsam said:**
> It had happened to me too!
It is because I had not typed this (in the Terminal):

**3.** sudo ln -s /usr/lib/libdbus-1.so.3.0.0 /usr/lib/libdbus-1.so.2

When you do it, everything should work fine after this...
Good Luck

P.S.> Anybody able to answer my question?
I.e. Can I connect to a Hotmail or Yahoo account?
What type of account do I need to have to be able to voice chat?
Thanks

Thanks for the advice. Now I can run it. But once I run it, I unable to login to my googletalk account?! Any suggestions :confused: 

Thankz,
Kadalz

---

### Post by dphan on 2007-01-29
Tapioca 0.39 has just release deb for Edgy Eft. Please go to [http://www.dcc.ufam.edu.br/~boa/edgy/](http://www.dcc.ufam.edu.br/~boa/edgy/) and give it a try
cheers,
D.phan

---

### Post by astrobit on 2007-02-05
i installed the official packs for ubuntu edgy that were on the tapioca website...
i installed em without problems
i load tapioca without problems too
but when i call someone, the program gets terminated as soon as the call is accepted...

why could it be? :confused:

---

### Post by dvarsam on 2007-02-06
[QUOTE=astrobit]I installed the official packs for Ubuntu Edgy that were on the Tapioca website...
I installed em without problems
I load Tapioca without problems too...
But when I call someone, the program gets terminated as soon as the call is accepted...
Why could it be? :confused:[/QUOTE]

Hello!
I also bet that your microphone does NOT record either!!!
Read this:
[http://ubuntuforums.org/showthread.php?t=351691](http://ubuntuforums.org/showthread.php?t=351691)

I used to think that "[color=blue]Ekiga[/color]" was the worst...
But now I believe that "[color=blue]tapioca[/color]" & "[color=blue]skype[/color]" are the "worse" of the "worse"... :)
Thanks.

---

### Post by jasonal on 2007-02-22
> **astrobit said:**
> i installed the official packs for ubuntu edgy that were on the tapioca website...
i installed em without problems
i load tapioca without problems too
but when i call someone, the program gets terminated as soon as the call is accepted...

why could it be? :confused:

Hi, I got exactly the same problem! However, my microphone does record according to instruction "[Configuring Microphone]("http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone")".

any one has a solution?

---

### Post by dvarsam on 2007-02-23
[QUOTE=jasonal]Hi, I got exactly the same problem! However, my microphone does record according to instruction "[Configuring Microphone]("http://tapioca-voip.sourceforge.net/wiki/index.php/Configuring_Microphone")".

Any one has a solution?[/QUOTE]

Of course your microphone _does_ record sound...
It is because you don't have High Definition Audio - Intel HDA...!!! :)
Anyone who has HDA will find his microphone **NOT** working!!!
Thanks.

---

### Post by jfif on 2007-03-10
Installed [COLOR="Red"]Tapioca[/COLOR] using **maciej**'s method. 

I can IM my Google Talk contact with no problem. 
We can also setup voice call. But the problem is there is no sound -- ringing or voice.  My MIC works well otherwise. 

Any advice?

---

### Post by adityanag on 2007-03-20
Same problem here.. My MIC works when i record sound. I have an Thinkpad T-43.. any help appreciated.

I have checked the volume on all the mixers.

---

### Post by spx3 on 2007-05-06
i'll put my 2 cents also
ok
i tried to install
got in trouble with farsight
got from here [http://download.ubuntu.pl/_Edgy_Eft/tapioca/](http://download.ubuntu.pl/_Edgy_Eft/tapioca/)
the file
farsight0.1-plugins-rtp_0.1.3-1ubuntu1indt1_i386.deb 
and i run a 
 sudo dpkg --force-overwrite -i farsight0.1-plugins-rtp_0.1.3-1ubuntu1indt1_i386.deb 
to overwrite my seemingly existing lib wich contained farsight blabla
then i installed tapioca0.3 and tapiocaui0.3 and it worked very well
(all this on edgy)

---

### Post by rhageman on 2007-05-24
Hi, I'm new to Linux but I'm trying to set up tapioca-voip on 6.10.  I've been following directions on this page
[http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide) and have made it as far as the "Tapioca modified libjingle" section.

When I try to run the first command, "autoreconf -i -f", I get the following message - autoreconf: `configure.ac' or `configure.in' is required".  What does that mean?  How do I fix it?

Thanks for any help and advice.

---

### Post by rhageman on 2007-05-28
Alright, I figured out that you have to be in the directory you're are suppose to be working on and I've progressed to  gst-plugins-farsight.  After I've given the listed commands...

sh autogen.sh
./configure --disable-debug \
--disable-jrtplib \
--disable-mimic \
--disable-gsm \
--disable-jasper \
--enable-jingle-p2p \
--with-plugins=rtpdemux,rtpjitterbuffer

I receive the following error message...

checking for GST... configure: error: you need gstreamer >= 0.10.11 development packages installed !

I've checked Synaptic for gstreamer packages.  Only one - gstreamer0.10-gnonlin.dev - gives any indication that it deals with development packages.  I've installed both gnonlin packages.

I'm still receiving the same error message.

So, what development package is being refered to and where do I get it?

---

### Post by rhageman on 2007-05-28
I'm frustrated!  I've used add/remove and synaptic to add every gstreamer (in add/remove) and every gstreamer 0.10.11 (in synaptic) package I could see.

Visual inspection in synaptic says I have installed on the system all gstreamer 0.10 packages that have avy indication of being development packages.

I'm still getting the same error message.

What do I do next?  Would it help to go back to the  Check dependencies section and work forward all over again?

---

