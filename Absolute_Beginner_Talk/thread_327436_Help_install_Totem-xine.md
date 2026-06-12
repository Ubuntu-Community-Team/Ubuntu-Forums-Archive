---
title: "Help install Totem-xine"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-29
Hi just on the pilgrimage to get my dvds working :).....and ran into this little problem when trying to install Totem-xine:
XXXX@comp:~/Desktop/get dvd working$ sudo dpkg -i totem*
Password:
tar: ./shlibs: time stamp 2006-05-25 00:44:21 is 43747203 s in the future
tar: ./postinst: time stamp 2006-05-25 00:44:22 is 43747204 s in the future
tar: ./prerm: time stamp 2006-05-25 00:44:22 is 43747204 s in the future
tar: ./postrm: time stamp 2006-05-25 00:44:22 is 43747204 s in the future
tar: ./md5sums: time stamp 2006-05-25 00:44:25 is 43747207 s in the future
tar: ./control: time stamp 2006-05-25 00:44:23 is 43747205 s in the future
tar: .: time stamp 2006-05-25 00:44:25 is 43747207 s in the future
dpkg: regarding totem-xine_1.4.1-0ubuntu4_i386.deb containing totem-xine:
 totem-xine conflicts with totem-gstreamer
  totem-gstreamer (version 1.4.3-0ubuntu1) is installed.
dpkg: error processing totem-xine_1.4.1-0ubuntu4_i386.deb (--install):
 conflicting packages - not installing totem-xine
Errors were encountered while processing:
 totem-xine_1.4.1-0ubuntu4_i386.deb

I also encountered some problem with some of my other software installs but instead of making one big post I thought of tackling one at a time :) thanks guys

---

### Post by ThrobbingBrain66 on 2006-12-29
I think you may be making this harder than necessary. :)

In a terminal type
```
sudo apt-get install totem-xine
```

---

### Post by nite owl on 2006-12-29
Thanks i typed the command *sudo apt-get install totem-xine* in the directory that I have the .deb package saved and it gave me E:Couldnt find package totem etc..

Oh and about the first few lines [I]tar: ./shlibs: time stamp 2006-05-25 00:44:21 is 43747203 s in the future
[/I] I was able to fix it( I set my computers clock to the correct time) :)

---

### Post by ThrobbingBrain66 on 2006-12-29
I'm sorry, I wasn't as clear as I should have been.  You don't need that package you downloaded.  totem-xine is available in the repositories.  All you have to do is fire up a terminal and type the command from my first post.

You may have to enable some extra repositories too.  Go to system>administration>software sources.  Then tick the universe checkbox if it's not already ticked

---

### Post by nite owl on 2006-12-29
Thanks 'ThrobbingBrain' however since I am new to Linux this pilgrimage of mine also includes a functioning internet which I havent succeeded in yet! So could anyone have a possible solution for me in reguards to the E:Couldnt find package??? or help in my original problem with the *dpkg* command????

---

### Post by ThrobbingBrain66 on 2006-12-29
I see the problem now, my apologies.  First, you'll have to uninstall totem-gstreamer as the two packages confict.
```
sudo apt-get remove totem-gstreamer
```
Then ```
sudo dpkg -i totem*
``` will work without a hitch,

---

