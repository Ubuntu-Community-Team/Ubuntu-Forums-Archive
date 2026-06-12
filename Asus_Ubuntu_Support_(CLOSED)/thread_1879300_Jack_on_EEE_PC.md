---
title: "Jack on EEE PC"
date: 2011-11-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Aqlor on 2011-11-11
Hey,

Just bought an Asus EEE PC (1215B) and I am having some problems with audio on it.

First of all, when I connect the headphones the sound goes out from both ends - headphones and computer speakers. I heard this is a normal problem with EEE's now, what I usually do is change the volume with "alsamixer" on the terminal for each channel.

The other problem is setting up jack. I installed jack and qjackcl for a gui.

However I get errors trying to start jack: 

Once I start qjackcl I get this messages:

```
14:57:17.152 Patchbay deactivated.
14:57:17.322 Statistics reset.
14:57:17.339 ALSA connection change.
14:57:17.366 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
14:57:17.381 ALSA connection graph change.
```

So something is already wrong at this time, I try to start jack and I get two popups. The new messages are:

```
14:58:29.860 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: driver "alsa" selected
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Saving settings to "/home/levi/.config/jack/conf.xml" ...
Fri Nov 11 14:58:29 2011: Starting jack server...
Fri Nov 11 14:58:29 2011: JACK server starting in realtime mode with priority 10
Fri Nov 11 14:58:29 2011: control device hw:0
Fri Nov 11 14:58:29 2011: control device hw:0
Fri Nov 11 14:58:29 2011: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
Fri Nov 11 14:58:29 2011: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
Fri Nov 11 14:58:29 2011: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Fri Nov 11 14:58:29 2011: control device hw:0
Fri Nov 11 14:58:29 2011: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
Fri Nov 11 14:58:29 2011: [1m[31mERROR: Cannot initialize driver[0m
Fri Nov 11 14:58:29 2011: [1m[31mERROR: JackServer::Open() failed with -1[0m
Fri Nov 11 14:58:29 2011: [1m[31mERROR: Failed to open server[0m
14:58:33.300 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

I am searching the internet for sometime now and I can't seem to find a solution.

Anyone can help me?

---

### Post by mohamedtoma73 on 2011-11-12
try this
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

---

### Post by Aqlor on 2011-11-28
I get this:



Fetched 3,988 B in 3s (1,252 B/s)
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

