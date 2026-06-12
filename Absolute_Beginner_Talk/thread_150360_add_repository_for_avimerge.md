---
title: "add repository for avimerge"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by vector on 2006-03-25
Hi all
Lost yet again.
Im trying to merge two avis.. cat didnt work but some posts said try avimerge.
apt-get avimerge.... nothin apt-cache search avimerge...nothin
ok so where is it?](*,)

---

### Post by vector on 2006-03-25
avimerge is part of the transcode (If only I knew how to find that out) which is already installed

---

### Post by shubjero on 2007-01-09
Nice, it does contain avimerge.  Thanks for your help!

---------------------------------------------------------------------------

root@venkman:/media/mp3# apt-get install transcode
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gawk libfame-0.9 libgtk1.2 libgtk1.2-common libmpeg2-4 libpostproc0d libpvm3
Suggested packages:
  libdvdcss xvid4conf
Recommended packages:
  pvm sox toolame transcode-doc
The following NEW packages will be installed:
  gawk libfame-0.9 libgtk1.2 libgtk1.2-common libmpeg2-4 libpostproc0d libpvm3 transcode
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 4092kB of archives.
After unpacking, 11.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y

----------------------------------------------------------------------------------

root@venkman:/media/mp3# avimerge
avimerge (transcode v1.0.2) (C) 2001-2004 Thomas Oestreich, T. Bitterberg

Usage: avimerge [options]
         -o file                   output file name
         -i file1 [file2 [...]]    input file(s)
         -p file                   multiplex additional audio track from file
         -a num                    select audio track number from input file [0]
         -A num                    select audio track number in output file [next]
         -b n                      handle vbr audio [autodetect]
         -c                        drop video frames in case audio is missing [off]
         -f FILE                   read AVI comments from FILE [off]
         -x FILE                   read AVI index from FILE [off] (see aviindex(1))

---

