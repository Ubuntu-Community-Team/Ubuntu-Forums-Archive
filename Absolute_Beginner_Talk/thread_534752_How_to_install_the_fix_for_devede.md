---
title: "How to install the fix for devede?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-08-25
There have been other posts about this, however, they have not been specific enough as to how to install the fix. Can anyone please tell me how to do it step by step. I had to revert to encoding and burning in windows. I hated having to go back to windows. Please help!!!

---

### Post by chrome307 on 2007-08-25
Are you referring to this?

[http://ubuntuforums.org/showthread.php?t=532861](http://ubuntuforums.org/showthread.php?t=532861)

If so what I did was download the latest update from the homepage and then unzip it and put it into my Home Folder.

Then you need to start up TERMINAL and type in the commands I have underlined in RED (just the 1st line)

Then you type in the line that is given by the other member to install the package.

---

### Post by bumanie on 2007-08-26
Thanks for your reply. I believe I tried that already and it did not work. I am probably doing something incorrectly. I will try again later. Except for the 'bug' re the sound, devede worked very well. I'd much prefer to use it than windows third party products that cost a fortune.

---

### Post by chrome307 on 2007-08-26
Do you need me to simply the instructions ( no offence ) - so it's clearer to follow?

That's why I moving over to Ubuntu .... maintaining a Windows based PC does mount up especially when you have to continually update software - I have 4 PC's at home :(

---

### Post by bumanie on 2007-08-26
> **chrome307 said:**
> Do you need me to simply the instructions ( no offence ) - so it's clearer to follow?

That's why I moving over to Ubuntu .... maintaining a Windows based PC does mount up especially when you have to continually update software - I have 4 PC's at home :(

I won't take offence - simplified instructions would be good.  I have extracted the tar.bz2 file to the desktop> Does it need to be extracted elsewhere? You mentioned you extracted yours to your home folder. 
Since moving to ubuntu, anything I have tried to do has worked, that's why I am frustrated with this.  I am sure it is a simple process, but I am missing something for some reason.
PS: On top of the cost of things for windows, it is also the hours spent maintaing the registry\scanning for spyware etc., not to mention the obsession with DRM that makes it a real pain to reinstall (which windows regularly needs).
I am at work at present and then study straight after work, therefore won't get to try any suggestions until Tuesday because after I study I have 2 hours sleep and return to work. Life's hard sometimes.

---

### Post by chrome307 on 2007-08-26
I downloaded the existing build using Applications --> Add & Remove --> DeVeDe

then I downloaded the package from here:

[http://www.rastersoft.com/descargas/devede-3.01.tar.bz2](http://www.rastersoft.com/descargas/devede-3.01.tar.bz2)

I copied the folder to my home folder and extracted it 

[img]http://img337.imageshack.us/img337/4686/68188164uz1.jpg[/img]

Now I went to APPLICATIONS --> TERMINAL 

then typed in ( gives you a list of contents )

```


ls


```

then typed in  ( changes directory to the extracted folder )

```


cd devede-3.01


```

then ( just to show the contents of the folder )

```


ls


```

finally type in ( gives you root permission to make changes and then install )

```


sudo ./install.sh


```

enter your password and that should be it

[img]http://img95.imageshack.us/img95/6627/51781790hq5.jpg[/img]

Don't give trying ........... it's easier when others show you how it's done that's what the forum is here for.

You'll get it working and the other apps .... if you do a search for my topics I've started you should see most of them have been solved, so instructions should be included in the post.

Goodluck with the studies .... I know how much of pain it is to work and study but you'll reap the rewards in the future.

---

### Post by bumanie on 2007-08-26
> **chrome307 said:**
> I downloaded the existing build using Applications --> Add & Remove --> DeVeDe

then I downloaded the package from here:

[http://www.rastersoft.com/descargas/devede-3.01.tar.bz2](http://www.rastersoft.com/descargas/devede-3.01.tar.bz2)

I copied the folder to my home folder and extracted it 

[img]http://img337.imageshack.us/img337/4686/68188164uz1.jpg[/img]

Now I went to APPLICATIONS --> TERMINAL 

then typed in ( gives you a list of contents )

```


ls


```

then typed in  ( changes directory to the extracted folder )

```


cd devede-3.01


```

then ( just to show the contents of the folder )

```


ls


```

finally type in ( gives you root permission to make changes and then install )

```


sudo ./install.sh


```

enter your password and that should be it

[img]http://img95.imageshack.us/img95/6627/51781790hq5.jpg[/img]

Don't give trying ........... it's easier when others show you how it's done that's what the forum is here for.

You'll get it working and the other apps .... if you do a search for my topics I've started you should see most of them have been solved, so instructions should be included in the post.

Goodluck with the studies .... I know how much of pain it is to work and study but you'll reap the rewards in the future.

Thanks chrome307. Think my main problem has been not extracting the file within my home folder. When I get time I will follow your instructions. Thanks again.

---

### Post by bumanie on 2007-08-27
Still trying to install this devede fix.
I don't know how to attach a screen shot. I managed to get the same read out in terminal as chrome 307 did, up until I give the sudo ./install.sh command, then instead of asking for a password, it shows the line
ian@ian-desktop: ~/devede-3.01 It doesn't matter how often I issue command ./install.sh, terminal returns to the same thing
Can anyone tell me what is wrong? Usually I can work things out, but this one has me stumped.
Maybe I will wait until gutsy gibbon's release and hope that the default install is fixed for that release.

---

### Post by MrKlean on 2007-08-27
I know this isn't what you're looking for, BUT the fix hasn't worked for me in feisty or gutsy..sooooooo  I do it differently !  I installed WinFF .. it's for Linux too !  I run WinFF to encode the movie from avi to mpeg, then I run QDVDAuthor to change it to DVD compatible and burn it to dvd with K3B.  It's multi-step but until Mplayer and Mencoder get fixed so they work with Devede, this is what I'm happy with.  If you need more help. lermme know!

---

### Post by MrKlean on 2007-08-27
Oops..I assumed you meant the problem with the sound being scratchy, but this still works !
LOL!!

---

### Post by TeaSwigger on 2007-08-27
Hello,

If I'm reading it right you are in the wrong folder - the "desktop" folder. Please open a terminal and enter:

cd ~/

This will put you in your home directory. You should see:

ian@ian:~$

There? Ok now assuming you have previously unpacked the devede archive in your home folder, enter:

cd ~/devede-3.10

This should put you in the right folder. You should see:

ian@ian:~/devede-3.10$

If so, now try the ./install.sh :)

---

### Post by MrKlean on 2007-08-27
TeaSwigger.. your devede works... makes dvd's without the distorted sound ??   Pray tell me how you did it ???? Thanks ; )

---

### Post by bumanie on 2007-08-28
Teaswigger, 
I  don't really know where it unpacked. I did it through synaptic. When I put cd ~/ into terminal it sill comes up with ian@ian-desktop. I have no idea how to get to the correct folder. Any instructions regarding this would be appreciated. Should I uninstall it and try again from scratch?

---

### Post by bumanie on 2007-08-28
> **MrKlean said:**
> I know this isn't what you're looking for, BUT the fix hasn't worked for me in feisty or gutsy..sooooooo  I do it differently !  I installed WinFF .. it's for Linux too !  I run WinFF to encode the movie from avi to mpeg, then I run QDVDAuthor to change it to DVD compatible and burn it to dvd with K3B.  It's multi-step but until Mplayer and Mencoder get fixed so they work with Devede, this is what I'm happy with.  If you need more help. lermme know!

Thanks for the suggestion. If you happen to see this and wish to offer command line and/or installation instructions, I would be very pleased. If not, I will attempt to install the above myself. I am not averse to trying - it is the best way to learn usually, ie learning from your mistakes. unfortunately with devede, whatever I have done incorrectly is not evident to me.

---

### Post by MrKlean on 2007-08-28
Hi Guy, here ya go ; )

First go here and get the optimized version of ffmeg.. [http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/)
It's a deb file, so you can just click on it and it will install.

Go here and download WinFF and install it ...  [http://biggmatt.com/winff/](http://biggmatt.com/winff/)
It's a front end for ffmpeg, and makes things alot easier ; )

When you run WinFF you will have to select your movie you want to decode.  Don't forget to tell it if you want PAL or NTSC. NTSC is or the usa and canada.
It will change the avi into mpeg or mpg.  THEN use DVDAuthor to make the 2 files audio and video .... then use K3B under other options to burn a New DVD Project ; )
If you need more help lemme know ; )

[email]mrklean@rcn.com[/email]

---

### Post by MrKlean on 2007-08-28
After you run WinFF you will have a file ending with Mpeg or MPG.  Use DVDAuthor to generate the 2 files ..audio and video .. THEN use K3B to burn them to disk LOL!!

I hope you understand this..if not...email me ; )

---

### Post by TeaSwigger on 2007-08-29
Have you folks tried Kmediafactory? If so configured, the burning app k3b can handle some video assembly as well. Kino is the one to look at for video editing etc. If you're dealing with DVDs of course there's dvd95 or k9copy. All of those are in the repositories for easy install. For DVD backups I still use DVDShrink tho'.

bumanie, about the terminal and these directories, that seems to be where the confusion is coming in. It's something that'll really be nice for you to get the hang of. It may come up a lot, and you should get the hang of these things before fussing with installing stuff from scratch. Fortunately it's easy once you get it figured. There are tutorials and guides galore. To give a few points though, in the hope it isn't redundant and doesn't just confuse the heck out of ya ;) :

> **bumanie said:**
> Teaswigger, 
I  don't really know where it unpacked. I did it through synaptic. When I put cd ~/ into terminal it sill comes up with ian@ian-desktop. I have no idea how to get to the correct folder. Any instructions regarding this would be appreciated. Should I uninstall it and try again from scratch?

hm so your login is ian and your computer is named ian-desktop. When you first open a terminal from the task bar or start menu, you see :

```
ian@ian-desktop:~$
```

Is that right? If so this is your home folder (directory). The command lines in your terminal will always start with "ian@ian-desktop:" See the wavy line ~ after the colon means "your home folder." That is where a terminal will open to by default. In the context of the whole ubuntu file system, your home folder should be /home/ian, a folder named ian in the home folder. cd means Change Directory, after which you enter the directory you want to change to. Hit enter and You Are There. ls means "list what's here in this directory." 

You'll usually be surfing around from there (starting in ~ which is /home/ian) but you can also use "absolute paths" or basically telling it a location starting at the very top (the first slash / ). Your desktop is a folder named, whew, desktop hehe, in your home folder. That means you can refer to it as either ~/desktop or /home/ian/desktop. To go there in the terminal you'd enter either cd ~/desktop or cd /home/ian/desktop. Say you already know the name etc. To open a file in there without going there in the terminal, for example open a text file named text.txt with the text editor gedit, the line would look like this:

```
ian@ian-desktop:~$ gedit /home/ian/desktop/text.txt
```

or:

```
ian@ian-desktop:~$ gedit ~/desktop/text.txt
```

Make more sense?

To be clear... If you installed it from Synaptic, the "old" version is already installed; you wouldn't need to do anything further. If you wanted the newest version you'd need to download it from their site to your home directory; then run the codes to unpack and install; then you can delete the downloaded and unpacked packages from your home directory and enjoy.

> **MrKlean said:**
> TeaSwigger.. your devede works... makes dvd's without the distorted sound ??   Pray tell me how you did it ???? Thanks ; )

Strangely enough I had no idea there was a bug until I read this thread. It just... works. I'm using Kubuntu, but no idea if that's relevant.

---

### Post by MrKlean on 2007-08-29
Tea, yup... there's a bug.  Something with mplayer or mencoder and devede.  I loved that proggie, but since feisty, it has a terrible scratchy audio when ya use it.  Oh well,I'll muddle along the long way LOL!!!

---

### Post by TeaSwigger on 2007-09-04
> **MrKlean said:**
> Tea, yup... there's a bug.  Something with mplayer or mencoder and devede.  I loved that proggie, but since feisty, it has a terrible scratchy audio when ya use it.  Oh well,I'll muddle along the long way LOL!!!

Noticed this in the devede FAQ: 

> I tried to create a disk but the sound is pure noise. 
Version 1.0-rc1 of MPlayer/Mencoder (the one released, at least at April 20, 2007 with Ubuntu Feisty and other Linux distributions) is buggy and doesn't work fine. While they don't launch a fixed release, just download the file **mplayer_fixed** from DeVeDe's homepage and follow the instructions there. Or, if you are brave and experimented, you can compile MPlayer/Mencoder from SVN.

Maybe I have a newer MPlayer/Mencoder. Anyway have you tried the fix they offer? 

If it doesn't apply keep muddling along the scenic route lol :)

---

### Post by ponchuk on 2007-09-05
what is the fix you are talking about. loks like u are installing 3.01. Is there a patch and where is it. DeVeDe sound is a problem and I have been looking for an alternate program.

---

### Post by Glenn Matsu Matsu on 2007-09-06
You can try manDVD.
First i use DeVeDe but get things like "you running out of disk space".
I had 15 gig available but that was not enough ??
ManDVd works fine for me.

---

