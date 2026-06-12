---
title: "Can Jahshaka be installed to Feisty?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-05-19
Or just to Dapper?  This is the file ext from the [download page]("http://www.jahshaka.org/component/option,com_docman/task,cat_view/gid,42/Itemid,49/"):   jahshaka-dapper-x86.sh


And if you can download to Feisty, can you give this noob a walk-through?

---

### Post by MyR on 2007-05-20
add the repository
system > administration > software sources > third party software > add
add: deb [http://repo.jahshaka.org/ubuntu/dapper/](http://repo.jahshaka.org/ubuntu/dapper/) binary-i386/

install from terminal
```
sudo aptitude install jahshaka
```

i haven't actually installed it, so good luck ;]

---

### Post by Killtown on 2007-05-20
> **MyR said:**
> add the repository
system > administration > software sources > third party software > add
add: deb [http://repo.jahshaka.org/ubuntu/dapper/](http://repo.jahshaka.org/ubuntu/dapper/) binary-i386/

install from terminal
```
sudo aptitude install jahshaka
```

i haven't actually installed it, so good luck ;]
After I added it, it said software not up-to-date.

---

### Post by MyR on 2007-05-20
> **Killtown said:**
> After I added it, it said software not up-to-date.

just hit reload when it asks you to update

---

### Post by Killtown on 2007-05-20
ok worked, but now says:

> WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  olib-mlt++ jahshaka openlibraries olib-mlt olib-ffmpeg 

Do you want to ignore this warning and proceed anyway?

Is that cause it's not from Ubuntu's Repos?

---

### Post by MyR on 2007-05-20
> **Killtown said:**
> Is that cause it's not from Ubuntu's Repos?

yes

---

### Post by Killtown on 2007-05-20
Finished installing it, but now icon does not show up in Application/Sound&Video.

---

### Post by MyR on 2007-05-20
can you run it from the terminal by typing jahshaka? if so, you can add an icon by system > preferences > main menu
under sound and video click new item and for command put jahshaka

---

### Post by Killtown on 2007-05-20
> **MyR said:**
> can you run it from the terminal by typing jahshaka? if so, you can add an icon by system > preferences > main menu
under sound and video click new item and for command put jahshaka
It woooooorked!   Thanks a million.  \\:D/

---

### Post by Skerit on 2007-05-28
It "wooooorked"? I haven't had *any* success at installing Jahshaka through that repository, it won't go beyond the splash screen...

---

### Post by MyR on 2007-05-28
> **Skerit said:**
> It "wooooorked"? I haven't had *any* success at installing Jahshaka through that repository, it won't go beyond the splash screen...

so it installed, but it's just not working properly?

---

### Post by gth759k on 2007-05-29
This didn't work for me. After the install, jahshaka dies at the splash screen. I've tried compiling jahshaka from source on Fiesty, but I run into errors over the openlibraries. Anyone succeded in installing Jahshaka on Fiesty fawn?

---

### Post by MyR on 2007-05-29
well, i just followed my own tut and it installed and seems to be running all right... i did get some errors on the teminal while starting it up though.
..
actually it even seems to play videos properly. which is somewhat surprising given my video card

---

### Post by gth759k on 2007-05-29
Yay!!! I got it to work, you have to do a search in the Synaptic Package Manager for libgl1-mesa and you'll find that there is a libgl1-mesa-glx and a libgl1-mesa-swx11. 
I selected to install libgl1-mesa-swx11 and it told me that some other packages would be removed (including libgl1-mesa-glx), then apply and Jahshaka works!

However, this disables direct rendering, but not 3d acceleration. I've noticed some lag when I change the Blender UI, ie. spliting and joining the layout, but everything still works and the buttons and 3d space still respond fine. Games like BilliardGL run too slow to play, but glxgears still returns about 500 fps. This fix only proves something in jahshaka is clashing with glx, but it works for now.

I was trying to get beryl working and I followed this tutorial, [http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty). After I finished getting xgl working I tried jahshaka again and it just worked, I don't know how though. Good luck.

---

### Post by Skerit on 2007-06-15
Hmm yeah, guess I don't need my **nvidia drivers!**

So, that totally didn't work ... However, even after I installed the other libmesa thing, without my drivers, it still didn't work, something else must be conflicting ... God, if only I could figure out WHAT...

Guess this is the clear result of a poorly made DEB package?

---

### Post by Fred Torssander on 2007-06-19
Hello.
I started trying out Ubuntu two or three days ago, and your discussion/description of how to install Jahshaka helped me to success at the first try.
Thank you very much!:D

---

### Post by willsomebody on 2007-06-21
your synaptic solution worked for me back when I was using 32-bit feisty, but it will not work now that I have 64-bit feisty.  When I add the jahshaka repo and refresh synaptic, jahshaka does not show up.  Also, apt-cache search jahshaka returns nothing.

---

### Post by kit89 on 2007-08-08
> It "wooooorked"? I haven't had *any* success at installing Jahshaka through that repository, it won't go beyond the splash screen...

I have the same problem. For some reason if you run "sudo jahshaka" first. It will then run normally with just "jahshaka".

Strange....

---

### Post by NULL712 on 2007-08-13
If any one is using 7.04 and still wants to use compiz/beryl don't attempt to get jahshaka working! When I got jahshaka working on my Dell Inspiron 6000 using libgl1-mesa-wx11 it messed every thing up.:( I found a different editor called open movie editor but have not been able to install it. I found it on linuxappfinders.com, the .deb file I downloaded needs some dependencies but I don't know how many. I'll get back when I find out more info.  But if you insist on using jahshaka...best to install it on 6.10 or something unless you don't want to use compiz or beryl.

---

### Post by MyR on 2007-08-13
> **NULL712 said:**
> If any one is using 7.04 and still wants to use compiz/beryl don't attempt to get jahshaka working! When I got jahshaka working on my Dell Inspiron 6000 using libgl1-mesa-wx11 it messed every thing up.:( I found a different editor called open movie editor but have not been able to install it. I found it on linuxappfinders.com, the .deb file I downloaded needs some dependencies but I don't know how many. I'll get back when I find out more info.  But if you insist on using jahshaka...best to install it on 6.10 or something unless you don't want to use compiz or beryl.

it seems to be working fine on my inspiron 6000 with ubuntu 7.04 and beryl 0.2.1 
however i don't use libgl1-mesa-wx11

peace

---

### Post by NULL712 on 2007-08-15
??I have bad video play back when I use jahshaka. I deleted it but now that I know some one is having luck with it I might give another try. Beryl is not working yet for me because I still have to reconfigure xorg.conf

---

### Post by Leon945 on 2007-10-23
Now.. what about Gutsy?

i've read the whole thread.. and it seems i probably shouldnt even try to install it...

But, i do have the nvidia-glx-new driver..
Is it possible it will work?

I just dont wanna mess up my video settings/setup (whatever)

---

### Post by MyR on 2007-10-23
installing jahshaka wont mess up your video. i would give it a try and see if it works
peace

---

### Post by Leon945 on 2007-10-23
Ok..
I will give a try tonight..

:)
I'll let you know how it goes

---

### Post by dummyhead3 on 2007-11-04
Hey guys,

I installed the windows jersion of Jahshaka using wine, works, but your files must be in the ~/.wine/c_drive/

it is a miracle lol :).

---

### Post by MyR on 2007-11-07
thanks for the tip!

> **dummyhead3 said:**
> it is a miracle lol :).

yes, if by miracle you mean a lot of hard work by the wine devolopers ;]

peace

---

### Post by markdarb on 2007-11-19
I couldn't add the repo to the sources list. It doesn't seem to exist any more.

---

### Post by MyR on 2007-11-19
> **markdarb said:**
> I couldn't add the repo to the sources list. It doesn't seem to exist any more.
right you are!

i suggest you go complain about it on [http://www.jahshaka.org/forum/](http://www.jahshaka.org/forum/)

peace

---

### Post by kurageart on 2008-03-14
[http://jahshaka.org/forum/guide-compile-ubuntu-gutsy-amd64-t1604.html](http://jahshaka.org/forum/guide-compile-ubuntu-gutsy-amd64-t1604.html)

---

