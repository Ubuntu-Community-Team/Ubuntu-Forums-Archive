---
title: "Music console for webpages that end with .mp3 for firefox? (Ubuntu)"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by EagleScout on 2008-02-12
Hi hi! I'm a recent windows -> Ubuntu convert and am having a bit of trouble with firefox. when I used windows, if I went to a webpage that ended with .mp3 (for example: [http://kontarkhosz.free.fr/muzik/files/apocalyptica/path.mp3](http://kontarkhosz.free.fr/muzik/files/apocalyptica/path.mp3)) it would bring me to a blank white page but with a small playbar in the middle that looked like this:

[img]http://a664.ac-images.myspacecdn.com/images01/78/l_b1909e1e0da544ec3fa61295c01280f7.jpg[/img]

but when I use firefox on Ubuntu it brings me to a blank, all black page, and where the playbar used to be it only says:

(no video)

and it plays the sound file but I can't tell it to stop or pause or tell it what part of the sound file to play.

is it possible to add a play-bar like that to firefox in Ubuntu?

(please keep in mind that I am very new to linux, so if you give me terminal commands please tell me what, if anything, I have to do before copying and pasting them into the terminal, thanks!!)




The reason for wanting a playbay like this is that I'm taking a spanish class in college right now and a lot of our homework is to visit a website and listen to sound files form it... they are all in spanish and it is often necessary to pause the sound file, answer some question, and resume listening. Right now what I do is when I get to the "(no video)" page I just hit File > Save As, and open it with Amarok ...this works but is very inconvinient because I have to download the sound file which can take a pretty long time on my computer :/

---

### Post by EagleScout on 2008-02-12
I've messed arround a lot wit hinternet settings and looked through extensions but no luck with any of those either :(

---

### Post by EagleScout on 2008-02-13
bump form page 14

---

### Post by tgalati4 on 2008-02-13
In a terminal:

sudo apt-get install xmms

In Firefox:

Edit-->Preferences-->File Types-->Search MPGA-->Edit Action-->Custom Action: xmms

I agree, mplayer is brain-dead when it comes to playing mp3's in a tab.

---

### Post by sigge on 2008-02-13
Get the "Totem Mozilla plugin" from Synaptic Package Manager. And also make shure you have mp3 codecs installed. That should be all. :)

---

### Post by mozetti on 2008-02-13
You could also try Songbird. It's a product in development, but it's pretty stable and feature-filled. It's basically a music player mashed with a web-browser (essentially firefox) all built from the mozilla base.

Although it might not be the exact implementation you're looking for, it should give you everything you want and might give you more functionality than you hoped for.

---

### Post by EagleScout on 2008-02-13
> **tgalati4 said:**
> In a terminal:

sudo apt-get install xmms

In Firefox:

Edit-->Preferences-->File Types-->Search MPGA-->Edit Action-->Custom Action: xmms

I agree, mplayer is brain-dead when it comes to playing mp3's in a tab.

all good up until the preferences... my gui seems to be a bit different than yours... here's a quick screenshot of what I'm lookin at... I'm not sure what to do on the last step (it won't let me type things in, I have to browse for and click on the files to change anything.

[img]http://a755.ac-images.myspacecdn.com/images01/53/l_c4e570125d27e43c21ea581cdaa84872.png[/img]

it seems like I should just be able to type xmms in the last part, but that won't work.

---

### Post by mozetti on 2008-02-13
xmms isn't a plugin, it's a program. Choose the second radio button, "Open them with this application" and put xmms there. When you go to that site, xmms will load and play the file. xmms is the Linux equivalent to WinAmp, so if you've ever used WinAmp you'll have no problems. Even if you haven't used WinAmp, you shouldn't have any problems because it's very easy to use.

---

### Post by stevejesus on 2008-02-13
I would just try the mplayer plugin for FireFox.  I wouldn't really call it "braindead".  It works just fine for me and has for a couple of years.  It will also give you that magic little player bar scrubber deal like Windows Media Player that you have been looking for.  Better still, you won't have to mess with any Firefox settings.  

It's in the repositories and is a meta-package that will configure everything for you.

---

### Post by EagleScout on 2008-02-13
> **sigge said:**
> Get the "Totem Mozilla plugin" from Synaptic Package Manager. And also make shure you have mp3 codecs installed. That should be all. :)

