---
title: "I just wanna know..."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Jrazor on 2007-12-09
[COLOR="Black"][B]I haven't gotten my Ubuntu Discs yet, but i just wanna know:

1: Can you change your desktop background?

2: Can you use Firefox on Ubuntu?

3: Is there a Word Processor?

4: If there is can I save my Files in MS Word format?

5: Is the Desktop Cube real? 

6: I am very good with computers but I would like to know is Ubuntu easy to use?

7: Is it like Windows XP?

8: Is Ubuntu better than XP? [/COLOR][/B]:-k

---

### Post by Steveway on 2007-12-09
1. Sure, you can change even more things like the Window-borders or the themes of the Buttons etc...
2. Firefox comes preinstalled.
3. Yes it comes with OpenOffice preinstalled, there are even more in the Repositories. (Abiword ...)
4. Yes but I recommend to save your files in the .odt format, it is an ISO-standard for Documents.
5. Yes, why not?
7. No, it is Linux and Linux is not Windows.
8. For most people, yes. And technically, it is much better.

---

### Post by meborc on 2007-12-09
i suggest you go to the testimonialt subforum here.... and read some of the reviews or first timers adventures :) these will give you a nice overview...

edit: if you have so many questions still... why are you converting from windows? what appeals you about linux? (just interested)

---

### Post by Jrazor on 2007-12-09
Thanx Steveway[SIZE="4"][/SIZE]

---

### Post by misfitpierce on 2007-12-09
All yes but number 7... Do not compare linux to windows pls. It is open source not prop. If you mean by function then yes it can do everything windows can if not more. But not really to be compared. Run liveCD and get a feel for it and try a test partition or install. Enjoy :)

---

### Post by Arwen on 2007-12-09
1)Lots of stuff there-->[http://www.gnome-look.org/]("http://www.gnome-look.org/")
2)You can also use opera,epiphany,swiftfox..
5)You have to install compiz-fusion([http://ubuntuforums.org/forumdisplay.php?f=223]("http://ubuntuforums.org/forumdisplay.php?f=223")
6)Depends on your mood to accept its differences from windows
7)As far as appearence is concerned you could choose kubuntu which has KDE desktop environment that looks like XP a lot,Gnome of ubuntu is a lot different.As far as everything else is concerned yeah it's a whole lot different.
8)It's hard to give an answer,it works perfectly for me so I consider it to be the perfect OS for me for the time being as I got sick and tired of XP BSODs and viruses and ubuntu gave me a stable os with a great variety of applications to install(for free).
When you check it for yourself you'll create your own opinion:-)

---

### Post by RadiationHazard on 2007-12-09
well all your other questions are already answered i just wanted to throw in my opinion for the last question. I just switched to linux and out of mac windows and all of them that i have tried linux is by far better than the rest.

---

### Post by CCNA_student on 2007-12-09
If you want to play mp3's mpeg's and DVD's, use the command:
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot sudo /usr/share/doc/libdvdread3/install-css.sh.
    I just thought I should tell you, since Ubuntu does not play non-free audio and video formats. The terminal is under Applications>Accessories>terminal.

---

### Post by meborc on 2007-12-09
> **CCNA_student said:**
> If you want to play mp3's mpeg's and DVD's, use the command:
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot sudo /usr/share/doc/libdvdread3/install-css.sh.
    I just thought I should tell you, since Ubuntu does not play non-free audio and video formats. The terminal is under Applications>Accessories>terminal.

well :) easier would be to do ```
sudo apt-get install ubuntu-restricted-extras
```this will install all audio, media, java, flash etc... but be sure about the legal issues concerning mp3 codecs if you live in US etc...

---

### Post by CCNA_student on 2007-12-09
Installing the ubuntu extras did not work for me. Totem GStreamer cannot navigate DVD menus. It is a known bug in that movie player. You need Totem-xine or VLC to play DVDs. I was still not able to play a DVD. And if you want Jave Runtime Environment 6, Flash player, etc., just type those words(individually) under Applications>Add/Remove.

