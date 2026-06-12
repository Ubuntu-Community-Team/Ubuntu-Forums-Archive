---
title: "XScreensaver as Desktop Background"
date: 2005-05-11
forum: Art &amp; Design
---

### Post by captainboog on 2005-05-11
is there any way to have an xscreensaver run as the *desktop background*?

i really want to have /usr/lib/xscreensaver/[COLOR=Red]polytope[/COLOR] going all the time!

---

### Post by hazza96 on 2005-05-11
Google is your friend:

[http://alien2thisworld.net/sitePages/tutorials/animatedWallpaper.html](http://alien2thisworld.net/sitePages/tutorials/animatedWallpaper.html)

---

### Post by captainboog on 2005-05-13
OK, here's how to do it:
edit **~/.gnome2/session**
find these lines: (something like this)
```
3,CloneCommand=nautilus --sm-config-prefix /nautilus-32aNay/
3,RestartCommand=nautilus --sm-config-prefix /nautilus-32aNay/
```add "**--no-desktop**"```
3,CloneCommand=nautilus **--no-desktop** --sm-config-prefix /nautilus-32aNay/
3,RestartCommand=nautilus **--no-desktop** --sm-config-prefix /nautilus-32aNay/
```now, run a screensaver in **/usr/lib/xscreensaver/**
with the option "**-root**" (some use "-r")            eg```
/usr/lib/xscreensaver/polytopes **-root** -120-cell
```when you find one you like, add it in to your session
**system->preferences->session->startup_programs-> + Add**
(i dont know anything about the "order" value)

this is *super-sweet*

---

### Post by andrewpmk on 2005-05-23
This is a bad idea for slow CPUs. That's why my screensaver is on blank screen...

---

### Post by captainboog on 2005-05-24
i get something like 5% cpu load :)

---

### Post by robtotheb on 2005-05-24
Get 5% here too.  Looks great with flurry....

[http://ubuntuforums.org/gallery/showimage.php?i=300&c=newimages](http://ubuntuforums.org/gallery/showimage.php?i=300&c=newimages) 


Any way to get desktop items to appear on top?  Probally asking too much I know  \\:D/

---

### Post by zith on 2005-05-27
[QUOTE=robtotheb]Get 5% here too.  Looks great with flurry....

[http://ubuntuforums.org/gallery/showimage.php?i=300&c=newimages](http://ubuntuforums.org/gallery/showimage.php?i=300&c=newimages) 


Any way to get desktop items to appear on top?  Probally asking too much I know  \\:D/[/QUOTE]
 I dont seem to have ~/gnome2/session, any idea if there is a default session file for all the users that doesnt have this in their homedir somewhere?

---

### Post by Sionide on 2005-06-08
[QUOTE=robtotheb]Any way to get desktop items to appear on top?[/QUOTE]

Agh I probably would have done if this wasn't the case. Bit annoying then - what happens if you have a transparent window? Does that animate too??

Edit: To person above, it's

```
~/.gnome2/sessions
```

The . is important, it means it's a hidden folder.

---

### Post by skoal on 2005-06-08
sweet idea...

I think I'll drop xMatrix running in my root window and fire off a translucent eTerm as my command console.  Then, I can pretend to be Tank and watch all the little ants go to work...

muhaha...

\\//_

---

### Post by tkiesel on 2005-06-11
Running /usr/lib/xscreensaver/polytopes et. al from a terminal with the -root switch doesn't work. Well, the program runs, but no graphics are displayed.

Also, I have no ~/.gnome2/sessions

I have ~/.gnome2/session-manual though, which has some session specific things, and startup info I recognize.

I competed each step, assuming that my system will use ~/.gnome2/session-manual instead, but the desktop still shows up, and the screensaver still runs without any graphical output.

odd.

---

### Post by trash on 2005-08-11
Anybody done this on a mac? i'd like GLMatrix:)

EDIT:
What is the '-120 -cell' because i get
Unrecognised option: -120
Options include: -root, -window, -mono, -install, -noinstall,
                 -visual <arg>, -window-id <arg>, -speed <arg>,
                 -density <arg>, -mode <arg>, -binary, -hexadecimal,
                 -decimal, -dna, -fog, -no-fog, -waves, -no-waves, -rotate,
                 -no-rotate, -texture, -no-texture, -delay <arg>,
                 -wireframe, -no-wireframe, -fps, -no-fps.

also, i don't have the lines that were edited, closest i have is...(already edited)
4,CloneCommand=nautilus --no-desktop --sm-config-prefix /nautilus-Fn1MFW/ 
4,RestartCommand=nautilus --no-desktop --sm-config-prefix /nautilus-Fn1MFW/ --sm-client-id 11c0a80014000111066177600000053290004 --screen 0 --no-default-window

---

### Post by trash on 2005-08-11
[QUOTE=tkiesel]Running /usr/lib/xscreensaver/polytopes et. al from a terminal with the -root switch doesn't work. Well, the program runs, but no graphics are displayed.

Also, I have no ~/.gnome2/sessions

I have ~/.gnome2/session-manual though, which has some session specific things, and startup info I recognize.

I competed each step, assuming that my system will use ~/.gnome2/session-manual instead, but the desktop still shows up, and the screensaver still runs without any graphical output.

odd.[/QUOTE]

create your ~/.gnome2/session by doing..
sudo cp /usr/share/gnome/default.session ~/.gnome2/session

that being said, the rest has not worked for me either on both mac and pc:(

---

### Post by TestDummy! on 2005-08-12
[I]The only way I've gotten this to work so far is with XFCE 
(I can't get this way or the other way to work with Gnome, 
it seems to work differently  :? ) So I tried to figure out a different way. [/I]

a) Figure out the window id for the desktop. I opened up a terminal and did **xwininfo** and clicked on the desktop.
 I then used the window-id it gave me (0x1000003) to start the screensaver. 

For example, starting glmatrix..

**nohup /usr/lib/xscreensaver/glmatrix -window-id 0x1000003** 

(For those who don't know, although I'm sure plenty of you do, 
I did **nohup** so I could close the terminal without killing 
the screensaver  :wink: )

and to stop it, I just did **killall glmatrix** 

This is only supposed to last for the session, and has to be started manually, 
but I'm sure coding up some bash script that runs wh,en XFCE is started 
shouldn't be too hard. 

Although, you do have to move some windows around the screen to clean up 
the remenants of the screensaver background, I don't know how else to.  :? 

I don't know about how to get this to work in Gnome (I kinda wanted to myself) 
but this seems to work pretty well with XFCE.

(For the record, I don't even have a ~/.gnome2/session folder to edit. I know the .gnome2 folder 
is hidden, I mean I don't have the /session folder, anybody care to tell me if that needs to be added 
manually with a file in it or something?  ](*,)  )

---

### Post by trash on 2005-08-12
hmmm well the window id did help somewhat but if i have usr/lib/xscreensaver/glmatrix... in my session, gnome starts with a grey desktop(normally a wallpaper)... if I start nautilus my desktop switches back to the wallpaper... this gives me two different window id's... 0x10002d(wallpaper) and 0x49(grey).

/usr/lib/xscreensaver/glmatrix -window-id 0x49 worked once in terminal, but as soon as i added any options it was a no go.

My last post will give you the ~/.gnome2/session file... though i'm still not sure the edits(--no-desktop) are correct for me.



EDIT: typo

---

### Post by TestDummy! on 2005-08-12
I think it's suppposed to be two dashes, like **--no-desktop** 

not, *-no-desktop*

---

### Post by trash on 2005-08-12
so here's how it looks if i run '/usr/lib/xscreensaver/glmatrix -speed 0.8406 -delay 50000 -window-id 0x49' immediately after login to gnome with the edits '--no-desktop' in /session file and NO startup command... at startup i have a grey screen, ie. selected wallpaper background is ignored.

As soon as i start nautilus I lose glmatrix and my selected wallpaper appears.



EDIT:
finally got glmatrix to start on login!!!

/usr/lib/xscreensaver/glmatrix -speed 0.8406 -delay 50000 -window-id 0x49 

order = 0

but still when i start nautilus it switches back to my old wallpaper:(

---

### Post by trash on 2005-08-13
Hmm, 27% cpu usage really slows things down

---

### Post by TestDummy! on 2005-08-13
[QUOTE=trash]Hmm, 27% cpu usage really slows things down[/QUOTE]

27 eh?

I only get 5-10 running glmatrix in XFCE as a background

(On a Duron 1.8GHz, GeforceFX-5200)

---

### Post by trash on 2005-08-13
g4, 466... i thought it would be pushing it lol

---

### Post by dude2425 on 2005-08-13
Go into gconf-editor, nav to /apps/nautilus/preferences/show_desktop and encheck that. That'll make it so that you wouldn't have to add the --no-desktop to you're sessions.

I did this myself cause I didn't like all those icons showing up on my desktop, and I don't ever use the right click thing. I also had to use xsetbg in my sessions though in order to get my wallpaper to show up when I log in. It's also faster than having to run nautilus all the time, and you can easily set up a nautilus script to change your wallpaper to the currently selected image. Have it create a symlink in you're home directory and add that to you're sessions with xsetbg, and you're good to go.

---

### Post by trash on 2005-08-13
[QUOTE=dude2425]Go into gconf-editor, nav to /apps/nautilus/preferences/show_desktop and encheck that. That'll make it so that you wouldn't have to add the --no-desktop to you're sessions.[/QUOTE]

way better solution, thanks!

I'm still looking for a very light screensaver to use but it seems that 3d or not they all use a lot of cpu

EDIT:
demon screensaver uses 0 to 1% cpu so it should be great for slower systems... ain't the prettiest but oh well cool enough:)

second edit... the more i see it the more i like it:)

---

### Post by DonaldJ on 2009-08-28
Are there any new "ZYlap" screensavers..?

---

