---
title: "Media Center"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-17
Hello. I am looking for an easy-to-install media center program for the latest version of Ubuntu. I have tried MythTV and Elisa, but I found them too complicated to install. I am looking for a program that will give a media experience to play the various video, photos, and music I have, and also be able to play DVDs within the interface. However, I am not worried about watching television on the media center. Does anyone know of any good programs to do this task? Thank you.

---

### Post by nexu56 on 2007-08-17
I urge you to reconsider MythTV. Its by far the best media centre application for linux (and any other platform, IMHO :wink:).

There is even a very easy step by step walkthrough for setting it up in the Community documentation: [https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV")

---

### Post by newlinux on 2007-08-18
I recommend mythtv as well. But you can also try freevo.

---

### Post by amitroy5 on 2007-08-18
I just need a very simple media center. I'lll give MythTV another try and will post if I need any help on it. I do not need to worry about TV recording or even DVD watching (even if I said that earlier). My intention is to be able to watch music, photos, and video on my TV. I tried those boxes such as Netgear's EVA8000 I was unhappy.

Thank you very much for your help.

---

### Post by amitroy5 on 2007-08-22
I tried downloading freevo but when I downloaded, it did not seem like it downloaded anything. So I removed it. Are there any guides for Freevo and Ubuntu? Thank you.

---

### Post by newlinux on 2007-08-22
Where were you downloading it from? If it didn't download anything what did you delete?

In any event, there is a feisty repo for freevo:

[http://freevo.sourceforge.net/cgi-bin/doc/FreevoAptUbuntu](http://freevo.sourceforge.net/cgi-bin/doc/FreevoAptUbuntu)

That link also contains instructions for installing it from source which can probably pretty easily adapted to Feisty.

---

### Post by .nedberg on 2007-08-22
> **amitroy5 said:**
> I do not need to worry about TV recording or even DVD watching (even if I said that earlier). My intention is to be able to watch music, photos, and video on my TV.



If this is all you want then MythTV is indeed overkill. Why not just connect your TV to your computer? If you have a dual head videocard this is no problem. Connect your TV to one head and monitor to the other and make the TV a clone of your monitor. If you want to use a remote you can install lirc.

---

### Post by amitroy5 on 2007-08-28
So far, I have not had any luck with any of the media programs. Are there any that are simply an alternate shell? What I need is pretty simple considering how complex media center programs have become. Thanks.

I could connect my computer to my TV, but a TV-friendly interface would be nice.

---

### Post by phyrewall on 2007-08-28
> **amitroy5 said:**
> So far, I have not had any luck with any of the media programs. Are there any that are simply an alternate shell? What I need is pretty simple considering how complex media center programs have become. Thanks.

I could connect my computer to my TV, but a TV-friendly interface would be nice.

Have you tried GeeXboX? 
Homepage: [www.geexbox.com]("http://www.geexbox.com")
Review:  [linux.com]("http://www.linux.com/feature/118210")

---

### Post by amitroy5 on 2007-08-28
I have not tried this program. But it seems that this media center is its own operating system. If that is the case, I would like to see if there are any other options.

> **phyrewall said:**
> Have you tried GeeXboX? 
Homepage: [www.geexbox.com]("http://www.geexbox.com")
Review:  [linux.com]("http://www.linux.com/feature/118210")

---

### Post by phyrewall on 2007-08-28
It's a live cd, so there's no installation requirement.

---

### Post by amitroy5 on 2007-08-30
I tried geexbox, but I am having trouble with samba because I store my media on another computer. I prefer something that runs on Ubuntu and for some reason,  I am having trouble on every media center program.

---

### Post by scott_g on 2007-08-31
I would try Elisa again; add the following repository (System>Administration>Software Sources>3rd Party Software> Add)

```

deb http://elisa.fluendo.com/packages feisty main

```

Then, open the Synaptic Package Manager, and do a search for Elisa.

The only hard part is the configuration; telling it where your media files are.  I believe its in a file in /home/$username/.elisa/conf_file.  There should be a section for music, photos, and videos.  Also, it does not work well with Beryl/Desktop Enhancements.

I find its a very neat interface.

Scott

---

### Post by methane on 2007-09-08
I'd like to set up a media center linux box too.  I'd like it to do the following well:
Run SlimServer.
Allow for archiving DVD .iso so I don't have to get them out of my collection to watch them. 
And that's really about it.  Pictures are not so important to me, and neither is actually playing music.  I'd like the box to boot right into the interface and be able to rip DVDs to isos as a menu option.

So, the two questions are:
Is it worth keeping DVDs around in iso format? or, "how does Xvid compare to DVD iso?"
And what is the best solution to this?
My options, as I see them are as follows:
Under Xubuntu load Elisa or MythTV.  (Xubuntu for the small footprint)
Load the machine with GeeXboX.  And hopefully get SlimServer working on it. (shouldn't be much of a problem.)

Thoughs?  comments? 
Thanks for your help.

---

### Post by Jose Catre-Vandis on 2007-09-08
Did you use the Geexbox Generator to setup samba on Geexbox? You will need to give it some settings and user/pass details otherwise it can't find your share.

Is you media on a linux pc or windows? If Linux, try using nfs instead of samba (for me, samba = headache/trouble!)

I have tried every media center app I can find on Ubuntu, and nothing comes close to GeexBox for ease of use, compatibility with file formats and configuration, plus its a one minute boot up from CD, so no messing with your HDD setup (although you can install it if you want to).


Alternatively, think of Ubuntu as your Media Center, and use some of the great apps already installed to handle your media
Kaffeine/MoviePlayer/Rythmbox should handle all your video and audio requirements, and use F Spot for photos. Or for a more manual approach, use mplayer. For example:
```
mplayer "mf://*.JPG" -mf fps=0.25 -fs
```
will play all the files in a directory with a JPG extension for four seconds each (fps=0.25) at full screen. Your images will need to be in the correct orientation, not sure if mplayer can correct this.

---

