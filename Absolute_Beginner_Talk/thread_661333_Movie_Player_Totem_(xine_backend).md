---
title: "Movie Player Totem (xine backend)"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by machosos on 2008-01-07
I installed Movie Player Totem (xine backend) from add/remove programs.  I now inserted a DVD and it does not work.  I get the following:

Totem could not play 'dvd:/'.
There is no plugin to handle this movie.

How do I know what plugins i need to install?

---

### Post by yourpalal on 2008-01-07
Hello! this is actually a suprisingly easy problem to fix the codecs are available through a third party repository, medibuntu, this codec is not included due to legal issues, just follow the instructions at this site and they will be spinnin in NO TIME!

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

hooray!

---

### Post by RomeReactor on 2008-01-07
Hi. You'll also need the following packages (in case you don't have them):
```
sudo apt-get install libxine1-gnome libxine1-ffmpeg
```

---

### Post by machosos on 2008-01-07
it worked for the first 15 minutes of one movie and i had to turn it off...and another movie it stopped after like 3 minutes...i will try a full movie this weekend or something and let you all know....but thank you for all of your help so far!!!

---

### Post by RomeReactor on 2008-01-07
Maybe you don't have the necessary libraries;  [Try this]("http://ubuntuforums.org/showpost.php?p=4093602&postcount=15").

---

