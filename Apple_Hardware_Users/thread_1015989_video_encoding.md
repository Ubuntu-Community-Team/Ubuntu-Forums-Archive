---
title: "video encoding"
date: 2008-12-19
forum: Apple Hardware Users
---

### Post by ruthc on 2008-12-19
Hello,
I'm using Ubuntu 8.4 on a Mac ppc.
I'm looking for a video encoder (I used to use FFmpegx when I was a mac os x user) to convert from 3gp (or mov) to flv

The solution suggested [here]("http://ubuntuforums.org/archive/index.php/t-481595.html") looked hopeful (using ffmpeg, winff from [http://www.biggmatt.com/winff](http://www.biggmatt.com/winff) and Modile media converter from [http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm))
however neither winff nor mobileMediaConvert like the architecture of my computer. I presume that this is because they are made for Intel rather than ppc (guessing). 

Please can anyone advise?

---

### Post by FakeOutdoorsman on 2008-12-19
You can try ffmpeg itself:
```
ffmpeg -i input.3gp -sameq output.flv
```
The sameq options will automatically adjust the output file bitrate to attempt to match the quality of the input file.

---

### Post by ruthc on 2008-12-22
Ok, thanks for the advice:) I'll give it a go.
Now I realise that I was probably using QT pro to do simple video editing before (editing timeline) I'm going to need an ubuntu friendly replacement for that too.
Any suggestions?

cheers

---

### Post by mkvnmtr on 2008-12-22
I believe you have to have the Medibuntu repository enabled to download that encoder. I have been doing an install today and just enabled Medibuntu and foound it to install.

---

