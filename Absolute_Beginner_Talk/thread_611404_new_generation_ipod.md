---
title: "new generation ipod"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by crav on 2007-11-12
I know there are a lot of topics on this, but everything I could come up with in a search either didn't make a lot of sense to me or offered a now-dead link.

How can I get around the database issue on the newest generation of iPod? (specifically the iPod nano)

---

### Post by persev on 2007-11-13
bump

---

### Post by paradoxni on 2007-11-13
Ok Im getting a new gen ipod soon and have been investigating this myself. I cannot test it as I dont have the thing yet but I can tell you what I have learned so far.

in a terminal:
```
sudo apt-get install libsgutils1 libsgutils1-dev

```

then download libgpod 0.6 if you havent already (if you have you need to recompile it again with the above packages now installed)

[http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119](http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119)

extract the contents of this archive (I downloaded it to my desktop and right clicked and chose 'extract here')

open a terminal and change to the extracted directory
```
cd Desktop/libgpod-0.6.0
./configure
make
sudo make install

```

Now thats done you should have  an 'ipod-read-sysinfo-extended' tool available.

```

ipod-read-sysinfo-extended DEVICE MOUNTPOINT

```
e.g. ipod-read-sysinfo-extended /dev/sda /media/ipod

according to what i have read this will store your firewireID on the ipod so your music will be visible once you add all your music to your ipod again e.g. using rythmbox

---

### Post by llamakc on 2007-11-13
I'm not certain that works with 3rd gen. iPod Nanos. They have an encrypted firmware.

---

### Post by paradoxni on 2007-11-13
those instructions are for the latest ipod classic and nanos, support for the encrypted files was added in libgpod 0.6

> Overview of changes in libgpod 0.6.0
====================================

* support for iPod Classics and Video Nanos

The database from these models is protected by a checksum. When this checksum 
doesn't match the content of the iPod database, the iPod won't show any 
track (ie it will look empty). Support for writing this checksum has been 
implemented in this release thanks to the awesome work of a few people in
#gtkpod. However, to calculate this checksum, a so called "firewire ID" is 
needed which is different from iPod to iPod. Since reading it from the iPod
requires special permissions, the firewire ID must be written in a regular 
file on the iPod so that libgpod can find it and use it to generate the
checksum. 

---

### Post by llamakc on 2007-11-13
That is great news. Thanks for showing me the changelog.

---

### Post by paradoxni on 2007-11-13
post back here if it works, im getting one for xmas:)

---

### Post by ubuntios on 2007-11-20
> **paradoxni said:**
> Ok Im getting a new gen ipod soon and have been investigating this myself. I cannot test it as I dont have the thing yet but I can tell you what I have learned so far.

in a terminal:
```
sudo apt-get install libsgutils1 libsgutils1-dev

```

then download libgpod 0.6 if you havent already (if you have you need to recompile it again with the above packages now installed)

[http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119](http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119)

extract the contents of this archive (I downloaded it to my desktop and right clicked and chose 'extract here')

open a terminal and change to the extracted directory
```
cd Desktop/libgpod-0.6.0
./configure
make
sudo make install

```

Now thats done you should have  an 'ipod-read-sysinfo-extended' tool available.

```

ipod-read-sysinfo-extended DEVICE MOUNTPOINT

```
e.g. ipod-read-sysinfo-extended /dev/sda /media/ipod

according to what i have read this will store your firewireID on the ipod so your music will be visible once you add all your music to your ipod again e.g. using rythmbox

Hi there,
I have try what you say , everything was going fine till the last part.
when I type the ipod-read-sys.... command I get this error 
"ipod-read-sysinfo-extended: error while loading shared libraries: libgpod.so.3: cannot open shared object file: No such file or directory"
No mater what device and mount point I give , I get the same error.
Any help ????

---

### Post by paradoxni on 2007-11-20
at the terminal try

```
sudo updatedb
locate libgpod.so.3

```

where is libgpod.so.3 located (if at all)?

---

### Post by ubuntios on 2007-11-20
> **paradoxni said:**
> at the terminal try

```
sudo updatedb
locate libgpod.so.3

```

where is libgpod.so.3 located (if at all)?

After the update still the same error.

It is located  :  /usr/local/lib/libgpod.so.3
                       /usr/local/lib/libgpod.so.3.0.0

Thanks

---

### Post by Nano Geek on 2007-11-20
Hey, I just bought a new 8 GB Nano, and while I was able to get music on it with those instructions, I couldn't get videos or pictures on it. Unfortunately I had to go back to iTunes to get it to work like I wanted it to.

---

### Post by paradoxni on 2007-11-20
same here..hmm not sure, I do not get the same error , but im not sure why ?!?

---

### Post by paradoxni on 2007-11-20
> **asjdfwejqrfjcvm msz34rq33 said:**
> Hey, I just bought a new 8 GB Nano, and while I was able to get music on it with those instructions, I couldn't get videos or pictures on it. Unfortunately I had to go back to iTunes to get it to work like I wanted it to.

well at least this proves that support for the new generation at least works for music, cheers.

have you tried GTKPOD? it supposedly works with videos/pics and uses the same libgpod as rhythmbox so the new generation ipod classic/nanos will work with it too.

---

### Post by Nano Geek on 2007-11-20
> **paradoxni said:**
> well at least this proves that support for the new generation at least works for music, cheers.

have you tried GTKPOD? it supposedly works with videos/pics and uses the same libgpod as rhythmbox so the new generation ipod classic/nanos will work with it too.I didn't know that. I'll try it when I get a chance.

---

### Post by crav on 2007-11-21
I get the same error:
```
crav@AlphaCrav:~$ ipod-read-sysinfo-extended /media/SAM\ CRAVEN\'/
ipod-read-sysinfo-extended: error while loading shared libraries: libgpod.so.3: cannot open shared object file: No such file or directory

```

---

### Post by crav on 2007-11-21
Also, I just tried the new GTKPod to no avail

---

### Post by paradoxni on 2007-11-21
> **crav said:**
> I get the same error:
```
crav@AlphaCrav:~$ ipod-read-sysinfo-extended /media/SAM\ CRAVEN\'/
ipod-read-sysinfo-extended: error while loading shared libraries: libgpod.so.3: cannot open shared object file: No such file or directory

```


You could try linking the file to the other lib location:
```
 sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3
```
then try the 'ipod-read-sysinfo-extended' command again.

I am however clutching at straws, if i actually had an ipod I would help more! roll on christmas! :P

---

### Post by ubuntios on 2007-11-21
> **paradoxni said:**
> You could try linking the file to the other lib location:
```
 sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3
```
then try the 'ipod-read-sysinfo-extended' command again.

I am however clutching at straws, if i actually had an ipod I would help more! roll on christmas! :P

Thanks for the tip to link the lib. It works fine .
But still the ipod is not working on rythm.. or gtkpod , the same story, data on ipod nothing on the screen :(
The only difference that I saw after the ipod-read-sys.... was that when I eject the ipod I don't get any error like I did before .

---

### Post by paradoxni on 2007-11-22
Ok I got hold of a new gen IPOD nano to test this out and was getting the same problem as you, empty IPOD even with songs uploaded to it with Rythmbox. I fixed it thou...

Delete the old libgpod libraries:
```
 sudo rm /usr/lib/libgpod.so.2.0.0
sudo rm /usr/lib/libgpod.so.2
```

Create links to the new one:
```

sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2

```

ipod-read-sysinfo-extended is supposed to create SysInfo file on IPOD with FirewireID inside, but it did not work here, so I added it manually:

Connect IPOD to PC, then
```

sudo lsusb -v | grep -i Serial

```

Note down your FirewireID from the list, its the 16 digit one.
```

 iSerial                 1 0000:00:1a.1
  iSerial                 3 000A27001AD21163  <---- IPOD FirewireID
  iSerial                 3 3547160158733600
          line coding and serial state
          line coding and serial state
  iSerial                 0 
  iSerial                 1 0000:00:1d.7
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1a.0
  iSerial                 0 
  iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 3 060114014271000001
  iSerial                 1 0000:00:1a.7

```

Create SysInfo file on IPOD (assuming IPOD mounted at /media/IPOD):

```

sudo gedit /media/IPOD/iPod_Control/Device/SysInfo

```

SysInfo should only contain:
```

FirewireGuid: 0x<your firewire ID>

e.g. FirewireGuid: 0x000A27001AD21163

```



Now load up Rhythmbox and remove songs from the IPOD, then put songs back on IPOD, then eject IPOD (rhythmbox may freeze for a short while).

Songs should now be visible on IPOD.

---

### Post by paradoxni on 2007-11-23
Just to add..ive given up Rhythmbox and now using Amarok...I like how it works with the IPOD much better and uploads album art to the ipod, which wasnt working on rhythmbox. Give it a try :)

---

### Post by ubuntios on 2007-11-23
> **paradoxni said:**
> Just to add..ive given up Rhythmbox and now using Amarok...I like how it works with the IPOD much better and uploads album art to the ipod, which wasnt working on rhythmbox. Give it a try :)

Thanks,  I hope to work for me also ,I'lll give it a try, 
DId you check if its working with gtkpod?

---

### Post by paradoxni on 2007-11-23
gtkpod works, just isnt that good :)

---

### Post by ubuntios on 2007-11-23
First of all I'd like to say that   YOU ARE THE MAN!!!
Finally is working , also to add something , after all this you need to reboot in order the changes to take place.Then load your favorite player and enjoy
One more thing, I connected to a windows box and is working also with iTunes so you can transfer file from your friends windows or whatever .

