---
title: "How do you view terminal output?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by DJMattB241 on 2007-11-01
I've been trying to get the Banshee music player to sync my ipod, but it keeps hanging on "pre-processing tracks"... I did a search and came up with this thread:
[http://ubuntuforums.org/showthread.php?t=174290](http://ubuntuforums.org/showthread.php?t=174290)

Where the solution suggested was to "check the terminal output when you're doing it" and see if it gives any "file not found" errors. I don't know how to do this. Obviously, just opening the terminal does nothing outside of giving you a prompt.

Help?

---

### Post by Hospadar on 2007-11-01
if you start it up from a terminal, you can probably see the output that way.  go to a command line and type "banshee" and don't close the terminal window as this will close any applications running out of it.

---

### Post by DJMattB241 on 2007-11-01
Thanks, that was pretty straightforward... it brought me straight to another deadend though... Banshee gave this message: Could not find file "/#0%!.mp3"
As far as I know, I don't have a file named that anyways...

---

### Post by petteriIII on 2007-11-01
> **DJMattB241 said:**
> Thanks, that was pretty straightforward... it brought me straight to another deadend though... Banshee gave this message: Could not find file "/#0%!.mp3"
As far as I know, I don't have a file named that anyways...


When you are in terminal command first: sudo apt-get install banshee . (Or install package banshee via synaptic)

---

### Post by earobinson on 2007-11-01
could you cut and paste more of the output

---

### Post by llamakc on 2007-11-01
> **petteriIII said:**
> When you are in terminal command first: sudo apt-get install banshee . (Or install package banshee via synaptic)

OP already installed Banshee and is having a different problem.

OP, You can delete the stuff in /home/USER/.config/banshee/ and then reload your music collection. THEN try resyncing the ipod.

---

### Post by DJMattB241 on 2007-11-02
In an attempt to please everyone at once, I cleared out the /home/ME/.config/banshee folder and reloaded the music collection, didn't add any podcasts, and tryed to do a sync.

And here's the output. First of all, when I first connect the ipod, it does this:

```

** (Banshee:5999): CRITICAL **: ipod_device_parse_serial: assertion `strlen(serial) == 11' failed
Debug: [11/1/2007 11:22:31 PM] (DAP has been added) - Banshee.Dap.Ipod.IpodDap: /org/freedesktop/Hal/devices/volume_uuid_2FB9_FAEA
```

and then gives the following message about 10 times in a row:

```
(Banshee:5999): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
```

Neither of which look very good... when I try to sync, it gives me this:

```
Unhandled Exception: System.IO.FileNotFoundException: Could not find file "/#0%!.mp3".
File name: '/#0%!.mp3'
  at System.IO.FileInfo.get_Length () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileInfo:get_Length ()
  at IPod.Track.set_Uri (System.Uri value) [0x00000] 
  at Banshee.Dap.Ipod.IpodDap.Synchronize () [0x00000] 
  at Banshee.Dap.DapDevice.Transcode () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
```

See what I mean? "/#0%!.mp3"

Weird.

---

