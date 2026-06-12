---
title: "got Broadcom working....kind of"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by tentel on 2008-02-05
I finally managed to use fwcutter with my bcm94311 network adapter.

I enabled the firmware with the restricted drivers manager, and the little light on my laptop that signifies my card is on lit up.

but i still couldn't get a connection.

and then my computer completely froze.


after a hard restart, the little light on my laptop was no longer on, but the restricted drivers manager still said the firmware was enabled.

i have no idea what to do next.


could sombody point me in the right direction?




thanks

-Tim

---

### Post by (((X))) on 2008-02-05
at the terminal:
$ lsmod
and see if there are drivers loaded for your card.

try also
$ sudo iwlist scanning
this will tell you card is recogized or not

---

### Post by tentel on 2008-02-05
hmmm

when i type in lsmod, i get a long list of items, but nothing that looks even remotely close to anyting bcm related.

i wish i could copy and paste the info, but i'm dual booting, so i obviously copy and paste doesn't work accross OSs.


when i type in sudo iwlist scanning, it tells me "interface doesn't support scanning"

when i type in the same command but omict "scanning"

i get a long list of items that each begin with [interface], but nothing that seems broadcom related.



i've been thinking though...

everytime i try to use fwcutter, i run onto a constant stream of problems.
and everywhere i look, ndiswrapper is recommended over fwcutter.

and i have no problem finding excellent tutorials on how to use ndiswrapper, however, everyone of them assumes you can find some windows drivers.

i've had no problem finding drivers, heck, if i go to the hp site, it automatically detects my laptop model and gives me links to all the drivers i'll need for xp or vista, 32 or 64 bit.


only, they are all .exe files, so whenever i see them, it think "nope, i need .inf".


am i being incredibly stupid?
are .exes what i need, and it is just so basic that it is never mentioned?

---

### Post by tentel on 2008-02-05
Also, i was just wondering, why do i have to use xp drivers, and not vista drivers?

---

### Post by jan quark on 2008-02-05
you need only the bcmwl5.inf and sys file I can upload them and give you the link 

But I am myself fighting with the bcm 4311 fwcutter method so I dont know how long my internet connection will be active:)

---

### Post by jan quark on 2008-02-05
here

you actually need only the inf file
[http://www.doggyupload.com/file_info.php?file_id=445](http://www.doggyupload.com/file_info.php?file_id=445)

---

### Post by (((X))) on 2008-02-05
> **tentel said:**
> hmmm

when i type in lsmod, i get a long list of items, but nothing that looks even remotely close to anyting bcm related.

i wish i could copy and paste the info, but i'm dual booting, so i obviously copy and paste doesn't work accross OSs.


when i type in sudo iwlist scanning, it tells me "interface doesn't support scanning"

when i type in the same command but omict "scanning"

i get a long list of items that each begin with [interface], but nothing that seems broadcom related.



i've been thinking though...

everytime i try to use fwcutter, i run onto a constant stream of problems.
and everywhere i look, ndiswrapper is recommended over fwcutter.

and i have no problem finding excellent tutorials on how to use ndiswrapper, however, everyone of them assumes you can find some windows drivers.

i've had no problem finding drivers, heck, if i go to the hp site, it automatically detects my laptop model and gives me links to all the drivers i'll need for xp or vista, 32 or 64 bit.


only, they are all .exe files, so whenever i see them, it think "nope, i need .inf".


am i being incredibly stupid?
are .exes what i need, and it is just so basic that it is never mentioned?

Ok, you have to  extract .exe with following command:
unzip -a driver.exe
Then .inf should be in the directory you extracted the executable.

---

### Post by tentel on 2008-02-05
> **jan quark said:**
> here

you actually need only the inf file
[http://www.doggyupload.com/file_info.php?file_id=445](http://www.doggyupload.com/file_info.php?file_id=445)


Hmm..

at first, it could get to the page, but the download button was dead.

and now the link seems to be dead.


> enter command
unzip -a driver.exe

i put that in, replacing "driver" with "sp36542"

then i tried unzip -a /home/tim/desktop/sp36542.exe

it gave me a bunch of info, but didn't seem to do anything.

also, i do not have the ndisgtk package in the synaptics package manager.
i had my computer hardwired to the interent earlier and i updated, but it still isn't there.


thanks
-tim

---

### Post by tentel on 2008-02-06
I managed to open the link to the file, and it gave me a huge list of code which I'm assuming is the.inf file.

but now what?

do i copy and paste the text onto a file on my desktop?

sorry, I'm still really new at this.



actually, never mind.
i figured it out.

---

