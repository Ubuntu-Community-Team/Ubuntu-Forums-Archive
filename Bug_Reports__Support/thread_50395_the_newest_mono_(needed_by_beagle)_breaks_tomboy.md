---
title: "the newest mono (needed by beagle) breaks tomboy"
date: 2005-07-20
forum: Bug Reports / Support
---

### Post by kiddo on 2005-07-20
I might be wrong on this one, if so please delete this thread, but you would need a newer tomboy to work with mono 1.1.x. (take a look at [my post here]("http://ubuntuforums.org/showthread.php?p=263211#post263211") for details).

I hope this can get sorted out, thanks for bringing me the joy of desktop searching :)

---

### Post by kiddo on 2005-07-25
*shameless bump* I'm not the only one who has this problem I believe x_x? isn't there a bugzilla around for the backports?

---

### Post by jdong on 2005-07-26
Perhaps we need a newer version?


I'll backport the current Breezy build. Enable Backports Staging and see if this new build fixes anything.

---

### Post by Velvet Elvis on 2005-07-26
Here's what I get when I try to run it from an x-term:

```
joe@zara:~$ tomboy

** (/usr/lib/tomboy/Tomboy.exe:11463): WARNING **: The following assembly refere nced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=4)
     Version:    0.23.4.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MO NO_PATH environment variable, or in the location of the executing assembly (/usr /lib/tomboy).


** (/usr/lib/tomboy/Tomboy.exe:11463): WARNING **: The class DBus.Connection cou ld not be loaded, used in /usr/lib/tomboy/Tomboy.exe (token 0x0100000a)
/home/joe/.gtkrc-2.0:2: Unable to find include file: "(null)"

** (Tomboy:11463): WARNING **: The class DBus.Service could not be loaded, used in /usr/lib/tomboy/Tomboy.exe (token 0x0100000c)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in <0x00045> Tomboy.TomboyTrayIcon:.ctor (Tomboy.NoteManager manager)
in <0x00022> Tomboy.TomboyTrayIcon:.ctor ()
in <0x00019> Tomboy.Tomboy:StartTrayIcon ()
in <0x000d8> Tomboy.Tomboy:Main (System.String[] args)
joe@zara:~$
```

---

### Post by Velvet Elvis on 2005-07-26
Ok.  Got it to work.

I upgraded to the packages at:

[http://www.gnome.org/~davidsf/ubuntu/hoary/mono/](http://www.gnome.org/~davidsf/ubuntu/hoary/mono/)

I had to backport libdbus-cil_0.23.4-3_i386.deb myself using apt-get source and dpkg-build. 

Seems to work ok.

Now let's see if I killed Muine in the process.

It works as well.  Rawk.

---

### Post by davidsf on 2005-07-27
[QUOTE=Velvet Elvis]

I had to backport libdbus-cil_0.23.4-3_i386.deb myself using apt-get source and dpkg-build. 

[/QUOTE]

Oopps, I forgot to upload libdbus-cil, sorry. I will upload later to my site.

---

### Post by rwabel on 2005-07-27
[QUOTE=davidsf]Oopps, I forgot to upload libdbus-cil, sorry. I will upload later to my site.[/QUOTE]
 I had the same error message on my hoary with the bp of tomboy. Your bp of libdbus-cil depends on mono 1.1.8, but the bp version is 1.1.7
What's the deal with your bp stuff? I mean you have version 1.1.8, why aren't the one from the bp team also 1.1.8?

---

### Post by rwabel on 2005-07-27
[QUOTE=rwabel]I had the same error message on my hoary with the bp of tomboy. Your bp of libdbus-cil depends on mono 1.1.8, but the bp version is 1.1.7
What's the deal with your bp stuff? I mean you have version 1.1.8, why aren't the one from the bp team also 1.1.8?[/QUOTE]
 that's strange, I've reinstalled libdbus-cil from the bp and now there is no error message. Sometimes you need reinstall to make it work :-)

---

