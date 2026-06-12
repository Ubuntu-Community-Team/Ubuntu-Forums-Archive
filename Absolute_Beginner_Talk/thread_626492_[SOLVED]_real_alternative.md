---
title: "[SOLVED] real alternative"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by irishy on 2007-11-29
Help please
Is it possible to install the program real alternative to listen to bbc radio and if it is can anyone provide a link on how to do it 
also is this the best way  of listening to bbc
thanks

---

### Post by gn2 on 2007-11-29
> **irishy said:**
> Help please
Is it possible to install the program real alternative to listen to bbc radio and if it is can anyone provide a link on how to do it 
also is this the best way  of listening to bbc
thanks

Here's how I get BBC web site video and audio to work: [https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

And I use this Add-on for Firefox: [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by nick_h on 2007-11-29
Real Alternative is Windows software.

However, you do not have to install Realplayer to listen to BBC radio.  Make sure you install ubuntu-restricted-extras:
```
sudo apt-get install ubuntu-restricted-extras
```

Details on restricted formats can be found [here](https://help.ubuntu.com/community/RestrictedFormats).  Select Windows Media Player on the BBC site.  If it doesn't work then you may have to install the w32codecs package from the Medibuntu repository.

---

### Post by irishy on 2007-11-30
Thanks for all your advice I have installed the restricted extras but still no sound so can you instruct me on how  i get the w32 codec please or alternatively is real player a better proposition for what i want
thanks

---

### Post by gn2 on 2007-11-30
> **irishy said:**
> Thanks for all your advice I have installed the restricted extras but still no sound so can you instruct me on how  i get the w32 codec please or alternatively is real player a better proposition for what i want
thanks

I would advise you to follow the instructions in my original post.
I can assure you that they work.

---

### Post by nick_h on 2007-11-30
> **irishy said:**
> Thanks for all your advice I have installed the restricted extras but still no sound so can you instruct me on how  i get the w32 codec please or alternatively is real player a better proposition for what i want
thanks

To install the w32codecs look at [this](https://help.ubuntu.com/community/Medibuntu) wiki page.  There may be other packages that you might like to download from this repository as well.

Installing Realplayer will also work.  When you were asking about Real Alternative I assumed that you preferred not using Realplayer, but both methods will work.

---

### Post by irishy on 2007-11-30
Thank you all I did mean real alternative but I have now installed realplayer successfully my experience in the past with realplayer in windows was awful but after installing the linux version I find it is not the same and it is not bombarding me with rubbish
thank you all again

---

