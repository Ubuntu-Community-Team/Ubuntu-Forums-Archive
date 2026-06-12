---
title: "firefox + flash = :-/ help me :("
date: 2005-07-24
forum: Apple PPC Users
---

### Post by lycos on 2005-07-24
i am using ubuntu hoary with my mac. :smile: 
after installing mozilla flash plugin; all of the internet browsers such as firefox, mozilla, epiphany are failing in the pages includes flash. :roll: 
they are freezing and i have to start then again them.
i tried to remove and reinstall them but nothing. ](*,)  ](*,) 
the problem couldnt be solved.
please help me :::::::: :-?  :-?  :-?

---

### Post by twowheeler on 2005-07-24
I think we need a little more information.  What versions of the programs you mentioned are installed?  And what sites in particular give the problem?

---

### Post by phibxr on 2005-07-24
> **lycos]i am using ubuntu hoary with my mac. :smile: 
after installing mozilla flash plugin said:**
> (*,)  ](*,) 
the problem couldnt be solved.
please help me :::::::: :-?  :-?  :-?
 There are no stable flash-plugins for PPC+Linux.

Until there are, most flash-based sites will crash your browser.

---

### Post by procdan on 2005-07-24
[QUOTE=phibxr]There are no stable flash-plugins for PPC+Linux.

Until there are, most flash-based sites will crash your browser.[/QUOTE]

- I have to agree. The flash plugs are either painfully slow (although I have a slow machine, too) or buggy. This is due to the lack of an official PPC linux flashplayer from Macromedia. The open source players are (naturally) behind the closed source players from Macromedia.

Sorry we don't have very good news for you. I suppose we should all get more involved in coding/testing the existing flash plugs. Best of luck to you.

---

### Post by lycos on 2005-07-25
thanks guys.. ;-) 
i found a temporary solution for it. :razz: 
i removed the mozilla flash plugin and installed some other one. :| 
everybody has my problem can use it.
the plugin shows some swfs. but not all of them. :? 
at least it doesnt crush anymore. \\:D/ 

you can install it like this;
apt-get install libflash-swfplayer

---

### Post by ninotob on 2005-07-26
[QUOTE=procdan]-..Sorry we don't have very good news for you. I suppose we should all get more involved in coding/testing the existing flash plugs. ...[/QUOTE]

Just my personal opinion, but I see the failure to play flash as a **bonus feature** rather than a limitation.   Get rid of all the flash plugins and things will be way better!  ;-)

---

### Post by lycos on 2005-07-27
that is an idea too :)

---

### Post by lycos on 2005-07-29
with the new mozilla update awailable now, everybody can use mozilla flash plugin smoothly and with no crashing anymore.. :)  \\:D/  \\:D/  \\:D/

---

### Post by phibxr on 2005-07-29
[QUOTE=lycos]with the new mozilla update awailable now, everybody can use mozilla flash plugin smoothly and with no crashing anymore.. :)  \\:D/  \\:D/  \\:D/[/QUOTE]

Wow. Under Ubuntu/PPC? Does anyone have any more information on this subject?

---

### Post by dasaivet on 2005-07-29
...are you saying that I can download the flash player from the macromedia site and run ./flashplayer-installer and it will work??

Or are you talking about something else

cheers

---

### Post by phibxr on 2005-07-29
[QUOTE=dasaivet]...are you saying that I can download the flash player from the macromedia site and run ./flashplayer-installer and it will work??

Or are you talking about something else

cheers[/QUOTE]
```


$ ./flashplayer-installer

ERROR: Your architecture, \'ppc\', is not supported by the
       Macromedia Flash Player installer.
```

---

### Post by dasaivet on 2005-07-30
Yeah exactly... so about which flash plugin is lycos talking about?

---

### Post by lycos on 2005-07-31
i am talking the same mozilla flash plugin.
it hasnt changed. it is the same one.
it was crashing before. maybe because of the mozilla firefox.

