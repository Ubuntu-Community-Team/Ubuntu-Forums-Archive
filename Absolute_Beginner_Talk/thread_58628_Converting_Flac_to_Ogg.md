---
title: "Converting Flac to Ogg"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by bvilches on 2005-08-20
I can't convert Flac to Ogg ... I've tried many things but nothing seemed to work.

For example, I used oggenc ... but I get a 3kb file from a 24MB flac file!!
All of the scripts for Nautilus didn't work either.

I know something is wrong ... I've checked the libs but everything seems to be in order. What am I missing here?

I need your help on this one guys

Thanks

---

### Post by tom-ubuntu on 2005-08-21
I read sometime ago something about "audioconvert" (or "audio-convert"; can not remember). Do a search for it on google, you will find something. Post your experiences here, please.

---

### Post by cayamara on 2005-08-21
[QUOTE=bvilches]I can't convert Flac to Ogg ... I've tried many things but nothing seemed to work.

For example, I used oggenc ... but I get a 3kb file from a 24MB flac file!!
All of the scripts for Nautilus didn't work either.

I know something is wrong ... I've checked the libs but everything seems to be in order. What am I missing here?

I need your help on this one guys

Thanks[/QUOTE]

Hi!
How about [http://members.fortunecity.com/stateq/flac2ogg.html](http://members.fortunecity.com/stateq/flac2ogg.html)? It's a python script that does the converting (while preserving the metatags, I think).

To install it:
```
sudo apt-get install python perl vorbis-tools flac
cd ~ && wget -c http://freshmeat.net/redir/flac2ogg/50379/url_zip/flac2ogg-0.6.zip
unzip flac2ogg-*.zip && cd flac2ogg-*
chmod a+x flac2ogg
sudo mv ./flac2ogg /usr/bin
```

Now you should be able to run it by typing flac2ogg in the terminal. It will then ask you for the flac files you want to convert. I didn't try it yet, so use it at your own risk  ;-).

---

### Post by bvilches on 2005-08-22
I've tried with the python script ... but nothing happens.

I don't know if I'm doing something wrong or if it just doesn't work

---

### Post by cayamara on 2005-08-22
Allright, next try. The script didnt work for me either.  :-? 

This is how I got it working (flac -d test.flac supplies the wav file):
```
oggenc test.flac
```
If it doesnt work for you, you may try going over wav:
```
flac -d test.flac && oggenc test.wav
```
I hope you succed. At least it worked for me. If you still get errors, please post them and check that you have the "vorbis-tools" package installed.
```
sudo apt-get install vorbis-tools
```

Have fun!

---

### Post by bvilches on 2005-08-22
As I told before, when I use oggenc I get a 3kb ogg file from a 24MB flac file ... so something is wrong there.

I tried converting flac to wav first and here's what I get:

```
So_Nice.flac: *** Got error code 0:FLAC__STREAM_DECODER_ERROR_STATUS_LOST_SYNC


So_Nice.flac: ERROR while decoding data
              state = FLAC__STREAM_DECODER_READ_FRAME
```

---

### Post by cayamara on 2005-08-22
[QUOTE=bvilches]As I told before, when I use oggenc I get a 3kb ogg file from a 24MB flac file ... so something is wrong there.

I tried converting flac to wav first and here's what I get:

```
So_Nice.flac: *** Got error code 0:FLAC__STREAM_DECODER_ERROR_STATUS_LOST_SYNC


So_Nice.flac: ERROR while decoding data
              state = FLAC__STREAM_DECODER_READ_FRAME
```[/QUOTE]
hmm that's strange :-?. Does that happen with every flac?

Sorry that I overread that you tried oggenc before, btw. I have no problems with it, because it worked for me just fine.

---

### Post by bvilches on 2005-08-22
Yes, this happens with every file ... I really don't know what to do now

Thanks for your answers guys  ;-)

---

