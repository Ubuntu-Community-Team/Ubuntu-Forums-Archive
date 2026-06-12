---
title: "Windows Media Player under wine?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sethdotcom on 2007-05-31
Is there anyway to run windows media player under wine I really like the feel of it.

also can itunes be run under wine also?

---

### Post by pbw on 2007-05-31
Supposedly both wmp and itunes can run under wine, just google for it. Though I dont know why you don't give something like amarok a solid try, it's native and much nicer imo.

-- pbw

---

### Post by hanzomon4 on 2007-05-31
Yeah you can truly find much better apps under Gnu in my opinion. I've never tried WMP or iTunes under wine so I can't really help on that front. I have used wmp in a Virtualbox install of xp, I don't know how to get Virtualbox to see the music on my hardrive however. But it works with cds and such, I need to see if iTunes+ipod works. Truly though the Linux apps are so much better.

---

### Post by pbw on 2007-05-31
> **hanzomon4 said:**
> I need to see if iTunes+ipod works. 


amarok is great with ipods imo, easy updating of artwork and a drag/drop interface for adding to ipod or from ipod to collection, and deleting a song is a right click away. Alot nicer than gtkpod. Give it a shot and forget about itunes ;)

---

### Post by hanzomon4 on 2007-05-31
Yeah I use Rhythmbox now mostly but I've used Banshee, Listen, and Exaile! before and they all sync ipods really well. I'm just seeing what all I can do with Virtualbox.

---

### Post by Cyvros on 2007-05-31
Personally, I'd recommend something like XMMS or BMP (my absolute favourite two media players), but each to his own.

> **hanzomon4 said:**
> Yeah you can truly find much better apps under Gnu in my opinion. I've never tried WMP or iTunes under wine so I can't really help on that front. I have used wmp in a Virtualbox install of xp, I don't know how to get Virtualbox to see the music on my hardrive however. But it works with cds and such, I need to see if iTunes+ipod works. Truly though the Linux apps are so much better.

As far as I know, VirtualBox can't actually read the host HDD quite yet.

---

