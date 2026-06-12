---
title: "help, i'm goin' crazy"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by tommy_the_untouchable on 2007-02-09
i have istalled eciadsl package...
when i type the password in the textual configuration, it says that an unexpected error has occured...
the i confirm the password...and it says that the password doesn't match...every time...and it continues asking me the pw...
please reply!:(

---

### Post by shareMenaPeace on 2007-02-09
Hi,
first of i guess you just installed ubuntu?

Which version?
And did you tried to connect with the gnome ppoe tool?

Infos howto setup pppoe
```

Select the "?" icon on top of the Desktop panel, to start the Ubuntu Help Centre
Select Working with your desktop
Select Internet
Select Connecting to the Internet
Select ADSL Connections
```

Read this if you stuck post again, also my provider dont need a password (try blank).

Cheers

---

### Post by tommy_the_untouchable on 2007-02-09
well...
i've already installes pppoe packages...
now, i tried to start the visual configuration...it works...but when i create the .bin file another error tells me there's an "unexpected (", i think line 41, of eciadsl configuration file...

i've just installed the edgy version...
tnx for now...reply soon

---

### Post by shareMenaPeace on 2007-02-09
Looks liek a typo in the config file. Checlk line 41 for.

To find the config search it from the terminalk with

```
locate filename
``` 
 
or 
```

whereis filename
```

to open it 

```
gksudo gedit /path/to/file.conf
```

---

### Post by shareMenaPeace on 2007-02-09
Normaly to setup pppoe in edgy you just type

```
pppoeconf 

```
and follow the GUI there....

---

### Post by tommy_the_untouchable on 2007-02-09
so, the error after tryin' to do the .bin file says...

**eciadsl.makeconfig didn't update your files.**
[B]
/usr/bin/eciadsl-makeconfig : 41 : Syntax error: "( unexpected[/B]


but i can't find nothing wrong in the syntax...

](*,)

---

### Post by shareMenaPeace on 2007-02-09
What kind of modem you have?

USB, wireless or cable?

Can you try to setup your pppoe with 

```
pppoeconf


```
from terminal?

---

### Post by tommy_the_untouchable on 2007-02-09
D-Link DSL 200 USB Modem...i think 2nd generation...it's supported by eciadsl...

---

### Post by shareMenaPeace on 2007-02-09
Hi please read this thread 
[http://ubuntuforums.org/showthread.php?t=64127&highlight=D-Link+DSL+200+USB+Modem](http://ubuntuforums.org/showthread.php?t=64127&highlight=D-Link+DSL+200+USB+Modem)

---

### Post by tommy_the_untouchable on 2007-02-09
i tryed with pppoeconf as you told me...it says i've no ethernet cards and i cant'go on...

i downloaded the previous version of eciadsl but there's still the same error...

and i can't understand why my password doesn't match in the text mode...

---

### Post by shareMenaPeace on 2007-02-09
Ok make sure the password is correct entred (case sensitive as everything in linux is case sensitive to type).

Please recheck if you correctly installed ecdiadsl and that you have the working drivers.

Read this 
[http://users.tpg.com.au/johnd/dsl200.html#basic-installation-and-configuration](http://users.tpg.com.au/johnd/dsl200.html#basic-installation-and-configuration)

Than if all is ok regarding this open the conf file and check line "41".

---

### Post by tommy_the_untouchable on 2007-02-09
ok...i solved my previous problems...now i extracted the synch .bin files in the /etc/eciadsl directory...
then i type eciadsl-start...but step #2 tells me the firmware couldn't be loaded...and i can't go on...
i tried typin' eciadsl-probe-device and the modem seems to be recognised...

i think it doesn't depend on the synch file i loaded, 'cause the firmware step comes before...

what can i do?
i've read on other posts i have to disconnect and recnnect the modem...but...i do't understand...


pls help!

---

### Post by vithan_hunt on 2007-04-21
I'm totally new to this forum. I guess your old problem should be due to the fact that eciadsl requires bash in spite of dash. So I found here on some forums a modified version which works for ubuntu edgy too. Here's the link:
[ http://ubuntuforums.org/attachment.php?attachmentid=16721&d=1159812308]("http://ubuntuforums.org/attachment.php?attachmentid=16721&d=1159812308"). (thanks damidalla)

Now it works for me too, in the sense that all programs of eciadsl start, but it still can't synchronize my modem (a nortek jetADSL 2021) :(  Does anyone know how to build/find a correct synch.bin file? The one they suggest for globespan chipset based modem seems not to work...

---

