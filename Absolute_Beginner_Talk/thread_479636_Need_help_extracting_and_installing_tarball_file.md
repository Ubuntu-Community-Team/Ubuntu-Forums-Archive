---
title: "Need help extracting and installing tarball file"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by acadiansteph on 2007-06-20
I downloaded a tar.gz file (divx611-20060201-gcc4.0.1.tar.gz) on to my Desktop. It is Divx converter for Linux. This is the website URL:  [http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)  . Does anyone know the commands (shell sripts) to install this program? I tried to do it with no luck.... I wonder, is this just a codec or a complete program? Alas, I do not know the code to execute this one...

---

### Post by dstew on 2007-06-20
Once you download the file, move it to your home directory. Extract the archive by double-clicking it. It should create a folder of the same name. Move into the folder. Open a terminal window. Enter the command```
sudo ./install.sh
```This archive appears to be only a codec.

---

### Post by Alex&amp;Linux on 2007-06-20
Heyo

Im a little green in that area, but this is a great article I plan on using to learn, you could practice on something like this.
Regarding the codecs, there are a couple of "gstreamer" codec packs that do EVERYTHING Ive ever needed.
They are in the repo's (make sure you have universe/multiverse enabled in software sources)

Use synaptic...synaptic is your friend!

[http://mandrivausers.org/index.php?showtopic=10615](http://mandrivausers.org/index.php?showtopic=10615)

---

