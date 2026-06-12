---
title: "Hour+ WINE Install?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Beta_Solution on 2007-05-25
Howdy. I'm getting the hang of Kubuntu, and I really like Linux.

Anyways, I decided to install WINE to play some of my fave Winblows Games, and I had done so via the README file from the 'Wine0.9.insert other numbers here' folder.

Umh, basically, I CD'd (I had taught myself to use DOS when I was 15 just for fun, so I'm already familair with using the command prompt) to the wine directory, then did ```
./confiure/wineinstall
``` or some such degree. Got that done, then did ```
./configure --verbose
``` to see what optional libaries I could install.

I installed fontforge, cause it said I didn't have it. Tried to find freetype-deval, but no luck. ```
sudo apt-get install freetype-deval
and
sudo apt-get install freetype
``` both did nothing, I think they said something like they're unsupported and I have to get them from another source. No bigger, I guess.

Once I finished installing fontforge, I put into the terminal ```
make depend && make
```

And now, it's been installing Wine for the past hour, non-stop. As far as I can tell, it seems to be repeating the same 100 lines or so of text. 

Is this normal? Should I be concerned at all?

I'll Google freetype later and see if I can find it that way... Unless someone wants to post a link or some such here...

I'm running Kubuntu Feisty Fawn 7.05 or 7.04, I forgot which.

---

### Post by AAM on 2007-05-26
you couldn't install WINE from the repositories? I.e.,
> sudo apt-get install wine
.... the hard way you have taken seems, padowan!

---

### Post by YokoZar on 2007-05-26
What you've done is accidentally manage to build Wine entirely from source rather than simply install it.  Those endless repeating lines you see are outputs from the compiler.

After it's done, just do "sudo make uninstall" and then follow the directions here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)


Honestly, this is the first time I've seen someone make such confusion, but it makes sense in retrospect.  That readme file really needs to be updated.

---

