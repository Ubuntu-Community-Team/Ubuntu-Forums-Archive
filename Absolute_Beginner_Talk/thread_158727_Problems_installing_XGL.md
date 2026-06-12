---
title: "Problems installing XGL"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by ubunutu_it_is on 2006-04-11
Hi.
I need some help here.
I've been following this tutorial
[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)
and i made it work untill the system restarts and it says that my settings for x-server (or something like that) isnt right and that i should change those.
To make Ubunutu work i have to uninstall glx....
any clue?

---

### Post by nalmeth on 2006-04-11
If you have to uninstall glx specifically then that may be the source of your problem. Is your card supported? Are you actually using dapper? 
Sorry to ask these simple questions but you didn't give us much info.
I know you can install XGL in breezy somehow, but this is a guide for dapper.
The dapper development forum would be the best place to ask for help if you are using dapper.

---

### Post by ubunutu_it_is on 2006-04-11
[QUOTE=nalmeth]If you have to uninstall glx specifically then that may be the source of your problem. Is your card supported? Are you actually using dapper? 
Sorry to ask these simple questions but you didn't give us much info.
I know you can install XGL in breezy somehow, but this is a guide for dapper.
The dapper development forum would be the best place to ask for help if you are using dapper.[/QUOTE]
exactlly what is a drapper?
Sorry beeing such a newbie but i didnt got ubuntu installed since yesterday.
btw where can I check which card im using becouse i cant remember that stuff. :/
thanks for ur answer!

---

### Post by gord on 2006-04-11
'dapper' is a reference to 'dapper drake', which is the codename for the next version of ubuntu, but it is very much still in development (not slated for release until july), you can install it now but its not recomened for people new to ubuntu.

it is rather hard to get XGL working in breezy (breezy badger, the codename for the current version) but its a... breeze to get it running in dapper :) id advise waiting a few months for dapper drake to come out.

---

### Post by ubunutu_it_is on 2006-04-11
OK thx for ur answer.
Than im currently using brezy badger (spelling?).
Just to ad, the glx works fine with karora through a live cd.
But ill try to install glx once again and beeing more specific.

---

### Post by ubunutu_it_is on 2006-04-11
So..
I've tried again
and it still says that its probably the settings of my x-server that is wrong.
When i want to look closer to the prob. it says that it couldn't open a file called RGB_BG..
Anyone that has got a clue, maby?

---

### Post by nalmeth on 2006-04-11
Yeah sorry if I wasn't clear.
Dapper Drake is the next release, and the guide you are following for XGL is for dapper not breezy. This must be the source of the problem.
I use Dapper on both my laptop and desktop, and it's gotten quite stable. If you really just want XGL I would just install Dapper Drake Flight 6 and go from there. You can even install it along Breezy Badger.
I don't know where to find the proper XGL guide for Breezy, but use the search function here in the forums and I think you'll find some info

---

### Post by ubunutu_it_is on 2006-04-11
okey scince im already exploring the Linux world I've decided to install drake :)
Any clue where to get started?

---

### Post by nalmeth on 2006-04-11
start here:
[ubuntu]("http://cdimage.ubuntu.com/releases/dapper/flight-6/")
[kubuntu]("http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/")

installing XGL is a little different with kubuntu, but far as I know it can still be done.
Frequent the Dapper Development Release subforum for news help and howtos

---

### Post by ubunutu_it_is on 2006-04-11
just a quick question do I have to burn the image file when the download is comple or how should it be done?
Like can I install it directly from breezy badger?

---

### Post by nalmeth on 2006-04-11
Actually you can, but I have found better results with fresh install.
To upgrade from within dapper, go:
sudo gedit /etc/apt/sources.list
and change EVERY instance of breezy to dapper
comment out any extra repositories you might have added by putting a ## at the start of the line.
i.e.
       This line is active
##  This line is commented out.

When you have done this, save the file, and in the terminal type
sudo apt-get update 
sudo apt-get upgrade

