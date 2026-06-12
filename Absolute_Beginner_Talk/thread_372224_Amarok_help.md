---
title: "Amarok help"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by ChonkeyMonkey13 on 2007-02-27
I am having trouble configuring my Amarok player. I tried using the lite version, that didnt work. I then tried using the MySQL version, but I wasn't sure of my port number. When I tried playing a stream I get this error:

 ERROR LOADING MEDIA

 No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
[http://ubuntu.hbr1.com:19800/trance.ogg](http://ubuntu.hbr1.com:19800/trance.ogg)


It's an .ogg file that works fine with Rhtyhmbox but not amarok. I also tried to play an .pls from shoutcast, and I got the same error.

 Can someone please help?

---

### Post by louis_nichols on 2007-02-28
Yeh, I have that problem with amaok too. It's not permanent, though. I mean, a crtain link will not work for the first few tries, but then start working. It seems it's quite "sensitive" to network conditions. At least, I read somewhere on the page or the forum that these errors are caused by network problems, although no good explanation was given as to why amarok shows these errors but other players don't, at the exact same time.

It seems it's amarok-xine that does this. Unfortunatelly, for some, again, unknown reason, amarok-gstreamer is not available under Edgy. At least, last I checked, it wasn't. I got tired of searching for amarok-gstreamer and learned to live with this little problem, though.

---

### Post by FyreBrand on 2007-02-28
Chonkey make sure you have the SQLite database selected for use because the dbase isn't your problem.

Next make sure you have libxine-extracodecs installed.  From the terminal:
```
sudo apt-get update && sudo apt-get install libxine-extracodecs
```

You can also install libxine-extracodecs using Adept package manager.  If you get an error message from the Konsole or can't find them in Adapt make sure you have your Multiverse repository enabled because that's where they live.

As louis pointed out sometimes you get an error message that a stream or song won't play.  If you do have the codecs installed just click play again once or twice and the stream or song should start playing.  You can avoid this whole hassle by playing ogg and flac files instead of mp3 files.  ogg/flac are open formats and supported by default in xine and gstreamer without extra hassle and configuration.

---

### Post by Drakkor on 2007-02-28
If streaming audio is what you want , why not install streamtuner ?? It rocks !! :)
Click picture 2X to enlarge to normal !
Edit: I use xmms to play the streams

---

### Post by ChonkeyMonkey13 on 2007-03-01
Thanks, I got the update, but when I tried to get the libxine, it gave me this error:

Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

Any ideas what happened and what I could do to fix it?

---

### Post by FyreBrand on 2007-03-01
Ugh it was late and I didn't realize you were streaming an ogg file.  Your Amarok should play the ogg file by default with just the standard xine back end. 

I'm trying it now and it's working fine.

The pls file is an mp3 stream and you would need the extra codecs for that.  If you are just trying to do the ogg then Amarok should work.  So let's find out what's going on:

1. What version of Ubuntu are you running?

2. Did you install Amarok from the repositories or download and install from the KDE site.

3. Did you check your network connection and make sure it wasn't just cutting out at that time?

4. Did you try and press play again a couple times after getting that message?

---

### Post by ChonkeyMonkey13 on 2007-03-01
> **FyreBrand said:**
> Ugh it was late and I didn't realize you were streaming an ogg file.  Your Amarok should play the ogg file by default with just the standard xine back end. 

I'm trying it now and it's working fine.

The pls file is an mp3 stream and you would need the extra codecs for that.  If you are just trying to do the ogg then Amarok should work.  So let's find out what's going on:

1. What version of Ubuntu are you running?

2. Did you install Amarok from the repositories or download and install from the KDE site.

3. Did you check your network connection and make sure it wasn't just cutting out at that time?

4. Did you try and press play again a couple times after getting that message?

ANSWERS:

1. version 6.10; GNOME 2.16.1

2. I installed Amarok from the repositories I suppose. The add/remove applications button

3. I don't think so, I kept trying over and over again, and I was on GAIM, so I would of lost connected if that happened right? I'm not sure, I have Cable.

4. I did try pressing play afterwards, and I still got the same error.

 Sorry If no help, Im still new at ubuntu and LINUX in general.

---

### Post by spoot on 2007-03-01
[This page]("http://packages.ubuntu.com/edgy/libs/libxine-extracodecs") tells me that the package you are looking for is located in the Multiverse repository, did you enable that?

(step 4. in "Adding extra repositories")
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by ChonkeyMonkey13 on 2007-03-01
.....

---

### Post by ChonkeyMonkey13 on 2007-03-01
> **spoot said:**
> [This page]("http://packages.ubuntu.com/edgy/libs/libxine-extracodecs") tells me that the package you are looking for is located in the Multiverse repository, did you enable that?

(step 4. in "Adding extra repositories")
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

I believe I have those libraries. I downloaded the extracodecs before I installed. Well when I typed:

 sudo get-apt install libxine-extracodecs, I get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

So I don't know what the deal is....

---

### Post by spoot on 2007-03-02
> **ChonkeyMonkey13 said:**
> I believe I have those libraries. I downloaded the extracodecs before I installed.
Did you download them manually from the website then or something? In that case you can usually just doubleclick the .deb file you have gotten.
> **ChonkeyMonkey13 said:**
>  sudo get-apt install libxine-extracodecs, I get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

So I don't know what the deal is....
That message tells you it actually cannot find the package, could you verify if you enabled the Multiverse repository? (link is in my previous post)

---

### Post by ChonkeyMonkey13 on 2007-03-02
Ok, I just now enabled multi-verse. I thought I had it enabled in my repositories, I guess not. I just ran:
 sudo apt-get install libxine-extracodecs  , and It seemed to work. Now what's next after enabling it?

---

### Post by FyreBrand on 2007-03-02
Chonkey with an ogg stream it should "just work".  There shouldn't be a problem with streaming ogg.  I'm heading to work and will hit Google and see what I can find out.  I really can't think of a reason why that stream won't play.

I'll post back in a while.

---

### Post by ChonkeyMonkey13 on 2007-03-03
> **FyreBrand said:**
> Chonkey with an ogg stream it should "just work".  There shouldn't be a problem with streaming ogg.  I'm heading to work and will hit Google and see what I can find out.  I really can't think of a reason why that stream won't play.

I'll post back in a while.

Thanks, I really appreciate your help and sorry for the inconvenience. I did install streamplayer, and it seems to work, but I dont know why amarok isn't working. If push comes to shove, its ok. I'll just stream through streamplayer.

---

### Post by FyreBrand on 2007-03-03
> **ChonkeyMonkey13 said:**
> Thanks, I really appreciate your help and sorry for the inconvenience. I did install streamplayer, and it seems to work, but I dont know why amarok isn't working. If push comes to shove, its ok. I'll just stream through streamplayer.
Okay.  I have looked and can't find anything that appears relevent.  Sorry we couldn't figureit out.

---

### Post by ChonkeyMonkey13 on 2007-03-04
> **FyreBrand said:**
> Okay.  I have looked and can't find anything that appears relevent.  Sorry we couldn't figureit out.

It's alright ,thanks for your help anyways.

---

