---
title: "Pidgin Question :)"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by doomster on 2007-11-20
is there a way  to edit the "friendly message" shown next to your name at  msn Messenger, when using msn account? any addon that shows other ppls friendly msg when they are in contact list?

---

### Post by Microsoft_Sam on 2007-11-20
"Pidgin uses an outdated version of the MSN protocol that does not support status messages. For this reason, until our MSN protocol support is updated, status messages will not be supported."

[http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIsetastatusmessageonMSN]("http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIsetastatusmessageonMSN")

---

### Post by Inxsible on 2007-11-20
i think aMSN supports that. If you want you can try it out.```
sudo aptitude install amsn
```

---

### Post by Bimbambum on 2008-04-21
Hello there,

currently my main operation system is Windows but I'm just a step away from switching to Ubuntu for good. It may be ridiculous but the only thing that holds me back is Windows Live Messenger. I'd like to ask you Pidgin users if you know any possibilities for the following in Pidgin, either by plugins or by editing some files.

 - changing logging folder
 - making logs store custom emoticons
 - see and set a personal message
(Maybe there's a change with it since the last post of this thread.)
 - sort incoming files by sender
 - set conversation background for individual windows
(It's something personal, you know.)
 - see the list of deleted contacts
 - use Messenger Plus!-like text formatting codes
 - last but not least: a drawing tool
(Might seem dumb but actually I often communicate with colors and drawings rather than words to tell more using less.)

I'd be thankful if you showed me the way to these if they exist at all. :)

---

### Post by StOoZ on 2008-04-21
there is also an overall issue with the away,n/a etc.. messages in pidgin.

---

### Post by Vadi on 2008-04-21
> **Bimbambum said:**
> Hello there,

currently my main operation system is Windows but I'm just a step away from switching to Ubuntu for good. It may be ridiculous but the only thing that holds me back is Windows Live Messenger. I'd like to ask you Pidgin users if you know any possibilities for the following in Pidgin, either by plugins or by editing some files.

 - changing logging folder
 - making logs store custom emoticons
 - see and set a personal message
(Maybe there's a change with it since the last post of this thread.)
 - sort incoming files by sender
 - set conversation background for individual windows
(It's something personal, you know.)
 - see the list of deleted contacts
 - use Messenger Plus!-like text formatting codes
 - last but not least: a drawing tool
(Might seem dumb but actually I often communicate with colors and drawings rather than words to tell more using less.)

I'd be thankful if you showed me the way to these if they exist at all. :)

Hiya,

" - changing logging folder": I poked around in pidgin, didn't find how to make it change the ~/.purple/logs directory to something else, You can cheat it though. Go to places - home folder, and press Ctrl+H. You'll get a list of hidden files/folders displayed (anything that starts with a dot is considered "hidden"). Then start typing ".purple", it'll fine that folder. Enter it, then right-click on the logs folder and select "Make Link". You'll get another one called "Link to logs" - feel free to copy that over wherever you want (you're welcome to rename it too). Whenever you double-click on this "link" folder, you'll go into place where pidgin logs.

Though, you can just right-click on a person in pidgin's list and select "View Log", which is a lot nicer and has a search feature, so no real need to dig in the logs manually.

" - making logs store custom emoticons" I don't know, because I don't use them and nobody that I chat with uses them. Sorry.

" - see and set a personal message" The pidgin icon-top left shows your personal message when you hover your mouse over it. Right-clicking on it gives you options to set/create new ones.

Rest I'm unsure about either. I do know that aMSN sports better MSN support, but a warning, it looks pretty fugly.

---

### Post by Tom--d on 2008-04-21
Use [www.emesene.org](www.emesene.org) 

Its the best MSN messenger for Linux me thinks :) 

The only think it doesn't support is webcam.

---

### Post by atomkarinca on 2008-04-21
> **Tom--d said:**
> Use [www.emesene.org](www.emesene.org) 

Its the best MSN messenger for Linux me thinks :) 

The only think it doesn't support is webcam.

+1

---

### Post by Vadi on 2008-04-21
Right, sorry about that. Heard emesene is coming out real well there.

---

### Post by Bimbambum on 2008-04-21
Thank you for all the answers.

**Vadi:** I wanted to actually have the log files on another drive, I do the same in Windows so if I want to install another Linux/reinstall Ubuntu, I don't need to backup anything. So thank you but it's not exactly what I'm looking for. :)

As for **emesene**, it's far the most comfortable alternative for Windows Live Messenger, the only thing it doesn't have and I need is a complex logging system, with automatic HTML logging sorted by contacts, the possibility to change logging folder and stuff like that. Please note if I'm wrong but as far as I know emesene stores only manually saved logs. Or is there some plugins I don't know about?

---

### Post by pluckypigeon on 2008-04-28
I was just wondering if their is a way to export contacts from pidgin messenger in a cvs format so I can import them in to my hotmail address book.

Thanks in advance

---

