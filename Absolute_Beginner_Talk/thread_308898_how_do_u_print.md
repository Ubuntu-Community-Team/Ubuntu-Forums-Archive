---
title: "how do u print?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-11-28
i make a doc in abiword processor, i click print, i click ok, it does nothing. how do i print something?

o, this is on xubuntu dapper

---

### Post by taurus on 2006-11-28
Does your printer work in Ubuntu?  Can you print to it at all with firefox or other apps?

---

### Post by tripwire on 2006-11-28
you might want to use the System>Administration>Printer tool
it's quit obvious how to install a printer through this and once you have installed the right driver for you're printer it works perfectly.

---

### Post by taurus on 2006-11-28
> **tripwire said:**
> you might want to use the System>Administration>Printer tool
it's quit obvious how to install a printer through this and once you have installed the right driver for you're printer it works perfectly.
But that's for Gnome while he runs XFce4!

---

### Post by Cardmaster91 on 2006-11-28
im using my parents computer right now, i have installed xubuntu on it, and anything i try to print in doesnt work. it goes all the way up to the print properties screen, then i click ok, and nothing happens. idk if the printer is installed or not. but when i tried to print firefox, it says

Printer Name: postscript/default

i have no idea wat that means, but the printer is an hp photsmart 2610 all-in-one


my parents are threatining to go bak to windows,(lol)
but seriously, i need to print on this comp.

---

### Post by Cardmaster91 on 2006-11-28
> **tripwire said:**
> you might want to use the System>Administration>Printer tool
it's quit obvious how to install a printer through this and once you have installed the right driver for you're printer it works perfectly.

ya, um...

i have one menu, apps
and no administration


but in settings, i have printing sytem settings, it has two options on the left, none and CUPS
i dont rlly know wat they mean, although i have tried both

---

### Post by tripwire on 2006-11-28
ok here is a solution since it doen't seems that a printer is installed (ubuntu doesn't do this by default) go to the printer configuration tool. Click on new printer and folow the steps written there. Porbably you will get there then. 
That did it for me and I'm using a network Laserjet 1012 so it should 9/10 work for you.

---

### Post by tripwire on 2006-11-28
in xubuntu it is a like ubuntu, just look for it under apps>administration or just plain apps> for a couple of minutes you'll find it for sure. the printer tool, and just look for an icon or a menu that says add a printer

---

### Post by tripwire on 2006-11-28
> **taurus said:**
> But that's for Gnome while he runs XFce4!
sorry about that, it isn't that different in xfce imho.

---

### Post by Cardmaster91 on 2006-11-28
xubuntu is like ubuntu, but the interface is quite different, the only printer tool i have are printer configuration settings. and that no where has add printer

---

### Post by taurus on 2006-11-28
Can you take a snapshot of that screen?

---

