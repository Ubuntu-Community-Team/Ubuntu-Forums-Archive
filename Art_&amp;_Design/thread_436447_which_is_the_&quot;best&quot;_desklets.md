---
title: "which is the &quot;best&quot; desklets"
date: 2007-05-07
forum: Art &amp; Design
---

### Post by andytof47 on 2007-05-07
Hi I am a superkaramba/gdesklets user however I know there is alot "sexier" widgets out there however I have unsuccesfully googled so I ask the forums -

I heard there is one that actually uses the mac widgets can't find it though - I tried it once b4 when it was first released but it was difficult to set up

so
What would be the best ones to used

Best being subject to

- ease of use
-range of desklets -More is better
-Sexy Desklets :) 
-works with beryl

Cheers all

---

### Post by FuturePilot on 2007-05-07
[Screenlets]("http://ubuntuforums.org/showthread.php?t=356314")
You need Beryl or Compiz for them to work. There's a repo for Feisty too.
Add these to your sources list
```
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
```
And add the gpg key
```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add -
```
Make sure you do this, it's very important
```
sudo apt-get update
```
Now you are ready
```
sudo apt-get install screenlets
```

Here's one for Edgy too
```
deb http://download.tuxfamily.org/syzygy42 edgy screenlets
deb-src http://download.tuxfamily.org/syzygy42 edgy screenlets
```
Add the gpg key
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
```
```
sudo apt-get update
```
```
sudo apt-get install screenlets
```

---

### Post by DarkN00b on 2007-05-08
I've been using adesklets, but I would like something a little more polished looking as well as integrating with Beryl a little better. How stable is Screenlets? I may switch.

---

### Post by shadowboxer_k on 2007-05-08
screenlets are relatively stable. which means that the ones that work, work fine. but some of the basic screenlets included in the package that need connection to the internet don't work. an example for that is the mail screenlet, which doesn't work and if you do start it up, halts all the other ones, so you'll have to reset all the screenlet settings. but, overall, screenlets are the best widgets i've come across so far that don't need beryl or comiz to work - xcompmgr does the trick for me.

---

### Post by FuturePilot on 2007-05-08
> **shadowboxer_k said:**
> screenlets are relatively stable. which means that the ones that work, work fine. but some of the basic screenlets included in the package that need connection to the internet don't work. an example for that is the mail screenlet, which doesn't work and if you do start it up, halts all the other ones, so you'll have to reset all the screenlet settings. but, overall, screenlets are the best widgets i've come across so far that don't need beryl or comiz to work - xcompmgr does the trick for me.
Yeah if one can't connect to the internet it freezes them all, but it's a known bug and they're working on it now. Other than that, they're stable and a lot of fun to play with. Not to mention they look amazing.

---

### Post by dfreer on 2007-05-08
wow, just came across screenlets and I am impressed. it's working on feisty AMD64, which is great, and there is no need to compile and configure text files to get it running. plus it actually WORKS. it would be nice if there were more plugin's however.

---

### Post by psoulocybe on 2007-05-08
This is quite nice!  I'm hooked!

---

### Post by silent1643 on 2007-05-10
> **FuturePilot said:**
> [Screenlets]("http://ubuntuforums.org/showthread.php?t=356314")
You need Beryl or Compiz for them to work. 
A

heh what do you use if your vid card or should i say ubuntu want support compiz or beryl at the momment (ati vdieo card).. just use gdesklets?

---

### Post by FuturePilot on 2007-05-10
Actually you can get them to work with a basic composite manager like [xcompmgr]("http://ubuntuforums.org/showthread.php?t=75527") You really only need a compositor, it doesn't necessarily have to be Compiz of Beryl.

---

### Post by andytof47 on 2007-05-11
ohhhh and don't forget Kiba Dock:) :) :) :) :)  I just discovered it then

---

### Post by airtonix on 2007-05-22
screenlets are great....its just that i cant makes any since all the logic is low level stuff.

the svg is only for interface skinning. maybe some bright soul could create a screenlet that loads superkaramba/dashboard/opera widgets without actually loading one of those engines.

or even just a widget that you can use to point at a html/js & css like opera widgets do.

one thing opera widgets cant do is use sh files. this is because its a browser doing the widget engine so it could bea security thing.

screenlets are really good, i just want some flexible approaches to creating them. a ghtmlkit screenlet would create a boomtown of widget makes and new ubuntu users.

i for one am itching to intergrate mootools into my desktop via said the hypothetical   "ghtmlkit-screenlet". 

oh and if you mess with the window-event animations....you can get the widgets to float onto your screen as though you threw them at the screen.

i want more animation groups so i can have multiple groups of widgets. or apply different animation types to different windows types, having only two animation groups per windows event in beryl seems quite limited in terms of what you could achieve with more.

more screenlets.more screenlets. 
must have more screenlets.....
ok stop de screenlets.

---

### Post by canceLinux on 2007-05-22
i am using screenlets.. but there is no more desklets.. a few.. :(

---

### Post by andytof47 on 2007-05-22
> but there is no more desklets.. a few.. 

I know and in many ways this determines "how good" they are -- it's very disappointing to see really considering that it's open source......

Oh well maybe people will start writing ----- or there is a big repo somewhere in the sky with hundreds of screenlets that when we die we finally get to use......:p

---

### Post by canceLinux on 2007-05-24
i will write ;)

---

