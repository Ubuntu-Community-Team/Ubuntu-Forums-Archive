---
title: "TIP: How to download Youtube movies!"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-11-24
Because of the annoying synchronizing problem with Flash 7 for Linux, and Flash 9 insisting on not working, i started to think: Those movies have to go to some temp folder or something.

 Then i started doing some research. Turns out i didn't find what the folder is, but i stumbled on a program developed by someone who had the same problem/idea i had: DOWNTUBE!

 The only problem is the program and the page are in portuguese so i decided i should post the link and the instructions here

[http://www.downtube.kit.net/index2.htm]("http://www.downtube.kit.net/index2.htm")

actually i think this is the only thing u need to know. The Linux version it easy to find out (it's the one that Says LINUX and has a .tar.gz extension) and the 2 commands are there to. 

Note that this is a console program, not a GUI one. 

Then all u have to do is type 

```


downtube [url]


```

and that's it!

But now...this will save your video in the downtube folder, but with a .flv extension. Anywayz, this is Linux, so u can stop with the "Oh no! i'll have to install a 52mb program that converts .flv to .mpeg!! i'll just stick to downloading the file everytime i wanna watch it!!"

run this:
```

ffmpeg -i [name].flv -ab 56 -ar 22050 -b 500 -s 320x240 [name].mpg

```

where u replace [name] with....well...the name u want =\

If u have any doubts, or if i wasn't clear in some point, don't hesitate to tell me :) 

IMPORTANT NOTE: this is not supposed to download your bands favorite videos. What u do with this program is your responsability. There are a lot of legal and funny/entertaining/whatever videos on youtube that u can download. I don't like to be boring by saying this, but those guys did a good job, and we shouldn't ruin it.

---

### Post by paul6 on 2006-11-24
There is also a Firefox extension called [VideoDownloader]("http://javimoya.com/blog/youtube_en.php") that has a similar effect.

---

### Post by raul_ on 2006-11-24
They're both pretty straightforward. I guess that after installing downtube it's very easy to just type 2 commands. :) and many people just like to do things in the console (like me) so it's really just another option :)

---

### Post by rlozano on 2006-11-24
> **raul_ said:**
> They're both pretty straightforward. I guess that after installing downtube it's very easy to just type 2 commands. :) and many people just like to do things in the console (like me) so it's really just another option :)

good post raul. really appreciated. thanks.

---

### Post by argie on 2006-11-25
Yay, I like this. Especially since I've changed to Konqueror now instead of Firefox and haven't looked for an equivalent to VideoDownloader.

Also, mplayer and vlc can both play flv, so you won't really need to convert :)

---

### Post by revertex on 2007-03-15
There are some debian packages in dreamlinux repo, it works fine with all debian based distros.

here the debian package (CLI only)

[http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-2.1.deb](http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-2.1.deb)

Then a GUI interface (optional) 

english version:
[http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-gui-en-1.0_i386.deb](http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-gui-en-1.0_i386.deb)

portuguese version:
[http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-gui-ptbr-1.0_i386.deb](http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-gui-ptbr-1.0_i386.deb)

Thanks to point me to downtube linux site, i haven't found this, only the windoze one.

---

### Post by jbayone on 2007-03-15
There's also a site for doing this - keepvid.com

---

### Post by zazen666 on 2007-03-31
I dowloaded a video from you tube using one of the above websites but then tried to coverte from FLV to MPEG (so I can watch on my creastive zen)via the code posted and I get this error:

bash: ffmpeg: command not found

any ideas?

---

### Post by revertex on 2007-03-31
> **zazen666 said:**
> I dowloaded a video from you tube using one of the above websites but then tried to coverte from FLV to MPEG (so I can watch on my creastive zen)via the code posted and I get this error:

bash: ffmpeg: command not found

any ideas?

```
sudo apt-get install ffmpeg
```

i suggest you install a package called "command-not-found" it will suggest you to install the correct package when it happens.

```
sudo apt-get install command-not-found
```

---

### Post by Keys18 on 2007-04-01
I have found out one solution to solve all this. Use ZillaTube - from [http://www.zillatube.com](http://www.zillatube.com)

Just one software to use - to grab youtube video, convert them easily (with good quality video options), etc... cool!

Hope this helps  :KS

---

### Post by revertex on 2007-04-01
> **Keys18 said:**
> I have found out one solution to solve all this. Use ZillaTube - from [http://www.zillatube.com](http://www.zillatube.com)

Just one software to use - to grab youtube video, convert them easily (with good quality video options), etc... cool!

Hope this helps  :KS

come on dude, it's a commercial application for windows.
are you zillatube developer advertising your product here?

---

### Post by izizzle on 2007-04-22
.......an alternative............

Go to [http://kej.tw/flvretriever/](http://kej.tw/flvretriever/) , input your video's URL, download it, then play it with XGine or Mplayer.

hope it helps, Imran

---

