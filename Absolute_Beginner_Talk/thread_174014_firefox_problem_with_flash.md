---
title: "firefox: problem with flash"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-05-11
hi,
i have a problem when i load pages with flash.
The problem is when there is form to write (e.g. login and password form): it doesn't let me to insert values, that no cursor. For the rest of the page the flash job works correctly.
thanks

---

### Post by zluka on 2006-05-11
i had the same problem..

but it seems to be solved now. what are the versions of firefox and flash?

---

### Post by ubunlilluz on 2006-05-12
firefox 1.5.2 and flash 7

---

### Post by Kobalt on 2006-05-12
Is it a version of firefox & flash you downloaded and installed by yourself ? Or is it you're under Dapper ?

---

### Post by ice91 on 2006-05-12
Great respect. Very interesting site. Best design.  Good content.

[http://guerria-skateboard-tommy.tabrays.com/](http://guerria-skateboard-tommy.tabrays.com/)
[http://mesotherapy.jino-net.ru/](http://mesotherapy.jino-net.ru/)
[http://aid-golf-golfdust-training.tabrays.com/](http://aid-golf-golfdust-training.tabrays.com/)

---

### Post by ubunlilluz on 2006-05-13
i've breezy.
i tried many solutions: installing ubuntu packages for flaSH;
downloading the pluging from the mozilla site.
Now if click the right button of mouse and i choose setting
appears the setting window, but with no text, only images.
Other information i can give (i hope usefull to solve the prolem) is that if i do "about:plugins" in a tab appears the list 
uf plugins and there is the shockwaves flash and another one
kind of flash plugin that i don't remember

---

### Post by EdThaSlayer on 2006-05-13
When is flash 8.0 going to be released for firefox because my flash applications dont seem to have sound...

---

### Post by DSn0wMan on 2006-05-13
[QUOTE=ubunlilluz]i've breezy.
i tried many solutions: installing ubuntu packages for flaSH;
downloading the pluging from the mozilla site.
Now if click the right button of mouse and i choose setting
appears the setting window, but with no text, only images.
Other information i can give (i hope usefull to solve the prolem) is that if i do "about:plugins" in a tab appears the list 
uf plugins and there is the shockwaves flash and another one
kind of flash plugin that i don't remember[/QUOTE]

You may have allready tried this, but the following command got the plugin working for me.

  sudo apt-get install flashplugin-nonfree
  sudo ln -s /usr/lib/mozilla-firefox/*flash* /opt/firefox/plugins

You need to enable the multiverse repository for apt to find the package.

---

### Post by janrocks on 2006-05-13
Yes.. that worked fine for me as well...yesterday, but now firefox has gone and lost all it's plugins and accounts.. It presented me with a create account screen earlier, and as I have only ever used default I cancelled it.. I couldn't select default because (apparently) it was already in use??? how?, I only had one desktop going as I had only just booted up... lost all my plugins and links and can't get back to where I was...anyway the question.. I know all the accounts are saved somewhere and I can import them back into firefox... but where are they saved, and how can I set that account back to default, with my plugins and bookmarks?.. help..I'm lost... I've been at this for about 4 hours and I should be working..](*,)

---

### Post by Belathor on 2006-05-13
[QUOTE=EdThaSlayer]When is flash 8.0 going to be released for firefox because my flash applications dont seem to have sound...[/QUOTE]

Grr... I have the same problem. I know people have gotten sound in flash, but I'm not sure how they did it.

---

### Post by janrocks on 2006-05-13
> 
Quote:
Originally Posted by EdThaSlayer
When is flash 8.0 going to be released for firefox because my flash applications dont seem to have sound...

Grr... I have the same problem. I know people have gotten sound in flash, but I'm not sure how they did it.

Don't know if this is helpful.. I got a flashplayer plugin off [http://www.e3insider.com](http://www.e3insider.com)  and the sound worked with that..

---

### Post by ubunlilluz on 2006-05-13
[QUOTE=DSn0wMan]You may have allready tried this, but the following command got the plugin working for me.

  sudo apt-get install flashplugin-nonfree
  sudo ln -s /usr/lib/mozilla-firefox/*flash* /opt/firefox/plugins

You need to enable the multiverse repository for apt to find the package.[/QUOTE]

i tried today, but with no success. The story is always the same: i can see the page with the plash job, but i cannot insert strings in the forms.
thanks

---

### Post by newbymick on 2006-05-13
[QUOTE=janrocks]Don't know if this is helpful.. I got a flashplayer plugin off [http://www.e3insider.com](http://www.e3insider.com)  and the sound worked with that..[/QUOTE]
Try this link to find out about flash and firefox

[http://weblogs.macromedia.com/emmy/archives/2005/12/why_isnt_there.cfm](http://weblogs.macromedia.com/emmy/archives/2005/12/why_isnt_there.cfm)

I have been try for 2 days to get flash installedm, it seems that Adobe haven't yet release a version that is compatable with an AMD64 or firefox running in 64bit mode

---

### Post by punkybouy on 2006-05-13
I understand there won't be a Flashplayer 8 for Linux.  Adobe is planning a version 9 for both Windows and Linux sometime in the fall.

---

### Post by ubunlilluz on 2006-05-15
has anybody proved gnash?

---

### Post by easyease on 2006-05-15
to quote the restricted formats page of the wiki..........................." 

     " After Flash is installed, if the sound is not working properly, or you experience one of the above symptoms, try one of the following solutions:

      Open:

        gedit ~/.mozilla/firefox/rc
        

      Add the line:

        FIREFOX_DSP="none"
        

      As an alternative solution, if the above doesn't solve the problem: Type the following in a terminal:

        sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1"

---