Many many thanks 

p.s
Add 'Solved' on the title so others can follow

---

### Post by jd8001 on 2007-11-24
Hey,
    I get this error after running the ./configure for ligbpod 

checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGPOD_CFLAGS
and LIBGPOD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



Any ideas?

J.D

---

### Post by ubuntios on 2007-11-24
> **jd8001 said:**
> Hey,
    I get this error after running the ./configure for ligbpod 

checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGPOD_CFLAGS
and LIBGPOD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



Any ideas?

J.D

From where are you trying to install glib-2 ?
Try to go to the Synaptic manager search for libgpod2, install it from there.
Then start  'paradoxni' how-to.
Follow the guide , it doesn't say anywhere to ./configure anything, I don't understand why you try to install glib-2(if is not all ready installed).
Anyway good luck :)

---

### Post by Folk Theory on 2007-11-24
i downloaded the files it says to in the OP but when i run make it says "make: *** No targets specified and no makefile found.  Stop.

what am i missing?

Thanks

---

### Post by paradoxni on 2007-11-24
did u do ./configure first?

---

### Post by paradoxni on 2007-11-24
> **jd8001 said:**
> Hey,
    I get this error after running the ./configure for ligbpod 

checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGPOD_CFLAGS
and LIBGPOD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



Any ideas?

J.D

try installing the required libraries first:

```
sudo apt-get install libglib2.0-0 libglib2.0-dev 
```

---

### Post by mtb-cliff on 2007-11-25
This last bit got me a little bit further as I was struggling with the same issue. Now, however, I am getting an error from the makefile in the PO directory:

Making all in po
make[2]: Entering directory `/home/userOne/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/userOne/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/userOne/libgpod-0.6.0'
make: *** [all] Error 2

Anyone have any ideas? Thanks, Cliff.

---

### Post by mtb-cliff on 2007-11-25
Found the problematic statement in the po/Makefile:

.po.gmo:
	file=`echo $* | sed 's,.*/,,'`.gmo \
	  && rm -f $$file && $(GMSGFMT) -o $$file $<

But I have no idea on how to fix it.

---

### Post by mtb-cliff on 2007-11-25
sol'n

The variable $(GMSGFMT) is apparently not set on your system. The GMSGFMT variable should be set by the configure script. Gettext is required to set GMSGFMT. I've seen several people having problems with this on Debian and *buntu systems. In all of the solutions I've seen, installing the gettext package was common.
Code:

sudo apt-get install gettext

---

### Post by Wobblybob on 2007-11-25
I have just been bought a iPod video classic 80GB for my birthday and am watching this thread with interest, has anyone got this model running on ubuntu yet or am I gonna be the first to try?  I'm still running 7.04 on the laptop at the moment.

---

### Post by paradoxni on 2007-11-25
should hopefully be the same as for the new nano's, let us know how you get on :)

---

### Post by Folk Theory on 2007-11-25
so i did the entire process and all worked fine. problem is..when i click eject it says theres data that needs to be written dont eject ipod. then  it says ipod ejected. and when i check it says no music...

so how do i make it write that data that it says it needs to write to the iPod? is it not verifying the database for some reason?

---

### Post by jo.pettitt on 2007-11-26
I have followed these instructions with ipod-read-sysinfo-extended and the longer way of manually adding the FirewireGuid to the file for my Classic 160gb with Firmware 1.0.2. 

It mounts fine and Amarok will let me load music to it and also delete etc. GTKPOD sees the files too. However, when back in iPod mode there appears to be no music so it is obviously not writing to the database file properly... Any ideas?

---

### Post by tafsen on 2007-11-26
After I installed these things, Rhytmbox crashes at startup.

 rhythmbox

(rhythmbox:5769): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)

Edit: After I started gtkpod once and created the system on it, I got Rhytmbox to work. But how do I add coverarts on music I allready have added?

Edit2: I found out how to do it with gtkpod,but even if it says it got cover in gtkPod, it doesn't show on the iPod.

Edit3: I works with amaroK for a strange reason :S

What program can I use to convert videos to iPod?

---

### Post by Folk Theory on 2007-11-26
very strange update!!
(read my above post to know what was happening before)
today i tried using rythmbox again...and it failed again.
then i used gtkpod and the first thing it did was greet me with a [quote=gtkpod]Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.[/quote]

i have no clue if that meant it cant access the ipod or if it cant get artwork for it, or if it cant verify the database...
so then i try to play a song from the ipod on gtkpod...[quote=gtkpod]could not find command xmms specified for 'play now'[/quote]
i erase a song from it and click save changes, eject, and surprise!! it actually worked! my ipod is now functional. oddly enough, rythmbox now works too...

now my questions
1. do i need to download xmms since gtkpod said it cant find it?
2. does gtkpod get artwork by itself or do i have to find the pics and then upload them somehow from gtkpod?

if you were having a similar problem then try gtkpod..itll make rythmbox magically work too! now im off to try amarok.

---

### Post by tafsen on 2007-11-26
I got the artwork right. Now I just want the Video :p

---

### Post by jo.pettitt on 2007-11-27
Also in Amarok once the new libgpod 0.6.0 has been built shouldn't it allow you to select the iPod Classic 80gb or 160gb from the iPod selection menu?

This still displays the same options (iPod video as highest sized iPod) as when libgpod 0.5.2 was installed.

---

### Post by paradoxni on 2007-11-27
> **jo.pettitt said:**
> Also in Amarok once the new libgpod 0.6.0 has been built shouldn't it allow you to select the iPod Classic 80gb or 160gb from the iPod selection menu?

This still displays the same options (iPod video as highest sized iPod) as when libgpod 0.5.2 was installed.
yes it should!? you have to set the correct model to get the artwork working with amarok.

[IMG]http://www.s44gan.com/ipod_amarok.jpg[/IMG]

So I can only presume your amarok is still using 0.5.2 libgpod, did you follow the instructions to delete the old libraries and link to the new ones? This would be why your music is not appearing on your ipod. I had the same problem until i deleted libgpod.so.2 and replaced with links to libgpod.so.3 as per my instructions on page 2.

---

### Post by bd_italy on 2007-11-27
Hi,

i just registered here because I found this thread with google and have some problems getting my Ipod Nano 3g 8gb work under ubuntu 7.10.
using amarok,gtkpod and rythmbox i can add songs to the ipod and delete them, other programs can find them as well.
But the ipod can't find the music altought the memory space on it is used.

i have installed amaroK 1.4.7, gtkpod 0.99.10, and rhythmbox 0.11.2 with the synaptic package manager.

which packages exactly do I need and where can I get them from?
When I try to build the latest libgpod (0.6.0) manually i get:

```
......
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/max/Desktop/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/max/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/max/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/max/Desktop/libgpod-0.6.0'
make: *** [all] Error 2

```

in the meanwhile I try to remove all packages and clean all, in order to avoid package conflicts,

hoping for quick replies and greets from italy
~bd_italy

Edit:
now I tried the steps suggested the steps on page 2 of this thread.
after starting rhythmbox it says Unable to activate plugin Portable Players - iPod , Why is that?

---

### Post by paradoxni on 2007-11-27
try 

```
sudo apt-get install gettext

```

and please report back if that solves the problem as a few others are getting the same error.

---

### Post by bd_italy on 2007-11-27
> **paradoxni said:**
> try 

```
sudo apt-get install gettext