The totem mozilla plugin is already installed... idk anything about codecs though... the MP3's play, if that's any indication, there's just no console to control it.

---

### Post by EagleScout on 2008-02-13
> **mozetti said:**
> xmms isn't a plugin, it's a program. Choose the second radio button, "Open them with this application" and put xmms there. When you go to that site, xmms will load and play the file. xmms is the Linux equivalent to WinAmp, so if you've ever used WinAmp you'll have no problems. Even if you haven't used WinAmp, you shouldn't have any problems because it's very easy to use.

It won't let me just type xmms in... I have to browse for it and actually click it, but I can't find it (?) is there a way to force it in with the terminal?

---

### Post by stevejesus on 2008-02-13
Just use the Mplayer plugin.  Its gives you exactly what you asked for... a scrubber and a couple of buttons.

---

### Post by EagleScout on 2008-02-13
> **stevejesus said:**
> Just use the Mplayer plugin.  Its gives you exactly what you asked for... a scrubber and a couple of buttons.

The mpeg files on webpages are set to use "mplayerplug-in 3.40" but it still just shows the "(no video)" thing - no console :(

...other than that I'm not really sure what the "repositories" are so I don't know how to get the mplayer plugin for firefox... is that the synaptic package manager or something different?

I have mplayer but its just a media player... I just set it as the default application when a sound file is opened or streamed from firefox (usr/bin/mplayer instead of mplayerplug-in 3.40), but now instead of playing the song when I go to a .mp3 page it downloads it (>.< now the RIAA will probably sue me, lol) and nothing happens... when I click 'open' in the downloads, the song then opens with amarok (??)

---

### Post by stevejesus on 2008-02-13
Yes, Synaptic is a frontend used to access the software repositories.  Try;

```
sudo apt-get install mplayer-firefox-plugin
```

This plugin will allow you to play .mp3's WITHIN the firefox browser, just as you wanted.

To install this software, you may need to enable some additional repositories, but that is another story.

---

### Post by EagleScout on 2008-02-13
> **stevejesus said:**
> Yes, Synaptic is a frontend used to access the software repositories.  Try;

```
sudo apt-get install mplayer-firefox-plugin
```

This plugin will allow you to play .mp3's WITHIN the firefox browser, just as you wanted.

To install this software, you may need to enable some additional repositories, but that is another story.

that didn't seem to work:

```
kevin@kevin-laptop:~$ sudo apt-get install mplayer-firefox-plugin
[sudo] password for kevin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mplayer-firefox-plugin
```

is there another way to get the application?

---

### Post by stevejesus on 2008-02-13
Yeah, you need to add repositories.
You have 2 options...  You can 1)  Open up a text editor and uncomment the necessary repositories then save and then do a;
```
sudo apt-get update
```
Or, you can go the easiest route possible.  You can 2)  download an application called "Automatix" (google it).  Then once you have installed Automatix, it will give you an option to install the mplayer plugin for Firefox.
Your choice...
Just make sure that you download the version on Automatix that matches your version of ubuntu, which I assume is Gutsy.

---

### Post by EagleScout on 2008-02-13
> **stevejesus said:**
> Yeah, you need to add repositories.
You have 2 options...  You can 1)  Open up a text editor and uncomment the necessary repositories then save and then do a;
```
sudo apt-get update
```
Or, you can go the easiest route possible.  You can 2)  download an application called "Automatix" (google it).  Then once you have installed Automatix, it will give you an option to install the mplayer plugin for Firefox.
Your choice...
Just make sure that you download the version on Automatix that matches your version of ubuntu, which I assume is Gutsy.

I installed automatix using the second option you listed and installed the mplayer firefox plugin.... but now I can't figure out how to tell firefox to use the plugin. right now its still set to use mplayer as mentioned before and still does the download -> open with amarok thing.

what is the file name of the firefox plugin? (searched for "mplayer-firefox-plugin" but no results)

or, what do i need to do to tell ff to use it?




thanks for all the help btw!!

---

### Post by EagleScout on 2008-02-13
> **mozetti said:**
> You could also try Songbird. It's a product in development, but it's pretty stable and feature-filled. It's basically a music player mashed with a web-browser (essentially firefox) all built from the mozilla base.

Although it might not be the exact implementation you're looking for, it should give you everything you want and might give you more functionality than you hoped for.

