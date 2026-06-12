---
title: "Streaming from myp2p with sopcast"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by jfd on 2007-12-15
I'm running Ubuntu 7.10, and I want to be able to watch videos streams from MyP2P.eu using Sopcast. I'm completely at loss as to how to get it up and running, and from what I've tried so far it doesn't look like it will run in Firefox.

Can anybody give me a beginners lesson in how to set it up and get it working?

I'm still fairly new to Ubuntu...

Any help would be greatly appreciated.

---

### Post by subs on 2007-12-15
maybe this will help..


[http://ubuntuforums.org/showthread.php?t=258049](http://ubuntuforums.org/showthread.php?t=258049)

---

### Post by jfd on 2007-12-15
I tried that and I got as far as installing the first link, and then I got stuck because when I went to Myp2p and tried to stream from a link i just got the message:

Firefox doesn't know how to open this address because the protocol (sop) isn't assosiated with any programe.

And the second link of that post says that it can't establish a connection.

:confused:

---

### Post by Chris Weaver on 2008-03-25
This is an old post and you might have come across the solution but I followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=703409](http://ubuntuforums.org/showthread.php?t=703409)

Worked like a treat!

---

### Post by pluckypigeon on 2008-03-31
The best way to view sopcast streaming is through the command line.

Open a terminal and type the sopcast address and the outgoing and incoming ports. In this example we use 8908 and 8909 as the ports.

(Hover the mouse over the link at myp2p to get the sopcast address)

Type:
```
sp-sc sop://broker1.sopcast.com:3912/22260 8908 8909
```

replace sop://broker1.sopcast.com:3912/22260 with the appropriate channel.

8908 and 8909 are the incoming and outgoing ports that you will be using

Give it a few seconds to load and open a new tab

Type:

```
vlc http://localhost:8909
``` replace vlc with your media player of choice. 

I find that you have to fiddle about with this sometimes to make it work e.g, you might have to type it twice or something. That's only in my experience though.

---

### Post by jfd on 2008-04-08
I did that, and it was working fine until I typed [http://localhost:8909](http://localhost:8909), where I got this error pop up:
[I]
Unable to open 'http://localhost:8909'[/I]

And this in the terminal:
[I]
VLC media player 0.8.6c Janus
[00000287] main access error: Connection to localhost port 8909 failed: Connection refused
[00000287] access_http access error: cannot connect to localhost:8909
[00000287] main access error: Connection to localhost port 8909 failed: Connection refused
[00000287] access_http access error: cannot connect to localhost:8909
[00000287] main access error: Connection to localhost port 8909 failed: Connection refused
[00000287] access_mms access error: cannot connect to localhost:8909
[00000284] main input error: no suitable access module for `[http://localhost:8909](http://localhost:8909)'
[00000279] main playlist: nothing to play
[00000279] main playlist: stopping playback
jfd@jfd-desktop:~$ vlc [http://localhost:8909](http://localhost:8909)
VLC media player 0.8.6c Janus
[00000294] main access error: Connection to localhost port 8909 failed: Connection refused
[00000294] access_http access error: cannot connect to localhost:8909
[00000294] main access error: Connection to localhost port 8909 failed: Connection refused
[00000294] access_http access error: cannot connect to localhost:8909
[00000294] main access error: Connection to localhost port 8909 failed: Connection refused
[00000294] access_mms access error: cannot connect to localhost:8909
[00000291] main input error: no suitable access module for `[http://localhost:8909](http://localhost:8909)'
[00000282] main playlist: nothing to play
[00000282] main playlist: stopping playback[/I]

So it's the closest I've got so far, but would you be able to help me with that?

---

### Post by northern lights on 2008-04-08
You might want to check out soplaunch - a GUI for sp-sc.

I think it's in the repos.

If so, run ```
sudo apt-get install soplaunch
```

---

