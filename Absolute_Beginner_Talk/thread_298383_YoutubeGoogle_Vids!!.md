---
title: "Youtube/Google Vids?!?!"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-11-12
i can stream the videos but sound does not work in firefox y is that?is therea solution?
thanks

---

### Post by ciscosurfer on 2006-11-12
You can [download the Flash 9 beta]("http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin").

---

### Post by xpod on 2006-11-12
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```

Thats what i was advised to do to get my Flash sound...
Hitting enter after each and then rebooting.

Might help.

EDIT..Mind you.that was in dapper so im not sure if thats relevant in edgy.

---

### Post by dbott67 on 2006-11-12
It works for me... have you got all the plug-ins installed (flash, audio codecs, etc.?)

Does sound work in other applications?

One things I have noticed is that if I have another audio player open (such as beep or rhythmbox), then audio does not work on Youtube or Google Video, so make sure all other audio-related apps are closed.

-Dave

---

### Post by ciscosurfer on 2006-11-12
> **xpod said:**
> ```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```Thats what i was advised to do to get my Flash sound...
Hitting enter after each and then rebooting.

Might help.

EDIT..Mind you.that was in dapper so im not sure if thats relevant in edgy.

These instructions work for Dapper, but is irrelevant in Edgy.

---

### Post by DaveBorealis on 2006-11-12
In Dapper if I have xmms running it'll kill flash sound in Firefox.  Close Firefox, close all apps using sound, then relaunch Firefox and see if that makes a difference.

Something to try....
Dave

---

### Post by xpod on 2006-11-12
I thought as much.....I forget half the time just what one im actually using at any given moment.It was`nt until i posted i realised he too was using edgy

I never had the same prob in edgy now that i recall....just dapper.
Sorry for confusion mazen.
Hope you suss it out

---

### Post by Mazen on 2006-11-12
allright thanks all,
i downloaded the flash packages but don't know how to get them to install as plug-ins for firefox!!!

---

