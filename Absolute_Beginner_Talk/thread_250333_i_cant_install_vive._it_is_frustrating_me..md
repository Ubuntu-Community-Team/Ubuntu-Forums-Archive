---
title: "i cant install vive. it is frustrating me."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by krazed nun on 2006-09-03
I am trying to install vive and i keep getting this error:

kingluis@BLEEK:~/Desktop/vive-0.3$ ./configure
Checking your system in order to install Vive...
Checking for ffmpeg...Use of uninitialized value in pattern match (m//) at ./configure line 10.
Use of uninitialized value in pattern match (m//) at ./configure line 10.
Found
The program ffmpeg has been installed, but it does not have the optimal configuration for Vive.  Run:
        ./install ffmpeg

This will activate the Vive install script to install ffmpeg.  If you prefer to compile it yourself, the optimal configuration for Vive is:
        ./configure --enable-gpl --enable-pp --enable-zlib \
                --enable-vorbis --enable-libogg --enable-theora \
                --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm\
                --disable-debug --enable-mp3lame --enable-faad\
                --enable-faac --enable-xvid --enable-ogm
You may continue on with installing Vive and install an updated ffmpeg later, if you so choose, as well.
Checking for vobcopy...Can't exec "vobcopy": No such file or directory at ./configure line 41.
Use of uninitialized value in pattern match (m//) at ./configure line 42.
Found
Checking for cpdvd...Use of uninitialized value in pattern match (m//) at ./configure line 54.
Checking for MP4Box...Can't exec "MP4Box": No such file or directory at ./configure line 61.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Not found or incorrect version
Please install MP4Box by running:
        ./install mp4box
Or, run the following commands by yourself:
        wget [http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz](http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz)
        wget [http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz](http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz)
        tar -zxf gpac-0.4.0-rc2.tar.gz
        tar -zxf  gpac_extra_libs-0.4.0.tar.gz
        cd gpac_extra_libs
        cp -r * ../gpac/extra_lib
        cd ../gpac
        chmod +x configure
        ./configure
        make lib
        make apps
        make install
        sudo cp bin/gcc/libgpac.so /usr/lib



i installed mp4box, and it still wont install. i followed the instructions in the monkeyblog thing and i cant install it. please help....:-D

---

