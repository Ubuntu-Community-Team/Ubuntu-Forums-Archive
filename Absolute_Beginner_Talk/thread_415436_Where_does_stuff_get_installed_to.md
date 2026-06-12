---
title: "Where does stuff get installed to?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by swey on 2007-04-20
One thing I prefer about Windows is you can find things easily. I've just installed Thunderbird and want to open some backed up mail from my old PC but I can't find the folder it's been installed into - even search can't find it.

Mozbackup doesn't work on Linux does it?

---

### Post by LaRoza on 2007-04-20
To find something type:

whereis programname

Programs are usually installed in /usr/bin
or any directory named bin, or sbin, which requires you to be root.

---

### Post by swey on 2007-04-20
I typed whereis thunderbird and it just said "thunderbird" so not good. It's not in usr bin or sbin or bin as far as I can see unless its hidden - don't know how to be root and look. Surely someone knows where Thunderbird stores its mail? I just want to put my backed up mail into that folder.

---

### Post by markl187ld on 2007-04-20
Try looking for  a hidden folder in your home directory.

---

### Post by band-aid on 2007-04-20
This is one of my biggest complaints with linux in general. The way I understand it is

*anything*/bin is usually where binary programs are stored.
your documents and things are stored in /home
your personal config files are usually stored in hidden (starts with .) folders in your /home
global configs for things like X11 are stored in /etc
your mounted things are in /media
dynamic libraries (.so) are stored in /lib
I'm not entirely sure what you would call the stuff in /proc but I think it has something to do with holding system info
system stuff is stored in /sys (like kernel)
I'm not sure how you would describe /usr
/var holds logs as stuff

as always I reserve the right to be completely wrong in any of the above areas.

---

### Post by ego093 on 2007-04-20
Swey - Go to "Places" -> "Home Folder".  When that window opens up, type CTR-H to show hidden folders - the ones that start with a period.  Find ".mozilla" and you'll have a Thunderbird folder in there that holds everything related  to the mail client.

---

### Post by mech7 on 2007-04-20
Yeah i hate this about linux too.. every app seems to install at a different place :confused:

---

### Post by Fidelio on 2007-04-20
Is there a good guide to this? I knew where to look for things in windows, but now, apart from all the things band-aid mentioned, you've myriad subdirectories called locale and local and stuff. And all the programs you need to install seem to put things all over them.
Can anyone point me to somwhere that explains this structure? I think it would greatly help me get my head round linux.

One thing that's great, actually, is that all your personal stuff, emails, bookmarks etc ends up in the home folder. That's so much handier than Windows.

---

### Post by vanadium on 2007-04-20
I also still do not see clear in the GNU/Linux way of organizing files. It is mainly designed to be very easy navigable using the command prompt.

Obviously, the better you will get to know the system, the better you'll find your way.

---

### Post by swey on 2007-04-20
> **ego093 said:**
> Swey - Go to "Places" -> "Home Folder".  When that window opens up, type CTR-H to show hidden folders - the ones that start with a period.  Find ".mozilla" and you'll have a Thunderbird folder in there that holds everything related  to the mail client.

Thanks that did it - wish it was easier to navigate though.

---

