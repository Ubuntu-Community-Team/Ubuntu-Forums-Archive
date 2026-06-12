---
title: "[SOLVED] Online radio"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by cybo on 2008-03-04
I'm trying to listen to online radio but it won't work. The website is [www.wncu.org](www.wncu.org) ([http://152.9.6.199:1910](http://152.9.6.199:1910), MP3 ShoutCast playlist). When I click on the link Rythmbox Music Player pops out and then nothing happens. After that I go to the Radio menu and try to play something from the list but I get the unknown error. The station I'm trying to play is also in that list but when I click on I get the following message: Couldn't start playback. You do not have a decoder installed to handle this file. You might need to install the necessary plugins.Can anyone help? I'm new to Ubuntu and computers but really want to learn it.

---

### Post by meindian523 on 2008-03-04
Can you listen to local mp3s?

---

### Post by meindian523 on 2008-03-04
I faced no problem with either amarok or vlc.Maybe you will have to add the playlist specifically to Rhythmbox.How you would do that,I've no idea,I uninstalled Rhythmbox coz I never used it.

---

### Post by cybo on 2008-03-04
> **meindian523 said:**
> Can you listen to local mp3s?

I haven't tried to listen to local MP3's. I'll check it out and see what happends. If that doesn't work what do you recommend to use for music, video, online video and online radio listening ?

---

### Post by navneeth on 2008-03-04
I wish I remembered the exact steps that I took. 

1. I installed mplayer plugin for Firefox. For a while, I was listening to the internet station on my browser. 

2.Then I copied the URL (right click inside the player window/tab and click copy)

3. Paste the URL in Amarok and play the station.

Of late, Amarok doesn't load for me, so I'm using Rythmbox instead. To add a new radio station in RB, click on the "New Internet Radio Station..." button in the toolbar, and then paste the **URL of the stream** in the box that appears and click Add.

Of course, before I did all this my computer had the necessary stuff to play propereitry formats.

---

### Post by backflip on 2008-03-04
Do you have the 'restricted extras' loaded? Go to applications/add remove and search for ubuntu restricted extras. This will install codecs etc missing from the initial system installation. Your radio link plays ok with realplayer.

---

### Post by navneeth on 2008-03-04
> **cybo said:**
> I'm trying to listen to online radio but it won't work. The website is [www.wncu.org](www.wncu.org) ([http://152.9.6.199:1910](http://152.9.6.199:1910), MP3 ShoutCast playlist). When I click on the link Rythmbox Music Player pops out and then nothing happens.

Hmm. Did you click the play button?

---

### Post by meindian523 on 2008-03-04
> **cybo said:**
> I haven't tried to listen to local MP3's. I'll check it out and see what happends. If that doesn't work what do you recommend to use for music, video, online video and online radio listening ?

Hmm,if local mp3s don't work,you need to install the gstreamer plugins which are basically mp3 codecs,search for them in Synaptic.If you want an all-in-one package,install Vlc.

```
sudo apt-get install vlc
```

---

### Post by click4851 on 2008-03-04
I think meindian and navneeth have it down...if using rhythmbox make sure all the gstreamer codecs are loaded. and then add the "media link" in the New Internet Radio Station dialog box....should play.

---

### Post by cybo on 2008-03-04
> **navneeth said:**
> Hmm. Did you click the play button?

Yes I did try the play button. Nothing happened. I'm currently at work and they don't use Ubuntu. I'll check your suggestions as soon as I get back. Thank you to everyone. I really appreciate the help.:)

---

### Post by cybo on 2008-03-04
Thank you everyone. I have removed the Rythmbox and installed the necessary codecs through Add/Remove. I'm using Totem. Thank you everyone. :guitar:

---

### Post by andrew.46 on 2008-03-05
Hi,

 I have just listened to a few minutes with the following:

```
$ mplayer -playlist http://152.9.6.199:1910/listen.pls
```

And if you want to save it for offline playback you can try:

```
$ mplayer -playlist http://152.9.6.199:1910/listen.pls -ao pcm:file=radio.wav -vc null -vo null
```

which works well for me, and then convert it to mp3 or ogg or whatever :-) This is using the svn mplayer, so if your copy of mplayer does not do the above try this:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

Because the repository version has limitations deliberately built into it for political / legal reasons.

             Andrew

---

### Post by meindian523 on 2008-03-05
> **cybo said:**
> Thank you everyone. I have removed the Rythmbox and installed the necessary codecs through Add/Remove. I'm using Totem. Thank you everyone. :guitar:

Well,we didn't tell you to uninstall Rhythmbox,you could have used it as outlined above by click4851.

---

