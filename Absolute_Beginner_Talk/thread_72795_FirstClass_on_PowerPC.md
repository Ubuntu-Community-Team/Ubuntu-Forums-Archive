---
title: "FirstClass on PowerPC"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by squirk on 2005-10-07
Hi All, I'm fairly new to this, but I'm making my way around.  I've gotten FirstClass Client 8.043 installed (including in the Applications menu), but it won't fully launch.  I get "Starting Firstclass" it hangs for a second and then nothing.  I installed libqt-mt.so and lib.so.6 was installed, which it requires.

I assume I have the current Linux Kernal and X11 installed, the other two items it mentions as necessary.  I know this is a bit of a slightly obscure mail app beta version on a beta release of an OS, but any help would be appreciated.  Thanks.

---

### Post by aysiu on 2005-10-07
By what method did you install FirstClass (was it a .deb, .tar.gz, an .rpm)?

---

### Post by squirk on 2005-10-07
it was a .tar.gz 

in the terminal I did "tar xvfj fcc-8.043..." etc. in the / directory

---

### Post by Ampersand on 2005-10-07
Try running it from a terminal to see whether it provides any error messages.

---

### Post by squirk on 2005-10-07
Funny you should say that, I was just doing that.  I did get an error:

# /fcc/opt/firstclass/fcc
/fcc/opt/firstclass/fcc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


So I tried "creating symbolic links to make the libraries appear in the old folder" (I found that suggestion on a search):

ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
ln -s /usr/local/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1

Although, I don't have libstdc++.so.5 I have libstdc++.so.6.05.  After I noticed that, I did links for that as well, still nothing.

---

### Post by squirk on 2005-10-24
Anybody?  I'm still having the same issue.  Actually I installed the final 5.10 and FC doesn;t show up in the internet menu, but I got the same issue when I try and launch it from the terminal.  I did not make the links this time.  HELP!  Thanks, SQ

---

