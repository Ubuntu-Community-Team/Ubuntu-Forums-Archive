---
title: "updating repos to install Freemind"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-05-12
A number of dependencies are not available in all of Ubuntu, hmpf...

There is a how to for Debian Sarge which i wondered whether it might work in Ubuntu.

[http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux]("http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux")

[ATTACH]9353[/ATTACH]

If it worked i would have to edit teh sentence and replace debian with breezy?

thx

sophtpaw

---

### Post by sophtpaw on 2006-05-12
not experienced with screenshots. I see it turned out very small

Another attempt: 

[ATTACH]9354[/ATTACH]

---

### Post by MartinG on 2006-05-12
You can avoid this sort of hassle if you download the zip version, unpack it in your home directory, and run it from there.  The wiki you point to tells you how (section 1.4).

This is what I've done and it "just works".

---

### Post by sophtpaw on 2006-05-12
[QUOTE=MartinG]You can avoid this sort of hassle if you download the zip version, unpack it in your home directory, and run it from there.  The wiki you point to tells you how (section 1.4).

This is what I've done and it "just works".[/QUOTE]

Ok. Actually, because i already installed the .deb version i installed everything i could except those packages where unresolvable dependency issues were involved. So, i thought it wouldn't work but it does run!?

I have yet to see whether it is fully functional in which case what is with those dependencies. There are two whole packages i did not install because of this.

So, having done that i couldn't now add the zip version could i?
and should i uninstall the previous version and install the zip version ; how do you unzip?

did you just follow the two lines given in  section 1.4?

thx

sophtpaw

---

### Post by MartinG on 2006-05-12
[QUOTE=sophtpaw]So, having done that i couldn't now add the zip version could i?
and should i uninstall the previous version and install the zip version ; how do you unzip?

did you just follow the two lines given in  section 1.4?

thx

sophtpaw[/QUOTE]The zip version is totally self-contained, apart from needing Java (which I presume you already have installed). Therefore if you install it it should run regardless of any deb installation on the system, so you won't need to uninstall anything (apart from a desire to keep your system clean).

You should have zip/unzip capability as part of your base install, so just follow the instructions in the wiki, as you suggest.  Once installed, to run it you need to enter the directory where it is and run ./freemind.sh, or else it's probably more convenient to create a menu entry that does this  (the command in mine reads  /home/martin/Freemind/freemind.sh).

---

### Post by xamfer on 2006-11-13
*You should have zip/unzip capability as part of your base install, so just follow the instructions in the wiki, as you suggest. Once installed, to run it you need to enter the directory where it is and run ./freemind.sh, or else it's probably more convenient to create a menu entry that does this (the command in mine reads /home/martin/Freemind/freemind.sh).*

Ok, I downloaded the file, created a folder, unzip the file in that created folder ... the what. I don't quite understand how to proceed as above.
Please some help. I am a totally neebe.

Thanks.

---

