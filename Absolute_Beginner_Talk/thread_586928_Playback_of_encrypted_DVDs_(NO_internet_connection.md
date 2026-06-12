---
title: "Playback of encrypted DVDs (NO internet connection!)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Howl01 on 2007-10-22
Pleeeeease help...
I need to play back a commercial, encrypted DVD (Hero if ou were wondering) in about 2hours time.

I do not however have a working internet connection, and it is too big of a problem 2be able 2sort out by then - so libdvdcss is ought of the question unless there's a way for me 2transfer it across from my home comp 2my ubunt laptop.

Does anybody have ANY ideas?please...i'm desperaate here tbh
Thanks, Ben

---

### Post by Maestro23 on 2007-10-22
> **Howl01 said:**
> Pleeeeease help...
I need to play back a commercial, encrypted DVD (Hero if ou were wondering) in about 2hours time.

I do not however have a working internet connection, and it is too big of a problem 2be able 2sort out by then - so libdvdcss is ought of the question unless there's a way for me 2transfer it across from my home comp 2my ubunt laptop.

Does anybody have ANY ideas?please...i'm desperaate here tbh
Thanks, Ben

Get the tarball from the following website.  Copy to a flash drive, cd, etc...

[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

*Look under Releases

Good luck.:guitar:

---

### Post by RomeReactor on 2007-10-22
Hi. You can also get a .deb package for libdvdcss, along with other packages you'll need:

[LIST][libdvdcss2]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb")[/LIST]
[LIST][libdvdread3]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb")[/LIST]
[LIST][libdvdnav4]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_0.1.10-0.2_i386.deb")[/LIST]
[LIST][gstreamer0.10-ffmpeg]("http://mirrors.xmission.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb")[/LIST]
[LIST][libdvdplay0]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdplay/libdvdplay0_1.0.1-7_i386.deb")[/LIST]

To install .deb packages, just double-click on them.

---

### Post by Maestro23 on 2007-10-22
> **RomeReactor said:**
> Hi. You can also get a .deb package for libdvdcss, along with other packages you'll need:

[LIST][libdvdcss2]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb")[/LIST]
[LIST][libdvdread3]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb")[/LIST]
[LIST][libdvdnav4]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_0.1.10-0.2_i386.deb")[/LIST]

You may also need [libdvdplay0]("http://debian.mirror.frontiernet.net/debian/pool/main/libd/libdvdplay/libdvdplay0-dev_1.0.1-7_i386.deb"), though I could only find a Debian package (however, it works fine here).

Thanks RomeR. Should have posted those myself also. :smile:

---

### Post by Howl01 on 2007-10-22
Thanks sooo much for you're help...
but I have a problem - libdvdcss2, gstreamer and libdvdplay0 do not work.

I get an error message that says:
Error: Debendancy is not satisfiable: libc6 
for libdvdcss2, and gstreamer

and:

Error: Dependancy is not satisfiable: libdvdplay0
for libdvdplay0

I think I may have made an error erlier on as I only installed the .deb for libdvdcss...nothing else

(sorry for my ignorance...this is my first day w/Ubuntu)

---

### Post by RomeReactor on 2007-10-22
As far as I know, those packages *should* already be installed on your system; in any case, here they are:

[LIST][libgcc1]("http://mirrors.xmission.com/ubuntu/pool/main/g/gcc-4.2/libgcc1_4.2.1-5ubuntu4_i386.deb")[/LIST]
[LIST][libc6]("http://mirrors.xmission.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu9_i386.deb")[/LIST]

These packages come from [packages.ubuntu.com]("http://packages.ubuntu.com/").

Please post back with the results.

---

### Post by Howl01 on 2007-10-22
Again thankyou so much for your help (and patience)
But...I have encountered problems when trying to install those 2packages:

with libc6:
Error: Conflicts with the installed package 'tzdata'

with libgcc1:
Error: Dependancy is not satisfiable: gcc-4.2-base

---

### Post by RomeReactor on 2007-10-22
Let's backtrack a little; which version of Ubuntu are you running? the packages I posted were for Gutsy (7.10). If you have Feisty (7.04), that could explain the conflicts.The packages for Feisty are:

[LIST][*][libdvdplay0]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdplay/libdvdplay0_1.0.1-7_i386.deb")
[*][libdvdread3]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-2ubuntu1_i386.deb")
[*][libdvdnav4]("http://mirrors.xmission.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_0.1.10-0.1_i386.deb")
[*][libdvdcss2]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2%2bbuild1_i386.deb")[/LIST]

It should not ask you for the libc6 and libgcc1 packages now, but in case it does, here they are for Feisty:

[LIST][*][libgcc1]("http://mirrors.xmission.com/ubuntu/pool/main/g/gcc-4.1/libgcc1_4.1.2-0ubuntu4_i386.deb")
[*][libc6]("http://mirrors.xmission.com/ubuntu/pool/main/g/glibc/libc6_2.5-0ubuntu14_i386.deb")[/LIST]

Also, the previous **libdvdplay0** package I posted for Gutsy was wrong; it's now corrected on my first post.

**EDIT**: Seeing as it asks you for gcc-4.2-base, I think you have Gutsy now. Do you still have the CD? you can use it as a repository for some packages, which I think include libc6 and lbgcc1. To add it as a repository, go to "System->Administration->Synaptic", and once it opens, go to "Settings->Repositories", on the first tab make sure the case for the CD is checked. If it was unchecked, mark it, close that window, and press the blue "Reload" button. Then try searching for libc6 and libgcc1 there.

---

### Post by Howl01 on 2007-10-22
RomeReactor you are a genius, and i cant believe i didnt think 2mention which version of Linux i have.

You were right, I have feisty.

But now I have a slight problem in that I need 2uninstall the gutsy versions of libdvdnav4 and libdvdread3, as when i try and install them it says that a later version is already installed.
Sorry for my incompetance.

---

### Post by Maestro23 on 2007-10-22
> **Howl01 said:**
> RomeReactor you are a genius, and i cant believe i didnt think 2mention which version of Linux i have.

You were right, I have feisty.

But now I have a slight problem in that I need 2uninstall the gutsy versions of libdvdnav4 and libdvdread3, as when i try and install them it says that a later version is already installed.
Sorry for my incompetance.

> sudo dpkg -P libdvdread3

sudo dpkg -P libdvdnav4

*Will remove any config files for the packages as well.

---

### Post by RomeReactor on 2007-10-22
No need to apologize, you are not incompetent; learning a new operating system can sometimes be difficult. I know I had loads of trouble when I first started, and it was only thanks to these forums that I eventually solved them, and learned a lot. So just be patient; you'll get the hang of it soon.

To uninstall the packages, do it from Synaptic; find them, right click on them and select **Mark for Complete Removal**. Once they're uninstalled, press the blue "Reload" button, close Synaptic, and try installing the correct packages.

**EDIT**: Maestro23 already answered that.

---

### Post by Howl01 on 2007-10-22
I have progress...but not complete success.

I managed, using Maestro 23 's method, to uninstall the navigator one and install the earlier version.

It wouldn't let me uninstall libdvdread, as other libdvd packages are reliant on it.

Now I haven't a clue how to get round this...any ideas?

---

### Post by RomeReactor on 2007-10-22
Try uninstalling the other libdvd packages first, then libdvdread, and remember to mark them all for **complete removal**. Then press the "Reload" button, and try installing the correct packages.

Did the Gutsy version of **gstreamer0.10-ffmpeg** install?

---

### Post by Howl01 on 2007-10-22
It won't let me do that though...as when i click reload it needs an internet connection 2check for updates.

No ther was a dependancy error: libc6 

Thanks for all your help

---

### Post by Unicycle on 2007-10-22
Vlc?

---

### Post by philinux on 2007-10-22
If your gonna run with no internet connection then get linux mint it comes with all the nonfree drivers installed.

---

### Post by Howl01 on 2007-10-22
I don't think ther is anyway 2get VLC across without having 2use my ubuntu laptop's internet connection.

Nah Im trying 2sort out my internet connection, it's jus not something i can do before i need 2play this DVD tbh.

---

### Post by RomeReactor on 2007-10-22
The version of the gstreamer package I posted earlier was for Gutsy; [this one]("http://mirrors.xmission.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-0ubuntu4_i386.deb") is for Feisty.

---

### Post by Unicycle on 2007-10-22
> **Howl01 said:**
> I don't think ther is anyway 2get VLC across without having 2use my ubuntu laptop's internet connection.

Nah Im trying 2sort out my internet connection, it's jus not something i can do before i need 2play this DVD tbh.

You're on the Internet now, I don't understand why you can't burn a CD of VLC, and then run it on your non-internet-connected box?

---

### Post by Howl01 on 2007-10-22
Thanks RomeReactor.

@Unicycle, I thought that was not possible on Ubuntu as it needs 2install it which means that it needs 2connect 2the server or w/e.

If anybody could tell me how I would go about bringing VLC across please tell...

---

### Post by Maestro23 on 2007-10-22
> **Howl01 said:**
> Thanks RomeReactor.

@Unicycle, I thought that was not possible on Ubuntu as it needs 2install it which means that it needs 2connect 2the server or w/e.

If anybody could tell me how I would go about bringing VLC across please tell...

Get the source code from videolan.org

[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

Once you extract the tarball:

From the README doc:

> Installing and running VLC
==========================

You can install the VLC and its plugins by typing:

   make install

But you don't need to install it if you don't want to; VLC can be launched
from the current directory as well:

   ./vlc


Good luck.

---

### Post by Howl01 on 2007-10-23
what do i click on 2launch it from the current directory?

---

### Post by quinnten83 on 2007-10-23
i think you have to change into the directory in terminal and then type ./vlc

so open up a terminal
ubuntu>Accesories> terminal
change into the folder where you have downloaded the tarball to or where you extracted it to
cd /"location" where location could be for example your desktop /home/Desktop
and then in terminal type

./vlc

that should run it

"please correct me if I am wrong"

---

### Post by quinnten83 on 2007-10-23
oh wait I am  wrong, nevermind my post...!

---

### Post by Howl01 on 2007-10-23
Thanks for yout help everyone, but I no longer need 2play the DVD (i've kind of get away with it-with only minimal repercussions)

Now I just need 2find out how 2fix my internet connection and i'll be happy....that might take a while thought tbh.

Thanks anyway, sorry 2take up so much of your time.

---

