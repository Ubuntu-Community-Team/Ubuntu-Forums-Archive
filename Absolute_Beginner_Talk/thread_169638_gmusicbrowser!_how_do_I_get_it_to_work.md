---
title: "gmusicbrowser! how do I get it to work?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-05-03
I downloaded the tar, saved to disk, extracted but can't get it to run.

what do I do?

---

### Post by aysiu on 2006-05-03
Any reason you're using the .tar.gz instead of the .deb?

I would download [this .deb](http://freshmeat.net/redir/gmusicbrowser/60337/url_deb/gmusicbrowser_0.951_all.deb) to your desktop and then go to a terminal (see my sig) and copy and paste these commands: ```
cd ~/Desktop
sudo dpkg -i gmusicbrowser_0.951_all.deb
```

---

### Post by RAV TUX on 2006-05-03
[QUOTE=aysiu]Any reason you're using the .tar.gz instead of the .deb?

I would download [this .deb](http://freshmeat.net/redir/gmusicbrowser/60337/url_deb/gmusicbrowser_0.951_all.deb) to your desktop and then go to a terminal (see my sig) and copy and paste these commands: ```
cd ~/Desktop
sudo dpkg -i gmusicbrowser_0.951_all.deb
```[/QUOTE]

ok thanks will do.

WOW you are awesome implemented within seconds without a delay or any problems!

Thank you very much.

please take a look at my other post and see if there is any way you can help me in other ways, particularly on how to get Ubuntu running on my EM64T.


[http://www.ubuntuforums.org/showthread.php?t=164563](http://www.ubuntuforums.org/showthread.php?t=164563)

---

### Post by RAV TUX on 2006-05-03
ooops can't get it to play I get a notice that I need to install

 alsa-utils

but when I check my Synaptic Package manager I see it already installed?

not sure what to do?

the error message says this:

Can't set the volume, that's probably because amixer (packaged in alsa-utils) is not installed.

---

### Post by aysiu on 2006-05-03
Don't know much about that. You can try *re*installing it, maybe. ```
sudo apt-get install --reinstall alsa-utils
```

---

### Post by jazzgossen on 2006-05-04
[QUOTE=yozef]ooops can't get it to play I get a notice that I need to install

 alsa-utils

but when I check my Synaptic Package manager I see it already installed?

not sure what to do?

the error message says this:

Can't set the volume, that's probably because amixer (packaged in alsa-utils) is not installed.[/QUOTE]

I had problems getting gmb to play anything, too. The reason for me was that it needs either the perl bindings for gstreamer (not available in the Ubuntu repositories) or the mpg321 packge. 

What happens when you run the program? Can you edit the preferences? What kind of audio output is selected in the preferences dialog?

---

### Post by RAV TUX on 2006-05-04
[QUOTE=jazzgossen]I had problems getting gmb to play anything, too. The reason for me was that it needs either the perl bindings for gstreamer (not available in the Ubuntu repositories) or the mpg321 packge. 

What happens when you run the program? Can you edit the preferences? What kind of audio output is selected in the preferences dialog?[/QUOTE]


no audio output at all, it list the artist and songs hit play and nothing happens.

---

### Post by Sef on 2006-05-04
Do you have any audio output at all from any device?

---

### Post by RAV TUX on 2006-05-04
[QUOTE=Sef]Do you have any audio output at all from any device?[/QUOTE]

yes most audio devices work, I primarily use Quark

---

### Post by jazzgossen on 2006-05-05
Then you probably need to install mpg321 (sudo apt-get install mpg321) and choose mpg321 under Audio in the Preferences dialog.

---

### Post by RAV TUX on 2006-05-06
[QUOTE=jazzgossen]Then you probably need to install mpg321 (sudo apt-get install mpg321) and choose mpg321 under Audio in the Preferences dialog.[/QUOTE]


Thanks for the help but I got your message late, I got it to work but not sure how?
I enabled some other players and other stuff on Synaptic Package Manager, perhaps the thing you spoke of.

Gmusicbrowser works great! and I love it!

:razz:

---

