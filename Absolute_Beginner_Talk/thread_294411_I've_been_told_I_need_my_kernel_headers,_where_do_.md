---
title: "I've been told I need my kernel headers, where do I get these?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by mysfit_i on 2006-11-06
I have recently installed Ubuntu 6.10 from the alternate CD.
I have a Topfield PVR that I am trying to connect to using an application called puppy (not the Puppy distro) ([http://sourceforge.net/projects/puppy)](http://sourceforge.net/projects/puppy)).

However when I following the instructions on this ([http://guppy.nongnu.org/documentation.html](http://guppy.nongnu.org/documentation.html)) site i get an error when running the make command which very near the top says:-

usb_io.h:33:23: error: linux/usb.h: No such file or directory 

I have been told from the Topfield forum that this is probably because I don't have the necessary kernel header files.

So my question is what are these files, can I confirm whether I have them, and if I don't, how do I get them?  

I have used Synaptic and searched for header which says I have linux-headers-2.6.17-10 installed (2.6.17-10.33) and -10-generic and linux-headers-generic.  I have just also installed build-essentials if that makes any difference.  Are there any others I should have?

Many thanks from a novice.

David

---

### Post by Joe_CoT on 2006-11-06
You need to download the kernel source, untar it, and make the link

```
sudo apt-get install linux-headers-$(uname -r)
```

After that's done, you need to untar it
```
cd /usr/src
sudo tar -xf linux-source-2.6.x.tar.bz2
```

The filename will depend on your version
then make the symlink
```
sudo ln -s linux-source-2.6.x linux
```

---

### Post by John.Michael.Kane on 2006-11-06
Open synaptic click search type in **linux kernel headers** 

If their not installed install them if you need to. if building from source you may need to install **build-essential** this package can be found with synaptic as well.

---

### Post by mysfit_i on 2006-11-06
I rechecked in synaptic with this search but I already had these packages installed.

---

### Post by Joe_CoT on 2006-11-06
If you already have them installed, check your /usr/src directory to see if the tar files are there. If they are, untar and link like i mentioned earlier.

---

### Post by mysfit_i on 2006-11-06
Hi Joe_CoT,
      well i tried this actions you said, although the adp-get was for headers and the tar was for source so I downloaded linux-source as well and carried on.

Unfortunately I still get exactly the same error message when I run make in the puppy directory.

The complete error message is:-
cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o puppy.o puppy.c
In file included from puppy.c:48:
usb_io.h:33:23: error: linux/usb.h: No such file or directory
In file included from puppy.c:48:
usb_io.h:137: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
usb_io.h:137: warning: its scope is only this definition or declaration, which is probably not what you want
usb_io.h:139: warning: &#8216;struct usb_config_descriptor&#8217; declared inside parameter list
usb_io.h:141: warning: &#8216;struct usb_descriptor_header&#8217; declared inside parameter list
usb_io.h:143: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
usb_io.h:144: warning: &#8216;struct usb_config_descriptor&#8217; declared inside parameter list
puppy.c:69: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
puppy.c: In function &#8216;main&#8217;:
puppy.c:98: error: storage size of &#8216;devDesc&#8217; isn&#8217;t known
puppy.c:98: warning: unused variable &#8216;devDesc&#8217;
puppy.c: At top level:
puppy.c:1138: warning: &#8216;struct usb_device_descriptor&#8217; declared inside parameter list
puppy.c:1139: error: conflicting types for &#8216;isToppy&#8217;
puppy.c:69: error: previous declaration of &#8216;isToppy&#8217; was here
puppy.c: In function &#8216;isToppy&#8217;:
puppy.c:1140: error: dereferencing pointer to incomplete type
puppy.c:1140: error: dereferencing pointer to incomplete type
make: *** [puppy.o] Error 1

---

### Post by mysfit_i on 2006-11-06
Joe, do I also need to set up a link for the linux headers as well as the linux source?

---

### Post by Joe_CoT on 2006-11-06
And now that I look, SD-Plissken had the right answer ;)

Check to see there's /usr/include/linux directory. If you have the headers installed as SD-Plissken said, there will be. The issue is just that puppy can't find them. Look in the readme and ./configure --help to see what the argument is you need to pass to configure to set the include path.

---

### Post by mysfit_i on 2006-11-06
Joe and SD-Plissken, I have checked and I do have the /usr/include/linux directory.  I have checked inside it and there is no usb.h file.  However there are usb_ch9.h and usbdevice_fs.h.

Now do I actually need a usb.h file in this directory, or is one of these the correct one and I should create a symbolic link? 

Does anybody have an Ubuntu 6.06 install as the make worked fine when I had that installed.

thanks

---

### Post by Joe_CoT on 2006-11-06
> Joe and SD-Plissken, I have checked and I do have the /usr/include/linux directory. I have checked inside it and there is no usb.h file. However there are usb_ch9.h and usbdevice_fs.h.

Yeah, you're right ... damn.

Check your /usr/lib/modules directory. (on my system at least), there's a directory for your kernel. usb.h is located in /lib/modules/2.6.x/build/include/linux/

Try this for me

```
sudo mv /usr/include/linux /usr/include/linux2
sudo ln -s /lib/modules/2.6.x/build/include/linux/ /usr/include/linux
```

---

### Post by mysfit_i on 2006-11-06
Joe, I did as you wrote.  One question it seems that I have renamed a directory and used another directory in its place.  Does this mean that I have a directory full of files that other either duplicated or not needed in /usr/include/linux2 now?

Oh and my problem has now changed.  It gets past the usb.h problem and I now just get the following list of errors:-

cc -std=gnu99 -Wall -W -Wshadow -Wstrict-prototypes -pedantic -fexpensive-optimizations -fomit-frame-pointer -frename-registers -O2   -c -o puppy.o puppy.c
In file included from /usr/include/linux/usb.h:4,
                 from usb_io.h:33,
                 from puppy.c:48:
/usr/include/linux/mod_devicetable.h:21: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:36: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:119: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:143: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:157: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:162: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:189: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:222: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
/usr/include/linux/mod_devicetable.h:280: error: expected specifier-qualifier-list before &#8216;kernel_ulong_t&#8217;
make: *** [puppy.o] Error 1

Looks like I should go and speak to the puppy author, or is it still a problem with my installation?

BTW:  thank you for the patience and help.  This has been the quickest and most clear responses I have had on any forum so far :-)

cheers

David

---

### Post by Joe_CoT on 2006-11-06
> Joe, I did as you wrote. One question it seems that I have renamed a directory and used another directory in its place. Does this mean that I have a directory full of files that other either duplicated or not needed in /usr/include/linux2 now?

I had you move it instead of delete it, because you're quickly moving into unhealthy install territory (the change may cause problems in subsequent upgrades). I'd suggest moving it back to how it was after you get puppy to compile.


As for *that* error, yes, I'd suggest googling it or looking/asking on their forums. You've left Ubuntu territory :)

---

### Post by John.Michael.Kane on 2006-11-06
The error you have could be because of the ln -s command you passed. It makes a symbolic link between the file, and could be making it hard for the program to find the headers,however. it is just a guess.

Your other option is what Joe_CoT suggested. personally I would find out if other users of that program have got it to work with out errors before continuing.

---

### Post by mysfit_i on 2006-11-07
Thank you for your time and effort.  I am off to the programs forums to take this on further.

regards

David

---

### Post by x-na on 2006-11-09
Did you get this issue resolved? I'm having the same problem with puppy and ftpd-topfield.

No idea where to go next...

---

### Post by mysfit_i on 2006-11-09
I'm afraid I didn't get this resolved.
I changed things back so I didn't have the symlink to /usr/include/linux and probably doing something I shouldn't I copied usb.h and mod_devicetable.h into the directory incase the fact that it was a symlink was not liked by puppy's make.  But that didn't help - didn't make it worse - but didn't make it better either.

So I tried at the Toppy forums, but have had no feedback at all.  I couldn't find a way of contacting the puppy author from his site, so went to the author of guppy but he hasn't responded yet either.

So I can only assume that the fault lies with some change Ubuntu did while changing to 6.10.  But it is going to probably rest with the puppy author to accommodate Ubuntu's new system.

Which leaves me stuck not being able to offload files from the Topfield, using my Linux box.

---

### Post by x-na on 2006-11-10
I actually took a different path and created .deb-packages from the available puppy and guppy .rpm:s with alien.

This however is not the recommended way to go and took some adjusting to get guppy running (manual editing of the guppy python executable). Your mileage may vary.

I haven't tried to do anything with my Topfield yet, I'll probably do that during the weekend so I'll report if it worked or not.

If someone can get these compiled and knows how to make .debs for puppy, guppy and ftpd-topfield, I bet it'd be appreciated.

---

### Post by x-na on 2006-11-11
I got it working. Not the easiest way and certainly not the recommended way, but it works.

If you need help (or the deb-files I converted from the rpm's) let me know.

---

### Post by mip on 2006-11-11
> **x-na said:**
> I got it working. Not the easiest way and certainly not the recommended way, but it works.

If you need help (or the deb-files I converted from the rpm's) let me know.

I'd like these debs if you have them lying around. I've also tried, unsuccessfully, to build puppy.

---

### Post by belgrave on 2006-11-11
having the same troubles but with trying to compile ftp-topfield - can't find usb.h and mod_devicetable.h under /usr/include/linux (because they aren't there). 

Tentatively tried the symlinking, but as expected, this threw further errors. Tried setting makefile flags, but with little/no success. The only luck I had was with raw hacking of one of the source files (libtopfield/usb_io.h). After hacking with comments, here are the changed lines:

[FONT="Courier New"]/*#include <linux/usb.h>*/
#include <linux/usbdevice_fs.h>

/*#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,0)*/
#include <linux/usb_ch9.h>
/*#endif*/
[/FONT]

essentially killed reference to usb.h and opened up usb_ch9.h - logic being that usb.h wasn't in the include dir, usb_ch9.h was. That got it to compile nicely, but it doesn't seem to be able to talk USB to the topfield - so much for comment hacking.

There has to be a reason why usb.h is not included in the std include dir while usb_ch9.h is. The distro source for ftp-topfield *seems* to support usb_ch9.h, but it's commented out and looks like they were targetting specific kernel versions.... but, the header is there in edgy...... 

if anyone could provide any help it'd be greatly appreciated - next stop is the slug mailing list.

---

### Post by x-na on 2006-11-13
I moved the debs over there. Read the disclaimer too. I take no responsibility about anything. You're on your own to get this working.

[http://www.kauhajoki.fi/~peti/puppy-deb/]("http://www.kauhajoki.fi/~peti/puppy-deb/") 

I had to manually edit the guppy python file to get it working, it checks python version and ubuntu's versioning scheme isn't something it can handle. This is the ugly part, I haven't used python so had to kinda hard code the version in the file to get this working.

I also got a message from the puppy maintainer that puppy doesn't compile against kernel 2.6 header files and he doesn't know why. To get it compiled you need to get kernel 2.4 header files.

[I]"Hi,

I get the same problem when I try and compile puppy. It
turns out the error is because puppy doesn't compile against the 2.6
kernel header files. I'm not sure how to fix the problem yet. For now
you'll have to download the 2.4 kernel headers and compile against that.
I'll send you an update if I fix the problem.

Thanks,
Tony"[/I]

---

### Post by mip on 2006-11-13
Cheers x-na.

I used the puppy deb and the source version of guppy from [http://guppy.nongnu.org/download.html](http://guppy.nongnu.org/download.html)

---

### Post by mip on 2006-11-13
I really need to build this myself though. I'm suffering from the problems described here [http://forum.toppy.org.uk/forum/viewtopic.php?p=79167](http://forum.toppy.org.uk/forum/viewtopic.php?p=79167)

---

### Post by belgrave on 2006-11-17
@x-na: thanks for making these available!

have just run through the setup, but guppy failed using the debs you provided.

Puppy worked right out of the box as you mentioned, but yr deb of Guppy failed with odd Python errors. The source verison from the [developers site ]("http://guppy.nongnu.org/") contains a pre-compiled version of guppy which "just works" - to an extent; I had to apply your hack for the version detection and it looks like it's having issues with ubuntu's sudo thing (read/write on the dynamic USB device).

The instructions on the dev's site do specifically mention debian usb/sudo issues, but the solution deals with hotplug scripts (outdated and not used in Ubuntu AFAICS). bit too late in the evening right now, but will get the permissons thing sorted with udev tomorrow-ish  and post a solution. Anyone wanna beat me to the punch?

---

### Post by belgrave on 2006-11-17
think this runs a little deeper into guppy than my first assumptions. Managed to get puppy working (temporarily) without root privileges by chmod'ing the USB device.

guppy still gives the same errors (can read the remaining space on the topfield, but gives an error when retrieving the directory listing). Will post what I find when i get the time

---

### Post by wschubi on 2006-11-23
Hello 
I am new here and I saw found this thread because I want get some files from my Topfield to my Ubuntu-Pc (Ubuntu 6.10). 
Because the problem with usb.h and so on, I got the deb-files from X-NA and used the terrible hack (but it works).
Now my question (my be a bit trivial): when I start guppy per command guppy I get the following message:

Traceback (most recent call last):
  File "/usr/bin/guppy", line 86, in ?
    from guppy import GuppyWindow
ImportError: no module named guppy

When I change into my the guppy directory and start there with "./guppy" all is well.

Has anyone any idea what is my mistake?

Many thanks.
Werner.

---

### Post by mip on 2006-11-23
> **wschubi said:**
> Hello 
I am new here and I saw found this thread because I want get some files from my Topfield to my Ubuntu-Pc (Ubuntu 6.10). 
Because the problem with usb.h and so on, I got the deb-files from X-NA and used the terrible hack (but it works).
Now my question (my be a bit trivial): when I start guppy per command guppy I get the following message:

Traceback (most recent call last):
  File "/usr/bin/guppy", line 86, in ?
    from guppy import GuppyWindow
ImportError: no module named guppy

When I change into my the guppy directory and start there with "./guppy" all is well.

I suggest that you only use the deb for puppy. For guppy get the source distro from the guppy web site and put it somewhere like '/opt/guppy' then run it from there.

---

### Post by wschubi on 2006-11-24
No, I've installed both deb-files: puppy and guppy.
I can call "puppy" from anywhere and it works. But calling "guppy"  brings this error-message. 
Only when I am in the directory from guppy and say "./guppy". then guppy is working fine. Even being in the directory of guppy and saying "guppy" it dosn't work.

Werner

---

### Post by mip on 2006-11-24
> **wschubi said:**
> No, I've installed both deb-files: puppy and guppy.
I can call "puppy" from anywhere and it works. But calling "guppy"  brings this error-message. 
Only when I am in the directory from guppy and say "./guppy". then guppy is working fine. Even being in the directory of guppy and saying "guppy" it dosn't work.

Werner

I suggest you remove the guppy deb and try the source version. You can create a symlink to the executable in /usr/local/bin if you like.

---

### Post by wschubi on 2006-11-25
Hi
I don't know, why I should remove guppy, because it's working fine. The only problem is, that I can not call it from anywhere with the command "guppy", per example with an icon from the desktop. A symbolic link also doesn't work.

---

### Post by belgrave on 2006-11-26
after much messing about and some discussion with the Guppy author, I have managed to get it all up and working. I've [written up a howto]("http://ubuntuforums.org/showthread.php?t=307216") for Edgy. If anyone wants to contribute/ask questions please feel free.

---

