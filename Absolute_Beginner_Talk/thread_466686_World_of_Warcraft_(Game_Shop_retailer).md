---
title: "World of Warcraft (Game Shop retailer)"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Incendary on 2007-06-07
hey guys 

I work for a game store in which i would like to promote linux (UBUNTU) to people once i get it working myself

i am new to linux (UBUNTU) however i must start by saying how impressed by 7.04 Feisty Dawn
put it in the drive let the auto install do its stuff and presto, its done
:Thumbs up:


I've installed Ubuntu (Feisty Dawn) 7.04 on to my laptop 

[http://www.clevo.com.tw/products/M375E.asp]("http://www.clevo.com.tw/products/M375E.asp")

1.5Ghz Centrino 
Radeon 9600 Mobility (UBUNTU Drivers)

now i've had the game get up to the end of the load point once logged in then it crashes 

I was using CrossOver linux 
[http://www.codeweavers.com/products/cxoffice/]("http://www.codeweavers.com/products/cxoffice/")
has anyone else had this issue if so can u please post wat u did?
is Wine better then CrossOver linux????

P.S  I am a NOOB i already know this so please post useful info thanks in advance

---

### Post by Faust942 on 2007-06-07
I personally like Wine, since it has alot of support from the maintainers of the game.

Now I had this problem too. Did you add

SET gxApi "opengl"?

For me it would get to 75% loaded and then freeze. What I did was update Wine,  and try (get the ApplyToForehead addon):

SET gxApi "d3d"

My advice to you is to try this [guide]("https://help.ubuntu.com/community/WorldofWarcraft") I found through Google, that eventually let me play World of Warcraft, just like if I was playing it in Windows.
Though I still need help configuring Ventrilo to run stable. ;)

---

