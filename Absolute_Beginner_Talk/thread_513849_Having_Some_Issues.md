---
title: "Having Some Issues"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by definedglory on 2007-07-31
Well I understand that I am not able to play MP3s right out of installing Ubuntu. But when I hear about these codecs and opening up a terminal I have no idea what to do. 

Also when I try to install Flash it brings up three files. Does it matter which one I choose?

By the way I don't mean to be annoying but I'm new to this whole open source thing can anyone direct me to some really good linux media players and things like that? That would be awesome.

---

### Post by RobMunda on 2007-07-31
I'm sort of new to Ubuntu myself. I was able to play songs right after the installation was complete. It might not hurt to try. I'm not sure if Banshee is installed by default, but I have liked that the best of the media players I've tried so far.

Just click on Applications > Sound & Video (the > symbol means go to that menu choice) and you should have a few players installed already. Some are audio and some are video (which you probably guessed for yourself). Generally speaking, hovering the mouse over the name of the program will pop up a mini description of what it is and what it does.

If you can't get songs to play, come back and post a follow-up in here. I'm sure someone can help you.

-Rob.

---

### Post by aysiu on 2007-07-31
Go to System > Administration > Synaptic Package Manager

Search for the phrase *ubuntu-restricted-extras*

Mark it for installation by right-clicking it

Click *Apply*

You should have MP3 support and Flash and Java and a bunch of other stuff.

---

### Post by definedglory on 2007-07-31
Thanks. 

Well I resolved the whole installing issue by myself, I realized that I was an idiot and I didn't realize that it doesn't show you typing the password. So sorry for that. 

No Banshee is not pre-installed. But I will try that out.

Thanks alot.

---

### Post by kostkon on 2007-07-31
You don't need to open a terminal. If you try to play an mp3, I assume you have 7.04, Ubuntu will install the codecs for you.

As fas as the flash concerned, go to Synaptic and search for f*lashplugin nonfree*, then select the package *flashplugin-nonfree* that the search result will give you and install it.

Now for media players, I recommend you to try first the default media player in Ubuntu. If it does not meet your needs then you can try other ones. Some good ones are:

[LIST]
[*]Amarok
[*]Banshee
[*]Listen
[/LIST]

---

### Post by aysiu on 2007-07-31
Yeah, that's a bug (some consider it a feature) that will never be fixed:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

