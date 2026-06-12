---
title: "Very new-trouble opening down loads"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by DougieFresh4U on 2006-08-26
[FONT="Comic Sans MS"][/FONT]Hi every one!! I have finally got ubuntu downloaded & I am trying to bring my music onto the system using limewire to download songs. I dowload but am not able to extract/opem the limewire download. I am new to all this zipped files. I am using IBM & online using Ether net. Can some one please guide me??](*,)

---

### Post by Tomosaur on 2006-08-26
It basically depends on what format the file is in:

If they are in .tar.gz format, you use:
```

tar -zxvf myfile.tar.gz

```

If they're in .zip format, you use:
```

unzip myfile.zip

```

And if they're in .tar.bz2:
```

tar -xvf myfile.tar.bz2

```

to name but a few formats. Since you're new to Ubuntu, you should probably take a little time to learn about the terminal (or command-line, as many people call it). Once you get used to it it's a lot faster. Many compressed files you can just double click on and a program will load which will allow you to decompress the files, but it doesn't work on all compressed formats.

That being said, you can use Frostwire, which is a free alternative to Limewire and is basically exactly the same.

---

