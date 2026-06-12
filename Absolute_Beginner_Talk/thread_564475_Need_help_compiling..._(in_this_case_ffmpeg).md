---
title: "Need help compiling... (in this case ffmpeg)"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by isync on 2007-10-01
Can somebody talk me through compiling the latest and greatest ffmpeg with mp3 support on my Dapper 6.06 on AMD64?

Which would also answer this thread: [http://ubuntuforums.org/showthread.php?t=554048](http://ubuntuforums.org/showthread.php?t=554048))



BTW: I also have problems adding the medibuntu repository. Is it down? Or, any hints for a good working amd64 sources.list

---

### Post by por100pre1 on 2007-10-01
Please check if [this]("https://help.ubuntu.com/community/Medibuntu") works for you.

EDIT: The Medibuntu repository is up, if it doesn't work for you lets us know.

---

### Post by justleen on 2007-10-01
in genreral  for compiling you can take these steps:

- unpack the source tar (tar -xcvf package.tar.gz)
- enter the dir (cd package)
- configure the source (./configure)
- make the binaries ( make)
- install the binaries (sudo make install)

make sure you have the comilers installed! (sudo apt-get install build-essential)

---

### Post by isync on 2007-10-01
So far I tried compiling by hand with:

# svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
	resulted in "external link checked out, Revision 24679.
	Checkedout, Revision 10630."
# cd ffmpeg
# ./configure --prefix=/usr  \
--enable-libmp3lame --enable-libogg --enable-libvorbis --enable-libfaad --enable-libtheora \
--enable-libfaadbin --enable-libfaac --enable-liba52 --enable-liba52bin --enable-libx264  \
--enable-pp --enable-libamr-nb --enable-libamr-wb  \
--enable-shared --enable-pthreads --disable-debug --enable-gpl  \
--enable-swscaler --enable-libxvid --enable-libgsm  \
--enable-libdc1394 --enable-gprof

which gave me a "ERROR: libamrnb not found". So far I could not figure out how to heal this...

Next I tried the procedure suggested by por100pre1 and Medibuntu [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) "Installing Individual Packages".
And traversed the dependencies, first downloading and trying to libavcodec1d leading to libavutil1d which finally said: "Error: Unsatisfyable dependency: libc6". Although I have libc6 installed 2.3.6.0ubuntu-20.5

---

### Post by Chris S. on 2007-10-01
You usually need libxxx-dev packages when configuring and compiling from source.  I'm guessing the dev packages include the necessary header files that don't come with the libraries.  So, you have libc6-dev, or just libc6?

---

### Post by isync on 2007-10-01
I have libc6, libc6-dev, libc6-pkg, libc6-i386, ... all of them! (in the version posted above.)

---

### Post by isync on 2007-10-01
I tried it by hand again, leaving out the amr libs and it worked until make, which trew a lot of warnings and ened with
> libx264.c: In function »X264_init«:
libx264.c:151: Fehler: »struct <anonymous>« hat kein Element namens »i_rc_method«
libx264.c:151: Fehler: »X264_RC_CRF« nicht deklariert (erste Benutzung in dieser Funktion)
libx264.c:151: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgeführt
libx264.c:151: Fehler: für jede Funktion in der er auftritt.)
libx264.c:152: Fehler: »struct <anonymous>« hat kein Element namens »f_rf_constant«
libx264.c:154: Fehler: »struct <anonymous>« hat kein Element namens »i_rc_method«
libx264.c:154: Fehler: »X264_RC_CQP« nicht deklariert (erste Benutzung in dieser Funktion)
libx264.c:161: Fehler: »struct <anonymous>« hat kein Element namens »i_rc_method«
libx264.c:161: Fehler: »X264_RC_ABR« nicht deklariert (erste Benutzung in dieser Funktion)
make[1]: *** [libx264.o] Fehler 1

make: *** [lib] Error 2

So I would like to get the .deb package installation working, but how can I update my libc6-dev (as I have it installed, it seems to be out of date..)

---

### Post by isync on 2007-10-01
To : por100pre1
Medibuntu does not work for me!

As I said, I am running Dapper, which uses libc6 in version 2.3.x . But the deb from medibuntu requires 2.6.1...

SD-Plissken told me in [http://ubuntuforums.org/showthread.php?t=564609](http://ubuntuforums.org/showthread.php?t=564609) that it is nearly impossible to upgrade libc6 to this version.

So is it possible? What should I do to get a up-to-date ffmpeg?

---

### Post by por100pre1 on 2007-10-01
I been reading the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/138602"), and after considering it, my suggestion to you is to upgrade your Ubuntu installation to the next release. But if you can, backup your files to an external media, and install Feisty; it would be unlikely that you get those dependency issues in Feisty.

---