### Post by tripwire on 2006-11-28
well I can't use xfce at the moment but you might wanna try the web-interface of you're printer configuration (9/10 it is cups) by entering this following url into you're favorite browser:
[http://localhost:631/admin](http://localhost:631/admin)
I tried it on ubuntu and it worked fine, hope the same for you.

---

### Post by Cardmaster91 on 2006-11-28
[IMG]http://i130.photobucket.com/albums/p270/cardmaster91/Untitled.png[/IMG]

this is the only printing option i have in apps mennu

---

### Post by tripwire on 2006-11-28
if you wan't to do it through fxce rather than the web-interface i guess you should look under system...but not sure..

---

### Post by taurus on 2006-11-28
And have you tried the suggestion by tripwire, [http://localhost:631/admin](http://localhost:631/admin) from a web browser?

---

### Post by Cardmaster91 on 2006-11-28
[IMG]http://i130.photobucket.com/albums/p270/cardmaster91/Untitled3.png[/IMG]

there is nothing that has to do with printers in sytem, if there is, idk wich one it is

---

### Post by tripwire on 2006-11-28
ok, sorry has been some time since i last worked with xubuntu, try the other option with the following url: [http://localhost:631/admin](http://localhost:631/admin)
It should work fine..

---

### Post by Cardmaster91 on 2006-11-28
> **tripwire said:**
> well I can't use xfce at the moment but you might wanna try the web-interface of you're printer configuration (9/10 it is cups) by entering this following url into you're favorite browser:
[http://localhost:631/admin](http://localhost:631/admin)
I tried it on ubuntu and it worked fine, hope the same for you.

ok, ive got to the part where i select it from a big list, and clickd add. it prompts me for CUPS username and password. at first i thot it wanted me to amke a password, but it just prompted me again. ive tried my username and password for xubuntu, but that dont work. what password do i use?


p.s. 

"entering this following url into you're favorite browser"

your**

---

### Post by tripwire on 2006-11-28
sorry about the spelling mistakes :) (I speak dutch)
try you're username and use the root password(guessing here)
or use root and the root password (still guessing)
sorry, I'm just trying to help out...:)

---

### Post by Cardmaster91 on 2006-11-28
ive tried those, ive tried like every combination of passwords from all users. 


P.s.

Lol, u did it again
"try _you're_ username and use the root password(guessing here)"
just fyi, you're stands for you are, and that doesnt fit with that sentence

---

### Post by minispalla on 2006-11-28
i have a printing problem as well i have a gestetner 5390 and there are no drivers that i caught in the printer drivers for ubuntu 6.10 they do have the dll files for windows that don't work for anything modern (not xp) so is there any possible way i could get this thing to work with my ubuntu 6.10 desktop and i am all out of ideas so if you have anything i could try i will and tell you if it works thanks for your help 

http://www.gestetnerusa.com/Gestetner/gestetner_com.nsf/SupportDrivers?OpenForm&zone=ZIDTDIE-54FRT7GE51&NavExpand=02~Support*and*Drivers^Support*and*Drivers
on the right side on the top its copyprinters and click on 5390 and it should open a window that has the drivers

---

### Post by minispalla on 2006-11-29
can i get some help please

---

### Post by tripwire on 2006-11-29
Ok, now that I am awake again, i have looked on the net for a decent explenation on how you should do it,well here it is:

[LIST]
[*]Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups[/LIST][LIST]
[*] Select the group shadow and click Properties.[/LIST][LIST]
[*] Add the user cupsys to the group.[/LIST][LIST]
[*] Restart CUPS with this command:[/LIST]```
$sudo /etc/init.d/cupsys restart
```
[LIST]
[*] Open a browser and type this in the address bar:[ http://localhost:631]("http://localhost:631/")[/LIST] 
[LIST]
[*] You should then be able to configure the printer.[/LIST][LIST]
[*] You (most likely) will not need to download any driver.If you do take a look here [http://www.linuxprinting.org/](http://www.linuxprinting.org/)[/LIST]good luck with it hope it works out then :)

---

### Post by minispalla on 2006-11-29
it configured all the other printers on the network but i can't find driver support for the Gestetner CopyPrinter 5390 anywhere at all if maybe you know other places to look that would be much apreciated and also i have publisher files from my windows install and do you know what that would run natively on linux i tried open office and i have no idea what template to use if you have any ideas that would also be much apreciated thank you very much

---

### Post by carlosqueso on 2006-11-29
@Cardmaster:

You'll find it much easier if you install gnome-cups-manager and just run it from the "run program" dialog box.  You should then be able to add a printer with no problem.  XFCE's print management is more than crappy.

@minispalla:

That seems to be a new printer, but that brand seems to work with the generic PostScript drivers according to linuxprinting.org, try using one of them.

---

### Post by Cardmaster91 on 2006-12-23
my printing problems were solved for that ciomputer, thank you. but now i have new printing problems on MY computer running ubuntu edgy. I've tried the cups thing, but it don't work. so then i tried that link, it took my usr name and pass, but then returned this error message
" 	

Error:

    Unable to copy PPD file!

"


so, wat i do now?

---

