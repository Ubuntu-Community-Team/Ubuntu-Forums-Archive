---
title: "Kino Compile Help!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2007-06-15
Hello
 
I have never compiled a package before, and I pretty much figured it out on my own, but when I **make** it, it gives me this garbage: (it is a little cut off)
 
 
[FONT=Courier New][SIZE=2][COLOR=#000000]text’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from psxstr.c:32:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o raw.o raw.c
In file included from avformat.h:36,
                 from raw.c:22:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from raw.c:22:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o nutdec.o nutdec.c
In file included from avformat.h:36,
                 from nut.h:24,
                 from nutdec.c:25:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from nut.h:24,
                 from nutdec.c:25:
avformat.h:280: warning: ‘AVFrac’ is deprecated
nutdec.c: In function ‘get_packetheader’:
nutdec.c:103: warning: unused variable ‘start’
nutdec.c: In function ‘decode_stream_header’:
nutdec.c:308: warning: ‘codec_get_bmp_id’ is deprecated (declared at riff.h:51)
nutdec.c:314: warning: ‘codec_get_wav_id’ is deprecated (declared at riff.h:52)
nutdec.c: In function ‘sp_pos_cmp’:
nutdec.c:428: warning: suggest parentheses around + or - inside shift
nutdec.c:428: warning: suggest parentheses around + or - inside shift
nutdec.c: In function ‘sp_pts_cmp’:
nutdec.c:432: warning: suggest parentheses around + or - inside shift
nutdec.c:432: warning: suggest parentheses around + or - inside shift
nutdec.c: In function ‘add_sp’:
nutdec.c:441: warning: passing argument 3 of ‘av_tree_insert’ from incompatible pointer type
nutdec.c: In function ‘nut_read_timestamp’:
nutdec.c:793: warning: label ‘resync’ defined but not used
nutdec.c: In function ‘read_seek’:
nutdec.c:829: warning: passing argument 3 of ‘av_tree_find’ from incompatible pointer type
nutdec.c:829: warning: passing argument 4 of ‘av_tree_find’ from incompatible pointer type
nutdec.c:838: warning: passing argument 3 of ‘av_tree_find’ from incompatible pointer type
nutdec.c:838: warning: passing argument 4 of ‘av_tree_find’ from incompatible pointer type
nutdec.c:846: warning: passing argument 3 of ‘av_tree_find’ from incompatible pointer type
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o rm.o rm.c
In file included from avformat.h:36,
                 from rm.c:21:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from rm.c:21:
avformat.h:280: warning: ‘AVFrac’ is deprecated
rm.c: In function ‘rm_read_packet’:
rm.c:880: warning: ‘len’ may be used uninitialized in this function
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o segafilm.o segafilm.c
In file included from avformat.h:36,
                 from segafilm.c:30:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from segafilm.c:30:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o sierravmd.o sierravmd.c
In file included from avformat.h:36,
                 from sierravmd.c:30:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from sierravmd.c:30:
avformat.h:280: warning: ‘AVFrac’ is deprecated
sierravmd.c: In function ‘vmd_read_header’:
sierravmd.c:79: warning: ‘st’ may be used uninitialized in this function
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o smacker.o smacker.c
In file included from avformat.h:36,
                 from smacker.c:26:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from smacker.c:26:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o sol.o sol.c
In file included from avformat.h:36,
                 from sol.c:26:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from sol.c:26:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o swf.o swf.c
In file included from avformat.h:36,
                 from swf.c:22:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from swf.c:22:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o tiertexseq.o tiertexseq.c
In file included from avformat.h:36,
                 from tiertexseq.c:27:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from tiertexseq.c:27:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o tta.o tta.c
In file included from avformat.h:36,
                 from tta.c:21:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from tta.c:21:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o vocenc.o vocenc.c
In file included from avformat.h:36,
                 from voc.h:25,
                 from vocenc.c:22:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from voc.h:25,
                 from vocenc.c:22:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o wav.o wav.c
In file included from avformat.h:36,
                 from wav.c:21:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from wav.c:21:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o wc3movie.o wc3movie.c
In file included from avformat.h:36,
                 from wc3movie.c:30:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from wc3movie.c:30:
avformat.h:280: warning: ‘AVFrac’ is deprecated
wc3movie.c:72: warning: ‘AVPaletteControl’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o westwood.o westwood.c
In file included from avformat.h:36,
                 from westwood.c:36:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from westwood.c:36:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o wv.o wv.c
In file included from avformat.h:36,
                 from wv.c:22:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from wv.c:22:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o yuv4mpeg.o yuv4mpeg.c
In file included from avformat.h:36,
                 from yuv4mpeg.c:21:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from yuv4mpeg.c:21:
avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o audio.o audio.c
In file included from avformat.h:36,
                 from audio.c:21:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from audio.c:21:
avformat.h:280: warning: ‘AVFrac’ is deprecated
rm -f libavformat-kino.a
ar rc libavformat-kino.a utils.o cutils.o os_support.o allformats.o framehook.o avio.o aviobuf.o file.o 4xm.o adtsenc.o aiff.o riff.o amr.o asf.o asf-enc.o au.o avidec.o avienc.o avs.o vocdec.o voc.o crc.o daud.o dsicin.o dv.o dvenc.o electronicarts.o ffm.o flic.o flvdec.o flvenc.o gif.o gifdec.o gxf.o gxfenc.o idcin.o idroq.o img2.o ipmovie.o matroska.o mm.o mmf.o mov.o isom.o movenc.o mp3.o mpc.o mpeg.o mpegts.o mpegtsenc.o mpjpeg.o mtv.o mxf.o nsvdec.o nuv.o ogg2.o oggparsevorbis.o oggparsetheora.o oggparseflac.o oggparseogm.o psxstr.o raw.o nutdec.o rm.o segafilm.o sierravmd.o smacker.o sol.o swf.o tiertexseq.o tta.o vocenc.o wav.o wc3movie.o westwood.o wv.o yuv4mpeg.o audio.o 
ranlib libavformat-kino.a
make[3]: Leaving directory `/home/kyle/kino-1.0.0/ffmpeg/libavformat'
make -C libswscale  all
make[3]: Entering directory `/home/kyle/kino-1.0.0/ffmpeg/libswscale'
gcc  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o swscale.o swscale.c
In file included from swscale.c:875:
swscale_template.c: In function ‘hyscale_MMX’:
swscale_template.c:2556: warning: passing argument 4 of ‘palToY_MMX’ from incompatible pointer type
swscale_template.c: In function ‘hcscale_MMX’:
swscale_template.c:2772: warning: passing argument 6 of ‘palToUV_MMX’ from incompatible pointer type
swscale_template.c: In function ‘swScale_MMX’:
swscale_template.c:3172: warning: cast from pointer to integer of different size
swscale_template.c:3180: warning: cast from pointer to integer of different size
swscale.c: In function ‘gray16swap’:
swscale.c:1791: warning: initialization from incompatible pointer type
swscale.c:1792: warning: initialization from incompatible pointer type
gcc  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o rgb2rgb.o rgb2rgb.c
gcc  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3  -c -o yuv2rgb.o yuv2rgb.c
yuv2rgb.c:368: warning: ‘yuv2rgb_c_8’ defined but not used
yuv2rgb.c:423: warning: ‘yuv2rgb_c_4’ defined but not used
yuv2rgb.c:495: warning: ‘yuv2rgb_c_4b’ defined but not used
rm -f libswscale-kino.a
ar rc libswscale-kino.a swscale.o rgb2rgb.o yuv2rgb.o 
ranlib libswscale-kino.a
make[3]: Leaving directory `/home/kyle/kino-1.0.0/ffmpeg/libswscale'
gcc -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3 -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec -I"/home/kyle/kino-1.0.0/ffmpeg"/libavformat -I"/home/kyle/kino-1.0.0/ffmpeg"/libswscale -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -c -o ffmpeg.o ffmpeg.c
In file included from /home/kyle/kino-1.0.0/ffmpeg/libavformat/avformat.h:36,
                 from ffmpeg.c:24:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from ffmpeg.c:24:
/home/kyle/kino-1.0.0/ffmpeg/libavformat/avformat.h:280: warning: ‘AVFrac’ is deprecated
gcc -fomit-frame-pointer -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3 -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg" -I"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -I"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec -I"/home/kyle/kino-1.0.0/ffmpeg"/libavformat -I"/home/kyle/kino-1.0.0/ffmpeg"/libswscale -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -c -o cmdutils.o cmdutils.c
In file included from /home/kyle/kino-1.0.0/ffmpeg/libavformat/avformat.h:36,
                 from cmdutils.c:22:
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2439: warning: ‘ImgReSampleContext’ is deprecated
/home/kyle/kino-1.0.0/ffmpeg/libavcodec/avcodec.h:2442: warning: ‘ImgReSampleContext’ is deprecated
In file included from cmdutils.c:22:
/home/kyle/kino-1.0.0/ffmpeg/libavformat/avformat.h:280: warning: ‘AVFrac’ is deprecated
touch .libs
gcc -L"/home/kyle/kino-1.0.0/ffmpeg"/libavformat -L"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec -L"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -Wl,--warn-common  -Wl,--as-needed -Wl,-rpath-link,"/home/kyle/kino-1.0.0/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/kyle/kino-1.0.0/ffmpeg"/libavformat -Wl,-rpath-link,"/home/kyle/kino-1.0.0/ffmpeg"/libavutil -g -L./libswscale -o ffmpeg_g-kino ffmpeg.o cmdutils.o -lavformat-kino -lavcodec-kino -lavutil-kino -lm  -lswscale-kino
cp -p ffmpeg_g-kino ffmpeg-kino
strip ffmpeg-kino
make[2]: Leaving directory `/home/kyle/kino-1.0.0/ffmpeg'
Making all in src
make[2]: Entering directory `/home/kyle/kino-1.0.0/src'
Making all in cell-renderers
make[3]: Entering directory `/home/kyle/kino-1.0.0/src/cell-renderers'
cd . \
        && glib-genmarshal --prefix=mg_marshal mg-marshal.list --body >> xgen-gmc \
        && cp xgen-gmc mg-marshal.c \
        && rm -f xgen-gmc xgen-gmc~
cd . \
        && glib-genmarshal --prefix=mg_marshal mg-marshal.list --header >> xgen-gmh \
        && (cmp -s xgen-gmh mg-marshal.h || cp xgen-gmh mg-marshal.h) \
        && rm -f xgen-gmh xgen-gmh~
make  all-am
make[4]: Entering directory `/home/kyle/kino-1.0.0/src/cell-renderers'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -I../.. -I../../src -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2   -MT mg-cell-renderer-popup.o -MD -MP -MF ".deps/mg-cell-renderer-popup.Tpo" -c -o mg-cell-renderer-popup.o mg-cell-renderer-popup.c; \
        then mv -f ".deps/mg-cell-renderer-popup.Tpo" ".deps/mg-cell-renderer-popup.Po"; else rm -f ".deps/mg-cell-renderer-popup.Tpo"; exit 1; fi
mg-cell-renderer-popup.c: In function ‘mcrp_start_editing’:
mg-cell-renderer-popup.c:412: warning: dereferencing type-punned pointer will break strict-aliasing rules
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -I../.. -I../../src -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2   -MT mg-cell-renderer-list.o -MD -MP -MF ".deps/mg-cell-renderer-list.Tpo" -c -o mg-cell-renderer-list.o mg-cell-renderer-list.c; \
        then mv -f ".deps/mg-cell-renderer-list.Tpo" ".deps/mg-cell-renderer-list.Po"; else rm -f ".deps/mg-cell-renderer-list.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -I../.. -I../../src -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2   -MT mg-popup-entry.o -MD -MP -MF ".deps/mg-popup-entry.Tpo" -c -o mg-popup-entry.o mg-popup-entry.c; \
        then mv -f ".deps/mg-popup-entry.Tpo" ".deps/mg-popup-entry.Po"; else rm -f ".deps/mg-popup-entry.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -I../.. -I../../src -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2   -MT mg-marshal.o -MD -MP -MF ".deps/mg-marshal.Tpo" -c -o mg-marshal.o mg-marshal.c; \
        then mv -f ".deps/mg-marshal.Tpo" ".deps/mg-marshal.Po"; else rm -f ".deps/mg-marshal.Tpo"; exit 1; fi
rm -f libcellrenderers.a
ar cru libcellrenderers.a mg-cell-renderer-popup.o mg-cell-renderer-list.o mg-popup-entry.o mg-marshal.o 
ranlib libcellrenderers.a
make[4]: Leaving directory `/home/kyle/kino-1.0.0/src/cell-renderers'
make[3]: Leaving directory `/home/kyle/kino-1.0.0/src/cell-renderers'
Making all in timfx
make[3]: Entering directory `/home/kyle/kino-1.0.0/src/timfx'
Making all in lumas
make[4]: Entering directory `/home/kyle/kino-1.0.0/src/timfx/lumas'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/kyle/kino-1.0.0/src/timfx/lumas'
make[4]: Entering directory `/home/kyle/kino-1.0.0/src/timfx'
if /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -D_FILE_OFFSET_BITS=64 -DKINO_PLUGINDIR=\""/usr/local/lib/kino-gtk2/kino-gtk2"\" -DDATADIR=\""/usr/local/share"\"    -g -O2 -MT entry_points.lo -MD -MP -MF ".deps/entry_points.Tpo" -c -o entry_points.lo entry_points.cc; \
        then mv -f ".deps/entry_points.Tpo" ".deps/entry_points.Plo"; else rm -f ".deps/entry_points.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -D_FILE_OFFSET_BITS=64 -DKINO_PLUGINDIR=\"/usr/local/lib/kino-gtk2/kino-gtk2\" -DDATADIR=\"/usr/local/share\" -g -O2 -MT entry_points.lo -MD -MP -MF .deps/entry_points.Tpo -c entry_points.cc  -fPIC -DPIC -o .libs/entry_points.o
/usr/include/pthread.h:285: error: conflicting declaration 'typedef struct pthread_st* pthread_t'
/usr/include/bits/pthreadtypes.h:36: error: 'pthread_t' has a previous declaration as 'typedef long unsigned int pthread_t'
/usr/include/pthread.h:286: error: conflicting declaration 'typedef struct pthread_attr_st* pthread_attr_t'
/usr/include/bits/pthreadtypes.h:43: error: 'pthread_attr_t' has a previous declaration as 'typedef union pthread_attr_t pthread_attr_t'
/usr/include/pthread.h:287: error: conflicting declaration 'typedef int pthread_key_t'
/usr/include/bits/pthreadtypes.h:109: error: 'pthread_key_t' has a previous declaration as 'typedef unsigned int pthread_key_t'
/usr/include/pthread.h:289: error: conflicting declaration 'typedef int pthread_mutexattr_t'
/usr/include/bits/pthreadtypes.h:79: error: 'pthread_mutexattr_t' has a previous declaration as 'typedef union pthread_mutexattr_t pthread_mutexattr_t'
/usr/include/pthread.h:290: error: conflicting declaration 'typedef struct pthread_mutex_st* pthread_mutex_t'
/usr/include/bits/pthreadtypes.h:73: error: 'pthread_mutex_t' has a previous declaration as 'typedef union pthread_mutex_t pthread_mutex_t'
/usr/include/pthread.h:291: error: conflicting declaration 'typedef int pthread_condattr_t'
/usr/include/bits/pthreadtypes.h:105: error: 'pthread_condattr_t' has a previous declaration as 'typedef union pthread_condattr_t pthread_condattr_t'
/usr/include/pthread.h:292: error: conflicting declaration 'typedef struct pthread_cond_st* pthread_cond_t'
/usr/include/bits/pthreadtypes.h:99: error: 'pthread_cond_t' has a previous declaration as 'typedef union pthread_cond_t pthread_cond_t'
/usr/include/pthread.h:293: error: conflicting declaration 'typedef int pthread_rwlockattr_t'
/usr/include/bits/pthreadtypes.h:142: error: 'pthread_rwlockattr_t' has a previous declaration as 'typedef union pthread_rwlockattr_t pthread_rwlockattr_t'
/usr/include/pthread.h:294: error: conflicting declaration 'typedef struct pthread_rwlock_st* pthread_rwlock_t'
/usr/include/bits/pthreadtypes.h:136: error: 'pthread_rwlock_t' has a previous declaration as 'typedef union pthread_rwlock_t pthread_rwlock_t'
make[4]: *** [entry_points.lo] Error 1
make[4]: Leaving directory `/home/kyle/kino-1.0.0/src/timfx'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/kyle/kino-1.0.0/src/timfx'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kyle/kino-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kyle/kino-1.0.0'
make: *** [all] Error 2[/COLOR][/SIZE][/FONT]

 
Can someone tell me what's wrong? ( I configured it to enable quicktime)

---

### Post by nylecoj813 on 2007-06-15
Unfortuantely, I'm not quite sure how to help with the compiling.  But if you're not completely set on compiling it, there's a .deb here: [http://www.getdeb.net/app.php?name=Kino](http://www.getdeb.net/app.php?name=Kino)

---

### Post by dillbertdabomb on 2007-06-15
I tried the deb, it's cool and all, but I want to custom compile it because the deb didn't let me use raw1394 (no camcorder control) and I want quicktime support with it.

---

### Post by nylecoj813 on 2007-06-15
I got ya. Sorry, I can't help much more right now...but I may try to compile it once I'm home and on Ubuntu and see what happens. Hopefully someone more knowledgable can help in the meantime. 

Good luck!

---

### Post by benyau on 2007-07-24
The following worked for me with kino-1.1.0

1. make sure you have all the dependent files installed, [http://www.kinodv.org/article/view/155/1/13/](http://www.kinodv.org/article/view/155/1/13/)

2. uninstall libpthread-dev (it is a reported bug, [https://bugs.launchpad.net/ubuntu/+source/pth/+bug/81169](https://bugs.launchpad.net/ubuntu/+source/pth/+bug/81169))

3. compile as usual:
$ ./configure --sysconfdir=/etc --enable-quicktime
$ make
$ sudo make install

---