```

and please report back if that solves the problem as a few others are getting the same error.

jeah, now it compiles just fine and in amaroK i can select the right ipod model.
i can now see the files on my ipod and coverart also works.

but i wonder if coverart also works with rhythmbox or gtkpod, since i plan to remove 
the (great) amaroK to avoid all that kde dependencies on my system.

thanks four the very fast help, you made my day :)

~bd_italy

---

### Post by paradoxni on 2007-11-27
I couldnt get coverart working with those programs, just amarok. I now use it as my prefered player, I like the coverart manager.

We now seem to be getting to the bottom of everyones problems, hopefully soon we can create a definitive guide to new gen ipods and Ubuntu.

---

### Post by crisnoh on 2007-11-27
Interesting problem... I can't find where my iPod is mounting to.

---

### Post by tafsen on 2007-11-28
type "dmesg | tail" after you mounted it.

I can't get gtkpod to transfer any of my converted videos. I've compiled everything from source with the mp4v2 lib, but it still doesn't work.

And I've tried to install gtkpod-aac.

I have also tried to transfer movies with thinliquidfilm, but then I only get sound and no video.

---

### Post by jo.pettitt on 2007-11-28
paradoxni - thanks for that screenshot, I don't see that at all. I'm suspecting that you are right about the wrong lib being used. I will redo those steps again. Many thanks!

---

### Post by crisnoh on 2007-11-28
Ok, I'm going to set aside the fact that I still can't find the mount point for my iPod for the moment.  I got the following error when I attempted to configure libgpod-0.6.0:

> checking for LIBGPOD... configure: error: Package requirements (glib-2.0 >= 2.8.0 gobject-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGPOD_CFLAGS
and LIBGPOD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I installed glib-2.12.0 and can't find gobject-2.0.  Regardless, I'm still getting the same error.

---

### Post by crisnoh on 2007-11-28
Disregard.  I didn't realize someone has already had this issue.

---

### Post by bandersnatch on 2007-11-28
howdy. i've been having the same problem with ipod connectivity (space taken up on ipod, but showing up as other media rather than music, etc.) i've downloaded the libgpod 0.6 package, ran the configure file, but when i tried to run the ./configure command in terminal it came up with the error message: 

jabberwock@jabberwock:~/Desktop/libgpod-0.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

i'm new at all this, but that's as far as i can get. any suggestions? am i just missing something stupid?

---

### Post by jo.pettitt on 2007-11-29
OK so I removed all traces of libgpod, rebuilt and relinked as per the instructions, created the file with the FirewireGuid number. Amarok wouldn't give me the option of the Classic 160Gb so I rebuilt my Amarok-svn and hey presto it showed up as an option.

All working now! The covers have transferred where I had them so I'm very happy. Thanks for help.

---

### Post by paradoxni on 2007-11-29
> **bandersnatch said:**
> howdy. i've been having the same problem with ipod connectivity (space taken up on ipod, but showing up as other media rather than music, etc.) i've downloaded the libgpod 0.6 package, ran the configure file, but when i tried to run the ./configure command in terminal it came up with the error message: 

jabberwock@jabberwock:~/Desktop/libgpod-0.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

i'm new at all this, but that's as far as i can get. any suggestions? am i just missing something stupid?

```
sudo apt-get install build-essential
```

---

### Post by ubuntios on 2007-11-29
Hi there 

I saw a lot of people asking if this is working or not.
I have a iPod nano 3G , I follow the how-to of 'paradoxni',in the 2 first pages of this thread and...
iPod nano is working fine with any media player, no problem ejecting ,unmount, etc.
Also I connect it after to a windows box and no problem with iTunes what so ever.
So probably there are some small things that you have to change in order to make it work, but the sure thing is that is working.

Good luck!

---

### Post by jo.pettitt on 2007-11-29
I've noticed that after listening to music all day at work that the play counts are not updated on Amarok when I resync the Classic 160Gb.

Anyone else having this issue?

---

### Post by crisnoh on 2007-11-29
I've about given up.  I've followed all the instructions here (spread out at they are) and I still can't see the music on my 80gb Classic.  libgpod is installed and my Firewire ID is in the SysInfo file.

---

### Post by paradoxni on 2007-11-29
just incase you have not tried this, your existing music will not appear if it was added before completing the steps in this post, you must add it all again.

---

### Post by crisnoh on 2007-11-29
Tried it and no luck.  Looks like I'm partially shackled to XP for just a little while longer.

---

### Post by jo.pettitt on 2007-11-30
In case it helps my info file is like this:

ModelNumStr: xB150
FirewireGuid: xxxxxxxxxxxxxx

Without the ModelNumStr, the iPod didn't show up. After rebuilding Amarok with iPod support the new libgpod was picked up and the option to choose the correct model was as the screenshot in previous pages.

---

### Post by bandersnatch on 2007-11-30
thanks for the build-essential command. it seemed to help.
i'm still running into some problems though. i've been trying to follow these steps:

Code:

sudo apt-get install libsgutils1 libsgutils1-dev

then download libgpod 0.6 if you havent already (if you have you need to recompile it again with the above packages now installed)

[http://sourceforge.net/project/showf...ease_id=553119](http://sourceforge.net/project/showf...ease_id=553119)

extract the contents of this archive (I downloaded it to my desktop and right clicked and chose 'extract here')

open a terminal and change to the extracted directory
Code:

cd Desktop/libgpod-0.6.0
./configure
make
sudo make install

Now thats done you should have an 'ipod-read-sysinfo-extended' tool available.

Code:

ipod-read-sysinfo-extended DEVICE MOUNTPOINT

e.g. ipod-read-sysinfo-extended /dev/sda /media/ipod

according to what i have read this will store your firewireID on the ipod so your music will be visible once you add all your music to your ipod again e.g. using rythmbox

when i get to the sysinfo command, it is giving me the message "bash: ipod-read-sysinfo-extended: command not found"

also, how do i set (or find out) where the mount point is (eg: /dev/sda.....etc.)?
thanks for the help (and the patience) with us beginners

---

### Post by zsugiart on 2007-12-01
Thank you very much for this great post. I managed to get my 3rd gen ipod Nano (finally). I was rather disappointed that there's NOTHING in ubuntu that I could use to work with my ipod nano - until this workaround. It's a bit of a pain, but such is the world of linux!

It's pretty good considering that, in Windows I think ppl are stuck with iTunes - otheralternatives like vpod and anapod can't get it working with the latest ipod gen yet ( I think? ) 

Anyway my ipod is lock&loaded and I'm a happy man!

---

### Post by paradoxni on 2007-12-01
> **bandersnatch said:**
> 
when i get to the sysinfo command, it is giving me the message "bash: ipod-read-sysinfo-extended: command not found"

also, how do i set (or find out) where the mount point is (eg: /dev/sda.....etc.)?
thanks for the help (and the patience) with us beginners

```

df

```
..will display the mounted devices, one of which should be your IPOD, assuming its connected.

bash: ipod-read-sysinfo-extended: command not found would indicate that this command hasnt been  found / hasnt compiled properly, so you may have to follow the instructions on manually creating the SYSINFO file. (page2)

---

### Post by bandersnatch on 2007-12-01
thanks again. this thread has been very helpful.

---

### Post by tafsen on 2007-12-02
Sudenly my iPod Nano won't charge!!! Anyone else had trouble with this?

---

### Post by ubuntios on 2007-12-02
> **crisnoh said:**
> Tried it and no luck.  Looks like I'm partially shackled to XP for just a little while longer.

Don't give up , try this program is working fine .

 Originally Posted by tafsen  View Post

[http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/)

This works perfect No need for windows anymore 

Thanks  'tafsen'

The only thing is that it doesn't have options for photos or video.
Does anybody have figure it out how to put photos to ipod ?

---

### Post by ColombianGold on 2007-12-05
pardaoxni...thanks for all the support!! 

I need your help...I've followed all your intructions and everything has worked well. My ipod is recognized and I can add music to it, the only thing is that when I eject it, I get no music on it.

I think (noob) libgpod 0.6 was not installed, should it appear in synaptic? All I get in synaptic is version 0.522.

When I was installing it, I got a bunch of errors that I have no clue...

I am attaching each step when I wworked with libgpod package. Im just guessing, the rest of the steps showed no errors.

Plz help me out...thanks

CG

---

### Post by ColombianGold on 2007-12-06
Fixed...it was a problem with my sources.list so I could not build dependencies.

If you get errors like mine...just edit your sources.list.

sudo gedit /etc/apt/sources.list

copy any of the repositories that are being used and add -src after deb...something like this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse

This did it for me. Hope it helps anybody.

Thanks, great howto

CG

---

### Post by Wobblybob on 2007-12-07
I'm using Gutsy 7.10 on an Intel PC and my iPod is an 80GB Classic with firmware 1.0.2, I can now use Amarok to upload music and GTKpod-acc to upload my video and all goes well and goodbye to itunes & windows. 

Thanks guys for your help, great stuff, it took me a couple of days and a little help from the following [[COLOR="Navy"]**http://ubuntuforums.org/showthread.php?t=619615**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=619615") post. I had all of the problems listed but after finally added the firmware id manually it worked me. [I may even try to do the same on the laptop now!]

now all we need is a way of uploading images but that's not a major problem.

---

### Post by conito on 2007-12-08
Hi, 
I've just follow all the steps as paradoxni explained. Thanks, now I can use my ipod with Amarok.

My problem now is that I can't upload the artwork with Amarok. The ./configure returned tha
ArtworkDB was not supported.
And reading the log i found:
checking for GDKPIXBUF... no

But i have libgdk-pixbuf-dev package installed, so I don't know what is missing.

Any ideas?

---

### Post by bandersnatch on 2007-12-09
Hello, I'm back with yet another question. When I went to create a firewire ID manually it gave me this:

jabberwock@jabberwock:~$ sudo lsusb -v | grep -i Serial
Password:
  iSerial                 0 
  iSerial                 1 0000:00:0b.0
  iSerial                 3 000A2700155CCE99
  iSerial                 1 0000:00:0b.1
jabberwock@jabberwock:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            151060676  20893364 122493868  15% /
varrun                  481228       112    481116   1% /var/run
varlock                 481228         0    481228   0% /var/lock
procbususb              481228       116    481112   1% /proc/bus/usb
udev                    481228       116    481112   1% /dev
devshm                  481228         0    481228   0% /dev/shm
lrm                     481228     38972    442256   9% /lib/modules/2.6.20-16-generic/volatile
jabberwock@jabberwock:~$ sudo gedit /iPod_Control/Device/Sysinfo

** (gedit:6645): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

it's missing the whole line coding and serial state bit. Also, when I checked the mount point there was nothing pertaining to my iPod. I was guessing it was the dev/sda1 so I went with that to no avail. Any suggestions?

---

### Post by conito on 2007-12-09
bandersnatch,
your firewireId is 000A2700155CCE99

regarding to the mounting point or device. In my case is sdb1
sda1 is your root in your case.

---

### Post by zygut on 2007-12-19
I've got everything installed fine, but when I plug in my ipod nano (3rd gen), I cannot edit the file to add the ID because its mounted read-only. dmesg tells me:

```

hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only
hfs: filesystem is marked journaled, leaving read-only

```

I'm a little concerned about force mounting the device read-write....

any ideas?

---

### Post by Folk Theory on 2007-12-19
yo its me again. everytn works fine. the problem i have is that amarok gets the artowrk but doesnt transfer it to the ipod...anyone managed to solve this?

---

### Post by ubuntios on 2007-12-19
> **zygut said:**
> I've got everything installed fine, but when I plug in my ipod nano (3rd gen), I cannot edit the file to add the ID because its mounted read-only. dmesg tells me:

```

hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only
hfs: filesystem is marked journaled, leaving read-only

```

I'm a little concerned about force mounting the device read-write....

any ideas?

Ok , listen a nice way to work as root on GUI.

Open the terminal and just type ' sudo ' before any program you want to run as root 
In your case type :  ' sudo gedit ' .  The g editor will open with root permissions.
Drag drop the file there, make the change and save it .Thats it !
This will save you the ' terminal way ' witch is a bit more complicated.
Also very helpful command is ' sudo nautilus ' , and then you can act as a root inside nautilus and avoid the terminal.


Hope that helps.

---

### Post by uiberto on 2007-12-20
Thanks guys, Amarok finally worked with the iPod. I had problems where Amarok was not using the new libgpod2 library. You could tell because Amarok did had a very limited and dated list of iPod models. This thread helped too: [http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+amarok&page=7](http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+amarok&page=7)

---

### Post by zygut on 2007-12-20
> **ubuntios said:**
> Ok , listen a nice way to work as root on GUI.

Open the terminal and just type ' sudo ' before any program you want to run as root 
In your case type :  ' sudo gedit ' .  The g editor will open with root permissions.
Drag drop the file there, make the change and save it .Thats it !
This will save you the ' terminal way ' witch is a bit more complicated.
Also very helpful command is ' sudo nautilus ' , and then you can act as a root inside nautilus and avoid the terminal.

Hope that helps.

Thanks, but I know how to edit files, thats not my problem.

---

### Post by Folk Theory on 2007-12-21
any way to transfer artwork?

---

### Post by omar_mandeel on 2007-12-22
Im having issues. I have followed the instructions and everything went fine until ¨make¨. Whenever I enter that command this is what I get:

omar@omar-laptop:~/Desktop/libgpod-0.6.0$ make
make  all-recursive
make[1]: Entering directory `/home/omar/Desktop/libgpod-0.6.0'
Making all in src
make[2]: Entering directory `/home/omar/Desktop/libgpod-0.6.0/src'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT db-artwork-debug.lo -MD -MP -MF ".deps/db-artwork-debug.Tpo" -c -o db-artwork-debug.lo db-artwork-debug.c; \
        then mv -f ".deps/db-artwork-debug.Tpo" ".deps/db-artwork-debug.Plo"; else rm -f ".deps/db-artwork-debug.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-artwork-debug.lo -MD -MP -MF .deps/db-artwork-debug.Tpo -c db-artwork-debug.c  -fPIC -DPIC -o .libs/db-artwork-debug.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-artwork-debug.lo -MD -MP -MF .deps/db-artwork-debug.Tpo -c db-artwork-debug.c -o db-artwork-debug.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT db-artwork-parser.lo -MD -MP -MF ".deps/db-artwork-parser.Tpo" -c -o db-artwork-parser.lo db-artwork-parser.c; \
        then mv -f ".deps/db-artwork-parser.Tpo" ".deps/db-artwork-parser.Plo"; else rm -f ".deps/db-artwork-parser.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-artwork-parser.lo -MD -MP -MF .deps/db-artwork-parser.Tpo -c db-artwork-parser.c  -fPIC -DPIC -o .libs/db-artwork-parser.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-artwork-parser.lo -MD -MP -MF .deps/db-artwork-parser.Tpo -c db-artwork-parser.c -o db-artwork-parser.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT db-artwork-writer.lo -MD -MP -MF ".deps/db-artwork-writer.Tpo" -c -o db-artwork-writer.lo db-artwork-writer.c; \
        then mv -f ".deps/db-artwork-writer.Tpo" ".deps/db-artwork-writer.Plo"; else rm -f ".deps/db-artwork-writer.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-artwork-writer.lo -MD -MP -MF .deps/db-artwork-writer.Tpo -c db-artwork-writer.c  -fPIC -DPIC -o .libs/db-artwork-writer.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-artwork-writer.lo -MD -MP -MF .deps/db-artwork-writer.Tpo -c db-artwork-writer.c -o db-artwork-writer.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT db-image-parser.lo -MD -MP -MF ".deps/db-image-parser.Tpo" -c -o db-image-parser.lo db-image-parser.c; \
        then mv -f ".deps/db-image-parser.Tpo" ".deps/db-image-parser.Plo"; else rm -f ".deps/db-image-parser.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-image-parser.lo -MD -MP -MF .deps/db-image-parser.Tpo -c db-image-parser.c  -fPIC -DPIC -o .libs/db-image-parser.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-image-parser.lo -MD -MP -MF .deps/db-image-parser.Tpo -c db-image-parser.c -o db-image-parser.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT db-parse-context.lo -MD -MP -MF ".deps/db-parse-context.Tpo" -c -o db-parse-context.lo db-parse-context.c; \
        then mv -f ".deps/db-parse-context.Tpo" ".deps/db-parse-context.Plo"; else rm -f ".deps/db-parse-context.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-parse-context.lo -MD -MP -MF .deps/db-parse-context.Tpo -c db-parse-context.c  -fPIC -DPIC -o .libs/db-parse-context.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT db-parse-context.lo -MD -MP -MF .deps/db-parse-context.Tpo -c db-parse-context.c -o db-parse-context.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_artwork.lo -MD -MP -MF ".deps/itdb_artwork.Tpo" -c -o itdb_artwork.lo itdb_artwork.c; \
        then mv -f ".deps/itdb_artwork.Tpo" ".deps/itdb_artwork.Plo"; else rm -f ".deps/itdb_artwork.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_artwork.lo -MD -MP -MF .deps/itdb_artwork.Tpo -c itdb_artwork.c  -fPIC -DPIC -o .libs/itdb_artwork.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_artwork.lo -MD -MP -MF .deps/itdb_artwork.Tpo -c itdb_artwork.c -o itdb_artwork.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_device.lo -MD -MP -MF ".deps/itdb_device.Tpo" -c -o itdb_device.lo itdb_device.c; \
        then mv -f ".deps/itdb_device.Tpo" ".deps/itdb_device.Plo"; else rm -f ".deps/itdb_device.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_device.lo -MD -MP -MF .deps/itdb_device.Tpo -c itdb_device.c  -fPIC -DPIC -o .libs/itdb_device.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_device.lo -MD -MP -MF .deps/itdb_device.Tpo -c itdb_device.c -o itdb_device.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_itunesdb.lo -MD -MP -MF ".deps/itdb_itunesdb.Tpo" -c -o itdb_itunesdb.lo itdb_itunesdb.c; \
        then mv -f ".deps/itdb_itunesdb.Tpo" ".deps/itdb_itunesdb.Plo"; else rm -f ".deps/itdb_itunesdb.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_itunesdb.lo -MD -MP -MF .deps/itdb_itunesdb.Tpo -c itdb_itunesdb.c  -fPIC -DPIC -o .libs/itdb_itunesdb.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_itunesdb.lo -MD -MP -MF .deps/itdb_itunesdb.Tpo -c itdb_itunesdb.c -o itdb_itunesdb.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_photoalbum.lo -MD -MP -MF ".deps/itdb_photoalbum.Tpo" -c -o itdb_photoalbum.lo itdb_photoalbum.c; \
        then mv -f ".deps/itdb_photoalbum.Tpo" ".deps/itdb_photoalbum.Plo"; else rm -f ".deps/itdb_photoalbum.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_photoalbum.lo -MD -MP -MF .deps/itdb_photoalbum.Tpo -c itdb_photoalbum.c  -fPIC -DPIC -o .libs/itdb_photoalbum.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_photoalbum.lo -MD -MP -MF .deps/itdb_photoalbum.Tpo -c itdb_photoalbum.c -o itdb_photoalbum.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_playlist.lo -MD -MP -MF ".deps/itdb_playlist.Tpo" -c -o itdb_playlist.lo itdb_playlist.c; \
        then mv -f ".deps/itdb_playlist.Tpo" ".deps/itdb_playlist.Plo"; else rm -f ".deps/itdb_playlist.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_playlist.lo -MD -MP -MF .deps/itdb_playlist.Tpo -c itdb_playlist.c  -fPIC -DPIC -o .libs/itdb_playlist.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_playlist.lo -MD -MP -MF .deps/itdb_playlist.Tpo -c itdb_playlist.c -o itdb_playlist.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_sha1.lo -MD -MP -MF ".deps/itdb_sha1.Tpo" -c -o itdb_sha1.lo itdb_sha1.c; \
        then mv -f ".deps/itdb_sha1.Tpo" ".deps/itdb_sha1.Plo"; else rm -f ".deps/itdb_sha1.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_sha1.lo -MD -MP -MF .deps/itdb_sha1.Tpo -c itdb_sha1.c  -fPIC -DPIC -o .libs/itdb_sha1.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_sha1.lo -MD -MP -MF .deps/itdb_sha1.Tpo -c itdb_sha1.c -o itdb_sha1.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_sysinfo.lo -MD -MP -MF ".deps/itdb_sysinfo.Tpo" -c -o itdb_sysinfo.lo itdb_sysinfo.c; \
        then mv -f ".deps/itdb_sysinfo.Tpo" ".deps/itdb_sysinfo.Plo"; else rm -f ".deps/itdb_sysinfo.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_sysinfo.lo -MD -MP -MF .deps/itdb_sysinfo.Tpo -c itdb_sysinfo.c  -fPIC -DPIC -o .libs/itdb_sysinfo.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_sysinfo.lo -MD -MP -MF .deps/itdb_sysinfo.Tpo -c itdb_sysinfo.c -o itdb_sysinfo.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT itdb_track.lo -MD -MP -MF ".deps/itdb_track.Tpo" -c -o itdb_track.lo itdb_track.c; \
        then mv -f ".deps/itdb_track.Tpo" ".deps/itdb_track.Plo"; else rm -f ".deps/itdb_track.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_track.lo -MD -MP -MF .deps/itdb_track.Tpo -c itdb_track.c  -fPIC -DPIC -o .libs/itdb_track.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT itdb_track.lo -MD -MP -MF .deps/itdb_track.Tpo -c itdb_track.c -o itdb_track.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT ithumb-writer.lo -MD -MP -MF ".deps/ithumb-writer.Tpo" -c -o ithumb-writer.lo ithumb-writer.c; \
        then mv -f ".deps/ithumb-writer.Tpo" ".deps/ithumb-writer.Plo"; else rm -f ".deps/ithumb-writer.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT ithumb-writer.lo -MD -MP -MF .deps/ithumb-writer.Tpo -c ithumb-writer.c  -fPIC -DPIC -o .libs/ithumb-writer.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT ithumb-writer.lo -MD -MP -MF .deps/ithumb-writer.Tpo -c ithumb-writer.c -o ithumb-writer.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT pixmaps.lo -MD -MP -MF ".deps/pixmaps.Tpo" -c -o pixmaps.lo pixmaps.c; \
        then mv -f ".deps/pixmaps.Tpo" ".deps/pixmaps.Plo"; else rm -f ".deps/pixmaps.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT pixmaps.lo -MD -MP -MF .deps/pixmaps.Tpo -c pixmaps.c  -fPIC -DPIC -o .libs/pixmaps.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT pixmaps.lo -MD -MP -MF .deps/pixmaps.Tpo -c pixmaps.c -o pixmaps.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -MT sha1.lo -MD -MP -MF ".deps/sha1.Tpo" -c -o sha1.lo sha1.c; \
        then mv -f ".deps/sha1.Tpo" ".deps/sha1.Plo"; else rm -f ".deps/sha1.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT sha1.lo -MD -MP -MF .deps/sha1.Tpo -c sha1.c  -fPIC -DPIC -o .libs/sha1.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT sha1.lo -MD -MP -MF .deps/sha1.Tpo -c sha1.c -o sha1.o >/dev/null 2>&1
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o libgpod.la -rpath /usr/local/lib -version-info 3:0:0 -no-undefined db-artwork-debug.lo db-artwork-parser.lo db-artwork-writer.lo db-image-parser.lo db-parse-context.lo itdb_artwork.lo itdb_device.lo itdb_itunesdb.lo itdb_photoalbum.lo itdb_playlist.lo itdb_sha1.lo itdb_sysinfo.lo itdb_track.lo ithumb-writer.lo pixmaps.lo sha1.lo  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   
gcc -shared  .libs/db-artwork-debug.o .libs/db-artwork-parser.o .libs/db-artwork-writer.o .libs/db-image-parser.o .libs/db-parse-context.o .libs/itdb_artwork.o .libs/itdb_device.o .libs/itdb_itunesdb.o .libs/itdb_photoalbum.o .libs/itdb_playlist.o .libs/itdb_sha1.o .libs/itdb_sysinfo.o .libs/itdb_track.o .libs/ithumb-writer.o .libs/pixmaps.o .libs/sha1.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so  -Wl,-soname -Wl,libgpod.so.3 -o .libs/libgpod.so.3.0.0
(cd .libs && rm -f libgpod.so.3 && ln -s libgpod.so.3.0.0 libgpod.so.3)
(cd .libs && rm -f libgpod.so && ln -s libgpod.so.3.0.0 libgpod.so)
ar cru .libs/libgpod.a  db-artwork-debug.o db-artwork-parser.o db-artwork-writer.o db-image-parser.o db-parse-context.o itdb_artwork.o itdb_device.o itdb_itunesdb.o itdb_photoalbum.o itdb_playlist.o itdb_sha1.o itdb_sysinfo.o itdb_track.o ithumb-writer.o pixmaps.o sha1.o
ranlib .libs/libgpod.a
creating libgpod.la
(cd .libs && rm -f libgpod.la && ln -s ../libgpod.la libgpod.la)
make[2]: Leaving directory `/home/omar/Desktop/libgpod-0.6.0/src'
Making all in tools
make[2]: Entering directory `/home/omar/Desktop/libgpod-0.6.0/tools'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I../src -g -O2 -MT ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o -MD -MP -MF ".deps/ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.Tpo" -c -o ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o `test -f 'read-sysinfoextended-sgutils.c' || echo './'`read-sysinfoextended-sgutils.c; \
        then mv -f ".deps/ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.Tpo" ".deps/ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.Po"; else rm -f ".deps/ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I../src -g -O2 -MT ipod_read_sysinfo_extended-ipod-scsi-inquiry.o -MD -MP -MF ".deps/ipod_read_sysinfo_extended-ipod-scsi-inquiry.Tpo" -c -o ipod_read_sysinfo_extended-ipod-scsi-inquiry.o `test -f 'ipod-scsi-inquiry.c' || echo './'`ipod-scsi-inquiry.c; \
        then mv -f ".deps/ipod_read_sysinfo_extended-ipod-scsi-inquiry.Tpo" ".deps/ipod_read_sysinfo_extended-ipod-scsi-inquiry.Po"; else rm -f ".deps/ipod_read_sysinfo_extended-ipod-scsi-inquiry.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o ipod-read-sysinfo-extended  ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o ipod_read_sysinfo_extended-ipod-scsi-inquiry.o -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    -lsgutils ../src/libgpod.la 
mkdir .libs
gcc -g -O2 -o .libs/ipod-read-sysinfo-extended ipod_read_sysinfo_extended-read-sysinfoextended-sgutils.o ipod_read_sysinfo_extended-ipod-scsi-inquiry.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so //usr/lib/libsgutils.so ../src/.libs/libgpod.so  -Wl,--rpath -Wl,//usr/lib
creating ipod-read-sysinfo-extended
make[2]: Leaving directory `/home/omar/Desktop/libgpod-0.6.0/tools'
Making all in tests
make[2]: Entering directory `/home/omar/Desktop/libgpod-0.6.0/tests'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT itdb_main.o -MD -MP -MF ".deps/itdb_main.Tpo" -c -o itdb_main.o itdb_main.c; \
        then mv -f ".deps/itdb_main.Tpo" ".deps/itdb_main.Po"; else rm -f ".deps/itdb_main.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-itdb  itdb_main.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
mkdir .libs
gcc -g -O2 -o .libs/test-itdb itdb_main.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-itdb
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT test-ls.o -MD -MP -MF ".deps/test-ls.Tpo" -c -o test-ls.o test-ls.c; \
        then mv -f ".deps/test-ls.Tpo" ".deps/test-ls.Po"; else rm -f ".deps/test-ls.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-ls  test-ls.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-ls test-ls.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-ls
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT test-checksum.o -MD -MP -MF ".deps/test-checksum.Tpo" -c -o test-checksum.o test-checksum.c; \
        then mv -f ".deps/test-checksum.Tpo" ".deps/test-checksum.Po"; else rm -f ".deps/test-checksum.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-checksum  test-checksum.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-checksum test-checksum.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-checksum
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT test-fw-id.o -MD -MP -MF ".deps/test-fw-id.Tpo" -c -o test-fw-id.o test-fw-id.c; \
        then mv -f ".deps/test-fw-id.Tpo" ".deps/test-fw-id.Po"; else rm -f ".deps/test-fw-id.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-firewire-id  test-fw-id.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-firewire-id test-fw-id.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-firewire-id
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT test_thumbnails-test-covers.o -MD -MP -MF ".deps/test_thumbnails-test-covers.Tpo" -c -o test_thumbnails-test-covers.o `test -f 'test-covers.c' || echo './'`test-covers.c; \
        then mv -f ".deps/test_thumbnails-test-covers.Tpo" ".deps/test_thumbnails-test-covers.Po"; else rm -f ".deps/test_thumbnails-test-covers.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-thumbnails  test_thumbnails-test-covers.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-thumbnails test_thumbnails-test-covers.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-thumbnails
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT test_write_thumbnails-test-write-covers.o -MD -MP -MF ".deps/test_write_thumbnails-test-write-covers.Tpo" -c -o test_write_thumbnails-test-write-covers.o `test -f 'test-write-covers.c' || echo './'`test-write-covers.c; \
        then mv -f ".deps/test_write_thumbnails-test-write-covers.Tpo" ".deps/test_write_thumbnails-test-write-covers.Po"; else rm -f ".deps/test_write_thumbnails-test-write-covers.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-write-thumbnails  test_write_thumbnails-test-write-covers.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-write-thumbnails test_write_thumbnails-test-write-covers.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-write-thumbnails
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT test_photos-test-photos.o -MD -MP -MF ".deps/test_photos-test-photos.Tpo" -c -o test_photos-test-photos.o `test -f 'test-photos.c' || echo './'`test-photos.c; \
        then mv -f ".deps/test_photos-test-photos.Tpo" ".deps/test_photos-test-photos.Po"; else rm -f ".deps/test_photos-test-photos.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-photos  test_photos-test-photos.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-photos test_photos-test-photos.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-photos
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT get-timezone.o -MD -MP -MF ".deps/get-timezone.Tpo" -c -o get-timezone.o get-timezone.c; \
        then mv -f ".deps/get-timezone.Tpo" ".deps/get-timezone.Po"; else rm -f ".deps/get-timezone.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o get-timezone  get-timezone.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/get-timezone get-timezone.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating get-timezone
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\"    -g -O2 -MT test-init-ipod.o -MD -MP -MF ".deps/test-init-ipod.Tpo" -c -o test-init-ipod.o test-init-ipod.c; \
        then mv -f ".deps/test-init-ipod.Tpo" ".deps/test-init-ipod.Po"; else rm -f ".deps/test-init-ipod.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o test-init-ipod  test-init-ipod.o  -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-init-ipod test-init-ipod.o  /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so 
creating test-init-ipod
make[2]: Leaving directory `/home/omar/Desktop/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/omar/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/omar/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/omar/Desktop/libgpod-0.6.0'
make: *** [all] Error 2
omar@omar-laptop:~/Desktop/libgpod-0.6.0$ 


