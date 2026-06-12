---
title: "Probs with LastFm"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-09-30
I haven't been able to get LastFm's website to work using their client. It works with Last-Exit and Amarok. I followed the instructions from the ReadMe file and installed qt3.3.6 so that I could compile their program and had no problems. However, when I try to open a station at their website Firefox gives me a message saying it doesn't know how to open this address because the protocol isn't associated with any program. How do I fix this?

---

### Post by dwight on 2006-09-30
From [Lastfm forums](http://www.last.fm/forum/21714/_/42837/0):

Type in "about:config" in the location bar
right click, select New --> String

name of string should be: "network.protocol-handler.app.lastfm"
value should be the path to your player executable, eg "~/Last.fm/player"

---

### Post by beamo on 2006-09-30
Thanks for the help, dwight. I did this late last night and forgot that I never got it to install. :-#     The Makefile has been generated but when I run ./lastfm I get the following error message
```
timbo@AMD64:~/Desktop/Last.fm_Client_1.0.0b$ ./lastfm
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    147 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    147 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
Could not open log file "/home/timbo/Desktop/Last.fm_Client_1.0.0b/container.log"
Running on: "en_US"
Could not open log file "/home/timbo/Desktop/Last.fm_Client_1.0.0b/webservice.log"
Could not open log file "/home/timbo/Desktop/Last.fm_Client_1.0.0b/httpinput.log"
Could not open log file "/home/timbo/Desktop/Last.fm_Client_1.0.0b/transcode.log"
Could not open log file "/home/timbo/Desktop/Last.fm_Client_1.0.0b/playback.log"


```
I am clueless as to what is wrong. I really appreciate the help.

---

### Post by dwight on 2006-09-30
Is there a particular reason why you want to compile it yourself? I'm using the binary provided by lastfm and it works just fine.

---

### Post by danderson3 on 2006-10-14
LastFM labels their download a source download for beta 1.0.0. It is a
binary download.  Unfortunately it segfaults when I hit Play ( on Dapper ).
Any tips?

David

---

### Post by PriceChild on 2006-10-14
I've installed lastfm from the repositories. (I'm on edgy though, not sure if its in dapper)

I needed to change the output to oss from alsa in order to prevent a seg fault.

---

### Post by danderson3 on 2006-10-14
thanks... I can't find it in dapper under search fm/search last.
and the tools/options/radio/system picklist only shows alsa <sigh>

what version of lastfm are you running?

---

### Post by PriceChild on 2006-10-14
> **danderson3 said:**
> thanks... I can't find it in dapper under search fm/search last.
and the tools/options/radio/system picklist only shows alsa <sigh>Ah yes, its in Multimedia (Universe) on Edgy, not Dapper.

---

