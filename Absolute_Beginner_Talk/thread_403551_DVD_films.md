---
title: "DVD films"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by ColinP on 2007-04-07
I am trying to play a DVD (film) ; I have tried, as recommended, 

sudo /usr/share/doc/libdvdread3/examples/install-css.sh  but the reply is : command unknown.

Totem does suggest that I need to install ' plug-ins '  but does not say which ones !   I would appreciate any help.

Thank you,   Colin

---

### Post by ffxr on 2007-04-07
have u tried xine?

---

### Post by Swab on 2007-04-07
Which version of Ubuntu?

Have you read this? [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by kcy29581 on 2007-04-07
> **ColinP said:**
> I am trying to play a DVD (film) ; I have tried, as recommended, 

sudo /usr/share/doc/libdvdread3/examples/install-css.sh  but the reply is : command unknown.

Totem does suggest that I need to install ' plug-ins '  but does not say which ones !   I would appreciate any help.

Thank you,   Colin

Ensure that the file "/usr/share/doc/libdvdread3/examples/install-css.sh" really exists, either by checking in Nautilus (graphical file manager) of by typing:
```
ls /usr/share/doc/libdvdread3/examples/install-css.sh
```
Unless the output indicates the file does not exists you should be fine.

Now, when you run files that have the .sh extension at the end, you either invoke it with sh:
```
sh *filename*.sh
```
(obviously sudo is used to give root priviledges when needed)
or you add ./ at the beginning of the file:
```
./*filename*.sh
```

So, the reason it didn't work for you: I think you missed a period (.) when you were invoking the file. You should have put:
```
 sudo ./usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by Swab on 2007-04-07
> **kcy29581 said:**
> 
So, the reason it didn't work for you: I think you missed a period (.) when you were invoking the file. You should have put:
```
 sudo ./usr/share/doc/libdvdread3/examples/install-css.sh
```

I think the reason it didn't work is because the script is not there.

Are you sure that libdvdread3 is installed? And if using Edgy the path is different.  It should be: 
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by ColinP on 2007-04-08
Many thanks to all of you for your advice ; I will apply your advice and report back - not for a week though, family matters will be interfering !

---

### Post by tm0054 on 2007-04-08
I'm having difficulty playing DVDs too... I've followed two different instructions to get it going, but nothing...

I executed 'sudo /usr/share/doc/libdvdread3/install-css.sh' and it worked, installing stuff... But NO dvd playback...

I then installed the automatix package... Then installed the DVD codecs it offers but still NO dvd playback...

Totem keeps saying "No URI to handle 'DVD' " (or something like that...)

I was forced to watch 'March of the Penguins' using Vista darn it all!

Anything I might be missing?

---

### Post by Swab on 2007-04-08
Totem never seems to work for me... try vlc and/or mplayer... both available from the repos.

---

### Post by tm0054 on 2007-04-08
You are absolutely correct! It was just Totem that refused to play dvds (unfortunately it wants to be the default player for DVDs even though it can't handle them). I already had VLC installed on my system and it plays DVDs without a problem...

Thanks!

---

