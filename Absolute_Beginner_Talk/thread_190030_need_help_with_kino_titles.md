---
title: "need help with kino titles"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by MattCarp on 2006-06-05
Is anyone using Kino (0.8.0)?

I'm trying to get titles.  The ImageMagick Titler seems confusing and slow.

I'd like to use dvtitler (0.2.0), but it's only availble as source (I don't have all the build tools installed).

kino-dvtitler is in the repository - but - there seems to be some confusion that it's already been added to the kino package.  In fact, the kino-dvtitler package is broken - if you select kino-dvtitler it will remove the kino and kinoplus packages and then not actually install because it's dependent on kino!

Has anyone gotten dvtitler up?  If you've compiled the binaries, can I get them from you?

---

### Post by MattCarp on 2006-06-05
[QUOTE=MattCarp]
Has anyone gotten dvtitler up?  If you've compiled the binaries, can I get them from you?[/QUOTE]

Ok- I squeal for help a little too early.  I was able to find the compiled package here:

[http://packages.ubuntulinux.org/dapper/graphics/kino-dvtitler](http://packages.ubuntulinux.org/dapper/graphics/kino-dvtitler)

Scrolling down to the Download section on the page, I was able to download the binary Debian/Ubuntu Dapper package by clicking on i386.

I was not able to install it from the gnome GUI Package installer, due to the conflict with the kino package.  However, I was able to go to the terminal, navigate to the directory where my kino-dvtitler package was downloaded, and issued this command:

sudo dpkg --force-conflicts -i kino-dvtitler_0.2.0-1.1_i386.deb

I think it worked.  At least now in the FX tab of kino I see a video filter in the drop down list of "Titler", which, I don't think was there before.

Can someone confirm that Titler doesn't appear in the video filter drop down when you only have the kino (0.8.0) package installed from the ubuntu repository?

---

### Post by jon_gunnar on 2006-06-07
[QUOTE=MattCarp]Ok- I squeal for help a little too early.  I was able to find the compiled package here:

[http://packages.ubuntulinux.org/dapper/graphics/kino-dvtitler](http://packages.ubuntulinux.org/dapper/graphics/kino-dvtitler)

Scrolling down to the Download section on the page, I was able to download the binary Debian/Ubuntu Dapper package by clicking on i386.

I was not able to install it from the gnome GUI Package installer, due to the conflict with the kino package.  However, I was able to go to the terminal, navigate to the directory where my kino-dvtitler package was downloaded, and issued this command:

sudo dpkg --force-conflicts -i kino-dvtitler_0.2.0-1.1_i386.deb

I think it worked.  At least now in the FX tab of kino I see a video filter in the drop down list of "Titler", which, I don't think was there before.

Can someone confirm that Titler doesn't appear in the video filter drop down when you only have the kino (0.8.0) package installed from the ubuntu repository?[/QUOTE]

No,the kino-dvtitler package is provided by kino itself now.I got it working nicely here om my amd64 system.

---