---

### Post by meborc on 2007-12-09
> **CCNA_student said:**
> Installing the ubuntu extras did not work for me. Totem GStreamer cannot navigate DVD menus. It is a known bug in that movie player. You need Totem-xine or VLC to play DVDs. I was still not able to play a DVD. And if you want Jave Runtime Environment 6, Flash player, etc., just type those words(individually) under Applications>Add/Remove.

the dvd stuff is a bit problematic... i have always used the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories for that ;)

---

### Post by CCNA_student on 2007-12-09
I meant Totem-GStreamer could not play DVD's, but Totem-xine and VLC can play DVD's.

---

### Post by crimesaucer on 2007-12-09
You're going to love ubuntu.

1-6 = yes
7 = better
8 = yes, it's much better... but you might want to dual boot at first while you get used to it.

---

### Post by nikoPSK on 2007-12-09
[COLOR=Black][B]I haven't gotten my Ubuntu Discs yet, but i just wanna know:

1: Can you change your desktop background?
[/B]Yes, very easily, (duh;)) you just right click your desktop then "change desktop background".
[B]
2: Can you use Firefox on Ubuntu?
[/B]It comes by default, Application > Internet > Firefox Web Browser
[B]
3: Is there a Word Processor?
[/B]There is Open office, very similar to msword. It's in Applications > Office > OpenOffice Word Processor. There is also Abiword if you want.
[B] 
4: If there is can I save my Files in MS Word format?
[/B]In OpenOffice just tell it to save it as .doc, same in Abiword
[B]
5: Is the Desktop Cube real? 
[/B]Yes, It is. You will need to install your graphics card driver then in synaptic install *compizconfig-settings-manager. *Once there open it by going to System > Preferences > Advanced Desktop Effects. Goto "general Options" then the "Desktop Size" tab. Set the first slider to four then go back to the main screen of cssm. You will then need to enable "desktop Cube" and "cube Rotate". There Is also "Cube Reflection" which will give your cube a nice reflective surface to rest on. Feel free to play with the other plugins and modify their settings.

[B] 6: I am very good with computers but I would like to know is Ubuntu easy to use?
[/B]Ubuntu is very easy to use. If you do not like terminal or synaptic to install items you can goto Applications > Add/ Remove. Then just Select "All available Software" from the drop down menu. You can check or uncheck things as you go by then apply and it will install or remove it all for you. There are Also "debs" which are Debian's Package Management System. You just download the deb, open it and Install. Another example of how easy to use Ubuntu is is when you open Totem Movie Player (Applications > Sound & Video > Movie Player) to play, say, and MP3. It will say you need to get codecs then open up the exact ones you need for you to install. 
[B] 
7: Is it like Windows XP?
[/B]Not very, If you want you can customize it with themes and such to better suit your needs.
[B] 
8: Is Ubuntu better than XP? [/B][/COLOR]
Depends who you ask, I believe it is and haven't had windows for 3 months now. (Even though I have been using ubuntu since Drapper and Linux since three years back) Hope you enjoy,
nikoPSK

---

### Post by crimesaucer on 2007-12-09
> **Jrazor said:**
> [COLOR="Black"][B]I haven't gotten my Ubuntu Discs yet, but i just wanna know:

2: Can you use Firefox on Ubuntu?

[/COLOR][/B]:-k

You will get Firefox 2, you can install Firefox 3 beta 1 or prebeta 2 Minefield. You can even get Swiftfox 2, or Swiftfox 3 prebeta 2, or Swiftweasel, Iceweasel, Flock, Sea monkey, Netscape, Opera, Epiphany... and even more....

---

### Post by sagarhshah on 2007-12-09
Ubuntu is great!!

I'd still advise yu to keep your windows on a partition while you get used to ubuntu incase you break it!!

---

