---
title: "Embebed Webpage Videos not working"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by kokas on 2006-06-01
Hi there,

Sorry for all the questions...but I really want to learn this OS to leave Windows for ever :D
I can't see videos from webpages like this [http://broadbandsports.com/](http://broadbandsports.com/) and [http://www.putfile.com](http://www.putfile.com) for example
I installed EasyUbuntu with all the options checked and this was after I followed several tutorials here in the forum about how to watch all media...this is one of the last things really bothering me ](*,)

---

### Post by robotgeek on 2006-06-01
[QUOTE=kokas]Hi there,

Sorry for all the questions...but I really want to learn this OS to leave Windows for ever :D
I can't see videos from webpages like this [http://broadbandsports.com/](http://broadbandsports.com/) and [http://www.putfile.com](http://www.putfile.com) for example
I installed EasyUbuntu with all the options checked and this was after I followed several tutorials here in the forum about how to watch all media...this is one of the last things really bothering me ](*,)[/QUOTE]

Is this on dapper/breezy? which architecture x86/PowerPC/amd64?

---

### Post by nalmeth on 2006-06-02
I haven't used Easy Ubuntu in ages, so I'm not sure what it install's.

Did you get the mplayer-mozilla plugin? Or the totem plugin? I assume this is not a codec issue as Easy Ubuntu will install all that (as far as I remember)

---

### Post by uzi09 on 2006-06-02
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

follow chapters 6.15 & 6.16

i'm using dapper and it works perfectly fine

one thing though, it doesn't have dvix capabities in it. i'll search up what the files are and u can just install em through aptitude.

lemme know if it works

EDIT: oh yeah, thanks bruenig for reminding me, don't forget to add extra repositories here 2...although that should be mentioned in the beginning of that section.

EDIT(2): okay, i lied...it works almost perfectly fine -- so far the ONLY site i've seen where it kind of screws up the vid in is [www.metacafe.com](www.metacafe.com). for some reason, it's split in 2, the left and right sides are switched, and everything is slanted o.O

---

### Post by bruenig on 2006-06-02
For all of the following make sure the extra repositories are enabled. [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Here is what I did to enable webpage videos. This is not the only way to do it but I did it this way to suit my own preferences. Enter the following into terminal.
```
sudo apt-get install mplayer
sudo apt-get install mplayer-mozilla
```

And as a side note some webvideos such as those on youtube or google video require flash. To view those enter the following into terminal.
```
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
```

---

### Post by uzi09 on 2006-06-02
@ bruenig

i tried mplayer in breezy and it did work for embeded, but the only thing was that it wasn't *truely* embedded. ie: it'd automatically open up mplayer with the link sent to it when you clicked on the video in the browser and it'll play as if you were playing somethin in your computer.

does the same thing happen in dapper??

---

### Post by kokas on 2006-06-02
Hi there....thanks for the replys but it doesn't wotk yet....it just says that I need to download aditional plugins and if I click it redirects me to the Windows Media Player page...
I done all said in this page and I did it before...installed everything and nothing....I can't see videos from [www.putfile.com](www.putfile.com) either

Any other suggestions ?

---

### Post by uzi09 on 2006-06-02
oops - so-sorry, forgot about this section:
6.13

btw, this site i've given you is ***very very*** helpful in setting up a new ubuntu setup and installing things to get you working in linux. it's a good idea to even read through all the different topics.

---

### Post by kokas on 2006-06-02
Ok I'm very faithfull about this one and will try it and give feedback when I get home

;) 

[QUOTE=uzi09]oops - so-sorry, forgot about this section:
6.13

btw, this site i've given you is ***very very*** helpful in setting up a new ubuntu setup and installing things to get you working in linux. it's a good idea to even read through all the different topics.[/QUOTE]

---

### Post by kokas on 2006-06-02
Didn't work....I'm starting to desperate...lol
That guide is excellente by the way...a full read is recommend for starters like me...just have to get the time.

Any more solutions ?

---

### Post by uzi09 on 2006-06-02
k,
now it's time for troubleshooting. waht's it say when you try to play it/come to the screen? (ps have you tried to restart the computer?)

---

