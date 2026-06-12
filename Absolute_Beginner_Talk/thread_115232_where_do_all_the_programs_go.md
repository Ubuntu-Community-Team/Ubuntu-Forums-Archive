---
title: "where do all the programs go?"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by kencubilo on 2006-01-10
Forgive me for this really stupid question but the last time I used Linux it didn't have a GUI. When ever I download new software and run the packager to install it, I never can find where it ended up. Is there a way to run the install so the new software ends up in the applications menu?

---

### Post by Gustav on 2006-01-10
Most software should automaticly end up in the applications menu.

The program files are usually installed to /usr/share/ and the bin file to start the programs with usually ends up or gets a symlink in /usr/bin/

---

### Post by winlux on 2006-01-10
One way of having more control of where your programs go and still have it quite easy to remove all the files installed is by using a program called check install. You downloads and compile the source and then do ./configure --prefix=/directory_for_install then instead of running make install you run checkinstall make install and this will create a package file based on your system, then install that and you got your software where you want and still make it easy to manage in synaptic. Although.... you would need to make appropriate symbolic links into directories in your path to execute them by just typing the command or add the installed dir to your path. I prefer just making symbolic links as this does not clutter up your path

---

### Post by Qrk on 2006-01-10
You can right click an installed package in synaptic to see all of the files that it installs... and in which directory they are installed in.

But at the heart of it, Linux uses a different directory system than windows. Windows lumps things together based on the program; linux lumps things together based on the kind of file it is. So, the bottom line is that Linux doesn't have a "Program Files" folder. 

Once you get used to the idea it starts to make sense.

---

### Post by blair on 2006-01-10
there is also a useful command called "whereis". You can do a man page on this or search the web for Linux man pages sites. Whereis returns the path to the specified command. For example "whereis ping" returns:

user@PC:~$ whereis ping
ping: /bin/ping /usr/share/man/man8/ping.8.gz

thus, the ping coammand is in the /bin directory. Normally the executable name is the package name. So if you download the ping package, the executable is likely called ping, and the whereis command will help you find where it is hiding.

---

