---
title: "The many talents of ubuntu"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by mconway0003 on 2007-03-01
Hey, does anyone know if you can take songs off your ipod with gtkpod or something else? I know you can read the songs off your ipod with gtkpod but if you drag a song from your ipod to lets say, your desktop, the name consists of random numbers and not the actual song name. It would be great if someone could help me because I have some shows that i attended on my ipod and I would like to be able to transfer them to my new ipod because I cant get the songs from the show anymore.

Thanks,
MC

---

### Post by koconnor100 on 2007-03-01
I just finished uploaded 400+ songs from my winxp machine to my ubuntu box and the file names didn't get scrambled. Ubuntu was running a proftp server . 

That suggests ipod >> winxp >> ubuntu 

On the other hand , if your ipod is really a mac ipod , then it's got a ton of copy protection to make sure nothing leaves the world of mac products , and you could be beating your head against a brick wall for a long time trying various things.

---

### Post by ubu fubar on 2007-03-01
> **mconway0003 said:**
> I know you can read the songs off your ipod with gtkpod but if you drag a song from your ipod to lets say, your desktop, the name consists of random numbers and not the actual song name.

Assuming you're sticking with iTunes, this is not a problem. When you re-import your music into your iTunes library the song metadata magically reappears.

As the metadata (id3 tags) is stored in the files, I'd guess that you could still get at it using an id3 editor like EasyTag,  or an application that reads embedded id3 tags like Banshee. Have you actually tried? I haven't done this on Linux, but it works as described with iTunes.

---

### Post by lamalex on 2007-03-01
download amarok. it has great (insert pretty much any mp3 player here) support. I've used it with ipod video, ipod mini, 1st gen ipod, and creative zen vision:m (<--pwns them all). best music app for linux imo.

---

### Post by ubu fubar on 2007-03-01
> **koconnor100 said:**
> On the other hand , if your ipod is really a mac ipod , then it's got a ton of copy protection to make sure nothing leaves the world of mac products , and you could be beating your head against a brick wall for a long time trying various things.

The only problem you'll have with a Mac formatted iPod is that the filesystem is HFS+. The way round this is to copy from the iPod onto a Mac using something like [Senuti]("http://fadingred.org/senuti/"), then transfer the resulting mp3 files as usual.

If the iPod is Win formatted it's all FAT32, so copying should be straightforward on any machine.

---

### Post by kahping on 2007-03-01
You could also use [Ex Falso]("http://www.sacredchao.net/quodlibet") to do batch renaming. It lets you use the file's metadata when renaming so you needn't rename the files one at a time.

I believe there is a package available in the Ubuntu repositories.

---

### Post by mconway0003 on 2007-03-01
> **ubu fubar said:**
> Assuming you're sticking with iTunes, this is not a problem. When you re-import your music into your iTunes library the song metadata magically reappears.

> **koconnor100 said:**
> I just finished uploaded 400+ songs from my winxp machine to my ubuntu box and the file names didn't get scrambled. Ubuntu was running a proftp server . 

That suggests ipod >> winxp >> ubuntu 

On the other hand , if your ipod is really a mac ipod , then it's got a ton of copy protection to make sure nothing leaves the world of mac products , and you could be beating your head against a brick wall for a long time trying various things.


I'm not sure what you are trying to say when you suggested that I'm "sticking with iTunes" but I do not use iTunes, I'm currently using gtkpod and the ipod i want to export songs from is windows xp formated. Also, I'v been reading about the 'export tracks to database' option that gtkpod has. Is this option legit?

Thanks

---

### Post by ubu fubar on 2007-03-01
Ok, I just dragged a song from my iPod Nano to the desktop using GTKPod, and it created a file named QJVM.m4a. The original title on the iPod was "Le Foto Proibite Di Una Signora Per Bene (Alex Attias Mustang Mix 1)".

Viewing the properties of the file on the desktop, on the "audio" tab, showed the original track name.

Dragging that file into my Banshee library imported it with the original track name, play count, rating etc.

In other words, as the id3 info is embedded in the file, any music management program that understands id3 information will import the file with metadata intact.

As an aside, my iPod is Mac formatted, so the files are AAC. Banshee converted on import into mp3.

---

### Post by William the Conquerer on 2007-03-01
when you put songs on your ipod from iTunes it renames the files and has a little database to keep track of everything so when you take them off they're named the right thing...  if I understand all this correctly.  So basically if you just have all of your music on your windows xp installation and copy it all over to an external hard drive (haha, you could actually use your ipod in disk mode if you really wanted to) and and just mount that external hard drive in ubuntu and copy over the music with the filenames intact...  Also, I think amarok might work.

---

### Post by airtonix on 2007-03-25
no network cable? better hope your sub ports are version 2.....

version 1 is 11mbps a second...which is 100k/s...ithink ( im too tired, and my head is going too.....

---

### Post by eddddd89 on 2007-04-09
What you need to do is select the music you want in gtkpod, right click it, and say 'copy tracks to filesystem'.  It will then let you choose a directory to put them in.  Unfortunately, they do not preserve their orginal file hiearchy, but at least they are named logically.

---

### Post by jfinkels on 2007-04-09
When you use iTunes on Windows or on a Mac, iTunes will rename the files that it keeps on the iPod to a string of four random uppercase letters, and put them in random folders. This is to avoiid you from looking at the files and for example copying them to your friend's computer. Most of the time, when you use your iPod as an mp3 player to listen to music, this doesn't matter at all, but when you want to copy songs, like you do, it makes the process extremely annoying. The actual song title, album title, track number, etc. are stored in metadata (which is just extra info that comes along with each mp3 file so that you can make the filename whatever you want and maintain the song title, album title, track number, etc.). That's why your songs' filenames look like gibberish.

---

