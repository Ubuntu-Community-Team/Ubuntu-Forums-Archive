---
title: "[SOLVED] SMPlayer doesn't drag&amp;amp;drop"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by ofb on 2008-01-15
Title really says it all. I've got an otherwise normal 7.10 with an otherwise functioning SMPlayer. Just can't drag&drop into it.

Here's the terminal output for starting the player. Attempting a drag&drop does not add any output.

```
o@redfish:~$ smplayer
global_init
Preferences::load
Debug: This is smplayer v. 0.5.20 running on Linux
Debug: Qt v. 3.3.7
Debug:  * application path: '/usr/bin'
Debug:  * data path: '/usr/share/smplayer'
Debug:  * translation path: '/usr/share/smplayer/translations'
Debug:  * doc path: '/usr/share/doc/packages/smplayer'
Debug:  * themes path: '/usr/share/smplayer/themes'
Debug:  * shortcuts path: '/usr/share/smplayer/shortcuts'
Debug: Translator::load: trying to load translation file: '/usr/share/smplayer/translations/smplayer_en_CA.qm'
Debug: main: files_to_play: count: 0
Debug: Recents::load
Debug: MplayerWindow::languageChange
Debug: MplayerProcess::init_rx
Debug: Preferences::monitor_aspect_double
Debug:  warning: monitor_aspect couldn't be parsed!
Debug:  monitor_aspect set to 0
Debug: Playlist::setModified: 0
Debug: Playlist::loadSettings
Debug: Playlist::setModified: 0
Debug: BaseGui::initializeMenus
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: BaseGui::updateWidgets
Debug: Core::toggleRepeat: 1
Debug: BaseGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::updateRecents
Debug: MyClient::MyClient: trying to connect to the server
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: BaseGui::updateWidgets
Debug: BaseGuiPlus::loadConfig
Debug: DefaultGui::createStatusBar
Debug: BaseGui::initializeMenus
Debug: BaseGui::updateRecents
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: DefaultGui::loadConfig
Debug: DefaultGui::showMainToolBar: 1
Debug: DefaultGui::showLanguageToolBar: 1
Debug: DefaultGui::showMainToolBar: 1
Debug: DefaultGui::showLanguageToolBar: 1
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::loadActions
Debug: ActionsEditor::loadFromConfig
Debug: ActionsEditor::loadFromConfig
Debug: MyClient::socketError: error number 0 occurred
Debug: CSManager::notConnectedToPort
Debug: MyServer::MyServer:: server started at port 8000
Debug: BaseGui::continueStartUp: code: 0
Debug: BaseGuiPlus::firstShow
```

---

### Post by rvm4000 on 2008-01-15
I don't know why it doesn't work, but you're using a very old version (0.5.20), could you try at least [version 0.5.62](http://downloads.sourceforge.net/smplayer/smplayer_0.5.62_i386.deb)?

---

### Post by RomeReactor on 2008-01-15
Hi. SMplayer is based on Mplayer, and as far as I know Mplayer doesn't support drag and drop either.

---

### Post by rvm4000 on 2008-01-15
Dropping a file into the smplayer window works (or should work).

(Dragging something from smplayer to another application is not implemented)

---

### Post by ofb on 2008-01-15
I'm using 0.5.20-0ubuntu1, which is the current version in Synaptic.

Drag&drop works with MPlayer. Drag&drop also works with Totem, Kaffeine, and VLC.

Locally, I know that drag&drop works with SMPlayer in Ubuntu 7.04 and in Edubuntu 7.10, and both of those machines are using the Synaptic version as well.

So yeah, drag&drop into SMPlayer really ought to work in this U 7.10 machine, but it's not. Danged if I can figure out why, or where to poke it at it. I'm stumped.

(And it is indeed my favorite player, so I'd really like to have it work. Congrats, rvm4000.)

---

### Post by rvm4000 on 2008-01-15
Version 0.5.20 still used Qt 3. Current versions use Qt 4 and the drag&drop code (among a lot of other things) have been rewritten.

I don't know why drag&drop is not working for you in version 0.5.20 (it should, I think), but you should try a new version. If the deb package in my web doesn't work for you (it's compiled in a kubuntu feisty) you could try to compile yourself, it's easy, there's a script in the sources (create_deb.sh) which makes everything.

---

### Post by ofb on 2008-01-15
Tried Reinstall, and tried Complete Removal followed by Install in Synaptic, with no luck.

Had a look in ~/.qt and saw that .smplayerrc.lock and smplayerrc were not removed with SMPlayer. So I appended both filenames with OLD and did another Complete Removal and Install. New versions of those files were created when SMPlayer was started.

And now I can drag&drop. Hooray.

Remaining detail - this repaired SMPlayer does not remember that I like it to stay on top. That's a downer because it was the only player that did remember before. Now I have to select Always On Top from the player's top bar for every session. Is that in the preferences somewhere? I can't seem to find it. Perhaps a Gnome setting?

----

Anyhow, thanks for helping out rvm4000. I should say that I remain reluctant to install versions that are not in Synaptic - it's not bad advice to suggest it, but the real attraction of Ubuntu for me is having Synaptic deal with patches. I'm afraid I'm getting old and no longer wish to keep track of individual applications. My memory is becoming spotty.

With respect I'd suggest any such advice in a Beginners Forum should come with caveats to warn people that they are side-stepping a key feature that makes Ubuntu better than Windows. (And perhaps Mac? Do they have this yet?) Not to mention that it can lead them into Dependency Hell, which is an aspect of the old days of Linux that I try to forget.

---

### Post by ofb on 2008-01-15
Aha - the desired option is under Video > Stay On Top.

And after you select that, drag&drop no longer functions. You have to deselect Stay On Top and restart SMPlayer to get drag&drop to work again.

Ah well. Looking forward to the new version with U 8.04.

---

### Post by rvm4000 on 2008-01-15
I've just tested it right now, and you're right, once the Stay on top option is activated drag&drop stops working :confused:

---

### Post by ofb on 2008-01-15
In the new one too? Aw crud. Well good luck with it. Some sort of interface conflict bug, possibly upstream with QT or Gnome. (Same in KDE?)

EDIT:
Just to add fun, I notice that my VLC has View > Always On Top selected, but it doesn't work. Also, if I start Kaffeine then try to drag&drop a movie into it, I can't. Kaffeine has to be already running a movie before I can drop a new movie in. Kaffeine doesn't seem to have it's own Always On Top feature, so can't check for similar conflict there.

---

### Post by rvm4000 on 2008-01-16
> **ofb said:**
> In the new one too? Aw crud. Well good luck with it. Some sort of interface conflict bug, possibly upstream with QT or Gnome. (Same in KDE?)

Yes, the problem happens too in the new version.

I realized I was doing something wrong when setting the stay on top option (the other window flags were cleared) but after fixing it, the problem with drag&drop is still there :(

Maybe this is a bug of the window manager (I used KDE) or Qt.

BTW, this problem doesn't happen in the Windows version.

---

