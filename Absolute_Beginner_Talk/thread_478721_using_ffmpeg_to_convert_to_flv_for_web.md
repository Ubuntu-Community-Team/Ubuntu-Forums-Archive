---
title: "using ffmpeg to convert to flv for web"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-06-19
I've heard that ffmpeg is restricted in ubuntu and I'm wondering if that's why I'm not able to get audio out of my flv files when I convert them from uncompressed avi files.

Here is the command I'm using to convert..

```
ffmpeg -i original.avi -vcodec flv -s 320x240 compressed.flv
```

and got no audio...I also tried...

```
ffmpeg -i original.avi -vcodec flv -acodec mp3 -s 320x240 compressed.flv
```

and it said mp3 was unsupported.

any ideas?

---

### Post by Cypher on 2007-06-20
Just type "ffmpeg" and you will see after the header a bunch of flags like "--enable-shared" and so on that indicate how ffmpeg was built. In most cases, "--enable-libmp3lame" will  not be listed, so you're going to have to re-build from sources to get the MP3 codec built in and get audio for your FLV files.

I went through this exact same thing myself..

So start with this in a terminal
**Setup/File Download**
```

cd ~
mkdir Open_Source
cd Open_Source
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
wget http://rubyforge.org/frs/download.php/17497 flvtool2-1.0.6.tgz
sudo apt-get install liblame0 liblame-dev libogg0 libogg-dev libvorbia0a libvorbis-dev checkinstall
tar -zxf flvtool2-1.0.6.tgz

```

**Compile FLVTOOL2**
```

cd ~/Open_Source/flvtool2-1.0.6
ruby setup.rb config
ruby setup.rb setup
ruby setup.rb install

```

**Compile FFMPEG**
```

cd ~/Open_Source/ffmpeg
./configure --enable-libmp3lame --enable-libogg --enable-libvorbis --enable-shared
echo '#define HAVE_LRINTF 1' >> config.h
make
sudo checkinstall

```

This should now get you a FFMPEG with MP3 support and your commands with "-acodec" should work..

---

### Post by shanepardue on 2007-06-20
Thank you so much for your help! I followed your directions, but when I ran ffmpeg with any command, I get the following error message.

```
ffmpeg: error while loading shared libraries: libavformat.so.51: cannot open shared object file: No such file or directory
```

It appears I have the codec installed though..maybe they weren't at the time of compilation?

---

### Post by Cypher on 2007-06-20
Please do the following
```

sudo apt-get install libavformat0d libavformat-dev

```
And also
```

ldd `which ffmpeg`

```
and make sure there aren't any more "Not Knowns" for any of the libraries..

---

### Post by shanepardue on 2007-06-20
```
libavformat0d is already the newest version.
libavformat0d set to manual installed.
libavformat-dev is already the newest version.

```

```
linux-gate.so.1 =>  (0xffffe000)
libavformat.so.51 => not found
libavcodec.so.51 => not found
libavutil.so.49 => not found
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f58000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e17000)
/lib/ld-linux.so.2 (0xb7f93000)
```

Do I need to recompile?

---

### Post by Cypher on 2007-06-20
OK..I had the same issue..the issue is that the program is linked to a specific version of the library as opposed to .so.1 or .so.2..

So do the following
```

cd /usr/lib
sudo ln -s libavcodec.so.0d.51.11.0 libavcodec.so.51
sudo ln -s libavutil.so.0d.49.0.0 libavutil.so.49
sudo ln -s libavformat.so.0d.50.5.0 libavformat.so.51

```

You should now be OK..

---

### Post by shanepardue on 2007-06-20
I wish I were! I got yet another error message..I really appreciate all of your help with this hack.

```
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avcodec_alloc_context2
```

---

### Post by Cypher on 2007-06-20
OK..now before we hack at this aany further, are you using the newly compiled ffmpeg or a pre-compiled one? If the latter, then please compile ffmpeg and let's see if it behaves any better..

---

### Post by shanepardue on 2007-06-20
I followed your directions to compile a new one and I believe I'm running that one.

---

### Post by Cypher on 2007-06-20
OK..so if you were to do
```

cd ~/Open_Source/ffmpeg
ldd ffmpeg
./ffmpeg

```
Do you get the same result?

---

### Post by shanepardue on 2007-06-21
Yes I do.

---

### Post by javier.der on 2007-08-01
I fixed it doing:
```

sudo ln -s /usr/local/lib/libavformat.so.51 /usr/lib/libavformat.so.51

sudo ln -s /usr/local/lib/libavcodec.so.51 /usr/lib/libavcodec.so.51

sudo ln -s /usr/local/lib/libavutil.so.49 /usr/lib/libavutil.so.49

```

---

### Post by garbergs on 2007-08-03
> **Cypher said:**
> 

...

**Compile FFMPEG**
```

cd ~/Open_Source/ffmpeg
./configure --enable-libmp3lame --enable-libogg --enable-libvorbis --enable-shared
echo '#define HAVE_LRINTF 1' >> config.h
make
sudo checkinstall

```

This should now get you a FFMPEG with MP3 support and your commands with "-acodec" should work..


I had some problems getting ffmpeg to work with mp3 encoding. My configuration was:

./configure –enable-gpl –enable-pp –enable-libfaad –enable-libvorbis –enable-libogg –enable-liba52 –enable-dc1394 –enable-libgsm –enable-libmp3lame –enable-libfaac –enable-libxvid –enable-pthreads –enable-libx264

The problem occured when I compiled ffmpeg with “make”:

```

In file included from /usr/src/ffmpeg/vhook/imlib2.c:114:
/usr/include/Imlib2.h:108: error: syntax error before â*â token
...

```

I solved this by installing Imlib2 from source:
href=”[http://sourceforge.net/project/showfiles.php?group_id=2](http://sourceforge.net/project/showfiles.php?group_id=2)
(check at the bottom of the page)

I also installed a lot of libs to get the compilation to work:

apt-get build-dep ffmpeg
apt-get install liblame0 liblame-dev libtool libpng3 libpng3-dev libttf-dev cdbs libbz2-dev libid3tag0 libid3tag0-dev xlibs-dev libxvidcore4-dev libx264-dev libfaac-dev libfaad2-dev

---

### Post by manefraim on 2007-08-15
any updates? I'm getting 

```
/usr/local/bin/ffmpeg: symbol lookup error: /usr/local/bin/ffmpeg: undefined symbol: avcodec_alloc_context2 
```

now too.

---

### Post by kostkon on 2007-08-15
A good solution would be to install *ffmpeg* from  the [medibuntu]("http://medibuntu.org/") repository. I think it's a version with the support for many restricted formats enabled.

Just follow the [ instructions on how to add this repository to your software sources]("http://medibuntu.org/repository.php"), then go to *Synaptic* and install  *ffmpeg*.

---

### Post by jesseakc on 2007-09-18
> **kostkon said:**
> A good solution would be to install *ffmpeg* from  the [medibuntu]("http://medibuntu.org/") repository. I think it's a version with the support for many restricted formats enabled.

Just follow the [ instructions on how to add this repository to your software sources]("http://medibuntu.org/repository.php"), then go to *Synaptic* and install  *ffmpeg*.

I spent hours on this one.  Your suggestion was easy and it worked.  Thanks!

---

