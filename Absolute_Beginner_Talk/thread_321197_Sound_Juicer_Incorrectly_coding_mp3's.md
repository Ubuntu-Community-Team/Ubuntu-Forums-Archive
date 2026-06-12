---
title: "Sound Juicer: Incorrectly coding mp3's"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by thanorai on 2006-12-18
Sound Juicer will encode to the 4 default  without any problem.  I have created the mp3 option per numerous posts with the following pipelines:

audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux

audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc ! vbr=0 ! bitrate=196 ! id3v2mux

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

and some minor variations.  I do not get any errors, but the created *.mp3 is the same size as the original *.wav file and is not functional.

Lame is installed and I am truly baffled by the lack of errors and the incorrectly coded file.

Linux coldfyre 2.6.15-27-amd64-generic #1 SMP PREEMPT Fri Dec 8 17:50:54 UTC 2006 x86_64 GNU/Linux


:(

---

### Post by mitch.c on 2006-12-18
> **thanorai said:**
> Sound Juicer will encode to the 4 default  without any problem.  I have created the mp3 option per numerous posts with the following pipelines:

audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux

audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc ! vbr=0 ! bitrate=196 ! id3v2mux

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

and some minor variations.  I do not get any errors, but the created *.mp3 is the same size as the original *.wav file and is not functional.

Lame is installed and I am truly baffled by the lack of errors and the incorrectly coded file.

Linux coldfyre 2.6.15-27-amd64-generic #1 SMP PREEMPT Fri Dec 8 17:50:54 UTC 2006 x86_64 GNU/Linux


:(

Here's mine. Works for me:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3mux
```
Check output of:
```
$ gst-inspect-0.10 | grep lame
$ gst-inspect-0.10 | grep id3mux
```
Installed?

---

### Post by thanorai on 2006-12-19
> **mitch.c said:**
> Here's mine. Works for me:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3mux
```

**[SIZE="4"][COLOR="Red"]Same result.[/COLOR][/SIZE]**

> **mitch.c said:**
> 
Check output of:
```

$ gst-inspect-0.10 | grep lame
$ gst-inspect-0.10 | grep id3mux
```
Installed?


[COLOR="Red"]However the gst-inpect-0.10 did not return lame or id3mux.  My package manager shows the following lame packages as installed:
[SIZE="2"]gstreamer0.8-lame   0.8.12-1
lame                             3.96.1-1
liblime0                        3.96.1-1[/SIZE][/COLOR]

I could post the whole output, but it looks like you are on the right track.  Any idea of how to get gstream to show lame installed?

---

### Post by mitch.c on 2006-12-19
I could post the whole output, but it looks like you are on the right track.  Any idea of how to get gstream to show lame installed?[/QUOTE]
Here's the plugin packages I have installed:
```
$ aptitude -F "%c $a $M %30p %v#" search gstreamer0.10-plugins | grep ^i
i   gstreamer0.10-plugins-bad                       0.10.3-0ubuntu3
i   gstreamer0.10-plugins-bad-multiverse            0.10.3-3
i   gstreamer0.10-plugins-base                      0.10.7-0ubuntu5
i   gstreamer0.10-plugins-base-apps                 0.10.7-0ubuntu5
i   gstreamer0.10-plugins-good                      0.10.3-0ubuntu4
i   gstreamer0.10-plugins-ugly                      0.10.3-0ubuntu3
i   gstreamer0.10-plugins-ugly-multiverse           0.10.3-2
```
lame comes from 'plugins-ugly-multiverse'; id3mux from 'plugins-ugly'.

Make sure 'universe' and 'multiverse' repositories are enabled. After that, if you want to make this easy, copy and paste to terminal:
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs
```

---

### Post by thanorai on 2006-12-19
Working on the dependencies on this.  A little short on time, but I will update on this in the next week.  Thanks for all the help so far.  This looks like the right track...  Painful dependency.

---

### Post by vvlist on 2006-12-23
I had the -exact- problem you did, and installing the "gstreamer0.10-plugins-ugly" package fixes it. It contains "liblame." Merry Christmas!

---

### Post by brad558805 on 2007-05-28
Thanks everyone, this helped me too!

---

