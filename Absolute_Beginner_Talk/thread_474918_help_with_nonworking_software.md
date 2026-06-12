---
title: "help with nonworking software"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-06-15
I installed a software called pspvc (psp video converter) but I can't get It to run. When I try I get
```
KDEInit could not launch 'pspvc'.:
Could not find 'pspvc' executable.
```
I installed it with a .sh. So I don't know were the executable file is so any help getting it to run right or uninstalling it would be great.

---

### Post by YoG%*@ on 2007-06-15
hi

try locating the executable, 
```

sudo updatedb
locate pspvc

```
when you find the executable, you could add the directory it is in to your path. 
though the install script actually should have put it in a proper place ... are you sure that everything was correctly installed? 

hth
mux

---

### Post by microsoft92sucks on 2007-06-15
the instaltion seemed to go fine. But i'm not 100%. And here's what I got back from locate pspvc.
```
/usr/share/applications/pspvc.desktop
/usr/local/share/pspvc
/usr/local/share/pspvc/lib
/usr/local/share/pspvc/lib/vhook
/usr/local/share/pspvc/lib/vhook/null.so
/usr/local/share/pspvc/lib/vhook/ppm.so
/usr/local/share/pspvc/lib/vhook/fish.so
/usr/local/share/pspvc/lib/vhook/watermark.so
/usr/local/share/pspvc/lib/vhook/drawtext.so
/usr/local/share/pspvc/lib/libavutil.a
/usr/local/share/pspvc/lib/libx264.a
/usr/local/share/pspvc/lib/libavformat.a
/usr/local/share/pspvc/lib/pkgconfig
/usr/local/share/pspvc/lib/pkgconfig/x264.pc
/usr/local/share/pspvc/lib/pkgconfig/libavcodec.pc
/usr/local/share/pspvc/lib/pkgconfig/libavutil.pc
/usr/local/share/pspvc/lib/pkgconfig/libavformat.pc
/usr/local/share/pspvc/lib/libavcodec.a
/usr/local/share/pspvc/bin
/usr/local/share/pspvc/bin/ffmpeg
/usr/local/share/pspvc/bin/ffserver
/usr/local/share/pspvc/bin/x264
/usr/local/share/pspvc/bin/ffplay
/usr/local/share/pspvc/include
/usr/local/share/pspvc/include/ffmpeg
/usr/local/share/pspvc/include/ffmpeg/log.h
/usr/local/share/pspvc/include/ffmpeg/rational.h
/usr/local/share/pspvc/include/ffmpeg/avformat.h
/usr/local/share/pspvc/include/ffmpeg/fifo.h
/usr/local/share/pspvc/include/ffmpeg/opt.h
/usr/local/share/pspvc/include/ffmpeg/avio.h
/usr/local/share/pspvc/include/ffmpeg/mathematics.h
/usr/local/share/pspvc/include/ffmpeg/md5.h
/usr/local/share/pspvc/include/ffmpeg/avutil.h
/usr/local/share/pspvc/include/ffmpeg/avcodec.h
/usr/local/share/pspvc/include/ffmpeg/rtp.h
/usr/local/share/pspvc/include/ffmpeg/swscale.h
/usr/local/share/pspvc/include/ffmpeg/rtspcodes.h
/usr/local/share/pspvc/include/ffmpeg/adler32.h
/usr/local/share/pspvc/include/ffmpeg/common.h
/usr/local/share/pspvc/include/ffmpeg/integer.h
/usr/local/share/pspvc/include/ffmpeg/rtsp.h
/usr/local/share/pspvc/include/ffmpeg/intfloat_readwrite.h
/usr/local/share/pspvc/include/x264.h

```
So what do I do now to get it to run. 
Sorry still not very good at terminal install and stuff of that sort.

---

### Post by YoG%*@ on 2007-06-15
the stuff in the bin directory - 
/usr/local/share/pspvc/bin/ffmpeg
/usr/local/share/pspvc/bin/ffserver
/usr/local/share/pspvc/bin/x264
/usr/local/share/pspvc/bin/ffplay
should all be executables. is one of them the one you're looking for?

---

### Post by microsoft92sucks on 2007-06-15
I don't know. How would I check each one to find the one that works.

---

### Post by YoG%*@ on 2007-06-15
you can run the program using the full path, e.g.
/usr/local/share/pspvc/bin/ffmpeg

---

