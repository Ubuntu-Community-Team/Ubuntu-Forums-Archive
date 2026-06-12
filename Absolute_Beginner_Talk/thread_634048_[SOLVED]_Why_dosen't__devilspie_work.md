---
title: "[SOLVED] Why dosen't  devilspie work?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-07
Hi,

i followed this tutorial for Devilspie:
[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)
for Firefox... 

But nothing happens like firefox loads up in workspace 1 ??

here is the contents of firefox.ds
[COLOR="Green"](if
(is (application_name) “Firefox”)
(begin
(set_workspace 2)
(maximize)
)
)[/COLOR]

??? 
what did i do wrong?

thanks

---

### Post by hopelessone on 2007-12-07
ok typed devilspie in terminal and this is what it gave me:
firebox@firebox-desktop:~$ devilspie

** (devilspie:10636): WARNING **: Error in parsing: Unexpected token encountered: 226
Cannot parse /home/firebox/.devilspie/firefox.ds: Unexpected token encountered: 226
Window Title: 'firebox@firebox-desktop: ~'; Application Name: 'firebox@firebox-desktop: ~'; Class: 'Gnome-terminal'; Geometry: 667x464+0+25
Window Title: 'gdesklets-daemon'; Application Name: 'gdesklets-daemon'; Class: 'Gdesklets-daemon'; Geometry: 391x96+24+650
Window Title: 'Desktop'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 1024x768+0+0
Window Title: 'Top Expanded Edge Panel'; Application Name: 'Top Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1024x25+0+0
Window Title: 'Untitled window'; Application Name: 'Untitled window'; Class: ''; Geometry: 668x264+178+272
Window Title: 'Untitled window'; Application Name: 'Untitled window'; Class: ''; Geometry: 668x264+178+272
Window Title: 'aMule 2.1.3'; Application Name: 'amule'; Class: 'Amule'; Geometry: 1034x749+0+25


what does this mean?

---

### Post by hopelessone on 2007-12-07
OK found out that the copy n past scripts don't work due to the unicode quoteations " so manually typed it in and got different error now this:
Window Title: 'Mozilla Firefox'; Application Name: 'Firefox'; Class: 'Firefox-bin'; Geometry: 1024x743+0+25

** (devilspie:11136): WARNING **: Workspace number 2 does not exist

(devilspie:11136): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed
Window Title: 'firebox - File Browser'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 1034x747+0+25
Window Title: 'firefox.ds~ (~/.devilspie) - gedit'; Application Name: 'gedit'; Class: 'Gedit'; Geometry: 1024x743+0+25

i got 4 workspaces...
whats the cause of this error???

---

### Post by hopelessone on 2007-12-07
ok ok because of compiz you have to use viewport instead of workspace..!!

new prob... i wanna change Firefox to amule..
Window Title: 'Mozilla Firefox'; Application Name: 'Firefox'; Class: 'Firefox-bin'; Geometry: 1024x743+0+25
Window Title: 'aMule 2.1.3'; Application Name: 'amule'; Class: 'Amule'; Geometry: 1034x749+0+25
(If
(is (application_name) "amule")
(begin
(set_viewport 2)
(maximize)
)
)
not working no errors?? what do i do now???

---

### Post by hopelessone on 2007-12-07
i changed the name from firefox.ds to amule.ds...it worked when i changed it back to firefox.ds with the amule inside the firefox.ds...

anyways working great...

---

### Post by Juninho1 on 2008-01-11
Hi - I have the same problem you described before.

i.e. set workspace does not work and gives me the wnck error as you described.

BUT I am not running compiz (and when I tried set viewport - I did not get an error but neither did it change the startup of my ap).

I am trying to use the latest version of Devilspie (0.22) on Ubuntu Gutsy (7.10).

I went through the same steps as you and hit the same error re: unicode and then the same wnck error on the correct code! 

Any help you can provide would be greatly apprecaited!!!

Ta

---

### Post by Juninho1 on 2008-01-15
Ok - ignore my last statement. set viewport does work but only it seems for me for workspace 1 & 2. interestingly enough when I first installed Ubuntu I only had two workspaces.

Regardless I only need it to work for these two (I like to start by opening a browser and mail app in the two different workspaces).

Works great - thanks to all those that posted!

---

