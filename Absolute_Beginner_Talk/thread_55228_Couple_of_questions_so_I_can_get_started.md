---
title: "Couple of questions so I can get started"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by TechSonic on 2005-08-07
I only have a few questions.  Once I get these out of the way, I can start to enjoy Ubuntu. So any help would be great!

My first question is.
How do I either change permissions or change the folder where Totem and Firefox look for plugins?  I cannot add files to the plugins folder for Firefox because it says permission denied, so I tried root terminal and did chmod 775 on the folder "Plugins".  It does nothing at all...

Could I login to Root with a Gnome desktop instead of terminal?

How can I make it so I don't have to be in root to access write mode on any folder while still in my normal user login?

Where on earth can I find plugins for MPEG and other codecs for Totem?
I search but not find any.

I have 2 other drives installed, one is NTFS and the middle (Storage) is a FAT32, why do none of these drives appear in the Computer section where CDRW Drive and File System are at?


Most of them just have to do with permission problems, installing some applications and add-ons are difficult because of this.
I'm just so used to Windows XP Pro where my regular had Administrative rights.
I just hope maybe I can do the same with my regular login for Ubunto installation.

I already have an understanding of what files I shouldn't mess with.

---

### Post by aysiu on 2005-08-08
These two links should help you immensely:

[https://wiki.ubuntu.com/RootSudo?highlight=%28root%29](https://wiki.ubuntu.com/RootSudo?highlight=%28root%29)
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by TechSonic on 2005-08-08
So I have to manually type Sudo in terminal for everything?  Good god, this is annoying.  Thanks though, even if I don't like how it works.

Awesome, I actually got flash plugin for Firefox installed.  Thanks to the Sudo command, the permission denied thing didn't come up. ^.^

Great, now all but two questions have been answered.  The drives one and Totem plugins.  Also, whats up with Music Player?  It wont play shoutcast or windows media radio stations?  I tried to get on [www.di.fm](www.di.fm) to get some tunes going, but with no success in getting it to play.

---

### Post by OttoDestruct on 2005-08-08
[QUOTE=TechSonic]So I have to manually type Sudo in terminal for everything?  Good god, this is annoying.  Thanks though, even if I don't like how it works.

Awesome, I actually got flash plugin for Firefox installed.  Thanks to the Sudo command, the permission denied thing didn't come up. ^.^

Great, now all but two questions have been answered.  The drives one and Totem plugins.  Also, whats up with Music Player?  It wont play shoutcast or windows media radio stations?  I tried to get on [www.di.fm](www.di.fm) to get some tunes going, but with no success in getting it to play.[/QUOTE]

Drives you'll have to mount yourself, look over at [Ubuntu Guide](http://ubuntuguide.org/) for instructions. Ubuntu Guide also has info on the codecs in their 'installing multimedia codecs' section. Music could be a variety of things. Try installing beep-media-player, and messing around with a normal MP3 before you try streaming. You might have to go into the preferences and mess around with which output plugin it uses (if you want more info dig around in the tips & tricks section for Hoary), then try streaming.

*edit*

And Ubuntu Guide also has info on creating a root account/password.

---

### Post by aysiu on 2005-08-08
[QUOTE=TechSonic]So I have to manually type Sudo in terminal for everything?  Good god, this is annoying.  Thanks though, even if I don't like how it works.[/quote] Well, that's how it comes out of the box. If you create a new launcher in the panel with the command *gksudo nautilus*, that should ease some of your pain, I think.

> Also, whats up with Music Player?  It wont play shoutcast or windows media radio stations?  I tried to get on [www.di.fm](www.di.fm) to get some tunes going, but with no success in getting it to play. Music Player is more akin to iTunes or Winamp. It's not meant to play other stuff. Maybe you need RealPlayer?

By the way, I love Ubuntu, but it's because I like doing all the little customizations. If you want something that has nonfree codecs and plugins and automounts Windows partitions, you might want to give Mepis a try, too.

---

### Post by TechSonic on 2005-08-08
Now that I figured out the apt-get thing and got the wanted codecs installed, Music Player plays di.fm stuff and totem plays my movies now. YAY!

Now to look up the info on mounting my other drives, or atleast the storage one cause Ubuntu can read and write to FAT32 if i'm not wrong.

---

### Post by aysiu on 2005-08-08
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by AlexDe on 2005-08-08
> So I have to manually type Sudo in terminal for everything? Good god, this is annoying. Thanks though, even if I don't like how it works. 

You **can**  create a root account so you don't have to type sudo everytime, but that defeats the whole point of sudo. (Prevents you from having a root account.. a wee bit more secure because of the less accounts to work with)


[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

---

### Post by xmastree on 2005-08-08
[QUOTE=AlexDe]You **can**  create a root account so you don't have to type sudo everytime,[/QUOTE]Or just open a root terminal from Applications>System Tools

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=TechSonic]So I have to manually type Sudo in terminal for everything?  
[/QUOTE]

No you can make a root account and log into Gnome with it (and therefore undo the biggest security benefit over Windows- easy isn't always best).

---