### Post by microsoft92sucks on 2007-06-15
If I run it like that all that happens is this comes up.
```
-rc_qmod_amp       <float> E.V..
-rc_qmod_freq      <int>   E.V..
-rc_eq             <string> E.V.. set rate control equation
-maxrate           <int>   E.V.. set max video bitrate tolerance (in bits/s)
-minrate           <int>   E.V.. set min video bitrate tolerance (in bits/s)
-bufsize           <int>   E.V.. set ratecontrol buffer size (in bits)
-rc_buf_aggressivity <float> E.V..
-i_qfactor         <float> E.V.. qp factor between p and i frames
-i_qoffset         <float> E.V.. qp offset between p and i frames
-rc_init_cplx      <float> E.V.. initial complexity for 1-pass encoding
-dct               <int>   E.V..
   auto                    E.V..
   fastint                 E.V..
   int                     E.V..
   mmx                     E.V..
   mlib                    E.V..
   altivec                 E.V..
   faan                    E.V..
-lumi_mask         <float> E.V.. lumimasking
-tcplx_mask        <float> E.V.. temporal complexity masking
-scplx_mask        <float> E.V.. spatial complexity masking
-p_mask            <float> E.V.. inter masking
-dark_mask         <float> E.V.. darkness masking
-idct              <int>   EDV..
   auto                    EDV..
   int                     EDV..
   simple                  EDV..
   simplemmx               EDV..
   libmpeg2mmx             EDV..
   ps2                     EDV..
   mlib                    EDV..
   arm                     EDV..
   altivec                 EDV..
   sh4                     EDV..
   simplearm               EDV..
   simplearmv5te           EDV..
   h264                    EDV..
   vp3                     EDV..
   ipp                     EDV..
   xvidmmx                 EDV..
-ec                <flags> .DV..
   guess_mvs               .DV..
   deblock                 .DV..
-pred              <int>   E.V.. prediction method
   left                    E.V..
   plane                   E.V..
   median                  E.V..
-aspect            <rational> E.V..
-debug             <flags> EDVAS print specific debug info
   pict                    .DV..
   rc                      E.V..
   bitstream               .DV..
   mb_type                 .DV..
   qp                      .DV..
   mv                      .DV..
   dct_coeff               .DV..
   skip                    .DV..
   startcode               .DV..
   pts                     .DV..
   er                      .DV..
   mmco                    .DV..
   bugs                    .DV..
   vis_qp                  .DV..
   vis_mb_type             .DV..
-vismv             <int>   .DV.. visualize motion vectors
   pf                      .DV..
   bf                      .DV..
   bb                      .DV..
-mb_qmin           <int>   E.V..
-mb_qmax           <int>   E.V..
-cmp               <int>   E.V.. full pel me compare function
   sad                     E.V..
   sse                     E.V..
   satd                    E.V..
   dct                     E.V..
   psnr                    E.V..
   bit                     E.V..
   rd                      E.V..
   zero                    E.V..
   vsad                    E.V..
   vsse                    E.V..
   nsse                    E.V..
   w53                     E.V..
   w97                     E.V..
   dctmax                  E.V..
   chroma                  E.V..
-subcmp            <int>   E.V.. sub pel me compare function
   sad                     E.V..
   sse                     E.V..
   satd                    E.V..
   dct                     E.V..
   psnr                    E.V..
   bit                     E.V..
   rd                      E.V..
   zero                    E.V..
   vsad                    E.V..
   vsse                    E.V..
   nsse                    E.V..
   w53                     E.V..
   w97                     E.V..
   dctmax                  E.V..
   chroma                  E.V..
-mbcmp             <int>   E.V.. macroblock compare function
   sad                     E.V..
   sse                     E.V..
   satd                    E.V..
   dct                     E.V..
   psnr                    E.V..
   bit                     E.V..
   rd                      E.V..
   zero                    E.V..
   vsad                    E.V..
   vsse                    E.V..
   nsse                    E.V..
   w53                     E.V..
   w97                     E.V..
   dctmax                  E.V..
   chroma                  E.V..
-ildctcmp          <int>   E.V.. interlaced dct compare function
   sad                     E.V..
   sse                     E.V..
   satd                    E.V..
   dct                     E.V..
   psnr                    E.V..
   bit                     E.V..
   rd                      E.V..
   zero                    E.V..
   vsad                    E.V..
   vsse                    E.V..
   nsse                    E.V..
   w53                     E.V..
   w97                     E.V..
   dctmax                  E.V..
   chroma                  E.V..
-dia_size          <int>   E.V..
-last_pred         <int>   E.V..
-preme             <int>   E.V.. pre motion estimation
-precmp            <int>   E.V.. pre motion estimation compare function
   sad                     E.V..
   sse                     E.V..
   satd                    E.V..
   dct                     E.V..
   psnr                    E.V..
   bit                     E.V..
   rd                      E.V..
   zero                    E.V..
   vsad                    E.V..
   vsse                    E.V..
   nsse                    E.V..
   w53                     E.V..
   w97                     E.V..
   dctmax                  E.V..
   chroma                  E.V..
-pre_dia_size      <int>   E.V..
-subq              <int>   E.V.. sub pel motion estimation quality
-me_range          <int>   E.V.. limit motion vectors range (1023 for DivX player)
-ibias             <int>   E.V.. intra quant bias
-pbias             <int>   E.V.. inter quant bias
-coder             <int>   E.V..
   vlc                     E.V.. variable length coder / huffman coder
   ac                      E.V.. arithmetic coder
-context           <int>   E.V.. context model
-mbd               <int>   E.V..
   simple                  E.V..
   bits                    E.V..
   rd                      E.V..
-sc_threshold      <int>   E.V.. scene change threshold
-lmin              <int>   E.V.. min lagrange factor (VBR)
-lmax              <int>   E.V.. max lagrange factor (VBR)
-nr                <int>   E.V.. noise reduction
-rc_init_occupancy <int>   E.V..
-inter_threshold   <int>   E.V..
-flags2            <flags> EDVA.
   fast                    E.V.. allow non spec compliant speedup tricks
   sgop                    E.V.. strictly enforce gop size
   noout                   E.V.. skip bitstream encoding
   local_header            E.V.. place global headers at every keyframe instead of in extradata
   bpyramid                E.V..
   wpred                   E.V..
   mixed_refs              E.V..
   8x8dct                  E.V..
   fastpskip               E.V..
   aud                     E.V..
   brdo                    E.V..
   ivlc                    E.V.. intra vlc table
-error             <int>   E.V..
-antialias         <int>   .DV..
   auto                    .DV..
   fastint                 .DV..
   int                     .DV..
   float                   .DV..
-qns               <int>   E.V.. quantizer noise shaping
-threads           <int>   EDV..
-mb_threshold      <int>   E.V.. macroblock threshold
-dc                <int>   E.V.. intra_dc_precision
-nssew             <int>   E.V.. nsse weight
-skip_top          <int>   .DV..
-skip_bottom       <int>   .DV..
-profile           <int>   E.VA.
   unknown                 E.VA.
-level             <int>   E.VA.
   unknown                 E.VA.
-lowres            <int>   .DV..
-skip_threshold    <int>   E.V.. frame skip threshold
-skip_factor       <int>   E.V.. frame skip factor
-skip_exp          <int>   E.V.. frame skip exponent
-skipcmp           <int>   E.V.. frame skip compare function
   sad                     E.V..
   sse                     E.V..
   satd                    E.V..
   dct                     E.V..
   psnr                    E.V..
   bit                     E.V..
   rd                      E.V..
   zero                    E.V..
   vsad                    E.V..
   vsse                    E.V..
   nsse                    E.V..
   w53                     E.V..
   w97                     E.V..
   dctmax                  E.V..
   chroma                  E.V..
-border_mask       <float> E.V..
-mblmin            <int>   E.V.. min macroblock quantizer scale (VBR)
-mblmax            <int>   E.V.. max macroblock quantizer scale (VBR)
-mepc              <int>   E.V.. motion estimation bitrate penalty compensation (1.0 = 256)
-bidir_refine      <int>   E.V..
-brd_scale         <int>   E.V..
-crf               <float> E.V..
-cqp               <int>   E.V..
-keyint_min        <int>   E.V..
-refs              <int>   E.V..
-chromaoffset      <int>   E.V..
-bframebias        <int>   E.V..
-trellis           <int>   E.VA.
-directpred        <int>   E.V..
-complexityblur    <float> E.V..
-deblockalpha      <int>   E.V..
-deblockbeta       <int>   E.V..
-partitions        <flags> E.V..
   parti4x4                E.V..
   parti8x8                E.V..
   partp4x4                E.V..
   partp8x8                E.V..
   partb8x8                E.V..
-sc_factor         <int>   E.V..
-mv0_threshold     <int>   E.V..
-b_sensitivity     <int>   E.V..
-compression_level <int>   E.VA.
-use_lpc           <int>   E..A.
-lpc_coeff_precision <int>   E..A.
-min_prediction_order <int>   E..A.
-max_prediction_order <int>   E..A.
-prediction_order_method <int>   E..A.
-min_partition_order <int>   E..A.
-max_partition_order <int>   E..A.
AVFormatContext AVOptions:
-probesize         <int>   .D...
-muxrate           <int>   E.... set mux rate
-packetsize        <int>   E.... set packet size
-fflags            <flags> .D...
   ignidx                  .D... ignore index
   genpts                  .D... generate pts
-track             <int>   E....  set the track number
-year              <int>   E.... set the year

``` 
But there's a lot more of it then that and I tried the other things in bin and non of them do anything any better.

---

