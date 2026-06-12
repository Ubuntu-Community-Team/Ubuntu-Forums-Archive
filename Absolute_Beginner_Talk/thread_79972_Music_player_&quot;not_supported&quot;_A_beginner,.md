---
title: "Music player &quot;not supported&quot;? A beginner, need some help..."
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by sparkling_twinkle on 2005-10-21
guys, need some help.. i've been using ubuntu for a month now. but still can't handle it. i wanna use its music player but there's an error saying some kind of "not supported..." some tips and guidelines?

---

### Post by Jenda on 2005-10-21
Sure. I'm guessing you haven't downloaded the codecs, so I'll post you a link to one of my own earlier post on how to do this (a lot easier to find for me):
[http://www.ubuntuforums.org/showpost.php?p=428987&postcount=9](http://www.ubuntuforums.org/showpost.php?p=428987&postcount=9)

---

### Post by David Marrs on 2005-10-21
also check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for faqs. A lot of common problems are solved there.

---

### Post by sparkling_twinkle on 2005-10-21
thank you very much... i am now working it out with terminal... a million of thank u.. God bless u all!:KS

---

### Post by sparkling_twinkle on 2005-10-22
hi, im here again to ask help.. i have received an mp3 and trying to play it. and then xine appears, a message of "the... use unsupported codec. start playback anyway." i choose yes.. and as i was typing this to terminal [I]"sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list"[/I] it seems like its unable to load or cannot look up..

what will i do next? pls... thanking u in advance.. once again, thank u..

---

### Post by poofyhairguy on 2005-10-22
try muine, really.

> sudo apt-get install muine

---

### Post by sparkling_twinkle on 2005-10-22
[QUOTE=poofyhairguy]try muine, really.[/QUOTE]


:KS i am done sir... can i used the player now after that? there is a message appearing, "cannot fetch..."

---

### Post by Jenda on 2005-10-22
Not sure what the matter is. Could you explain a bit?

Did you paste the whole text above into the terminal at once? You should paste each line separately. One after another.

---

### Post by Jussi Kukkonen on 2005-10-22
sparkling_twinkle, here's some general advice on asking for help:
* Please explain what you want as clearly as possible (what you want to do, what program you're using, what buttons did you click etc.). Using too many words is rarely a problem.
* if you run commands from the command line, and there's a problem, please copy-paste everything into your post here (preferably using the CODE-tags). Everything means the prompt, your commands and the output.
* If you get errors (be it from command line or in a window), please try to tell us the exact text -- it's usually worth the trouble.

---

### Post by Jenda on 2005-10-23
So Twinkle, how's it going?

---

### Post by sparkling_twinkle on 2005-10-23
Thank's guys... got it now! :) God bless u all!


Linux rules!

---

### Post by Jenda on 2005-10-24
Don't you just love it when it works?

:)

---

