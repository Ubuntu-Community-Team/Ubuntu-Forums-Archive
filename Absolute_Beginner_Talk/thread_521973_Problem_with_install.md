---
title: "Problem with install"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-08-10
Im trying to install streamripper which I downloaded from the sourceforge website. I unzipped it to my home folder but im not sure how to install it. I read the install document which told me to type ./configure after I did cd /home. I tried this but got the message, 'no such file or directory./ wWhat am I missing here?

---

### Post by ukulele_ninja on 2007-08-10
**

---

### Post by ravenwere on 2007-08-10
The easiest way to install streamripper is via the Adept package manager, you could also install the kde frontend with it (kstreamripper).

If you still wanted to compile your own copy check the directory you are in type dir and see if the streamripper folder is there. If you installed it to your home directory it is usually /home/"username".

r

---

### Post by ukulele_ninja on 2007-08-10
I installed it from the packages...but how do i use it? Im tuned in using XMMS as that is what streamtuner opens for me. Do I need to use something else?

---

### Post by ravenwere on 2007-08-10
Having never used streamripper before I am no expert on it. I did find this however:

[http://www.unitedcoders.org/weblog/](http://www.unitedcoders.org/weblog/)

[I]Now you can rip music from your favorite internet station:
 
BASH-Code:

  streamripper [http://160.79.128.40:7754](http://160.79.128.40:7754) -d /home/xpheas/music -r 8008

 That rips music from sky.fm into my music folder.
 With "-r 8008" Streamripper creates a relay server on port 8008, so you can rip the stream and
 also listen it with your media player, without downloading the stream twice.
 Simply open "http://localhost:8008" on your media player.[/I]


It appears streamripper is basically a command line tool so you have to use it via the console as above. Of course substitute your directory instead of xpheas.

Typing kstreamripper from the command line gives you a GUI version of the above but you still have to get the IP address of the radio stream (eg 160.79.128.40: plus port number).

I quickly checked Amarok and that has radio streams available in the playlists section.

Hope this helps otherwise I would suggest posting a new question to get a quick reply.

cheers
r

---

