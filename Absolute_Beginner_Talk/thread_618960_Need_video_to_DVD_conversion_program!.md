---
title: "Need video to DVD conversion program!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by hennyyu on 2007-11-21
Hi guys,
I have some videos of my college’s functions that I want to convert into DVD format for watching it on my big TV screen. I want to share it into my all friends. I am looking for a good software program that can convert my videos files to DVD format. Can anyone recommend me any good program?
Thanks!

---

### Post by mouseboyx on 2007-11-21
A program called devede works nicely it creates an iso image that you can burn to a dvd that works perfectly.

Before you install it you might need to install ffmpeg:
```

sudo apt-get install ffmpeg


``` Install DeVeDe:```

sudo apt-get install devede

```

---

### Post by gigaferz on 2007-11-21
try DeVeDe.

it converts video files to mpeg ,then to an iso or dvd file structure,

I remember at the begining i could not  do it, but i installed a diferent version form getdeb

---

### Post by MrFSL on 2007-11-21
Just to be different:

```

sudo apt-get install ffmpeg

ffmpeg -i FileToConvert.avi -target dvd OutputFile.vob

```

Then you can burn it to disk using the  DVD-Video section in NeroLinux.

[http://www.nero.com/eng/downloads-linux3-trial.php](http://www.nero.com/eng/downloads-linux3-trial.php)

---