since you have made some changes, and possibly run automatix for firefox 1.5 and other packages, I would recommend downloading the image, burning it, and doing a fresh install.

---

### Post by ubunutu_it_is on 2006-04-11
so thw download is complete.
Now with which appication should i burn it.
I can't find anyone in the Program's menu so I have to dl one from synaptic I guess, but which one?

---

### Post by nalmeth on 2006-04-11
Nautilus can do it for you. Just browse to where you saved it, right click on it, and click "write to disc"
Good luck with dapper.
Gnome default interface will look the same (except for new theme, must say it's grown on me. I hated it at first), but you will notice differences as you use it.
The kubuntu default interface is very pretty now, if that's what you went with.

---

### Post by ubunutu_it_is on 2006-04-11
Should i just right click on the ISO-file and than chose burn to CD.
Will it burn the ISO image or the containings of the ISO image.
Becouse im running out of cd's  I only have a few left.

---

### Post by Mustard on 2006-04-11
You might have more luck if you installed an application that specifically supports burning images to CD.  Some examples of these applications are k3b and Gnomebaker.  These are available from the repositories and can be installed via the Synaptic Package Manager.

I know for certain that Gnomebaker has a 'Burn CD Image' option on the toolbar.  You should try to burn the CD's at the slowest rate possible to ensure that it does so as accurately as possible.  You should also use the md5sum checker to check the ISO you downloaded to make sure its not corrupted **before** you attempt to burn the image to a CD.

```
man md5sum
#entering the above command in the terminal will show you
#the manual for the md5sum command
```

Press 'q' to exit the manual.

---

### Post by nalmeth on 2006-04-11
No worries it will properly burn the image to disk.
I see why you might have some doubts, because it doesn't really assure that its going to perform that operation, but I use it all the time, even for burning DVD iso's.
EDIT:
Like mustard said, k3b and gnomebaker might be more reassuring for you, I personally love k3b, and it works well in gnome.
Too many options sometimes huh?

---

### Post by ubunutu_it_is on 2006-04-11
okay, well than.
I've downloaded and installed k3b :d
I chooesed to install a dvd-image file.which ofcorusely 
I chooesed the file.
But than in the option bar
it doesn't find any burning device...
any clue what i should do?

---

### Post by nalmeth on 2006-04-11
you can get k3b to work, but since you're likely just going to write over it with dapper, it's not worth it. Just install gnomebaker, or do the right-click nautilus trick.
Did you say you got a DVD-image??
The regular CD-image is quite fine unless DVD's are all you have.

---

### Post by Mustard on 2006-04-11
[QUOTE=ubunutu_it_is]okay, well than.
I've downloaded and installed k3b :d
I chooesed to install a dvd-image file.which ofcorusely 
I chooesed the file.
But than in the option bar
it doesn't find any burning device...
any clue what i should do?[/QUOTE]

Well, the most obvious question that needs to be asked up front is, do you have a DVD burner?

---

### Post by ubunutu_it_is on 2006-04-11
okay, folks.
I've succefully installed ubunutu drapper drake (cheers)
And I have been following the guide to install XGL (the one I posted before) this time no error messages showed up but like wtf i can't c any change?
like i tried to use the commands for eg. Ctrl + Alt and left mouse but that didnt work .. :/
Do I have to activate it or something, if yes, how?

---

### Post by ubunutu_it_is on 2006-04-12
Check next replay please.

---

### Post by ubunutu_it_is on 2006-04-12
Ok i've tried to sort things out....
Im currently following this guide
[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)
And I'm in the 3 step;
3#

Log in, then in a terminal start compiz and the Gnome window decorator (do NOT use sudo here)

[PHP]compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher[/PHP]

[PHP]nohup gnome-window-decorator &[/PHP]

As I write:
$ compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher
In the terminal i get this errormessage:

x@x:~$ compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher
bash: compiz: command not found

---