(sorry, I dont know how to put it in a little code box.)

---

### Post by apd on 2007-12-26
cd Desktop/libgpod-0.6.0
./configure
make

does´nt work

---

### Post by paradoxni on 2007-12-27
> **omar_mandeel said:**
> 
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/omar/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/omar/Desktop/libgpod-0.6.0'
make: *** [all] Error 2
omar@omar-laptop:~/Desktop/libgpod-0.6.0$ 


(sorry, I dont know how to put it in a little code box.)

sudo apt-get install gettext

should help with compiling (this was solved in this very thread a few pages ago!)

---

### Post by paradoxni on 2007-12-27
> **Folk Theory said:**
> any way to transfer artwork?

I will assume you have compilied and installed libgpod 0.6 ? and stored you firewireid on the ipod?

if so start amarok, goto devices, make sure your ipod is connected/detected, then click the button (see pic below) to set the correct model to get the artwork to work.

[ATTACH]54381[/ATTACH]

If the list of ipods models is outdated (no classic 80GB etc) then your still using the old libgpod library, go back to the first few pages of this thread and read everything.

---

### Post by paradoxni on 2007-12-27
Finally I have my very own IPOD Classic 80GB (xmas pressie!!) and due to what I have learned from all my posts to this thread, it connected fine and transfered all my albums including artwork using amarok. Works fantastically well. Here's the proof that album art works :)

