---
title: "make kaffeine stop saving stream (or a software that records stream on demand)"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2006-08-21
I just discovered ( :) ) that kaffeine can record streams (like an online radio channel) when you do file > save stream. but how do you make it stop?? 

or, if you can't, do we have a software on th repos that records radio stream on demand? what I wanna do is to start listening, record one song, stop the recording while I continue to listen to the radio, and start recording again when I hear something I like. 

Disclaimer: this is legal afaik bc radio station is not in the US. 

thanks a lot :)

---

### Post by easyease on 2006-08-21
"streamripper" is a command line tool for ripping streams and "streamtuner" is a graphical front-end for it.

---

### Post by towsonu2003 on 2006-08-21
> **easyease said:**
> "streamripper" is a command line tool for ripping streams and "streamtuner" is a graphical front-end for it.

hmmm, it didn't work for some reason. it launches xmms, which wants to open a file... the station begins with mms://station.url.here

weird? 

PS. I quit smoking, so I'm a little stupid these days...

---

### Post by towsonu2003 on 2006-08-22
mimms solved the problem. I use kaffeine to listen, mimms to record... 
```

mimms -o filename.asf mms://url.url.url
```

---

### Post by msak007 on 2006-08-22
> **towsonu2003 said:**
> hmmm, it didn't work for some reason. it launches xmms, which wants to open a file... the station begins with mms://station.url.here

weird? 

streamtuner has a "Record" button along the top toolbar. Rather than double-clicking the station name (which will open it up in xmms), either right-click and choose "Record" or click on the button. It'll open up a terminal, tune into the station, and record it using streamripper. This method doesn't have a "Stop" button either, but you can stop it via CTRL+C.

---

### Post by jonesyp on 2006-10-02
Can I ask how you confirgured Kaffeine, and which version of Ubuntu or Kubuntu you are using?  I like many other have a problem trying to save streams.  The system just hangs.  Thanks for your help.

Peter

---

### Post by towsonu2003 on 2006-10-02
> **jonesyp said:**
> Can I ask how you confirgured Kaffeine, and which version of Ubuntu or Kubuntu you are using?  I like many other have a problem trying to save streams.  The system just hangs.  Thanks for your help.

Peter

I have Ubuntu 6.06 (apt-getted kaffeine afterwards). didn't do any specific configuration. after starting to play, I tell it to record and it does. but I have to close it as I donno how to tell it to stop... 

maybe the problem is with specific streams you tried? try this one: mms://xiphias.vargonen.net/PowerXL
it  doesn't hang for me. 

I use this one now though to record:
mimms -o filename.asf mms://url.url.url

---

