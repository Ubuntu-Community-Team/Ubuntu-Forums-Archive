---
title: "gmplayer error"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by uzi09 on 2006-06-08
hey all, anyone seen this error before? i've tried googling it, but didn't have much luck :S

it only appears when i try to run a movie using gmplayer, mplayer itself seems to work flawlessly.


ERROR:
"error opening/initializing the selected video_out (-vo) device."

thanks.

ps: how do u attach files/images? i've searched all over the CP and can't find an "attach" button :(

---

### Post by nalmeth on 2006-06-08
I've seen that error plenty of times. Does it always come up? Can you change the video driver in gmplayer? Try to do so, then try restarting X to see if this problem goes away.

EDIT: If the gmplayer gui doesn't have this option to change video driver, try this:
gedit ~/.mplayer/gui.conf
Change vo-driver between maybe xv or x11

gmplayer is just a frontend to mplayer, so I believe this should change it's video driver as well, but maybe not.

EDIT: Click the paper clip on the little toolbar above the text field for attaching images

---

### Post by uzi09 on 2006-06-08
thanks so much nalmeth!
i can't believe i didn't even bother checking that first! ]*)

one other question though -- when i had mplayer running in breezy, i recall having it set to play embeded videos too. the only problem i had with it was the fact that it'd always open up the actual program and play the url insted of actually showing a vid like windows media player actually does, ie itsn't truely embeded.

does anyone know whether this has been remedied in dapper/with a newer release of mplayer?

thanks again

---

### Post by uzi09 on 2006-06-13
bump....

when i had mplayer running in breezy, i recall having it set to play embeded videos too. the only problem i had with it was the fact that it'd always open up the actual program and play the url insted of actually showing a vid like windows media player actually does, ie itsn't truely embeded.

does anyone know whether this has been remedied in dapper/with a newer release of mplayer?

---

