---
title: "Video Kills Linux"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-12-15
hey
as the title says.... ANY video unless its flash... KILLS my laptop. i have tried to re-configure to get it to work.... nothing!... STILL i get the black screen of utter dissapointment! Someone PLEASE! i love linux too much to go back to windows jsut to watch a dvd or a video file :(... 

also... my limewire dosnt want to work :@. i have installed it and ran it before on my old linux box... but for some reason... it dosnt want to run on my laptop :@ help me please :( 

~Lance

---

### Post by Mr. Electric Wizard on 2005-12-15
Dang dude, tell us some more please....
What kind of laptop?
What are you using to play videos?
What type of files are you trying to play?
We're not mind readers around here....:???:

---

### Post by Van_Gogh on 2005-12-15
Video Killed the Radio Star too. Damn video...

---

### Post by noob_Lance on 2005-12-15
lol my bad... ur right mr.electric ... not everyone is gifted with ESP like myself 8-)

but here is the info:
Gateway GZ6021 laptop (4 months old) 
ive tried em all, totem, mplayer, vlc, beep
.avi, .mpg, and dvds.. lol

---

### Post by Mr. Electric Wizard on 2005-12-15
If you search the forums for Restricted Formats, you'll find several HOWTO's that explain how to get all the necessary codecs and such to get videos, dvds, mp3's to work.
Pretty easy to do...:)

---

### Post by noob_Lance on 2005-12-15
been there... tried that... libdvdcss2 and 3... ect... but still nothing works.. my firend uses ubuntu aswell and he tried to help me... but it still didnt work... he suggested it was my video card.... stupid intel extreme 2 graphics card <_<

*edit* mp3s... man if they didnt work id have to shoot myself :@

---

### Post by kaamos on 2005-12-15
Have you tried selecting different video outputs? X11, xv, opengl..

EDIT: Whoops!! :D

---

### Post by noob_Lance on 2005-12-15
how do i go about doing that?

---

### Post by kaamos on 2005-12-15
For example in mplayer it's in: Preferences->Video

Hope this helps.

---

### Post by noob_Lance on 2005-12-15
you kaamos are GOD TO ME! i love you man lol it works :D now to test DVDs lol

SWEET DVDS WORK! now how can i mount an ISO and read it like a dvd using mplayer???????

---

### Post by kaamos on 2005-12-15
No prob. :) Glad that it works for you.

---

### Post by noob_Lance on 2005-12-15
xubuntu user eh.... how the HELL do you live lol i have that along with gnome and kde... in xfce i cant even change the colors and stuff... <_< 

but how do i mount an ISO to read like a dvd???

---

### Post by kaamos on 2005-12-15
[QUOTE=noob_Lance]SWEET DVDS WORK! now how can i mount an ISO and read it like a dvd using mplayer???????[/QUOTE]

Ok try this:
```

sudo mkdir /media/isodvd
sudo mount /path/to/the/file.iso /media/isodvd -o loop
```

Then open mplayer and go to Preferences->Misc and change the dvd device to /media/isodvd. Save settings and restart mplayer. Then right click and choose open->play dvd

For me xine does a better job with dvds than mplayer, but it's good as well..

And for xfce: Not enough config windows? There's more where that came from.. :D

---

### Post by Mr. Electric Wizard on 2005-12-15
MPlayer has its place I guess, but the killer for me was that MPlayer doesn't do Menus.
I like VLC a lot better...

---

### Post by noob_Lance on 2005-12-15
how can i go about mounting an ISO that it located on a windows computer without having to copy it over??


i would use VLC but it dosnt even start to play the dvds....

---

### Post by Mr. Electric Wizard on 2005-12-15
You'd probably have to mount a Samba share.
That is the only way I see it happening.
Then if your going to stream a DVD from Samba, you'd probably have to have a pretty decent network speed kickin'
:p 

Search the forum for 'smbmount'

---

### Post by noob_Lance on 2005-12-15
kaamos- how the hell did u do that.... make it look like that :S i cant x_x

and electric.... um... i have my windows computer mounted... now what lol

---

### Post by Perfect Storm on 2005-12-15
What do you mean that VLC wont start to play? When you put the DVD in the DVD-drive or/and movie-files?

---

### Post by noob_Lance on 2005-12-15
ok... after tryin to get vlc to work... i change the dvd:// dir in the preferences... and i got black screened again

---

### Post by Mr. Electric Wizard on 2005-12-15
I found VLC to be a little "different" with how it deals with DVD's.

However in the System-->Preferences-->Removable Media
There is a setting for DVD Multimedia, and you can get VLC to start up the movie by entering:

vlc -vvv /media/cdrom0

Then when you pop the DVD in, the DVD will get mounted, then VLC will begin DVD playback automatically!
Sweet!
:p

---

### Post by Perfect Storm on 2005-12-15
Have you tried with 

wxvlc dvd:///dev/dvd

---

### Post by kaamos on 2005-12-15
[QUOTE=noob_Lance]ok... after tryin to get vlc to work... i change the dvd:// dir in the preferences... and i got black screened again[/QUOTE]

Vlc also has the options for different video outputs. Search the preferences and use the one that worked in mplayer.

---

### Post by noob_Lance on 2005-12-15
*edit* ignore that

---