[ATTACH]54384[/ATTACH]

Now to figure out how to get Photos on to it!?

---

### Post by Folk Theory on 2007-12-29
well its weird really. the artwork is there because it shows it on the menus, and yet, when i go to show artowork or when playing a song it wont display it. do you think if i erase all music and sync it again but using amarok this time then it will actually display it?

---

### Post by mcgodx on 2007-12-29
I tried to do this, but my system does not appear to be set up right or something is wrong... when I do  ./configure, it SEEMS like all is going well, it gives me the following, after all the checks:

```
Configuration for libgpod 0.6.0 :
--------------------------------

 Host System Type .....: x86_64-unknown-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc 
 Compiler .............: gcc -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall  -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
 Linker ...............: gcc   -lgobject-2.0 -lglib-2.0    -lgobject-2.0 -lglib-2.0  
 ArtworkDB support ....: no
 Python bindings ......: no
 PyGObject support ....: yes

 Now type 'make' to build libgpod 0.6.0,
 and then 'make install' for installation.

```

Then when I do make, I get the following output after a bunch of other script stuff:

```
make  all-recursive
make[1]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0'
Making all in src
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/src'
Making all in tools
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/tools'
Making all in tests
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/tests'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0'
make: *** [all] Error 2

```

Any idea?  Thanks.

---

### Post by Eladamri03 on 2007-12-30
This thread has been very helpful, if a bit scatted. I have managed to get my 4G Nano  Video to recognize the songs I put on it with Amarok. The songs will play back with amarok, rythmbox, and even totem.

The issue I am having is that when I hit play on a song after ejecting, the ipod goes to the song's play screen and just sits there. It says its playing but the time/progress bar doesn't move and no sound can be heard other than the click of the volume wheel.

Edit - I had the headphones properly connected. Of course!

I haven't been able to find any other reference to this kind of problem. I dropped windows like the bad habit it is a few months back and this is the first time a problem has come up that I couldn't figure out. Please help!

---

### Post by evolmachine on 2007-12-30
> **paradoxni said:**
> I will assume you have compilied and installed libgpod 0.6 ? and stored you firewireid on the ipod?

if so start amarok, goto devices, make sure your ipod is connected/detected, then click the button (see pic below) to set the correct model to get the artwork to work.

[ATTACH]54381[/ATTACH]

If the list of ipods models is outdated (no classic 80GB etc) then your still using the old libgpod library, go back to the first few pages of this thread and read everything.

I have the 8GB iPod Nano Video (3rd Gen) selected, but its still not updating the artwork on the iPod.  All songs transfer just fine, and when I eject it I can listen to music off the iPod, so the instructions so far have worked just fine for me.  However, no matter what I try, artwork still doesn't work.  Any suggestions?

Thanks tho for helping me get the music working.  I can live without album art.  I can't live without music at work :)

---

### Post by paradoxni on 2007-12-30
> **mcgodx said:**
> I tried to do this, but my system does not appear to be set up right or something is wrong... when I do  ./configure, it SEEMS like all is going well, it gives me the following, after all the checks:

```
Configuration for libgpod 0.6.0 :
--------------------------------

 Host System Type .....: x86_64-unknown-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc 
 Compiler .............: gcc -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall  -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
 Linker ...............: gcc   -lgobject-2.0 -lglib-2.0    -lgobject-2.0 -lglib-2.0  
 ArtworkDB support ....: no
 Python bindings ......: no
 PyGObject support ....: yes

 Now type 'make' to build libgpod 0.6.0,
 and then 'make install' for installation.

```

Then when I do make, I get the following output after a bunch of other script stuff:

```
make  all-recursive
make[1]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0'
Making all in src
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/src'
Making all in tools
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/tools'
Making all in tests
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/tests'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/mylan/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mylan/Desktop/libgpod-0.6.0'
make: *** [all] Error 2

```

Any idea?  Thanks.

sudo apt-get install gettext

---

### Post by reclusivemonkey on 2008-01-01
Hello,

This thread has been really useful for me as I have just received my free iPod Classic 80 Gb =]

I've managed to compile libgpod and get it working no problem. However, I still can't get gtkpod to add any album art. I've even downloaded and compiled the latest gtkpod from the website, but whenever I try to add any album artwork, I just get

```
Failed to set cover art: '/home/ftp/media/music/A Guy Called Gerald/Black Secret Technology/artwork.jpg'
```

Has anyone got album art working with gtkpod? I'm currently using iTunes to manage my iPod but would love to get it working in Ubuntu.

P.S. Tried Amarok; it won't even recognise my iPod.

---

### Post by omar_mandeel on 2008-01-03
> **paradoxni said:**
> sudo apt-get install gettext

I still get the same error

---

### Post by CheeseEatingBulldog on 2008-01-05
> **paradoxni said:**
> Ok I got hold of a new gen IPOD nano to test this out and was getting the same problem as you, empty IPOD even with songs uploaded to it with Rythmbox. I fixed it thou...

Delete the old libgpod libraries:
```
 sudo rm /usr/lib/libgpod.so.2.0.0
sudo rm /usr/lib/libgpod.so.2
```

Create links to the new one:
```

sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2

```

ipod-read-sysinfo-extended is supposed to create SysInfo file on IPOD with FirewireID inside, but it did not work here, so I added it manually:

Connect IPOD to PC, then
```

sudo lsusb -v | grep -i Serial

```

Note down your FirewireID from the list, its the 16 digit one.
```

 iSerial                 1 0000:00:1a.1
  iSerial                 3 000A27001AD21163  <---- IPOD FirewireID
  iSerial                 3 3547160158733600
          line coding and serial state
          line coding and serial state
  iSerial                 0 
  iSerial                 1 0000:00:1d.7
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1a.0
  iSerial                 0 
  iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 3 060114014271000001
  iSerial                 1 0000:00:1a.7

```

Create SysInfo file on IPOD (assuming IPOD mounted at /media/IPOD):

```

sudo gedit /media/IPOD/iPod_Control/Device/SysInfo

```

SysInfo should only contain:
```

FirewireGuid: 0x<your firewire ID>

e.g. FirewireGuid: 0x000A27001AD21163

```



Now load up Rhythmbox and remove songs from the IPOD, then put songs back on IPOD, then eject IPOD (rhythmbox may freeze for a short while).

Songs should now be visible on IPOD.

I tried what it said in this thread but get an error when writing firewire file on ipod:

You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.

---

### Post by shawnrgr on 2008-01-08
Installed gettext like i saw a few posts back. so i went to reconfigure the package, below is the output.

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for intltool >= 0.21... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... yes
checking for sg_ll_inquiry in -lsgutils... yes
checking for HAL... no
checking for TAGLIB... no
checking for GDKPIXBUF... no
checking for PYGOBJECT... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  de es fr he it ja ro sv
checking whether to build python bindings... yes
checking for python... /usr/bin/python
checking whether /usr/bin/python version >= 2.1.1... yes
checking for /usr/bin/python version... 2.5
checking for /usr/bin/python platform... linux2
checking for /usr/bin/python script directory... ${prefix}/lib/python2.5/site-packages
checking for /usr/bin/python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for python development headers... not found
checking for more warnings... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bindings/Makefile
config.status: creating bindings/python/gpod.i
config.status: creating bindings/python/Makefile
config.status: creating bindings/python/examples/Makefile
config.status: creating bindings/python/tests/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/version.xml
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating tests/Makefile
config.status: creating libgpod-1.0.pc
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