I'm trying the songbird player now... I got it from automatix but apparently it was an old version, and when I update to version 0.4 it just gives me a folder with a ton of stuff in it.... there's probably some way to make all the files do something by using the terminal but im pretty much useless without a gui - so I have no idea how to use the folder (Songbird_0.4_linux-i686.tar.gz)

I'm looking for a way to mesh it with firefox right now.... it just opens as a separate media player like amarok at the moment... I should probably figure out how to update it first tho.

---

### Post by stevejesus on 2008-02-13
Hey man, I dont think Songbird is gonna cut it.  All it is is a second-rate clone  of a second-rate piece of software (iTunes).

Go into Firefox > Preferences > Content

Down a couple of lines you should see "file types"
 Click on it.

Find MPGA in the extension column.  double-click and open it.

Find the radio button that says "use this plugin".  you are probably using mplayerplug-in 3.40.

Check the box!  Let me know how it goes.

---

### Post by tgalati4 on 2008-02-13
xmms is located in /usr/bin/xmms

You will have to navigate to /usr/bin in the dialog box then choose xmms.

The mplayer plug-in does not allow me to slide the pointer to an arbitary point in an hour-long podcast.  That's braindead.

---

### Post by EagleScout on 2008-02-13
> **stevejesus said:**
> Hey man, I dont think Songbird is gonna cut it.  All it is is a second-rate clone  of a second-rate piece of software (iTunes).

Go into Firefox > Preferences > Content

Down a couple of lines you should see "file types"
 Click on it.

Find MPGA in the extension column.  double-click and open it.

Find the radio button that says "use this plugin".  you are probably using mplayerplug-in 3.40.

Check the box!  Let me know how it goes.

here's what it looks like. it plays the sound file, but I can't control it -

[img]http://i22.photobucket.com/albums/b322/buubla/Screenshot.png[/img]

this is what is started as... and yes, it says mplayerplug-in 3.40

---

### Post by EagleScout on 2008-02-14
> **tgalati4 said:**
> xmms is located in /usr/bin/xmms

You will have to navigate to /usr/bin in the dialog box then choose xmms.

The mplayer plug-in does not allow me to slide the pointer to an arbitary point in an hour-long podcast.  That's braindead.

when set it to use xmms and go to a .mp3, instead of opening a page it opens the download window and downloads the sound file, then opens it with xmms... I got it to do the same thing with amarok earlier, which works, but very slowly. when I did it on windows (and I know - ubuntu isn't windows... thank god) it would open that play bar console in a separate tab and would play as it buffered - which was nice cuz it takes a while to download on my comp...

---

### Post by stevejesus on 2008-02-14
Here is what my browser looks like when playing an .mp3.  Is this what you want?

[IMG]http://www.myfootinyourass.com/Ubuntu/screens/mplayerplugin.png[/IMG]

Try right-clicking in the browser window and then clicking "show controls".  Ofcourse, make sure that you first re-enable the mplayer plugin...

---

### Post by tgalati4 on 2008-02-14
I experience the same problems as EagleScout, and my cheesy work-around is to use xmms.  I don't know why the control bar doesn't show up in mplayer and there's no way to change it's behavior.  It may be a bug in the mplayer plug-in, or a problem with Firefox.  Xmms works until something better comes along.

The advantage of using xmms is that it can be programmed to use my multimedia keys (which work regardless of what desktop I'm in) and I have an xmms control in my bottom panel.  The mplayer plug-in doesn't allow the same functionality.

---

### Post by stevejesus on 2008-02-14
Yeah, thats bizarre...  I have been using the mplayer plugin for mozilla for over 2 years...  Have never once had an issue with it...  Except that it has always been a little buggy when switching to fullscreen...

---

### Post by EagleScout on 2008-02-14
> **stevejesus said:**
> Here is what my browser looks like when playing an .mp3.  Is this what you want?

[IMG]http://www.myfootinyourass.com/Ubuntu/screens/mplayerplugin.png[/IMG]

Try right-clicking in the browser window and then clicking "show controls".  Ofcourse, make sure that you first re-enable the mplayer plugin...

rightclicking the browser doesnt yield any drop menus, nowhere does it say 'show controls' :confused:

I guess the xmms thing will work for now. Its way better than what it was doing!

thanks for all the help!!

---

