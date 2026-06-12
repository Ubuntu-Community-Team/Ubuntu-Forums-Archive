---
title: "Best Torrent Application"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-10
Just switched to Ubuntu from Windows.
Used to use Utorrent.
The Bittorrent application that launches automatically is neat and does a good job, but as far as I can see, it will only handle one file at a time. Subsequent files open in new windows.
Is there a torrent app for Ubuntu which will enable multiple downloads and which can run in the background while I work with other applications?
Or is it possible to configure the existing Bittorent application to do this?
Sorry if this has been posted before.
Regards

---

### Post by matthewcraig on 2007-11-10
You can configure multiple ports for the GNOME bittorrent, so it will handle multiple files.  The best bittorrent application is the one that is supported by the Ubuntu community.  That one is 'gnome-bittorrent', the default.

---

### Post by Seisen on 2007-11-10
I like Deluge myself you can give it a try and see if you like it.

---

### Post by rsambuca on 2007-11-10
> **matthewcraig said:**
> The best bittorrent application is the one that is supported by the Ubuntu community.  That one is 'gnome-bittorrent', the default.

Just because it is the default Gnome torrent client doesn't mean that it is the best one!  Frankly, in terms of features, it is probably one of the weakest torrent clients.  Bittornado, deluge, azureus are all better IMO.

---

### Post by Raven18940 on 2007-11-10
I tried Deluge, and while it will probably be great some day, it doesn't seem finished now. 

You can actually keep using Utorrent is you want, via Wine.  Simply install wine and then type the command "wine utorrent.exe"

If you wanna say in the linux, I like Ktorrent, but it uses a lot of CPU resources for reasons I don't really understand.

---

### Post by ffi on 2007-11-10
you can use utorrent with wine

[http://www.utorrent.com/faq.php#What_are_.C2.B5Torrent.27s_system_requirements.3F](http://www.utorrent.com/faq.php#What_are_.C2.B5Torrent.27s_system_requirements.3F)

I like Azureus/Vuze other clients are transmission and deluge....

---

### Post by matthewcraig on 2007-11-10
Sorry, but can I have my own opinion on which is best, please?

---

### Post by rsambuca on 2007-11-10
> **matthewcraig said:**
> Sorry, but can I have my own opinion on which is best, please?

Of course you can.  I only brought it up like that because your reason is invalid.

---

### Post by Raven18940 on 2007-11-10
> **rsambuca said:**
> Of course you can.  I only brought it up like that because your reason is invalid.

It's not invalid, it works very well with gnome no doubt, and it's probably lightweight too.

---

### Post by bgast1 on 2007-11-10
Should I start a new thread for this or is it ok if I join in here. I installed a-mule yesterday to give it a try, but could not connect. But then again, I have no idea how I should have gone about it either, I just hit the connect button like I did with e-mule in windows and it wouldn't connect. 

I have used both bit torrent like applications and e-mule in windows and by far my personal favorite was e-mule. It would be nice to use something like that in Linux. Can anyone help?

---

### Post by ffi on 2007-11-10
doesnt it run under wine? shareaza runs quite well under wine and also does ed2k else maybe amule, xmule or mldonkey?

---

### Post by rsambuca on 2007-11-10
> **Raven18940 said:**
> It's not invalid, it works very well with gnome no doubt, and it's probably lightweight too.

I was referring to this statement: > The best bittorrent application is the one that is supported by the Ubuntu community  Support by the community doesn't make it the best.  It **may **be the best, but not because of that reason.

---

### Post by markusf21 on 2007-11-10
I like deluge with 1 exception. I seems to be quick and works very well but it sucks up all my bandwidth when in use. I cant even look up a web page if its running.

---

### Post by Perfect Storm on 2007-11-10
> **markusf21 said:**
> I like deluge with 1 exception. I seems to be quick and works very well but it sucks up all my bandwidth when in use. I cant even look up a web page if its running.

Have you remembered to set min/max of download and upload? Upload have a great impact, if it set to maximum it's allmost impossible to anything on the web. Try lower the max setting on upload.

---

### Post by markusf21 on 2007-11-10
Thnks I'll try that

---

### Post by 01steven on 2007-11-10
> **01steven said:**
> Just switched to Ubuntu from Windows.
Used to use Utorrent.
The Bittorrent application that launches automatically is neat and does a good job, but as far as I can see, it will only handle one file at a time. Subsequent files open in new windows.
Is there a torrent app for Ubuntu which will enable multiple downloads and which can run in the background while I work with other applications?
Or is it possible to configure the existing Bittorent application to do this?
Sorry if this has been posted before.
Regards

Hey everybody- I just want someone to answer my original question if that's OK!
Don't want to run WINE.
If Gnome torrent app can do this please can someone explain to me how (currently if I download a 2nd torrent file a new window opens).

Let's get this thread back on track!

---

### Post by rsambuca on 2007-11-10
Deluge and Azureus both do what you want.

---

### Post by 01steven on 2007-11-10
Is there a way of configuring the standard GNOME app to do this?

---

### Post by rsambuca on 2007-11-10
Not that I could find.  Both 'deluge-torrent' and azureus are in the repos, though.

---

### Post by insineratehymn on 2007-11-10
I like uTorrent, you said you used that before... is there a reason that you don't like Wine? Its a one-shot job.

```
sudo aptitude install wine
```

Download your flavor:
[http://download.utorrent.com/1.7.5/utorrent.exe](http://download.utorrent.com/1.7.5/utorrent.exe)

Then create your menu icon.
I don't know the quick piece of code to do this, but right-click on 'Applications', click 'Edit Menus', select whatever Menu you want it under 'Command': ```
wine /home/billybob/utorrent.exe
```

Obviously you want to replace home/billybob with wherever you keep it.

Easy Peasy Fo' Sheezy.

---

### Post by matthewcraig on 2007-11-10
> **01steven said:**
> Is there a way of configuring the standard GNOME app to do this?

What do you mean by "do this" ?

---

### Post by 01steven on 2007-11-10
> **matthewcraig said:**
> What do you mean by "do this" ?
For it to run multiple downloads simultaneously.

---

### Post by OisinT on 2007-11-14
I really need help setting up my automatic rss downloads in Deluge... anyone out there want to help me?

---

### Post by yarozar on 2007-11-14
> **insineratehymn said:**
> I like uTorrent, you said you used that before... is there a reason that you don't like Wine? Its a one-shot job.

I'm trying to switch to Linux from Windows and that was my first search - something like 'good linux torrent client'. And what a shame was to see such conclusion ... :( ... I believe I will switch back to Windows before it's too late.

BitTornado eats about 10-20% of my CPU resources for each active torrent. And while I was on Windows I had my uTorrent with 30-40 active torrents without any significant system slow-down ... It's really a shame that so much talked about Linux community didn't come up with any decent Torrent client. I'm actually very surprised.

---

