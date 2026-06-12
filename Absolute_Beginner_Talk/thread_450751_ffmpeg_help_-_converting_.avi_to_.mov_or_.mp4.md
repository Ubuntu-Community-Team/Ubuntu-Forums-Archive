---
title: "ffmpeg help - converting .avi to .mov or .mp4"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-05-21
[Running Ubuntu 7.04]

Using the script from: [http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946) (due to vive on that page not working properly), i tried to convert an avi to either a mov or mp4 for my ipod.

The script is as follows:

```
#!/bin/bash
## ipodvidenc - The iPod Video Encoder for Linux.
## Created by Eric Hewitt, January 9, 2006.
## Released under the GPL.  Go nuts.

input_file=$1

echo "What would you like to name the output file (sans extension)?"

read output_file_name

echo "$output_file_name will be located in $PWD. Is this acceptable? [y/n]"

read output_file_loc_permis

if [ $output_file_loc_permis = 'n' ] || [ $output_file_loc_permis = 'N' ]
then
	echo "Where would you like to store $output_file_name.mov?"
	read output_dir
else
	output_dir=$PWD
fi

ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_dir}/${output_file_name}.mov"
```

Then i did this:

```
$ ipodvidenc inflamescloudconnectedmusicvid.avi 
What would you like to name the output file (sans extension)?
inflamesvid (i also tried with the file extension on here)
inflamesvid will be located in /home/daniel/Desktop. Is this acceptable? [y/n]
y
ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory
```

I then tried using just ffmpeg, and it gave the same error message.

I checked that both libraw1394 and it's corresponding -dev are installed, and they are.

Any help?

Thanks in advance :)

---

### Post by Cypher on 2007-05-21
Please do
```

ldd `which ffmpeg`

```
and show us the output

---

### Post by moredhel on 2007-05-22
sorry for the late reply - internet was off :(

```
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f70000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7f5c000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f58000)
        libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb7e9f000)
        libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb7da3000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7d7b000)
        libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb7d41000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb7d3c000)
        libfaad.so.0 => /usr/lib/libfaad.so.0 (0xb7ccd000)
        libfaac.so.0 => /usr/lib/libfaac.so.0 (0xb7cbc000)
        libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0xb7bd4000)
        libgsm.so.1 => /usr/lib/libgsm.so.1 (0xb7bc4000)
        libdc1394_control.so.13 => /usr/lib/libdc1394_control.so.13 (0xb7bb4000)
        libraw1394.so.5 => not found
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7a73000)
        /lib/ld-linux.so.2 (0xb7fad000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7989000)
        libmp4v2.so.0 => /usr/lib/libmp4v2.so.0 (0xb78ec000)
        libraw1394.so.8 => /usr/lib/libraw1394.so.8 (0xb78e5000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb78d9000)
```

---

### Post by moredhel on 2007-05-22
anyone know what is wrong?

---

### Post by moredhel on 2007-05-22
surely this can't be too hard to solve...

---

### Post by ron999 on 2007-05-22
Hi
I can't help you with that script.
But have you not considered using Avidemux to do the job.
I'm pretty sure that it will convert AVI files to MP4 format, and it's simple to use.

---

### Post by moredhel on 2007-05-22
thanks, I will try that :)

---

### Post by moredhel on 2007-05-22
yes it worked, thanks! :D

---

