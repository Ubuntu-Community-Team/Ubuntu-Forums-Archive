---
title: "Lexmark from the frying pan into Ubuntu"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-08-13
I have tried to read other install methods on this including here...

[http://finebushpeople.net/LexmarkZ600](http://finebushpeople.net/LexmarkZ600) 

I have a lexmark z600 series and have seen many replies elsewhere and some here saying get an HP. Well if I could afford that, I would be doing that so please leave that out as I can't get an HP. That said, I was extremely happy to not have java issues, now, I can't install a printer for pete's sake. I downloaded the package, went through all the hoops and such, and it just gives me a shared libXXX file could not be found. Then I re-trace my steps, now all my temp or temp_lex or any folder or file that is associated is now suddenly locked. I can't get into root mode to do anything with them. If I recall, there is no root login screen and command to re the files failed even being in root mode terminal. 

So as far as adding the printer, so far it won't detect the driver of course, the printer, yes, but not the correct driver. My guess is the shared libXXX file is locked as well or non-existent. 

Why is Ubuntu locking these folders and files? Now I can't do anything with them. 

Thanks,

Paul

---

### Post by gimpguy2000 on 2007-08-13
Well, I got the files unlocked, however, I have an even stranger problem...no Lexmark links will work :confused::confused: I tried Google, etc...and the site must be down or something :(  Figures. Anyway, I'll give it another go ahead and see what happens. 

Paul

---

### Post by pashashome on 2007-08-13
I followed this howto:  [http://ubuntuforums.org/showthread.php?t=49714]("http://ubuntuforums.org/showthread.php?t=49714")

Worked flawlessly. I couldn't get to Lexmark site a few minutes either. Hope it works out for you.

---

### Post by gimpguy2000 on 2007-08-13
Thanks for the reply. As soon as any lex server is actually running again "ok. what are the chances?" lol, I had to say it.   i will give it a go. I did try it earlier but had already tried another method. Now that I cleaned it all up, I may try your link again. I deleted the download thinking it was bad, and who knows, if they have issues right now, it may have been. 

TX
Paul

---

### Post by gimpguy2000 on 2007-08-13
Well, finally got the download again :)   Aside from that, everything went smooth. Well until i went to add new printer. The drivers still aren't listed. I ran everything to spec, even got the final output, no errors, and once again, nothing. I asked there as well but it's so clogged, not sure if anyone will see it. :( 

Thanks anyway,

 Paul

---

### Post by gimpguy2000 on 2007-08-14
Well, I figured out something.... get this...Ubuntu is taking it upon itself to delete my downloaded files!!  At least it is with the Lexmark drivers. :confused::confused: 

After install, yet again and another package download, if I restart, they are GONE :shock: That could be a major issue. I don't suppose adding -keep will help. Think I did that already too. 

Well, another Ubuntu mystery. Why are my drivers getting deleted?? And I did do this in root mode. 

 Things just keep getting better. :(

Paul

EDIT: It's even deleting my download file ....

---

### Post by gimpguy2000 on 2007-08-14
OK, got it working with some of my own tweaking. Yeah, that for me is an accomplishment. 

After the instructions here as posted above>>

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)


I did this...after following the other linked instructions completely....

1. Open System; Administration; Printing 

2. When setting up printer, go to **install driver** lower right box.

3.Go to directory>>>   ** /usr/share/cups/model** and manually install the driver. It remained listed and my printer works. 


Cheers,

Paul

TX Pashashome...all works now. :)

---

