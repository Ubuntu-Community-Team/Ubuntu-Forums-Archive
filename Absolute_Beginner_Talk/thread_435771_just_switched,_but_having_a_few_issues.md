---
title: "just switched, but having a few issues"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by swatF1RESTORM on 2007-05-07
A couple days ago I posted [this thread]("http://ubuntuforums.org/showthread.php?t=431303"). I got a couple of responses but never resolved my issue. That issue is viewing streaming video from NBA.com feeds. I can get them to load into VLC but they do not play. The 'status bar' that has the file info in the bottom left screen and I see that cycle a couple of times like it's trying to reload the link but the end result is the same. So that's one of the issues I have.

Another is more of a question than an issue because everything works like it should. My home network consists of 2 XP Boxes, a Mac laptop, and now my fully Ubuntu laptop. My question is this: is there a way to have Ubuntu remember my 'default keyring' (still confused a little on this concept but I can make it work by entering the keyring) so that I don't have to manually enter it every time I start up?

Next is a Totem player issue that I've searched for with no luck. I've got Totem player to play the DVD however the menus and fast forward/rewind buttons are no responsive and nothing happens when I click them. Any ideas?

I'm enjoying Ubuntu so far. I think I've finally got it setup and functioning to do what I want. I would like to get a composite manager (I think that's what they're called) like Beryl/Compiz to work but that can come later. I wanna have the basics down before I start in on the nice 3D graphics stuff. I tried to do everything at once on my first install and ended up screwing my resolution up bad enough to want to do a fresh install.

Thanks to anyone that can help me on any of these issues. I really like how you can turn to the forums to look for help from within the community. God Bless.

swatF1RESTORM

---

### Post by Zero Prime on 2007-05-07
I use Mplayer and the Mplayer plugin for all online media and I have had no issues.  For it to work right though I had to remove all Totem and VLC plugins from my Firefox directory.  I also had to edit all the file types I wanted to open with Mplayer in the Firefox preferences menu.  If you don't see any of your filetypes when you go to your manage file types in the menu type   about:config  in your browser bar.  Type  download  in the filter bar.  Make sure browser.download.hide_plugins_without_extensions is set to false.  If it isn't, click the value of true until it says false.  Now you can change what program opens what file types under the manage filetypes menu.

---

### Post by justleen on 2007-05-07
same here.. VLC works (the plugin) works, but not brilliantly..
I removed totem (especially the plugin), and installed mplayer and the plugin.. i can view all online streams now

---

### Post by swatF1RESTORM on 2007-05-07
sounds like that might be the answer that I'm looking for. I've downloaded mplayer but wasn't able to get the firefox plug-in installed correctly. I just search for help getting those files installed and I'll post back here if it worked or not. Thanks for the help Zero Prime and justleen.

---

### Post by swatF1RESTORM on 2007-05-07
Ok so I haven't been able to get the plug-ins straight. I downloaded mplayer but was unable to install the firefox plug-in. In my previous thread about this same issue someone pointed me to a different firefox extention called MediaPlayerConnectivity. It has a wizard that you can configure and select which media player you wish you use for various types of media (quicktime, windows, etc) I set all streaming media to go through mplayer but mplayer was still unable to properly view the stream or even load it.

Can anyone help me through this. I'm a beginner in Ubuntu and really want to make it work but it's looking more like I'll be partioning to windows to do (what has always been) simple tasks. I want to learn how to solve these problems. Ideally some really nice guru will help me ask the right questions and tell me how to detect my settings to be posted here so people know what my system looks like. Just throwing an idea out there. Patiently waiting...

swatF1RESTORM

---

