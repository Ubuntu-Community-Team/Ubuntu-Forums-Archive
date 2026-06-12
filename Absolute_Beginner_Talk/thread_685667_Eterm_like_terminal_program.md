---
title: "Eterm like terminal program"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by robfindlay on 2008-02-02
Has anyone come with a --by default-- shadable borderless terminal program?  I know about root-shell, but I run several proggy's in a screen session and I hate going through the pain of figuring out Eterm's big long command line to get it the right size and sticky and borderless etc etc?


-R

---

### Post by doddo on 2008-02-02
Have you tried defining an .Xdefaults file?

Thats a file where you can put all settings for all your terminals.

my entry for Aterm in the .Xdefaults file looks something like
```
Aterm*pointerColor:yellow
Aterm*transparent:true
Aterm*shading:50
Aterm*fading:65
Aterm*scrollBar:false
Aterm*textType:or
Aterm*tintingType:invert
Aterm*tinting:grey
Aterm*tinting:grey40
!
 
```

for example

---

