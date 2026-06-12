---
title: "libdvdcss2 installed yet still cannot play dvds"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by PatrickMay16 on 2006-10-27
I have installed libdvdcss2, yet totem-xine still gave the error message "the source seems encripted. Are you trying to play a dvd without libdvdcss2 installed?".
So I installed totem-gstreamer, and it gave me a message "could not open location; you may not have permissions to open this file.".

So how do I get dvds to play? I've installed libdvdcss2, yet this happens. I'm absolutely lost here.

---

### Post by PatrickMay16 on 2006-10-28
Come on. Somebody must know what the problem is.

---

### Post by dmizer on 2006-10-28
try a different dvd.  libdvdcss has a hard time with some decryption.  it's not perfect.

---

### Post by JayTee on 2006-10-28
Are you running Dapper or Edgy? I've not had any problems with playing DVD's on Dapper with Totem. I've got Totem and the Totem-xine installed with the GStreamer Win32 codecs. I used Automatix to install the codecs and had to add Totem-xine to get everything to play. Here's my installed versions.
libdvdcss2 1.2.9-1plf4 
gstreamer0.10-pitfdll 0.9.1.1+cvs200603 Gstreamer plugin for using MS Windows binary codecs.
libtotem-plparser1 1.4.3-0ubuntu1
totem      1.4.3-0ubuntu1
totem-xine 1.4.3-0ubuntu1
Hope this may shed some light on your problem.
I did have one DVD throw up the same error you had but it was halfway into the movie and the DVD had some gunk on it. I cleaned it and it played through fine the second time around.

---

### Post by dvarsam on 2006-11-06
Hello!

I _hate_ installing things I do not know what they really do...!!!

So, in my case, I don't choose the "automatix" way...

I like to have full control of my Ubuntu, and not to install other people's suggestions, no matter what...!!!

> So, instead, I installed the following:

1. libdvdcss2

2. totem-xine (it removes totem-gstreamer)

Now, all DVD movies play fine in my Totem Movie Player.

However, they do NOT play in MPlayer Movie Player.

At the same time, NONE of those 2 programs can handle/play VCDs.

Any ideas?

What package can I install that can handle VCD?

Thanks.

P.S.> In the end I will find my way out of this, its all a matter of time...

---

