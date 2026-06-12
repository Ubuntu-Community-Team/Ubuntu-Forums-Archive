---
title: "FFMPEG/h264 multithreading"
date: 2011-04-05
forum: Any Other OS
---

### Post by x2305andy2305x on 2011-04-05
Hi,

I'm trying to take advantage of the multithreaded capabilities of ffmpeg/x264 encoder. I've "gitted" and compiled latest x264 and ffmpeg from repository, with threads support:

FFmpeg version git-N-28880-g9c09dea, Copyright (c) 2000-2011 the FFmpeg developers
  built on Apr  5 2011 21:15:22 with gcc 4.1.2 20080704 (Red Hat 4.1.2-48)
  configuration: --enable-shared --disable-static --disable-doc --disable-ffplay --disable-ffserver --enable-avfilter --enable-postproc --enable-swscale --enable-gpl --enable-nonfree --enable-runtime-cpudetect --enable-pthreads --enable-bzlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libfaac --enable-libgsm --enable-libmp3lame --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libx264 --enable-zlib --enable-version3 --enable-libopenjpeg
  libavutil    50. 40. 0 / 50. 40. 0
  libavcodec   52.117. 0 / 52.117. 0
  libavformat  52.105. 0 / 52.105. 0
  libavdevice  52.  4. 0 / 52.  4. 0
  libavfilter   1. 77. 0 /  1. 77. 0
  libswscale    0. 13. 0 /  0. 13. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

and indeed both x264 and ffmpeg are compiled againts pthreads:

ldd /usr/local/bin/ffmpeg
	libavdevice.so.52 => /usr/local/lib/libavdevice.so.52 (0x00002b41302e9000)
	libavfilter.so.1 => /usr/local/lib/libavfilter.so.1 (0x00002b41304f2000)
	libavformat.so.52 => /usr/local/lib/libavformat.so.52 (0x00002b413075a000)
	libavcodec.so.52 => /usr/local/lib/libavcodec.so.52 (0x00002b4130a3e000)
	libpostproc.so.51 => /usr/local/lib/libpostproc.so.51 (0x00002b41316d9000)
	libswscale.so.0 => /usr/local/lib/libswscale.so.0 (0x00002b41318fb000)
	libavutil.so.50 => /usr/local/lib/libavutil.so.50 (0x00002b4131b55000)
	libm.so.6 => /lib64/libm.so.6 (0x000000319f200000)
	libpthread.so.0 => /lib64/libpthread.so.0 (0x000000319ee00000)
	libc.so.6 => /lib64/libc.so.6 (0x000000319de00000)
	libasound.so.2 => /lib64/libasound.so.2 (0x00002b4131d72000)
	libz.so.1 => /usr/lib64/libz.so.1 (0x000000319f600000)
	libx264.so.114 => /usr/local/lib/libx264.so.114 (0x00002b4132050000)
	libvorbisenc.so.2 => /usr/lib64/libvorbisenc.so.2 (0x00002b4132312000)
	libvorbis.so.0 => /usr/lib64/libvorbis.so.0 (0x00002b41326ec000)
	libtheoraenc.so.1 => /usr/lib64/libtheoraenc.so.1 (0x00002b4132919000)
	libtheoradec.so.1 => /usr/lib64/libtheoradec.so.1 (0x00002b4132b55000)
	libspeex.so.1 => /usr/lib64/libspeex.so.1 (0x00002b4132d6d000)
	libopenjpeg.so.2 => /usr/lib64/libopenjpeg.so.2 (0x00002b4132f86000)
	libopencore-amrwb.so.0 => /usr/lib64/libopencore-amrwb.so.0 (0x00002b41331a3000)
	libopencore-amrnb.so.0 => /usr/lib64/libopencore-amrnb.so.0 (0x00002b41333b8000)
	libmp3lame.so.0 => /usr/lib64/libmp3lame.so.0 (0x00002b41335e7000)
	libgsm.so.1 => /usr/lib64/libgsm.so.1 (0x00002b4133860000)
	libfaac.so.0 => /usr/lib64/libfaac.so.0 (0x00002b4133a6b000)
	/lib64/ld-linux-x86-64.so.2 (0x000000319da00000)
	libdl.so.2 => /lib64/libdl.so.2 (0x000000319e200000)
	librt.so.1 => /lib64/librt.so.1 (0x000000319fa00000)
	libogg.so.0 => /usr/lib64/libogg.so.0 (0x00002b4133c7e000)
	libstdc++.so.6 => /usr/lib64/libstdc++.so.6 (0x00002b4133e83000)
	libgcc_s.so.1 => /lib64/libgcc_s.so.1 (0x00000031a0200000)

ldd /usr/local/bin/x264
	libswscale.so.0 => /usr/local/lib/libswscale.so.0 (0x00002b6341cac000)
	libavutil.so.50 => /usr/local/lib/libavutil.so.50 (0x00002b6341f05000)
	libm.so.6 => /lib64/libm.so.6 (0x000000319f200000)
	libpthread.so.0 => /lib64/libpthread.so.0 (0x000000319ee00000)
	libc.so.6 => /lib64/libc.so.6 (0x000000319de00000)
	/lib64/ld-linux-x86-64.so.2 (0x000000319da00000)

here's the command i'm trying to issue:

ffmpeg -y -i infile.flv -f mp4 -vcodec libx264 -r 25 -b 2500000 -s 1280x720 -g 250 -crf 28 -threads 0 -pix_fmt yuvj420p -deblockalpha -1 -deblockbeta -1 -flags +loop -cmp +chroma -refs 3 -bf 3 -coder 1 -me_method dia -me_range 18 -subq 1 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -keyint_min 10 -level 30 -qmin 10 -qmax 51 -qcomp 0.7 -trellis 1 -directpred 3 -sc_threshold 40 -i_qfactor 0.71 -flags2 -mixed_refs+wpred+dct8x8+fastpskip-mbtree -qdiff 4 -b_strategy 3 -wpredp 1 -acodec libfaac -ar 44100 -ab 256000 -ac 2 outfile.mp4

Running CentOS 5.5 and checking system load with "top" command. No matter how i try, i always get the process to choke one of the cores (btw running on an i7) but the rest are pretty relaxed. TOP command reports ffmpeg process is using 200-400% CPU but when i look at the cores individually, only one is maxed, while the others are pretty much idle.

Is there anything in my command that is bottlenecking the processing?

---

### Post by howefield on 2011-04-07
Thread moved to "*Other OS/Distro Talk*"

---