```

The final result was of this...

Configuration for libgpod 0.6.0 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc 
 Compiler .............: gcc -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall  
 Linker ...............: gcc   -lgobject-2.0 -lglib-2.0    
[COLOR="Red"][B] ArtworkDB support ....: no
 Python bindings ......: no
 PyGObject support ....: no[/B][/COLOR]

 Now type 'make' to build libgpod 0.6.0,
 and then 'make install' for installation.

---

I'm guessing this isn't right. can anyone steer me in the right direction. ?

---

### Post by tigerplug on 2008-01-10
Does this work with the iPod touch?

---

### Post by jd8001 on 2008-01-10
Hey,
    Just wanted to say that I have used the method described for my new ipod nano (8 GB) twice and it has worked twice. This seems like a pattern with Ubuntu, i.e. once you find the solution, it is ridiculously easy to implement, but the solution itself is elusive. I admit I did use my wife's laptop to restore the ipod to its factory settings after messing with it in banshee (she has windows and itunes on her machine) and it was quite the trip back. Oh how I don't miss the days of three minute boot ups and nebulous applications running in the background. Anyway hope this lends credence to the method above

J.D Beck

---

### Post by paradoxni on 2008-01-12
for those who cannot manage to compile libgpod 0.6, try installing this [ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/libgpod2_0.5.3+actually0.6.0-0.1_i386.deb](ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod/libgpod2_0.5.3+actually0.6.0-0.1_i386.deb)

then continue the instructions to add your firewireID

which installs libgpod 0.6 pretending to be ligbpod 0.5.3

aint dont it myself but others have claimed it works.

---

### Post by chemical on 2008-01-27
Is anyone experiencing Ipod crashes when it's trying to show cover art previews? (the ones on the side in the menus)
I've got the green 8gb ipod nano video and the songs transfer and play correctly, but I can hear them only if I move quickly through the menus, so it doesn't try to load the covers.

Thanks for help!

---

### Post by mcraig on 2008-02-08
Just like to say thanks first of all to all the people who've posted on this thread for their help, hopefully I can provide the final piece of the puzzle for someone else.

I was getting this same problem when running configure

ArtworkDB support ....: no
Python bindings ......: no
PyGObject support ....: no

I found that installing libgtk2.0-dev fixed the ArtworkDB support and installing
python-gobject-dev fixed the PyGObject support.

I couldn't fix the python bindings but, I think you only really need the artwork support to get
cover art. After recompiling my libs I had cover art :D

Hope that helps someone else.

---

### Post by craigsall on 2008-02-19
After a lot painstaking research and many reformats of my ipod nano 3g I came across [this link ]("http://thefunkcorner.blogspot.com/2007/10/ubuntu-ipod-nano.html")somewhere. Anyways, let me know how this works for you.

---

### Post by bren on 2008-02-19
for paradoxni in post #93 thanks this worked for me

[COLOR="Red"] edit: forgot to mention you also have to del old libs and link to new ones as mentioned on this thread someweher[/COLOR]

1) for silver Nano video 8GB / Gutsy Gibbon
2) install .deb in post #93
3) use lsusb as per posts further up to create correct SysInfo file  In my case this was
FirewireGuid: 0x000A27001A29D352
4) Start Amarok 1.4.8
5) Settings | Configure Amarok and check your device is showing up OK in the DEVICES TAB
6) go back to main Amarok Screen
7) Select Devices from Tab at bottom left of screen
8) At right click menu "Ipod" and select the correct model (Ipod Video Nano Silver 8GB).   Note you may have to click small arrows pointing right to get Ipod menu to show.    Arrows are just to right of TRANSFER
9) You are IN
10) Playlists and songs sync just like you want them to

NNOOOOO MOOORRRREEEE IIIIIITTTUUUUNEEESS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


Have fun

bren

---

### Post by Muscar on 2008-02-28
I just get:

bash: ipod-read-sysinfo-extended: command not found

---

### Post by nbv4 on 2008-03-02
does anyone know if all this work is going to be required to get a new iPod working with Ubuntu 8.04? I really want to ditch XP on my laptop, but can't at the moment, because I need it sync my iPod.

---

### Post by Mega_Fauna on 2008-03-02
HI, 

I've tried this tutorial and got as far as ./configure. This is what the terminal gave me:

> constantine@Constantine-desktop:~/Desktop/libgpod-0.6.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
constantine@Constantine-desktop:~/Desktop/libgpod-0.6.0$ 

I've reinstalled my system twice this weekend trying to get my 80gig classic working, any and all help is really welcomed.

---

### Post by jw5801 on 2008-03-02
> **nbv4 said:**
> does anyone know if all this work is going to be required to get a new iPod working with Ubuntu 8.04? I really want to ditch XP on my laptop, but can't at the moment, because I need it sync my iPod.

It's really not all that much work. All we're doing is compiling and installing a newer version of the libraries that ship with gtkpod (and anything else that wants to connect to an iPod). One would assume that Hardy will have the newer version of the library in it's repositories, so manual compilation and installation shouldn't be necessary. I'm not sure what the progress on a workaround for the firewire port issue is, however. So you may still need to do a little work to get it working properly.

---

### Post by jw5801 on 2008-03-02
> **Mega_Fauna said:**
> HI, 

I've tried this tutorial and got as far as ./configure. This is what the terminal gave me:



I've reinstalled my system twice this weekend trying to get my 80gig classic working, any and all help is really welcomed.

Do you have build-essential installed?
```
sudo apt-get install build-essential
```

---

### Post by Mega_Fauna on 2008-03-03
> **jw5801 said:**
> Do you have build-essential installed?
```
sudo apt-get install build-essential
```

Thanks! That was it. My next problem for anyone's advice is that make is giving me these errors: 
[INDENT]
user@usere-desktop:~/Desktop/libgpod-0.6.0$ make
make  all-recursive
make[1]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0'
Making all in src
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/src'
Making all in tools
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/tools'
Making all in tests
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/tests'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0'
make: *** [all] Error 2
user@user-desktop:~/Desktop/libgpod-0.6.0$ [/INDENT]

Despite those errors I went ahead and did a sudo make install anyways (foolish?) and now Amarok recognizes the iPod but it appeared blank when I unplugged it. Sooo, before I go about linking libraries and uninstalling old stuff as detailed earlier in this thread, am I on the right track? Should I plow ahead or redo the above stuff (and how) till it's error free?

---

### Post by jw5801 on 2008-03-03
Maybe try it as root? ```
sudo make
```

---

### Post by Mega_Fauna on 2008-03-03
Hi, Thanks but unfortunately I get the same errors: 

[INDENT]constantine@Constantine-desktop:~/Desktop/libgpod-0.6.0$ sudo make
[sudo] password for constantine:
make  all-recursive
make[1]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0'
Making all in src
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/src'
Making all in tools
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/tools'
Making all in tests
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/tests'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/tests'
Making all in po
make[2]: Entering directory `/home/constantine/Desktop/libgpod-0.6.0/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127
make[2]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/constantine/Desktop/libgpod-0.6.0'
make: *** [all] Error 2[/INDENT]

---

### Post by jw5801 on 2008-03-03
```
sudo apt-get install gettext
./configure
make
sudo make install
```

The configure script screws up if gettext isn't installed.

---

### Post by reclusivemonkey on 2008-03-03
> **nbv4 said:**
> does anyone know if all this work is going to be required to get a new iPod working with Ubuntu 8.04? I really want to ditch XP on my laptop, but can't at the moment, because I need it sync my iPod.

I *very* briefly checked it with a install of Hardy Heron on my laptop; it seemed to work fine, Album Art was no problem. Although I had to ditch HH on my laptop as the wireless card no longer works.

I have a Mac Mini arriving this week, I'm pretty sure that will work with my iPod Classic ;-)

---

### Post by Mega_Fauna on 2008-03-03
> **jw5801 said:**
> ```
sudo apt-get install gettext
./configure
make
sudo make install
```

The configure script screws up if gettext isn't installed.

Thanks mate - That was it!

____________________________-

My next problem is that Amarok can transfer items to the iPod but the iPod is blank when ejected. I have done paradoxni's delete the old libraries, link new ones, and sysID the Firewire tutorial, but it doesn't work for Amarok.

GTK Pod has  transferred files successfully when Amarok isn't running. I have to create .m3u playlists, and import them into GTK for the system to work.

Any advice please?

---

