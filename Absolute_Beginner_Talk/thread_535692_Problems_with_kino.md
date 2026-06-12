---
title: "Problems with kino????"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by superjdf on 2007-08-26
Ok, I have to capture through sudu!! first problem!!

secound I can not save some editing I was doing with kino, it says could not save smil???

and it seems I can not save using save as....  ??  The other is I was also applying some FX's and I could not render the effects it was saying, unable to open output file???

---

### Post by Cypher on 2007-08-27
You probably need to run Kino as SUDO because your DV camera /dev files are not accessible to all users. So before starting Kino do the following
```

sudo chmod 666 /dev/raw1394
sudo chmod 666 /dev/dv1394/0

```
Now you should be abel to run Kino as a regular user and see if you still get the other errors.

---

### Post by superjdf on 2007-08-27
jared@jared-desktop:~$ sudo chmod 666 /dev/raw1394
Password:
jared@jared-desktop:~$ sudo chmod 666 /dev/dv1394/0
chmod: cannot access `/dev/dv1394/0': No such file or direct


How can I get a useful file format for my videos???
I need to be able to upload video??

I am running dapper drake

---

### Post by Amazona aestiva on 2007-08-27
Perhaps you should try Feisty with this version of Kino:
[http://www.getdeb.net/app.php?name=Kino]("http://www.getdeb.net/app.php?name=Kino")
It might run under Dapper! If not -> Feisty.

And see the link in my signature!

---

### Post by superjdf on 2007-08-27
I tried to install the codecs for kaffeine form your links and I guess I am not doind it right??

How do I do it??

---

### Post by Delkster on 2007-08-27
You can't save directly in compressed formats from Kino. Instead of saving you need to go to the export tab in the Kino main view, after which you'll probably want to open the "Other" tab to find options for several kinds of compression. Note, though, that Kino probably only exports in formats and codecs supported by ffmpeg, and due to patent issues the ffmpeg Ubuntu package has some limitations as to what formats it can encode to. MPEG-4 (ffmpeg) might work, and theora almost certainly does. The MEncoder XviD encoder might also work if you have MPlayer/MEncoder installed. You'll have to experiment a little.

The "save as" feature in Kino is for saving Kino project files. They're files describing how you have cut, combined and edited the original files, and are not usable for playing videos directly. However, as long as you have all the original and temporary DV files present and you have the SMIL file (the project file), you can return to where you left in your modifications and can continue editing. That's actually very useful, since if you only saved the result of your edits as a plain new video file, it would not contain any information about what kinds of cuts you have made, whereas the SMIL file is actually nothing but a description of what you have done and to what files.

---

### Post by superjdf on 2007-08-27
I need the necessary plugins to play media types from kino so I can then burn using dvd cd creator!! And also upload video to say youube??????

I have been having trouble with all of these things!
I am using dapper drake ubuntu 6.06!

I am starting to get the ubuntu blues!!!:confused:

---

### Post by Amazona aestiva on 2007-08-28
Win32 codecs for Kaffeine:
1. download the .tar.bz2 file
2.make a new directory  in /usr/lib/ named win32
3.copy the .dlls and the other files from the downloaded archive, to /usr/lib/win32/

---

### Post by superjdf on 2007-08-28
I dont know how to make a new directory????

I tryed doind it through file system but it says access denied???

---

### Post by Amazona aestiva on 2007-08-30
If You type:
```
gksudo nautilus
```
a window appears. You are root in it and can do anything.

---

