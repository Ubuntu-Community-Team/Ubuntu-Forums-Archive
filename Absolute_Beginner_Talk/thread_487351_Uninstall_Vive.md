---
title: "Uninstall Vive"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Cereus on 2007-06-29
Hello,

I am treating the Ubuntu thing as a learning experience and I'm kinda stuck right now.
I am running version 7.04

I am trying to install Vive. I found the vive-2.0.0-beta1.tar.gz package, decompressed it and followed the install instructions.

I would like to get dvd support with this package but when running ./configure it looks for libdvdcss and I have libdvdcss2. Can I install libdvdcss package (it isn't in the package manager)?

When I tried to ./configure this is the error:

```

checking for dvdcss_open in -ldvdcss... no
configure: error: libdvdcss is not installed. If you would not like to use libdvdcss or DVD functionality please use ./configure with --disable-dvd.
```

Just for the educational experience I installed vive like this:
./configure --disable-dvd
make
sudo make install clean

And sure enough, Vive installed and it didn't have dvd support.

I would like to learn how to go back and undo this stuff. How do I get rid of Vive (it doesn't show up in the package manager)? How could I do things differently so it would show up in package manager? How can I now get dvd support for Vive? How can I make sure after I install a package that I've cleaned things up? What stuff gets created on my system when I run a ./configure and where does it go and what do I do when I don't need it anymore?

Just another note:
I have libdvdread3 (not 4)

Any suggestions would be greatly appreciated.

Thanks,
Cereus

---

### Post by jfinkels on 2007-06-29
> **Cereus said:**
> Hello,

I am treating the Ubuntu thing as a learning experience and I'm kinda stuck right now.
I am running version 7.04

I am trying to install Vive. I found the vive-2.0.0-beta1.tar.gz package, decompressed it and followed the install instructions.

I would like to get dvd support with this package but when running ./configure it looks for libdvdcss and I have libdvdcss2. Can I install libdvdcss package (it isn't in the package manager)?

When I tried to ./configure this is the error:

```

checking for dvdcss_open in -ldvdcss... no
configure: error: libdvdcss is not installed. If you would not like to use libdvdcss or DVD functionality please use ./configure with --disable-dvd.
```

Just for the educational experience I installed vive like this:
./configure --disable-dvd
make
sudo make install clean

And sure enough, Vive installed and it didn't have dvd support.

I would like to learn how to go back and undo this stuff. How do I get rid of Vive (it doesn't show up in the package manager)? How could I do things differently so it would show up in package manager? How can I now get dvd support for Vive? How can I make sure after I install a package that I've cleaned things up? What stuff gets created on my system when I run a ./configure and where does it go and what do I do when I don't need it anymore?

Just another note:
I have libdvdread3 (not 4)

Any suggestions would be greatly appreciated.

Thanks,
Cereus

First, see the link in my signature about "Installing software", just for reference.

Second, sometimes, the developers put in a rule for "uninstall" in the Makefile for the program, so you can navigate to the directory in which you installed vive, then try the following:```
sudo make uninstall
```

Third, take a look at the program 'checkinstall'--it will make a .deb file that allows foreasy removal and resinstallation of packages that you compile yourself. To get checkinstall, type the following in the terminal:```
sudo aptitude install checkinstall
```

Fourth, when the configure script suggests libdvdcss, it probably means libdvdcss2. For info on how to install libdvdcss2, see the link in my signature about "Restricted Formats".

---

### Post by Cereus on 2007-07-05
Thanks for the tips.

The uninstall of Vive was successful following your suggestions.

Then I went and uninstalled libdvdcss2. I tried to reinstall it but it wouldn't work until I installed the Medibuntu repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then I was able to add libdvdcss2 and libdvdcss2-dev.

The next problem then I am currently working on is running ./configure returns this error:

```
configure: error: libdvdread development files are not install but are required to compile.

```

However, I have both libdvdread3 and libdvdread-dev both installed so I don't know whats going on.

---

### Post by Cereus on 2007-07-05
So the ./configure now works. I went and installed all the -dev packages for whatever was already installed and related to libdvd (i.e. libdvdnav-dev and libdvdplay0-dev)

I also installed checkinstall so my next step was to try:
sudo checkinstall.

And it worked. Hmmm, it didn't work last night. Maybe I had synaptic open when it was trying ti install the debian package which is where it hung last night.

So a question again about unintalling. I have to move to the directory where vive is installed - that would be usr/bin/ ???. I see other programs that I have installed but not vive. I guess my next task is to learn how to find where programs have been installed.

Thanks,
cereus

---

### Post by Cereus on 2007-07-08
So for more education and maybe if I did something blindingly stupid someone can point that out and give me hints for the future.

I had installed Vive and it was able to read DVD's but wasn't able to encode anything. It appeared that the converter Vive was using was ffmpeg and that wasn't working.

Since I am using feisty fawn and I enabled the mediauniverse (or something like that), the ffmpeg that I installed was supposed to have the aac codec ability. However, when I tried to run from the command line I would get errors such as:
```

ffmpeg: error while loading shared libraries: libavcodec.so.51: cannot open shared object file: No such file or directory
```

So I searched around in forums to see what I could find and found out something about symbolic links.

The idea is ffmpeg is looking for a library file? called libavcodec.so.51 but in directory /usr/lib the file is actually called libavcodec.so.0d.51.11.0. So I had to create a link with name libavcodec.so.51 to point to libavcodec.so.0d.51.11.0. The code was the link command "ln existing-file new-link" and I prefaced it with sudo. Then I would try and run ffmpeg from command line again using:

```
ffmpeg -i inputfile.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 16:9 outputfile.mov
```

I would get another error about error while loading shared libraries so I would look at what library was missing, look in /usr/lib to see the closest name and create the link. I did that a few times and then one time it just started encoding the video.

I wrote this post so I wouldn't forget what I was doing and so others might follow and I'll write an update if the video actually works.

**Update**: Video worked, I even loaded it onto my ipod and it played. The length of the show didn't transfer so I had to do that manually. I looked up the length of time in the properties of the file and then entered that length in gtkpod properties for the file (minute:second.000)

---

