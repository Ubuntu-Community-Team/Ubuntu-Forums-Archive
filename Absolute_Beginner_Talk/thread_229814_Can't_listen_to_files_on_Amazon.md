---
title: "Can't listen to files on Amazon"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-05
On Amazon.com where they have CDs you can listen to the tracks, with either Windows Media option or RealOne Player. I just installed ubuntu and neither of these optinos work. So I tried installing RealPlayer from the realplayer site. That put an icon on my desktop saying RealPlayer10GOLD.bin
Clicking on that did nothing, so in properties I changed the permissions to make it executable. My guess was lucky as after that I got it to instal. It asked if it could instal at justin/home/realplayer and as I have no idea where else it might go, I agreed. It did its stuff and is now there. And still I cannot open the files on Amazon! 

Here I have 2 questions:
1) On windows, installing a program gives a shortcut on the desktop, and also puts the icon on the list of applications, so it can be started by clicking on either of these 2 places. Neither of these 2 things happened. Must I therefor also navigate myself to the realplayer folder hidden away in justin/home ?

2) When I click on the file in Amazon, it says "open with", then I navigate my way to that realplayer folder, and find what might be the right thing to select, which simply says "realplayer". But clicking on that, it waits a bit and then says:

"The content you are trying to play uses an audio codec that is obsolete and no longer supported. Please contact the content provider about using a supported codec."

I also tried installing XMMS Music Player by using the Add/Remove option under applications. Nicely enough the icon for that program now appears under the Sound and Video section of applications. However when I click on either the Windows Media option or RealOne Player files on Amazon, the Windows Media option says I need to install missing plugins, whic turn out to be unavailable, and the RealPlayer option, when it says "open with" and I chose "other", I have no idea where to find XMMS. I have looked, but I cannot find where ANY programs are.

Thank you for the help!
Justin

---

### Post by benuski on 2006-08-05
You might need to install the windows codecs, found [here]("http://https://help.ubuntu.com/community/RestrictedFormats").  Scroll down to the win32codecs, and install those.  That should allow you to play the WMA files.

---

### Post by Nikusan on 2006-08-05
The correct way to install real player (or anything really) is from Applications > Add/Remove... Doing it from there will put all your menu items in place and such. Downloading a binary from the web and installing that is discouraged because it's an excellent way to introduce spyware/viruses/instability/etc. The first link in my sig will be a great read for you regarding installing software.

Now, before you jump in and install real player the correct way I would advise you to not even do that. It is a terrible piece of software in my opinion. A better approach is to install all the codecs and a media player plugin for your browser. Have a read of the second link in my sig for instructions.

---

### Post by woodlandjustin on 2006-08-05
Sounds good. So how do I now uninstall and totally get rid of RealPlayer?
Thanks
Justin.

---

### Post by tommcd on 2006-08-05
Have you tried using synaptic package manager? It is great for installing and uninstalling software. No command line need either!

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

That will get you started. Have fun!!

---

### Post by woodlandjustin on 2006-08-05
Yes I tried that. But just in case I'll start a new thread - see you there
Justin

---

### Post by tommcd on 2006-08-05
Is this what you used to install Real Player:

[http://www.real.com/linux](http://www.real.com/linux)

That is for RPM package. They can be made to work in ubuntu, but you probably should use the .deb package:

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

I'm not sure how to uninstall an RPM in ubuntu. Perhaps someone else can help with that.

---

### Post by Nikusan on 2006-08-05
It might have installed an uninstall script in the directory inside your home directory. If not you can probably simply delete the folder from your home directory.

---