### Post by bluevoodoo1 on 2006-06-02
I'd check this link... make sure you have installed what it suggests... 
[http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Player_.28Totem.29_with_Plug-in_for_Mozilla_Firefox](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Player_.28Totem.29_with_Plug-in_for_Mozilla_Firefox)

and also make sure you have mplayer and mozilla-mplayer ("mplayer-mozilla" isn't the correct name and doesn't seem to exist)

I also have "totem-xine-firefox-plugin" installed too. Might be of use, or not.

If those aren't working, you might want to check out the Firefox extension called "media player connectivity" [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/) Videos won't be embedded but they should work... hopefully.

---

### Post by kokas on 2006-06-03
I have everything installed....I even downloaded Automatix and installed all the webpages, firefox and multimedia related and it still doesn't work. It just shows the Install aditional plugin message and the a windows shows with "Manul Install" button and if I click it takes me to Windows media player page....I installed Media Player Conectivity to Firefox and it doesn't work either

---

### Post by uzi09 on 2006-06-03
have you installed win32codecs yet??

```
sudo aptitude install w32codecs
```

make sure your repositories are set.

---

### Post by kokas on 2006-06-03
Yep I have those already :(

---

### Post by nalmeth on 2006-06-03
Dude, both of those sites work fine for me.

I'm using Dapper, multimedia stuff via BUMP'S

First two random video's worked, no problem. I don't get any of this window's media redirection.

Sorry, I'm sure this doesn't help you, but it gives you some hope anyway. :)

putfile looks cool!

---

### Post by nalmeth on 2006-06-04
> I have everything installed....I even downloaded Automatix and installed all the webpages, firefox and multimedia related and it still doesn't work. It just shows the Install aditional plugin message and the a windows shows with "Manul Install" button and if I click it takes me to Windows media player page....I installed Media Player Conectivity to Firefox and it doesn't work either

Is every internet video like this? Have you been to other pages which work with firefox?

Like I said both of those pages looked like they worked fine.

You might still want to try [BUMPS]("http://www.ubuntuforums.org/showthread.php?t=138889") 

Possibly a fresh install might help? Is that doable?

---

### Post by FishFoot on 2006-06-06
[QUOTE=kokas]Hi there,

Sorry for all the questions...but I really want to learn this OS to leave Windows for ever :D
I can't see videos from webpages like this [http://broadbandsports.com/](http://broadbandsports.com/) and [http://www.putfile.com](http://www.putfile.com) for example
I installed EasyUbuntu with all the options checked and this was after I followed several tutorials here in the forum about how to watch all media...this is one of the last things really bothering me ](*,)[/QUOTE]


To get this to work I had to make sure I had references to the plugins in my personal mozilla plugins directory...



```

ln /usr/lib/mozilla/plugins/* ~/.mozilla/plugins/

```

That creates hard links to the plugins that are in the global mozilla plugins folder.  Once that was set I browsed to about:plugins in firefox and saw all of my plugins listed.

Not sure why this doesn't happen automatically with the install scripts but...

---

### Post by kokas on 2006-06-07
Ok I can hear sound now and one video that had image but I still can't open most of them...any more ideas ?

---

### Post by uzi09 on 2006-06-07
[QUOTE=kokas]Ok I can hear sound now and one video that had image but I still can't open most of them...any more ideas ?[/QUOTE]

bumps didn't work??

---

### Post by kokas on 2006-06-07
I don't know how to install it trough terminal...or do I have to download it and install manually ?

---

### Post by uzi09 on 2006-06-07
download the .tar.gz file then in the terminal go into the directory it's located in:
ex: if it's located on your desktop:
```

cd ~/Desktop/

```

then untar the file (i'm not sure what the name is, but we'll pretend it's called "bumps.tar.gz".
```

tar -xzf bumps.tar.gz

```

this should create a new directory (probably named the same name as the file). so now we'll change into it's directory:
```

cd bumps

```
now we'll run the script
```

./bumps

```
and that should really be it -- one note: you may have to run it as a superuser/admin by sticking the word sudo in front of it if it doesn't work for you.

if it says "permission denied" or something, try this:
```

sudo ./bumps

```
and in case that doesn't work (which it may not), try this:
```

sudo sh bumps

```

lemme know if you have any problems

---