now, having updated mozilla firefox it is working and not crashing. ;-) 
you can use these steps, i guess, remove all the flash plugins.
update mozilla (maybe you should have all repositories).
and install mozilla flash.
that is it... \\:D/

---

### Post by harryc on 2005-07-31
[QUOTE=lycos]i am talking the same mozilla flash plugin.
it hasnt changed. it is the same one.
it was crashing before. maybe because of the mozilla firefox.

now, having updated mozilla firefox it is working and not crashing. ;-) 
you can use these steps, i guess, remove all the flash plugins.
update mozilla (maybe you should have all repositories).
and install mozilla flash.
that is it... \\:D/[/QUOTE]What is the exact name of the package that you installed and how did you install it? The only packages I can see in the Ubuntu repositories are SWF. That is not Macromedia Flash Player.

libflash-mozplugin
GPL Flash (SWF) Library - Mozilla-compatible plugin

libflash-swfplayer
GPL Flash (SWF) Library - stand-alone player

---

### Post by lycos on 2005-07-31
ok guys  :-? 
my mozilla is;
Mozilla/5.0 (X11; U; Linux ppc; tr-TR; rv:1.7.10) Gecko/20050725 Firefox/1.0.6 (Ubuntu package 1.0.6).
i hope yours are as new as mine.
if not, then, update your repositories and, please install the mozilla updates.  ;-) 
there is nothing wrong with your swf players :)
we are talking the same plugin: libflash-mozplugin  :-) 
maybe, if you have other flash plugins, you may need remove them.
that is it  :roll:

---

### Post by harryc on 2005-07-31
[QUOTE=lycos]we are talking the same plugin: libflash-mozplugin  :-) 
maybe, if you have other flash plugins, you may need remove them.
that is it  :roll:[/QUOTE]Yeah that's what I thought you were talking about. Most folks have been able to use that SWF plugin all along TTBOMK. That's why I got excited when you said flash now works, I thought you were talking about the Macromedia Flash Player. Anyway, there's really only one site I go to that needs flash and it locks up here with the libflash-mozplugin installed. Lycos, maybe you can try this site and let me know if it works for you...

[http://www.pcper.com](http://www.pcper.com)

---

### Post by lycos on 2005-07-31
[QUOTE=harryc]Yeah that's what I thought you were talking about. Most folks have been able to use that SWF plugin all along TTBOMK. That's why I got excited when you said flash now works, I thought you were talking about the Macromedia Flash Player. Anyway, there's really only one site I go to that needs flash and it locks up here with the libflash-mozplugin installed. Lycos, maybe you can try this site and let me know if it works for you...

[http://www.pcper.com](http://www.pcper.com)[/QUOTE]

wow harryc you are so fast :)
i would add the pics of flash pages after printscreening them..

whatever, first i am writing them here,
[http://www.mezunbul.com/111.png](http://www.mezunbul.com/111.png)
[http://www.mezunbul.com/222.png](http://www.mezunbul.com/222.png)

---

### Post by harryc on 2005-07-31
[QUOTE=lycos]wow harryc you are so fast :)
i would add the pics of flash pages after printscreening them..

whatever, first i am writing them here,
[http://www.geocities.com/saimaktay/111.png](http://www.geocities.com/saimaktay/111.png)
[http://www.geocities.com/saimaktay/222.png](http://www.geocities.com/saimaktay/222.png)[/QUOTE]Nice, I'm glad it works for you. Can you try this site?

[http://www.pcper.com](http://www.pcper.com)

---

### Post by lycos on 2005-07-31
[QUOTE=harryc]Nice, I'm glad it works for you. Can you try this site?

[http://www.pcper.com](http://www.pcper.com)[/QUOTE]

sorry  harryc, i searched the web site but couldnt find any  page includes flash :(
can you give me a spesific page address?

---

### Post by hoyd on 2007-01-03
sign this petition to get macromedia wake up for linux/ppc users:
[http://www.petitiononline.com/fla4lppc/petition.html](http://www.petitiononline.com/fla4lppc/petition.html)

---