### Post by slumcat05 on 2007-05-31
There is a clever little trick in VirtualBox to create a shared folder for you virtual OS. I forget how to do it, but it's in the help manual on their website somewhere. It's really only two steps or so, really easy. I had a folder in my /home called VBox, and anything I wanted to acces from the virtual OS I just put in that folder, then in the virtual Windows session it was simply a matter of adding the folder as a network drive (which was also very simple and fully laid out in the help manual). You can share any folder (more than one if you'd like), for example if you have all your songs and movies in one folder, just add it as a share folder and voila, access your songs from VBox Windows! If you absolutely must use iTunes/WMP in Windows, you should check it out.

---

### Post by slumcat05 on 2007-05-31
OK, I went ahead and looked it up in case anyone is interested in sharing files for use in a VirtualBox session (for iTunes, WMP and such). Here is the command to run in Linux:

```
VBoxManage sharedfolder add "VM name" -name "sharename" -hostpath "/path/sharefolder"
```

Then in the virtual Windows, you do (in the command prompt):

```
net use x: \\vboxsvr\sharename
```

where you can replace x: with whatever you want the folder to be mapped as.

Thus if you want to share "/home/john/Media", your virtual OS is named "WinXP" in VirtualBox, you want the folder to be called "Media" in Windows, and you want it mapped as g:, you would do:

```
VBoxManage sharedfolder add "WinXP" -name "Media" -hostpath "/home/john/Media"
```

Then boot up your virtual Windows, open the command prompt, and do:

```
net use g: \\vboxsvr\Media
```

That's it. Then in My Computer, there will be a new network folder called g: that will contain all the files in your Media folder. I like to make a shortcut to it and put it on my Desktop or in the My Music folder, or whatever, but it's there and you can add or remove anything you want from it.

If you want to see the entire manual (many useful things for VBox in there) you can download the PDF from here: [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by hanzomon4 on 2007-05-31
Worked like a charm after I installed the guest additions thing. But usb doesn't work with the latest Ubuntu, devs are looking into it. To the OP: It's not worth trying to get iTunes to run on linux when better apps exist under linux. If you really want iTunes on linux ask apple to port it.

---

### Post by rickycodie on 2007-06-02
yeah rythmbox and exaile are both awesome.

btw this is post 100!!!

---

### Post by dfreer on 2007-06-02
The only thing I would want iTunes for is the music store. Unfortunately the only way I've seen to get itunes to install in linux is to use older versions that will no longer let you download from the store, so it is pointless.
Amarok is pretty great music player, and as for video I would go with VLC, mplayer, and xine (yes all three!)

---

### Post by DJ Wings on 2007-06-02
I use Exaile, and it rocks, but this guy probably needs iTunes/Winamp to be able to play DRMed tracks. Exaile/amaroK clearly can't do this.

---

### Post by Swab on 2007-06-02
You can skin VLC to look like WMP.

---

### Post by hanzomon4 on 2007-06-03
> **DJ Wings said:**
> I use Exaile, and it rocks, but this guy probably needs iTunes/Winamp to be able to play DRMed tracks. Exaile/amaroK clearly can't do this.

Ah yeah, I forgot about that one. I have maybe 40 tracks that I can't play on the desktop,can on the ipod though. You can see if some of your tracks can be un-drm'ed for 30 cents. The only other option would be a virtualbox install of xp, unless you can get wine to work.

---

### Post by Squid_blk on 2007-06-07
I do like Linux players better but I do unfortunately have a need for WMP.  I listen to some radio stations online but I can no longer use them on my home PC because they are WMP only due to lazy webmasters and webpage makers.  

I tried to download it but there is an ActiveX issue and I could not get it.  I thought of downloading it on my work computer and putting it on a CD and trying to install it with Wine but I am not sure it will be that simple because it might try to update and I do not need it to do that.

So is there a tried and tested way to get WMP to run in Linux?

---

### Post by drs305 on 2007-06-07
> **Squid_blk said:**
>  I listen to some radio stations online but I can no longer use them on my home PC because they are WMP only due to lazy webmasters and webpage makers.  


I listen to a lot of internet broadcasts. I was eventually able to find a way to listen to all of them. I use firefox with the mediaplayerconnectivity plugin. I then configure mpc to play Windows Media broadcasts using VLC. I think I posted the exact method of installing and configuring mpc and VLC a few months ago.

As with you, I still would really like to be able to use Windows Media Player. The two things that I can do with it that I haven't been able to do with VLC or any other player in linux concerns archived internet broadcasts. 

The first is the ability to play these archives at variable speeds without downloading the file first. WMP seems to be able to speed up the playback on the fly.

The second feature is the ability to use the slider bar to advance or retreat to a specific point of the broadcast. For instance, if listening to a sporting event, with WMP I can use the slider bar to advance the playback a few minutes or even through the entire halftime. I can do this with any archived streaming broadcast without downloading it first. With VLC, I can advance it a program set distance time but can't advance it very far or often without breaking the connection.

Someday maybe we will either be able to use WMP or have a linux derivative that is truly as elegant as WMP.

Not trying to start a flame war - I love ubuntu and use windows only a couple of times a week.

Edited:

Here is the link I referred to about installing mediaplayerconnectivity and vlc. I wrote this while using edgy but have it running in feisty wtihout problems. The instructions are in post #12.
[http://ubuntuforums.org/showthread.php?t=381769&highlight=vlc+mediaplayerconnectivity](http://ubuntuforums.org/showthread.php?t=381769&highlight=vlc+mediaplayerconnectivity)

There is a mozilla vlc plugin. The vlc apps I have installed are vlc, vlc-nox, and mozilla-plugin-vlc

---

### Post by Squid_blk on 2007-06-08
Thanks for the Link I will check it out.  Sounds like it will work.  If this works for me that will be cool. Next have to work on getting the other buttons on my mouse to work.

---

### Post by Squid_blk on 2007-06-09
drs305, this totally worked.  I used the terminal to get the VLC player which only took a minute or so and then got the plugin.  I set it with the wizard and it worked right from the start.  I was really hoping there was an alternative to the WMP only stuff on the net and this works for me.  Of note, although I only selected the plugin to use VLC for WMP files, the plugin has been completely ignoring other files if I have them open with Totem or Mplayer.  Not sure why it is doing that.  I had to install Mplayer to work with Sipie which is awesome for listening to the Sirius Online Radio which is not possible to access because of an ActiveX issue.  Now I have three media players to try out.  

So thanks a bunch, and to the others, this really works.  On a Feisty note, I found it a bit unusual to see that Feisty had Totem set as the default player to play MP3 files.  I was trying to figure out why Rhythmbox was not running. I had to manually reconfigure MP3s to open with the box instead of Totem.  Not sure if that was a slight oversight or a more dominant program trying to take over.

---

### Post by cleardensity on 2007-06-11
> **hanzomon4 said:**
> Worked like a charm after I installed the guest additions thing. But usb doesn't work with the latest Ubuntu, devs are looking into it. To the OP: It's not worth trying to get iTunes to run on linux when better apps exist under linux. If you really want iTunes on linux ask apple to port it.

BUT - is there a better way to purchase/download music, audiobooks and the like? I'm honestly TRYING to switch completely from windows to linux, and this is one thing i'm having a hard time finding... most everything you find that works is indie or something like that - i want access to the majors as well, and plenty of audiobooks - i'm looking at audible.com and will probably just spend the $30 on a book and see if it works like it should... I really don't want to use any virtual machines, but being the noob that i am, i can't find another way to get the music/audiobooks. Suggestions welcomed.

---

### Post by dfreer on 2007-06-11
I haven't really found a great music download site that has the range of artists that iTunes has in linux, (like you said mostly indie projects) about the only thing I could recommend would be [http://www.mp3search.ru/](http://www.mp3search.ru/) Haven't tried it myself but it seems to have a wide selection, and a few people here highly recommended it to me.

As for audiobooks, there is a site that has made audiobooks of a lot of classics books in the public domain, [http://librivox.org/](http://librivox.org/) I downloaded a few from there, worked great and in mp3 format.

---

### Post by cleardensity on 2007-06-12
> **dfreer said:**
> about the only thing I could recommend would be [http://www.mp3search.ru/](http://www.mp3search.ru/) Haven't tried it myself but it seems to have a wide selection

yeah, but is it legal here in the states? I only want legal means of getting music - i do not want anything to do with Piracy. I don't want anything that is "sketchy"... thanks for the suggestion though...

> **dfreer said:**
> As for audiobooks, there is a site that has made audiobooks of a lot of classics books in the public domain, [http://librivox.org/](http://librivox.org/) I downloaded a few from there, worked great and in mp3 format.

Yes, i've seen/used librivox before - what i'm talking about are new books - I'm a huge Grisham, Clancy, Flynn, Brown fan and i want to be able to get thier books, among many others, without any problems and at a moments notice. I've been using [http://www.podiobooks.com](http://www.podiobooks.com) for a while now - and i love those, but they are definately NOT Grisham/Clancy/Brown/etc. etc...

To the OP: I'm not trying to highjack your post, but rather expand upon what you first hit on. We have the same problem, and i'm wondering if anyone out there has a solution to this side of the problem that would help us both get off iTMS... but still be able to get the quality/quantity that we'd like. ;)

---

### Post by TravMan63 on 2007-06-12
Windows media player 6.4 installs and runs fine under wine (use '98' mode)
[http://appdb.winehq.org/appview.php?iVersionId=379](http://appdb.winehq.org/appview.php?iVersionId=379)

I had to install it using wine file - the terminal method didn't work for me. Do NOT run wine as root

As I stated above - it installs and run - unfortunately it won't play any files on my system (yet)
(states error that the path/filename is wrong)
may have something in common with my powerpoint issue
[http://ubuntuforums.org/showthread.php?t=470842](http://ubuntuforums.org/showthread.php?t=470842)

I haven't seen songbird mentioned yet - I think it's still in beta stage, but it's pretty cool - works on win and mac too.  Plays files embedded in a website, and makes it easy to download if you wish.

TM

---

### Post by dfreer on 2007-06-12
> **cleardensity said:**
> yeah, but is it legal here in the states? I only want legal means of getting music - i do not want anything to do with Piracy. I don't want anything that is "sketchy"... thanks for the suggestion though...


I was wondering if it was somewhat sketchy myself. However you do pay for the music, so I do believe it is legal.

> **cleardensity said:**
> 
Yes, i've seen/used librivox before - what i'm talking about are new books - I'm a huge Grisham, Clancy, Flynn, Brown fan and i want to be able to get thier books, among many others, without any problems and at a moments notice. I've been using [http://www.podiobooks.com](http://www.podiobooks.com) for a while now - and i love those, but they are definately NOT Grisham/Clancy/Brown/etc. etc...

To the OP: I'm not trying to highjack your post, but rather expand upon what you first hit on. We have the same problem, and i'm wondering if anyone out there has a solution to this side of the problem that would help us both get off iTMS... but still be able to get the quality/quantity that we'd like. ;)
Yeah, you might have problem then. I wish iTunes worked in linux, but alas.

---

### Post by revealer on 2007-06-12
running wmp under wine is slower than running a native app.
there are lots of alternatives:
if you like winamp, try xmms
if you like itunes, try songbird
else you can try amarok, exaile or listen (the one i use)

---

### Post by cleardensity on 2007-06-12
> **revealer said:**
> running wmp under wine is slower than running a native app.
there are lots of alternatives:
if you like winamp, try xmms
if you like itunes, try songbird
else you can try amarok, exaile or listen (the one i use)

i don't have a problem running a native application - i just really need to know where/how i can get access to a wide variety of downloadable mp3/etc that is legal... I would junk iTunes in a heartbeat, IF i can find an alternative to the music store...

music playback, cd ripping, podcasting - all those are covered, so i don't need Itunes for that, i just need to be able to access the music "mon" - and i'm thinking that's what the OP needs as well...

---

