---
title: "FFMPEG + x264"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-12-05
Ubuntu 6.06


What repositories do I need to compile ffmpeg with x264?
The normal universe/multiverse don't work.

---

### Post by pay on 2006-12-05
You might need to compile it yourself```
sudo aptitude install build-essential checkinstall subversion
svn co svn://svn.videolan.org/x264/trunk x264
cd x264*
./configure
make
sudo checkinstall make install
sudo dpkg -i x264*.deb
```That's x264 compilled now you need ffmpeg```
cd
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg*
./configure
make
sudo checkinstall make install
sudo dpkg -i ffmpeg*.deb
```

---

### Post by My-dial-up on 2006-12-06
You know, I've spent 10 days trying to work out how to compile x264 along with all the permutations in ffmpeg, and along comes this Pay chap, and in a few lines he explains it all.

Amazing.

Many many thanks.

---

### Post by jocheem67 on 2006-12-07
I've been eager to start encoding with x264. Tried mencoder but although not too difficult, the A/V was terribly out of sync.

Ffmpeg is an alternative but reading the howto's and manpages, brrrr.... way too complicated for me ( still..).

Now I compiled avidemux myself, not too hard, with mp4/faac/x264. I'm just waiting for my first dvd to finish encoding.

You know, that combo is the future and it would be nice if encoding in linux would mature rapidly.....

---

### Post by Kwis on 2008-05-20
Videolan doesnt use SVN any more, they use git, so this is how to do it:

```
sudo apt-get install git-core
git clone git://git.videolan.org/x264.git
cd x264/
./configure
make
sudo checkinstall make install
sudo dpkg -i ffmpeg*.deb
```

---