### Post by bren on 2008-03-03
[QUOTE=Mega_Fauna;4445669
My next problem is that Amarok can transfer items to the iPod but the iPod is blank when ejected. I have done paradoxni's delete the old libraries, link new ones, and sysID the Firewire tutorial, but it doesn't work for Amarok.

[/QUOTE]

Yes, Amarok does work!  For me!

I had one small problem about unmounting the ipod which didn't seem to work properly which had the symptoms you describe

try this once and see if it works - i put it in a script called ipodeject which i call BEFORE physically disconnecting

sudo umount /media/BREN\'S\ IPOD*
sudo eject /dev/sda

it is the later line that seems to do the trick.....
it takes about 5 secs for it to work ..... then you see the IPOD screen change from "connected" to "disconnecting".....

try that....

if that doesn't work you should be aware that transferring stuff to the ipod but finding no music when you disconnect probably means you messed up the ID/library links up the thread somewhere ..... check my earlier post and post #93

good luck - amarok is great when you have it working (right click playlist .. sync to ipod)

bren

---

### Post by Mega_Fauna on 2008-03-03
> **bren said:**
> Yes, Amarok does work!  For me!

I had one small problem about unmounting the ipod which didn't seem to work properly which had the symptoms you describe

try this once and see if it works - i put it in a script called ipodeject which i call BEFORE physically disconnecting

sudo umount /media/BREN\'S\ IPOD*
sudo eject /dev/sda

it is the later line that seems to do the trick.....
it takes about 5 secs for it to work ..... then you see the IPOD screen change from "connected" to "disconnecting".....

try that....

if that doesn't work you should be aware that transferring stuff to the ipod but finding no music when you disconnect probably means you messed up the ID/library links up the thread somewhere ..... check my earlier post and post #93

good luck - amarok is great when you have it working (right click playlist .. sync to ipod)

bren

Bren thanks for the advice. However...

I want to try to recompile libpod again from scratch and try it out. How do I uninstall the old one (which doesn't support album artwork / Amarok prior to installing the new one in?

---

### Post by bren on 2008-03-03
hi mega_fauna

you should be able to do this from SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER....

see attached for when i searched for libgpod

try that......

bren

---

### Post by Mega_Fauna on 2008-03-05
> **bren said:**
> hi mega_fauna

you should be able to do this from SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER....

see attached for when i searched for libgpod

try that......

bren


Thanks, that worked perfectly. I uninstalled it (and the dependent software), made a list of off the packages which I had previously missed when installing, installed them, and compiled the package (as well as reinstalling Amarok and such). Now the iPod runs with .m3u playlists dropped onto it via GKTPod (not Amarok though).

__________________________

Minor problems:
No python bindings - I read on a blog that this is stopping me from putting the video onto iPod. Can anyone advise on how I install them?

Album Artwork
I'd estimate that about 1% of my album artwork has been successfully transferred to the iPod, Does anyone know the whys and wherefores of this (and their fixes)?

Won't talk to Amarok
I've been told that I have to recompile Amarok (from #Amarok) to get it to work properly. My iPod Classic is Silver, I'm not even sure that it is properly supported by Amarok.....

---

### Post by bren on 2008-03-06
> Thanks, that worked perfectly

great!

>  I uninstalled it (and the dependent software), made a list of off the packages which I had previously missed when installing, installed them, and compiled the package (as well as reinstalling Amarok and such). Now the iPod runs with .m3u playlists dropped onto it via GKTPod (not Amarok though).



hmmnnn Amarok works great for me...

> Minor problems:
No python bindings - I read on a blog that this is stopping me from putting the video onto iPod. Can anyone advise on how I install them?

i don't know but the synaptic screenshot a couple of posts up has a package that looks like python for pod....

> Album Artwork
I'd estimate that about 1% of my album artwork has been successfully transferred to the iPod, Does anyone know the whys and wherefores of this (and their fixes)?

i have same situation but have not worried about it....
ipod is full already withouth artwork.... :)

> 
Won't talk to Amarok
I've been told that I have to recompile Amarok (from #Amarok) to get it to work properly. My iPod Classic is Silver, I'm not even sure that it is properly supported by Amarok.....

I think it is did you set the model correctly in Amarok - [COLOR="Red"]see attached screenshot [/COLOR]
Of course the guys in #Amarok know more than me...
My Amarok is 1.4.8 which i installed from .deb package (i think if i recall correctly) ie. not vanilla Gutys version

bren

---

### Post by briansvgs on 2008-03-26
I need help getting python-gpod 0.6 on my ubuntu system. I got my ipod working, but I have several programs such as exaile which won't work (with my ipod) without python-gpod.  I know that I need to recompile libgpod0.6 with the python extension, but I don't know the path and it doesn't seem to be finding it correctly. If this helps at all, the extension to configure is:

libgpod --with-python=pathtopython

---

### Post by jw5801 on 2008-03-26
You could try and be shifty and use:
```
./configure --with-python=`which python`
```
But it'd probably be safer to just use /usr/bin/python. If you're ever trying to find where a binary is, the simplest way to do so is to use the "which" command:
```
jw5801@jw5801:~$ which python
/usr/bin/python
```

---

### Post by briansvgs on 2008-03-26
I had been thinking that it was looking for the libraries and stuff (all the files, not just the binary) so I had specified the location of them (/usr/share/.....) using locate to find it. But specifying the location of the binary doesn't seem to work either.......here is my output from ./configure --with-python=/usr/bin/python

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for intltool >= 0.21... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... yes
checking for sg_ll_inquiry in -lsgutils... yes
checking for HAL... yes
checking for TAGLIB... no
checking for GDKPIXBUF... yes
checking for PYGOBJECT... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  de es fr he it ja ro sv
checking whether to build python bindings... yes
checking whether /usr/bin/python2.5 version >= 2.1.1... yes
checking for /usr/bin/python2.5 version... 2.5
checking for /usr/bin/python2.5 platform... linux2
checking for /usr/bin/python2.5 script directory... ${prefix}/lib/python2.5/site-packages
checking for /usr/bin/python2.5 extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for python development headers... not found
checking for more warnings... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bindings/Makefile
config.status: creating bindings/python/gpod.i
config.status: creating bindings/python/Makefile
config.status: creating bindings/python/examples/Makefile
config.status: creating bindings/python/tests/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/version.xml
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating tests/Makefile
config.status: creating libgpod-1.0.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Configuration for libgpod 0.6.0 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc 
 Compiler .............: gcc -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   
 Linker ...............: gcc   -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   
 ArtworkDB support ....: yes
 Python bindings ......: no
 PyGObject support ....: no

 Now type 'make' to build libgpod 0.6.0,
 and then 'make install' for installation.

---

### Post by jw5801 on 2008-03-26
> **briansvgs said:**
> I had been thinking that it was looking for the libraries and stuff (all the files, not just the binary) so I had specified the location of them (/usr/share/.....) using locate to find it. But specifying the location of the binary doesn't seem to work either.......here is my output from ./configure --with-python=/usr/bin/python

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for intltool >= 0.21... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... yes
checking for sg_ll_inquiry in -lsgutils... yes
checking for HAL... yes
checking for TAGLIB... no
checking for GDKPIXBUF... yes
checking for PYGOBJECT... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  de es fr he it ja ro sv
checking whether to build python bindings... yes
checking whether /usr/bin/python2.5 version >= 2.1.1... yes
checking for /usr/bin/python2.5 version... 2.5
checking for /usr/bin/python2.5 platform... linux2
checking for /usr/bin/python2.5 script directory... ${prefix}/lib/python2.5/site-packages
checking for /usr/bin/python2.5 extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for python development headers... not found
checking for more warnings... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bindings/Makefile
config.status: creating bindings/python/gpod.i
config.status: creating bindings/python/Makefile
config.status: creating bindings/python/examples/Makefile
config.status: creating bindings/python/tests/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/version.xml
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating tests/Makefile
config.status: creating libgpod-1.0.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Configuration for libgpod 0.6.0 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc 
 Compiler .............: gcc -g -O2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   
 Linker ...............: gcc   -lgobject-2.0 -lglib-2.0   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   
 ArtworkDB support ....: yes
 Python bindings ......: no
 PyGObject support ....: no

 Now type 'make' to build libgpod 0.6.0,
 and then 'make install' for installation.
```

Are you sure you need to specify a directory and not just --with-python? If you do, perhaps it wants the prefix.
```
./configure --with-python=/usr/
```
That way the binary will be in /usr/bin/, libraries in /usr/lib/ etc etc.

---

### Post by briansvgs on 2008-03-26
Tried that, and that didn't work, and then I tried: ./configure --with-python=/usr/lib/python2.5/, and it gave me this output.....this looks even more interesting seing as it is version 2.5 of python, and 2.5>2.1

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for intltool >= 0.21... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... yes
checking for sg_ll_inquiry in -lsgutils... yes
checking for HAL... yes
checking for TAGLIB... no
checking for GDKPIXBUF... yes
checking for PYGOBJECT... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  de es fr he it ja ro sv
checking whether to build python bindings... yes
checking whether /usr/lib/python2.5/ version >= 2.1.1... configure: error: too old

---

### Post by jw5801 on 2008-03-27
Try:
```
sudo apt-get install python-dev
./configure --with-python=/usr/bin/python
```
Sorry, should have read the output from the first time more closely.

---

### Post by briansvgs on 2008-03-27
ok. I got it to compile with support for python, but exaile is still saying that python-gpod could not be found. any ideas?

---

### Post by briansvgs on 2008-03-27
ok. found a package for python-gpod on debian's package l repository.[http://packages.debian.org/sid/python-gpod](http://packages.debian.org/sid/python-gpod). However, when I go to install it, it says that libc6 is not satisfiable. I have both libc6 and libc6-dev installed. I could try compiling it, but, if I remember correctly, when I compiled it in feisty, that i screwed up a whole bunch of other programs.

---

### Post by jw5801 on 2008-03-28
python-gpod is a separate package to libgpod, thus you'll have to find the source for it and compile it as well.

Yeah, installing things from Sid isn't a good idea. You'd need a newer version of pretty much everything. Compiling python-gpod from source shouldn't screw up a bunch of programs, attempting to compile glibc however, will break alot of things. So go looking for the source code for the newer python-gpod and compile away.

---

### Post by steampunk on 2008-05-08
I also spent a long time on this rigmarole, until I found this thread which solved my problem:

[http://ubuntuforums.org/showthread.php?t=658523&highlight=libgpod3](http://ubuntuforums.org/showthread.php?t=658523&highlight=libgpod3)

libgpod3 seems to be the key and this thread shows how to install it successfully.

Good luck!

---

