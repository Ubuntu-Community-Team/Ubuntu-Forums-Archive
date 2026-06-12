---
title: "[HOWTO] Beryl on PPC edgy with svn-builded debs !"
date: 2007-01-11
forum: Apple PPC Users
---

### Post by el-sio on 2007-01-11
Please be indulgent since this is my very first howto :)

Great news for PPC users !

I spent my all afternoon (it took me so much time because of my own ignorance of ubuntu autotools...) compiling the latest beryl svn into deb packages (because the current beryl package for PPC arch do not work) using [the script provided by 3v1n0]("http://3v1n0.tuxfamily.org/xtra/makedebs.tar.gz").

AND IT WORKS !!!!

Of course there are still a few bugs (disqperance of windows decoration when maximized, videos replaced by a black screen) but it is still fun and beautyfull.

It turned without problems on my ibook G4 with ATI radeon mobility 9200!!!

I have uploaded the builded debs on my website feel free to [download them here !]("http://japansio.info/ubuntu/")
(by the way if someone thinks of a better place to put them, feel free to do so ^^ I am not familiar with the repository creation procedure...
then with a simple 

```
sudo dpkg -i *.deb
```

you install beryl and lanch it with 

```
beryl-manager
```

if you are satisfied, go in System->Preference->Session and add the following in your startup programs : 

```

beryl
emerald --replace
beryl-manager
```

Enjoy !

P.S if you want to recompile by your self, please follow[ the instructions on the following thread]("http://ubuntuforums.org/showthread.php?t=279456")

---

### Post by bonvenon on 2007-01-31
oh, thanks a lot for the debs - works just fine!

---

### Post by JackosKing on 2007-02-01
It work fine, but very slow on iBook :/

---

### Post by minig4 on 2007-02-02
Works fine for me but in blue, after a quick searching in this forum and find out that forcing xgl I got a normal desktop and no the blue one.

Im new on this, I run edgy in a mac mini

aixgl goes faster for me, is a way to fix this blueish screen?

thx and sorry if it is not a very smart question but mr google didnt help me much

excuse my broken english

edit: one more thing when I run firefox and loads a site full of pics my fan drives crazy, and sometimes when I open firefox or evolution I only see the desktop and when I try to click the app is there just maybe too transparent as much as you cant see it, ghost one :D, is this happening to anyone else?

---

